---
layout: post
title:  "Wilson-Cowan"
date:   2021-11-06 13:00:00 -0500

tags: applet physics neuroscience 

summary: "Simulation of the Wilson-Cowan model"

tipo: applet
head_image: "/images/applets/wilsoncowan.png"
---

**[English]:** Play with the applet [here.](https://victorseven.github.io/interactive/wilson-cowan/index.html)  In this page you find a description for the model.

**[Español]:** Puedes jugar con la applet  [aquí.](https://victorseven.github.io/interactive/wilson-cowan/index.html) Más abajo en esta misma página hay una descripción en español.

The code is freely available [on GitHub](https://github.com/VictorSeven/wilson-cowan-webapp).

## Description

The model above simulates the famous *Wilson-Cowan* model in your device screen. You can imagine that each pixel in your screen is a small portion of brain that contains some thousands of neurons with a certain level of activity. The neuronal activity in the region self-regulates itself, and it can also spread to neighbouring pixels.

Each one of this regions have both *excitatory* and *inhibitory* neurons. Excitatory neurons tend to activate more neurons, increasing the activity of both the current pixel and the neighbouring ones. On the other hand, when inhibitory neurons are activated they tend to reduce and regulate the activity of their neighbours.

The Wilson-Cowan was introduced around 1972 to demonstrate that neuronal populations can exhibit different interesting patterns, such as oscillations and spiral waves. This model is relevant in theoretical neuroscience, due its mathematical simplicity and dynamical complexity.

In this simulation, excitatory activity is represented in red, and inhibitory one in blue. You'll see, however, a plethora of different colors in the middle, like pink or purple, which indicate that in that pixels there is a mixture of excitation and inhibition going on. This is normal: excitatory neurons activate inhibitory ones, which try to regulate activity. However, if there is enough excitation, both kind of neurons are constantly active. 

Clicking on the menu you can change some parameters of the system and see how it behaves:

- `E<E, E<I, I<E, I<I` represent how strongly each kind of neuron affect the other. For example, increasing `E<I` means that inhibitory neurons will strongly decrease the activity of the excitatory ones, and increasing `I<E` means that excitatory neurons will strongly activate inhibitory ones.
- `Gain` and `Threshold` are parameters for the neurons: the threshold in the minimum activity that neurons need to activate. Increasing it will reduce the amount of activity and filter background noise. The gain parameter reflects how much the population responds to the input once it is over the threshold. Increasing it will increase the activity of the population. There is a different gain and threshold for excitatory and inhibitory populations
- `Noise` is randomly activity that will perturb the system to create some patterns automatically. It is some kind of background noise. 
- You can click and drag on the applet to generate activity yourself. If you are in a PC, you can double click to generate inhibitory activity, and press the `space`  key to enter into fullscreen mode. 

## Descripción

Este applet simula el conocido sistema de *Wilson y Cowan* en la pantalla de tu dispositivo. Imagina que cada pixel en tu pantalla es una pequeña porción de cerebro, que contiene algunos miles de neuronas con cierto nivel de actividad. La actividad neuronal en cada pixel se regula sola, pero también puede contagiarse a píxeles cercanos. 

Cada una de las regiones cerebrales contiene neuronas excitadores e inhibidoras, como el cerebro de verdad. Las neuronas excitadoras tienden a activar más neuronas, incrementando la actividad del píxel donde se encuentran, así como las de píxeles cercanos. Por otro lado, las neuronas inhibidoras tienden a reducir y regular la actividad del pixel.

El modelo de Wilson y Cowan se introdujo en 1972 para demostrar que las poblaciones neuronales pueden mostrar diferentes patrones de actividad, como oscilaciones y ondas espirales. Estas ecuaciones son relevantes en neurociencia teórica, y su atractivo reside en su simplicidad matemática y complejidad dinámica.

En esta simulación, la actividad excitadora se representa en color rojo, y la inhibidora en azul. Sin embargo, como verás, hay todo un rango de colores de rosas a morados, que indican que en esos píxeles hay actividad excitadora e inhibidora al mismo tiempo. Esto es lo habitual: las neuronas excitadoras activan a las inhibidoras, que a su vez intentan regular la actividad. Si hay suficiente excitación, ambas pueden coexistir y estar activas constantemente.

Clicando en el menú puedes cambiar algunos de los parámetros del sistema y ver cómo se comporta:

- `E<E, E<I, I<E, I<I` representan cómo afectan unas neuronas a las otras. Por ejemplo, si se aumenta `E<I`  las neuronas inhibidoras afectan más fuertemente a las excitadoras, reduciendo su actividad.  `I<E` implica que las excitadoras afectarán más a las inhibidoras, encendiéndolas más.
- `Gain` y `Threshold` son parámetros para las neuronas: el umbral (threshold) es la actividad mínima que necesita recibir una neurona para activarse. Aumentarlo reducirá la cantidad de actividad. La ganancia (gain) indica cuánto afecta a la neurona la actividad que está sobre el umbral. Al aumentarla las neuronas disparan más.  Hay un umbral y una ganancia distintas para las neuronas excitadoras e inhibidoras.
- `Noise` (ruido) es una actividad aleatoria que perturba ligeramente al sistema para crear patrones de forma automática.
- Puedes clicar y arrastrar en la pantalla para generar tú mismo actividad excitadora. Si estás en un ordenador, el doble click genera actividad inhibidora. 

### Technicalities

The model has been implemented using Godot Engine 3.3.4 and exported to HTML5. Code is freely available [on GitHub](https://github.com/VictorSeven/wilson-cowan-webapp). Implementation is done using shaders on a texture. 

The equations simulated are not the original Wilson-Cowan partial differential equations (see the 1972 paper), but rather a simplified diffusive version of the coarse-grained dynamics, 


$$
\partial_t E(\vec x,t) = -E+(1-E)f(\omega_{ee}E-\omega_{ei}I+\nabla^2E+\sigma_e \eta_e(t)) \\
\partial_t I(\vec x,t) = -I+(1-I)f(\omega_{ie}I-\omega_{ii}I+\sigma_i \eta_i(t)) 
$$


where the function $f(x>0)=\tanh(x)$ and 0 otherwise, and $\eta_{e,i}(t)$ represents uncorrelated Gaussian white noise. Diffusion constant has been fixed to unity without lack of generality. I am not sure if it pays off the implement the full integro-differential spatial system, since the only difference is that the latest displays fast oscillations, which are difficult to capture with the technology used to simulate the system: the delta-time used to integrate the equations depends strongly on screen refresh rate, which is fixed to 60FPS (vsync), meaning that maybe the fast oscillations cannot be seen anyway.



 