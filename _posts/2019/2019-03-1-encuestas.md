---
layout: post
title:  "Encuestas en Twitter: una mala idea"
date:   2019-02-27 20:00:00 -0500

tags: estadistica opinion encuestas

summary: "Tu CIS casero está condenado al fracaso... ¡es estadística!"

tipo: divul
head_image: "/images/2019/encuestas.jpg"
---

La estadística es una de las ramas más interesantes de las matemáticas. Puede que calcular medias parezca aburrido, pero el diseño de test estadísticos es un puzle que requiere de mucho ingenio y está lleno de falacias y problemas sutiles.

Por eso, aprovechando que se acercan elecciones, hoy vamos a hablar de Twitter: ¿has visto esa gente que pone esas encuestas preguntando a quién vas a votar en las próximas? ¿Esa gente que pide que hagas muchos retuits porque "cuantos más retuits más fiable será la encuesta"? Pues me temo que no: así contesten 10 personas que todo Twitter, tu encuesta no es mejor que el CIS. ¡Veamos por qué!

## Monedas, sesgos y otros cuentos

Comenzaré por un ejemplo que ilustrará más adelante cuál es el problema con Twitter y otras redes sociales. Supongamos que tengo 10 monedas, y quiero jugar a cara y cruz con ellas. Las lanzo de una en una. ¿Cuántas caen de cara y cuántas de cruz?

Hay muchas posibilidades. Puede que haya 4 de cara y 6 de cruz. O 3 de cara y 7 de cruz. Cada posibilidad tiene una probabilidad diferente, por supuesto: sería muy raro ver todas de cara. Lo normal será tener algo parecido al 50%-50%. Y ahora vamos a la pregunta, ¿qué pasa si en vez de tener 10 monedas tengo 100?
Entonces la probabilidad de ver todas de cara es aún más pequeña. Espero tener algo más parecido todavía al 50%-50%. Y con 1000 monedas, o con 10000, todavía más parecido. En el fondo, tirar todas las monedas es lo mismo que tirar la misma muchas veces.

Déjame proponer ahora el siguiente experimento. Yo tengo un millón de monedas. Las lanzo al aire, y cuento si va a salir cara o cruz. Ahora, escojo _aleatoriamente_ 100 monedas, y te las doy. Ahora tienes 48 monedas de cara y 52 de cruz, y te pregunto, _¿qué he obtenido yo con mi millón de monedas?_.

Esto es lo que se conoce como un muestreo. Tú no tienes ganas de mirar mi millón de monedas, así que coges solamente 100, y llegas a la conclusión de que el 52% cayó de cruz, y por tanto yo tengo 520.000 monedas de cruz. Si estás un poco más trabajador, en lugar de 100, analizas 1000 monedas. Al coger más monedas del millón, esperas que el resultado obtenido con las 1000 monedas sea más parecido al real que el obtenido con 100 monedas. Esto es porque coger 1000 monedas es como hacer la estimación con 100 monedas, 10 veces, usando siempre monedas distintas. Con eso puedes estimar cuál es el porcentaje de monedas de cruz.

Hasta aquí probablemente pienses que es un poco inocente lo que te estoy contando. A más monedas, mejor. Claro. Pero vamos a ir complicando el asunto. Ahora yo tengo solamente 1000 monedas. De esas 1000, yo te digo que 400 están trucadas: cuando las lanzo, siempre sale cara. Este experimento se puede hacer esta forma. Yo lanzo las 1000 monedas, y de ellas cojo 400 y las pongo con cara. Y te doy 100 monedas al azar, y vuelvo a preguntar, _¿qué he obtenido yo con mis 1000 monedas?_

Usando estadística, se puede calcular el porcentaje de caras y cruces que se espera que yo obtenga. Hagámoslo. De las 1000 monedas, solo 600 son verdaderamente aleatorias, así que espero (en promedio) 300 caras y 300 cruces. Por tanto, en promedio hay un 70% de cara y un 30% de cruces en mis monedas.

Entonces tú puedes pensar: _si tienes 1000 monedas y 400 son trucadas, y las mezclas muy bien, al sacar 100 monedas aleatorias habrá 40 trucadas. Entonces el porcentaje de trucadas que tenemos tú y yo es el mismo, y por tanto puedo estimar cuántas tienes sin problema_. Esto ocurre porque he mezclado bien las monedas. E igual que antes, si en vez de con 1000 monedas jugamos con un millón, podrás hacer predicciones mejores.

Y ahora vamos al meollo del asunto. Yo tengo 1000 monedas, de las cuales 400 son trucadas. Pero cuando te doy las monedas, decido _fastidiarte_ a propósito. Te doy solo y únicamente 5 monedas trucadas. Si tú sabes que te he dado exactamente 5 caras, las apartas y haces la estadística sobre el resto.  Pero, ¿qué ocurre cuando no sabes exactamente cuántas monedas te he dado trucadas? ¿Cómo hacer para estimar cuántas caras tengo yo?

