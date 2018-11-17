---
layout: post
title:  "[RESEARCH] Limited role of space in emergent trade-offs"
date:   2018-10-05 20:00:00 -0500

tags: my-research evo-bio soc complex-systems

summary: "Discovered two different, self-regulartory mechanisms in host-pathogen system."

tipo: tech
head_image: "/images/2018/limitedrole.jpg"
---

To inaugurate the technical section of the blog -nothing better to start speaking about my own work. In particular, about my first published article, [Limited role of spatial self-structuring in emergent trade-offs during pathogen evolution](https://doi.org/10.1038/s41598-018-30945-1). 

> Image: (up) Patterns displayed by the system for different values of the base reproductive number $R_0$. (down,left) Evolutionary trajectories in no-diffusion case. (down, right) Results from analytical approximation. From the article in Scientific Reports.

## Pathongens, hosts and trade-offs

In the last years, scientists have put a lot of effort to understand dynamics of epidemic processes. The final goal of this kind of models is to have an epidemic forecast, maybe similar to the weather forecast -but for diseases. I'm pretty sure I do not have to convince you why this is important. 

However, even when data-driven compartamental models are really sucessfull, we still have a lot of open questions. One of these aspects is the evolutionary behaviour of the strains. This is very important: knowing something about how virus evolve could tell us better ways of facing epidemies.

So, the first question is: what are the features selected by evolution in current pathogens? It turns out that many of them follow a trade-off between transmissivity (how fast they can infect hosts) and virulence (capacity to kill the host). Most strains are not both very transmissive and very virulent: if you have one characteristic, you have to give up on the other. (Of course, there is a lot notable exceptions to this). The actual consequence of this is viral strains that have an intermediate value of the basic reproductive number, $R_0$, which controls many aspect of the epidemiological behaviour of the strain.
Biologist have been struggling with this question during a lot of time: what is the origin of this trade-off between this two features? The answer is complicated, due to technical reasons (Alizon, 2009). Despite of this, there is a growing evidence that the origin of the trade-off is not physiological, but arises from collective interactions in spatially extended parasite-host system. Some examples are (Alizon, 2008), (Sasaki, 2000) or (Lion, 2015).

The idea is that spatially extended population of hosts can force selection of intermediate values of the basic reproductive number $R_0$, meaning that spatial structure makes parasites more or less mild. So our original question was: how does diffusion of hosts affect the system? We have clear in the large diffusion limit, we have to recover the classical mean-field result by Robert May, that indicates that strains should evolve simply increasing their $R_0$ until infinity. So, are systems with limited amount of diffusion stable?

## The Model

The model we use is taken from (Ballegooijen, 2004). It is a modified SIRS-model where we have hosts in an 8-neighbour lattice. Hosts cannot die. Virulence of infection is measured through the time $\tau_I$ that the host remain infected. Both $\tau_I$ and the transmissivity $\beta$ of each strain mutate at a rate $\mu$. They do it in a purely independent way -so _in principle_ there is no trade-off.

As the original authors demonstrated, the result of evolution running in this model is a trade-off, i.e. a function $\tau_I=\tau_I(\beta)$ that relates both parameters. Moreover, it goes to a fixed value of $R_0$ challenging May's mean-field reasoning. The evolutionary trajectory, however, does not go to a fixed point: it keeps increasing $\beta$ (and decreasing $\tau_I$) forever. Ballegooigen and Boerlijst determine that this is a selection of "wave front frequency", which is pretty interesting.

Our work, however, uncovered an even more interesting feature of the selection process: there are in fact two different processes competing. If initial $R_0$ is very low, there is a lot of susceptible individuals, and increasing $R_0$ is therefore beneficial. When $R_0$ is very high, wave patterns develop. These leave very few susceptible individuals confined in tiny regions, so higher $R_0$ tend to occupy the full pool and die -thus selection for milder strains. Of course, during evolution both mechanism are at play -and they lead to equillibrium, as we demonstrate, in a SOC-like process.

This leaves clear what is the result of adding diffusion: as far as the system can create spatial structuring, the second selection mechanism can act, leading to equillibrium. If not, strains will increase their $R_0$ as in mean-field. In the case of finite diffusion, spatial structuring can happen only for a given set of initial $\tau_I$ and $\beta$, so both behaviours coexist. There are values at which the evolutionary trajectory can go to stable $R_0$ or to the mean-field. The interesting consequence is that the same strain can evolve in very different ways under the same conditions, so the evolutinary outcome may be very difficult to predict.

Of course, any other mechanism able to block the spatial structuring has the very same effect. For example, if the recovery time is very low, or the model run in a small world newtork, we are able to recover the classical mean-field results. However, take in account that in any finite-size system, the mean-field system will die as some point (since $R_0$ always grows and the whole system will be infected). In contrast, the self-organized patterns are very stable, so in the long-term, we may expect to see only these mild pathogens. 

## Some conclusions

Mobility of hosts may induce random outcome in the evolutionary trajectory. A system with finite diffusion can exhibit both self-organized and mean-field behaviours, depending on initial conditions. So, predicting what evolution will do sometimes is not so easy: there is even a set of initial conditions for which both outcomes are possible, and they are selected randomly. 

However, under my personal point of view, the most striking feature of the model is the SOC-like mechanism that is able to self-organize it to the edge of criticality. We are currently working on extensions to this model, and ways to understand the transition.




Some references:
1. **(Alizon _et al_, 2009):** Virulence evolution and the trade-off hypothesis: history, current state of affairs and the future.
2. **(Alizon, 2008):** Transmission-Recovery Trade-Offs to Study Parasite Evolution.
3. **(Sasaki, 2000):** The Evolution of Parasite Virulence and Transmission Rate in a Spatially Structured Population.
4. **(Lion, 2015)**: Evolution of spatially structured host–parasite interactions.
