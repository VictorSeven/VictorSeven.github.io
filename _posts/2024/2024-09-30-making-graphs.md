---
layout: post
title:  "Paper-ready figures with Python and Julia"
date:   2024-09-30 13:00:00 -0500

tags: research publication visualization

summary: "How to do nice graphs for your papers"

tipo: post
head_image: "/images/2024/gaussian.png"
---

During the last year, I have been trying to improve the way I make graphs for scientific publications.  When I was a PhD student, I felt quite frustrated with the graph-making process. It was slow, painful and there were many details that I had to manually adjust with Inkscape. This meant that for any change a posteriori (and there would be _many_)  I had to reopen the figure and edit it again. 

Hence, in the last years I have been slowly developing helper scripts and a more mature workflow to make figures better and faster. I will share with you how I do it. There are for sure better ways, and different situations demand different workflows, but I guess this post might be useful to many, in particular to people working on their paper figures for the first time.

I mostly use Python, but lately I have been migrating to Julia. Fortunately, the workflow is kinda language-independent. For most of the post, I will write examples in Python (as it's more common) and then I will dedicate some space to particular perks of Julia.


## Get your measures right!

For many years, I was just exporting the figures and then scaling down in LaTeX. But then also the font size decreases, and one needs to start increasing it in Matplotlib to compensate. Usually, text rescaling will necessarily lead to moving other elements around. Setting the correct target figure size from the very beginning elegantly solves this problem. Then what you see from the code is _exactly_ what you'll get in the paper. 

In Matplotlib, this is done through the `figsize` argument in `plt.figure`.  In Matplotlib 3.9.0, the default size is 6.4x4.8 inches. In centimetres, this is 16.3x12.2 cm. However, the usual A4 sheet is 21x29 cm, while the US Letter is 21.6x27.9. Now, even considering margins and all, a two-column figure will be 18 or 19cm. Most panels should be around 5-6 cm in height. Matplotlib's default plot size is too tall and has an undesirable aspect ratio for most graphs. 

How to know which are the correct measures? In LaTeX, you can always get the column width with `\the\columnwidth` for a single column and `\the\textwidth` for two columns. The measure is given in `pt`, or points. Makie.jl measures directly with this unit, and you can use the number given by LaTeX right away. For Matplotlib one needs to convert to inches. Observe that `\textwidth` is not just twice `\columnwidth`, because of margins, intracolumn space, etc.  Also, note that LaTeX allows one to plot placeholder figures with `\includegraphics[width=\textwidth, height=3cm]{example-image-a}` so you can check how big the graphs are even before going to your plotting software.

If you are aiming for a poster presentation, most graphical design software will tell you the physical dimensions of the figures. In Inkscape, you can just draw a rectangle in the place where your figure will be, see its dimensions, and pass this directly to `figsize`. In Scribus (which I prefer for posters) is the same. Draw your placeholder and measure it!

For slideshow programs, like PowerPoint, can get slightly trickier, as we're going to see in a second.

## Exporting the image (some trickery with sizes...)

First of all, you should be always saving in a vector format (SVG, PDF), which can be zoomed in and out without losing resolution, unless you have a good reason to use a bitmap one (like PNG). If you have, e.g. many scatter points, you could try always to rasterize the points and leave the axes in vector format. Functions such as `plt.scatter` support this.

Now, an important thing is that if you are working in a Jupyter Notebook: if you set the `figsize` to a reasonable value,  you' ll notice that the figures look very small in the notebook. The notebook is web-based, so to display the image inside the notebook it _always_ generates a PNG figure. A small trick to see a larger image in the notebook while keeping your vector's format size fixed is just change the `dpi` keyword. Thus, you have `plt.figure(figsize=yoursize, dpi=200)` the images will be very well visible without affecting your export settings.

Notice, however, that there are contexts where dpi matters, like graphs with rasterized content. Another potential trouble is slideshows. Although all presentation software now supports vector formats, we might want to add animations/videos. If you need to export to PNG or video, the dpi changes the figure size. In this case, be sure to match not only the width and height, but the target DPI of the software/media. For example, PowerPoint slides are 10x7.5 inches at 96 dpi. LibreOffice Impress has slightly different values. You can set a `dpi` value also in `plt.savefig` in order to have a different resolution for the exported values and inside the Jupyter notebook. 

Again, Makie.jl is more explicit than Matplotlib, and even has [a dedicated tutorial to get resolutions right](https://docs.makie.org/stable/tutorials/aspect-tutorial). 

## Format the axes

By default, both Matplotlib and Makie.jl plot the figure inside a "rectangle". However, I feel that the figures look better when the top and right lines are missing. In Matplotlib, you can disable the spines with `axis.spines['right'].set_visible(False)`. Do the same for the `top` spine and you are good to go. 

I also like to play around with the tick and axes size to something more to my liking. The easiest way is to use `rcParams` which allow you to set the global aspect of the graph for the current session. Just `import matplotlib as mpl` and then `mpl.rcParams[property]=value`. Some of the properties that I change include `'axes.linewidth'` -the width of the axes line- and `'xtick.major.width'`, `'xtick.major.size'`, and `'xtick.major.pad'`. These control the width, length and padding of the major ticks of the X axis. Whatever values you choose should be the same for the Y axis usually. Minor ticks can also be changed.

Other rcParams I like to change are the `'lines.dash_capstyle'` and `'lines.solid_capstile'` to be `'round'`, so the dashed lines and the end of the lines are rounded instead of an ugly rectangle. 

Finally, I do like to have a transparent background color in the axes. This is good even for paper figures because if you use the `plt.figures()` directive allows the subfigures to slightly overlap on each other, saving space. And it is an absolute must for posters and slides, where you might have background color. This can be accomplished by the rcParams `'axes.facecolor'` and `'figure.facecolor'` both to `'#00000000'`. 

If we want to accomplish all this in Makie, one just creates a theme by `paper_theme = Theme(Axis(...))` and fills all the desired properties for the figure and axes. These include `rightspinevisible`, `spinewidth` to set up the axes, `xticksize`, `xminorticksize` and `xticklabelpad` for the the ticks, and finally `backgroundcolor` to `:transparent`. Additionally, I usually set `xgridvisible` to false to turn off the default Makie grid. I find this approach way more clear than the Matplotlib one. To be fair, Matplotlib also has themes --they are called styles-- but one needs to write the rcParams properties to a specific file and I don't like it that much, personally. 


## Style the text

Our next step is the text. Now that the figure size is correct, the font size will be measured in actual points. LaTeX text usually is 10pt or 11pt, and this is a good reference for a font size. Smaller than 8pt is a no-go. If it is the first time you do this, you might think that the correct figsize is very small and text is really cluttered. And you're right: there's not that much space, and legible text has to be put intelligently.

I recommend also changing label, tick and legend font size separately. All of this can be accomplished again with rcParams, in a similar fashion than before, both for Makie.jl and Matplotlib.

The final cherry on top is to use a consistent font for all your graphs. Sans-serifs fonts are perfect for scientific graphs, due to their high readability. I recommend finding a nice sans-serif font you like, installing it and configuring either Python or Julia to use it. For papers, it is Helvetica, a choice inherited from a collaborator. For posters and slides, it is Lato, because I like to write the whole thing in that font and in makes the poster nice and consistent.

## The Legend

Many graphs will have a legend, but I have to say I highly dislike the default one. It takes up a lot of unused space, the handles are small to my taste, and it has a frame which I personally dislike. In Matplotlib, the rcParams I tweak to fix this are `'legend.handlelength'`, `'legend.handleheight'` and `'legend.handletextpad'` to control the size of the handle and its distance to text, respectively. Then, `'legend.labelspacing'` and `'legend.columnspacing'` control the separation between rows and columns. Finally, the frame can be disabled with `'legend.frameon'`. 

In Makie.jl, I do a similar thing. Inside the theme, I would have now `Theme(Axis(...), Legend(...))` where inside `Legend` I set `framevisible` to `false`, control the row/column separation with `rowgap` and `patchlabelgap`, the size with `patchsize`, and I tweak the `backgroundcolor` to be transparent. 

## Some auxiliary functions 

Design-wise, we are set. However, I have some auxiliary functions that help me automatize several tasks. For example, I have auxiliary functions to convert measures from centimetres to inches, so I can measure in centimetres, and default sizes for two-column and one-column widths are stored in the script. In this way, I can just call `style.two_col_fig(height=6)` to get a figure spanning two columns and a height of 6 centimiters. Additionally, I have defined common resolutions for software like Powerpoint. One can then have Matplotlib styles, or custom code, to call paper, poster or slide and re-generate all figures on the spot with the exact correct sizes, including adequate font size.

For the cherry on the cake, I have an auxiliary function to label axes, that writes (a), (b)... over each axis automatically in the position I have defined. Therefore, I only need to call `label_axes(my_axes, positions)` to have all the marks.

## Figure code philosophy

To end the post, I am going to explain more or less what is my approach to generating figures. This is very personal and varies between people, but I like this system because allows me to make changes to figure papers fast. 

The idea is that each figure will be a single script file. The file contains several functions which look like `plot_panel(axis, args)`. The idea is that each function plots a single subplot of your figure. Imagine I want a two-column figure that has 6 subplots. Then, I could do something like 

```python
fig, axes = plt.subplots(nrows=2, ncols=3)
plot_panel_1(axes[0,0])
plot_panel_2(axes[0,1])
plot_panel_3(axes[0,1])
#etc etc 
```

The advantage here is the following. Imagine I did the above code, and then my supervisor tells me that it would be better to do the top row with (i) the first one on the left (ii) the second and third on top of each other, sharing the X axis. Then, I would just change the `plt.subplots()` line to an adequate `plt.subplot_mosaic()` or even a pair of `plt.subfigures()`. In any case, the major advantage is that only the geometry of the figure changes, all the rest is just swapping the arguments to the `plot_panel` figures. 

Of course, small adjustments always have to be made to details, like showing/hiding ticks, text and legend positioning... I tend to have these details outside of the `plot_panel` functions, which are intended only for processing data and getting the meat of the plot. In this way, I can focus 100% on the figure layout without having to move large amounts of code, have problems with undefined variables, or other potential problems.  A typical code I would have looks like 


```python
data = data_analysis_pipeline() #Usually is just np.load(data) + some fast process

#Example mentioned above
fig, axes = plt.subplot_mosaic(
    """
    AAABBB
    AAACCC
    DDEEFF
    """, height_ratios=[0.5, 0.5, 1.])

#Magic
plot_panel_1(axes["A"], data)

plot_panel_2(axes["B"], data)
plot_panel_3(axes["C"], data)

#Do not show the xticks of B, it will share X with C
axes["B"].set_xticks([])

for k in "DEF":
    plot_panel(axes[k], data)
#etc etc 
```

In order to add more flexibility, what I usually do is to wrap this last code into a `plot_paper()` function. Then, I can create a `plot_poster` in which I tweak the necessary details to make a poster-adequate image. Most of the needed changes, like figure and font sizes, will be automatically solved by the code above, but there's always some rogue blank space or label. Or maybe you want to change the layout of your graphs for the poster.

Now, to be honest, I usually prototype the figures a bit on the notebook, where I can iterate very fast, and then 'freeze' the final result in the script, which I think is usually more readable and has fewer problems than the notebook for replicability. 

## Conclusion: an opinionated comparison

I hope you found useful the above post. I just wanted to share my workflow on customizing the aspect of my graphs and how to have them publication-ready, not only for papers, but for other uses, minimizing the amount of code changes and time to get your desired result. 

Of course, the workshop is not perfect and often I find that my general rule of thumb does not apply very well to the particular project or situation I am in, but there are so many use cases that it's impossible to find a single recipe for all problems. However, I can say I am quite happy with my current workflow. Nowadays I rarely do Inkscape post-tuning of the graphs and I produce and adapt figures for publications way faster than I used to do. 

Also, there are many things I have not covered here, like choosing colormaps for your graphs. There's a lot of info on the internet already on this topic and I'm not an expert. However, I really encourage you to check some packages (For Python I love [Cmasher](https://cmasher.readthedocs.io/index.html) and [MetBrewer](https://github.com/BlakeRMills/MetBrewer)) and lose a bit on time choosing adequate colors. It's totally worth it ~and not procrastination.~

To close the post, I have to say that I am very impressed by the design of Makie.jl. The syntax to plot is more concise than Matplotlib, and it gives [way better control to position panels](https://docs.makie.org/stable/tutorials/layout-tutorial), which is the most difficult part. Finally, the code needed to produce animations and interactive plots is an absolute no-brainer compared to its Python counterpart. I feel that both for quick tests and definitive figures I always need less code. The documentation is very good. The downside is that the amount of info on the internet is not as abundant as with Matplotlib, but Makie is definitely one of the main reasons I am moving more and more into Julia.








  