Sencillamente: no puedes. Si yo mezclo todas las monedas trucadas y te las doy, tú más o menos puedes contar cuántas tienes en tu muestra, y hacer una estimación. Pero si yo _elijo_ unas monedas concretas para engañarte, y tú no sabes cómo las he escogido yo, tu encuesta no sirve para nada. Podría ser que tenga un millón de monedas, de las cuales el 1% están trucadas para que cruz tenga más probabilidad que cara, y el 99% están trucadas al contrario. Yo doy 1000 monedas, de las cuales 800 pertenecen a ese 1% y 200 al 99%. Tú estimarías (incorrectamente) que el 80% están trucadas para que cruz tenga más probabilidad. ¡Pero eso no es cierto en absoluto!.


## ¿Y esto qué tiene que ver con Twitter?

Pongámonos en el caso de las encuestas electorales, y vamos a simplificarlas al máximo. Es una encuesta en la que la gente elige "Votar izquierda" o "votar derecha". La publicas, y esperas pacientemente los RTs. La gente vota, y tienes, digamos un 70% de votos a la izquierda. ¿Cuán fiable es ese resultado?

Como puedes ver, el experimento es muy parecido al de las monedas. Las monedas, en este caso, son las personas. El problema es que cada persona tiene una ideología (izquierdas o derechas), así que _todas las monedas están trucadas_. La pregunta es cuáles están trucadas para un lado y cuáles para otro.

Ahora, recordemos arriba. Si yo _elijo_ qué monedas te doy, no sirve para nada. El problema es que las redes sociales son exactamente como ese problema donde tus encuestas son inútiles. Los usuarios de Twitter no son gente _aleatoria_ de la población española. Por ejemplo, en Twitter hay mucha gente joven. No hay casi nadie de más de 60 años. ¡Pero hay muchísimas personas en la población española de más de 60 años! Y obviamente, los jóvenes y los mayores están "trucados" de forma diferente, porque han tenido una experiencia vital distinta. Que la ideología está relacionada con la edad es algo que se ha comprobado en varios estudios sociológicos.
El tema es: no sabes con qué criterio Twitter atrae más a un usuario que a otro. Puede que la gente mayor de España esté sesgada a votar derecha y  la gente joven esté sesgada a izquierda. Pero no sabes qué porcentaje ha "elegido" Twitter. Por tanto, no importa que preguntes a todo Twitter: son monedas de un conjunto más grande, cuya elección no ha sido aleatoria, sino sesgada. 

Esto es un concepto importantísimo en estadística. Para que una encuesta sea serie, no solo ha de preguntar a bastante gente, sino que la muestra ha de ser correcta. La gente critica que el CIS solo pregunte a 2000 personas, mientras su encuesta de Twitter tiene 10.000 votos. Sin embargo, el CIS es _mucho_ más fiable que tu encuesta de Twitter, porque ellos se preocupan de que la población española esté bien representada. Es decir, si el X% de la población española tiene entre 20 y 30 años, ellos se aseguran que de esas 2000 personas, el X% tiene entre 20 y 30 años. Si el X% de la población de Andalucía vive fuera de grandes ciudades, ellos se aseguran de que las encuestas que hacen en Andalucía sea a gente de pueblos perdidos. ¿Tu encuesta de Twitter pregunta a todos esos jornaleros que tienen más de 50 años y viven en un pueblo perdido de Dios? No. El CIS sí. 

Espero que el problema quede más o menos patente: tu encuesta silenciando sistemáticamente la opinión de sectores concretos de la población. Sectores que NO son minoritarios en absoluto y contribuyen mucho al resultado de las elecciones, pero que por su forma de ser no tienen Twitter. ¿Por qué? Porque no les gustan las nuevas tecnologías, porque no tienen dinero para comprar un ordenador, o cualquier otro motivo. Tu encuesta sobreestima el valor de cierto sesgo que aparece a menudo en Twitter pero que no está en la sociedad actual. Así de sencillo.

## Conclusiones

La gente que hace encuestas por Twitter a menudo piensa que representan a la población española. Realmente, no. Como mucho, pueden representar al conjunto de usuarios de la red social, que en general puede pensar muy diferente al conjunto de la población española. Además, factores como el tipo de conexiones que se establecen entre los usuarios de Twitter, que forman comunidades bastante cerradas, me hace decir:
    
**Una encuesta en Twitter evalúa en general cómo opinan tus seguidores de Twitter, a menos que se haga realmente viral.**

Toma estas encuestas realmente como lo que son, una herramienta desenfadada y divertida para conocer la opinión de tus seguidores. Si se hace viral, puede que seas capaz de conocer la opinión de toda la red, pero **nunca, bajo ningún concepto, al conjunto de la población**. 

Pequeña posdata: entonces, ¿es el CIS perfecto? No, hablando con un sociólogo en un viaje de autobús la mar de interesante descubrí que su muestreo tiene algunas cosas criticables. Sin embargo, (a) ellos te dicen cómo lo hacen, y sabes dónde están los fallos, y tú eliges si creértelo o no, y (b) son gente que sabe mucha estadística, y son conscientes de sus problemas, y (espero) trabajan por arreglarlos. **Tienen una metodología y saben que sus resultados están limitados por la metodología.** 

¡Usad la estadística con responsabilidad! :)


 




