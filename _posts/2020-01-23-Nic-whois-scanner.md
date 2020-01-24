---
layout: post
author: cvxz
title:  "Nic.cl Whois Scanner"
date:   2020-01-23 11:04:05 -0300
categories: python
---

Hace un par de meses se me ocurrió la idea de hacer un script en Python que entregara información de un listado de [dominios .cl](https://www.nic.cl/), a modo de poder descubrir un nuevo dominio corto, simple y bonito para montar un blog personal.

Para el diseño de este script decidí que solo quería analizar los dominios que personalmente considere _deseables_, como palabras comunes (como [ninjas.cl](http://ninjas.cl/)), letras (desde A.cl hasta Z.cl) y números cortos (desde 0.cl a 99.cl).

En el primer caso utilicé el [diccionario BIP39](https://github.com/bitcoin/bips/blob/master/bip-0039/spanish.txt) de Bitcoin en español, lo que entregó un gran listado de dominios disponibles, pero como no tenía idea de qué temas iba a tocar en mi _futuro blog personal_ decidí seguir con mi búsqueda, ya que [hoyo.cl](http://www.hoyo.cl/) no era una opción muy buena para un blog.

El segundo análisis lo hice con un rango numérico entre el [valor ASCII](https://www.asciitable.xyz/) de la letra A hasta la letra Z, y lamentablemente todos los dominios con una sola letra ya estaban registrados. 

Al final decidí modificar el rango anterior para buscar dominios entre 0 y 99, lo que arrojó solo un único dominio disponible.

{% highlight python %}
import os

for i in range(100):
    word = str(i)
    a = os.popen('whois %s.cl' % word).read()
    
    if 'no entries found' in a:
        print('%s.cl - disponible' % word)
    else:
    	# Expiration date
        date = a.split('\n')[13].split(': ')[-1]
        print('%s.cl - %s' % (word, date))
{% endhighlight %}

Gracias a este pequeño script puedo decir que soy el orgulloso dueño de [90.cl](https://90.cl)