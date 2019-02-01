---
layout: post
title:  "Free/Libre software for science"
date:   2018-11-30 20:00:00 -0500

tags: software_libre opinion 

summary: "Science should be made relying on free software -do you know why?"

tipo: tech
head_image: "https://upload.wikimedia.org/wikipedia/commons/thumb/2/22/Heckert_GNU_white.svg/535px-Heckert_GNU_white.svg.png"
---

Maybe you have read this in some other part of the Internet, but it is really a very important thing. Let me state it clearly:

**SCIENCE SHOULD BE MADE RELYING ON FREE SOFTWARE, AS MUCH AS POSSIBLE.**

Dot, there's no more. Here I want to speak about why you really should start using free software, and why we should care about free software projects in science. And also, I would like to talk about some of the myths regarding the use of free software in science. There are many reasons to use it, but let me emphasize two that -under my point of view- are very important. 

_Head image: Aurelio A. Heckert, CC BY-SA 2.0_ 

# One: results should be reproducible.

That means that everybody should be able to take your data, repeat your analysis and see if it was OK or not. That is one of the fundamental concepts in science. Moreover, the interest in experiment replication has grown in the last years (giving rise, for example, to the replication crisis in Psychology). 

Nowadays, a lot of research (both theoretical and experimental) is done through the computer. And since data generation and analysis needs computer code, each day more journals are requesting your code to be _available_. Maybe not publicly available, but at least accesible by _reasonable request to the authors_, as any other experimental data. Of course, I support the idea of code publication whenever possible. However, even when you do not publish your code, it is important that you use free software.

Let me illustrate this situation. I analyse some data using some privative code (for example, MatLab or IDL). This code relies on computations and packages made by other people, that are _black-boxes_. That means that the user cannot access to the code used by this applications. What if the black-box code has errors? Of course, enterprises check very carefully their code, but this does not mean that it is 100% error-free. Also, free libraries are not free of errors -but you can go inside of the code, see what it does, and see if something is wrong. And if you know, you may even fix it by yourself. 

It's more, you can download _any_ old version of free software, allowing you to compare codes written years ago, using exactly the same ecosystem of tools the original authors had, and check all the source code. Privative software usually don't allow you to download older versions, which could be a big problem for reproducibility. Finally, if you wrote your code on a privative environment, people who does not own this environment cannot run your code -which may be important to fully replicate your analysis. 

# Two: funding!

Another one of the key aspects of science is that everybody should be able to do it. No matter in which University you are, if you want to obtain results you need professional tools. It is often said that free software is-not-so-good, so privative must be used instead. In most cases, this is not true (I talk about it below). I have seen some little Universities and Departments spending a lot of money in privative licenses for their researchers and students. I understand it is a way to say, "we offer all these expensive things so our students learn the _industry-standard_ stuff". Not giving this software is like assuming your University is broken, so your researchers are bad and your students are going to use trashy stuff from the nineties.

This is very far from reality. Software licenses are expensive, and we are talking up to thousands or dozens of thousands of dollars, yearly. Why wasting 10.000$ each year in a package that does something that Python can do? Why not using all that nice money to contract one PhD student, or to renew the experimental setup? Maybe if you read this from a big departament or research group you say "Ok, 10.000$/year is not so much, we used this software for 20 years and we feel comfortable using it". Maybe for you is not critical, but it really is in many development countries, small Universities and similar. And since everybody speaks so well of privative software, they think they _need_ it to be like you -and actually, they are wasting the money they _really_ need in other stuff. 

# And now, let's talk about some stuff

## The idea is cool, but free software is trashy

Many people think that privative software is better. And since it is better, we must use it to do quality research. I'll be clear about this point: I don't think so.

On a side, for expensive computations, most of the linear-algebra-hard-work was done in Fortran/C, a long time ago. Many scientific packages are actually encapsulations of super-fast C/Fortran libraries, or are based on them. For example, [Matlab uses Lapack for some matrix computations](https://es.mathworks.com/company/newsletters/articles/matlab-incorporates-lapack.html). NumPy/SciPy use exactly the same Lapack functions. That means that I would not expect a huge difference between Matlab and Python functions that call the same Lapack code. 

"Ok, but a monster like Matlab for sure has more than Lapack calls". Yeah, for sure. Also does Python. Each day there is more and more specialized free-software packages targetting more and more specific tasks -and their efficiency is also improving. Of course, it may turn out that for _some tasks_ Matlab is faster than Python, or even way faster than Python. But think twice: do you have to do that task? Or does it really make a difference in computation time?

## But I rely a lot on support!

Software is used by a lot of people with different backgrounds, and they may need assistance. Some people like to have the possibility to contact the support team and receive help.

This is also compatible with free software. In fact, it is one of the standard ways of making profits from free software: you can pay to have additional support. Unfortunately, I have not seen this practice widely in academic packages (a nice counterexample is [Anaconda's](https://www.anaconda.com/what-is-anaconda/) Python distribution). However, you still have a lot of forums and the community supporting this software; the community is usually very nice and tends to answer all different questions and problems, providing support when you get stuck.

## I'm on that _specific task_ that free software is not got at

Well, what can I say... Bad luck. However, have always an eye on the libre community, because people start new project each day. Until now, the only software I found that cannot be substituted easily is _Mathematica_ (although the people at SymPy and SAGE did a impressive improvement, which I check yearly).

There are several solutions in the lon gterm. First, you could consider participating actively in the software development. If you are a big group you may be interested to hire a computer scientist in order to create the free libraries yourself. If you develop good code you can attract more people to your package, get citations (since yes, this is also publishable in computer science journals!), and improve the overall image of your lab -if everybody uses _your_ libs, then everybody _knows you_. You may even contact your Computer Science department, because maybe some of the PhD students or researchers there are interested in developing such frameworks! 

And remember: all projects start tiny and then start growing. It is normal that a 3-years old software is not able to do what your 20-years old software does -but this will change at some point. And as it grows and gets new users, it grows faster. You could also help by using it for some basic stuff and leaving issues and feedback to the developers!













