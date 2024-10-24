---
layout: post
title:  "Rizando la Locura"
image: /assets/images/test.jpg
date:   2024-10-24 22:10:05 -0500
categories: PY-adventure
tags:
  - python
  - Itertools
author: nreyes
comments: true
---

# Rizando el Rizo

En clases de pensamiento algoritmico, nos colocan a resolver el siguiente problema:

> desarrolle un programa que solicite un numero, y posteriormente determine de cuantas cifras es dicho numero


Se discutió el problema en clase y se llego a la conclusion que debiamos comparar dicho numero con potencias de 10, es decir, comparar con 10, 100, 1000, y asi sucevimente, entonces se me ocurre resolver el problema de la siguiente forma:

```python
n = int(input("ingese un numero "))
for i in range(1,n+1):
    test = 10**i
    if (n < test) and (n >= test/10):
        print(f'El numero {n}, es numero de {i} cifras')
        break 
````
la respuesta esta bien, pues cumple solicitado, ademas, quedaba implicito el uso obligatorio del bucle for pues era de eso trataba la clase, ahora por otro lado, ¿de cuantas maneras puedo abordar dicho problema? 

### Con logaritmos:
Primeramente probemos con logaritmos, no creo que este haciendo trampas, me gusta mucho este acercamiento por lo simple y conciso de la solución, ademas, no rrecurro a cadenas ni a ningun recurso intermedio u avanzado de programación.


{% highlight python %}

from math import log, trunc

n = int(input("ingese un numero "))
a = trunc(log(n,10))
print(f'El numero {n}, es numero de {a + 1} cifras')

{% endhighlight %}

### Itertools al auxilio
Es hora de ponerle sazon al asunto, tenia animos de trabajar con takewhile y dropwhile

````python
from itertools import takewhile

test2 = lambda x: n >= x

n = int(input("digite un numero "))

y = list(takewhile(test2, (10**i for i in range(n))))

print(f'takewhile: El numero {n}, es numero de {len(y)} cifras')
print()

````
### List Coprehension
En realidad 

````python
n = int(input("digite un numero "))
test1 = lambda x: (n >= x//10) and (x > n)
test2 = lambda x: n >= x

# espero que el digito ingresado no sea mayor a 6 cifras
li1 = [10**i for i in range (6) if test1(10**i)]
li2 = [10**i for i in range (6) if test2(10**i)]

print(f'list comprehension: El numero {n}, es numero de {li1} cifras')
print(f'list comprehension: El numero {n}, es numero de {len(li2)} cifras')
print()

````
### Lazy List
````python

test1 =  lambda x: (n >= x//10) and (x > n)

lazy_li = (i for i in range (n) if test1(10**i))

print(f'lazy list: El numero {n}, es numero de {next(lazy_li)} cifras')

````
### Itertools
me quedo varias dudas y curiosidades por resolver, asi que ¿porque no generar una lista de infinitos numeros?

````python

from itertools import starmap, count, repeat, takewhile

n = int(input('digite un numero '))
data = zip(repeat(10), count(0))
y = starmap(lambda x, y: x**y, data)
test = lambda x: n >= x

li = [i for i in takewhile(test, y)]
print(f'list comprehension: {li}')
print()
print(f'takewhile: El numero {n}, es numero de {len(li)} cifras')
````