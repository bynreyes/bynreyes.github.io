---
layout: post
title:  "Avanced Python I"
subtitle: dificultad ⭐⭐
image: /assets/images/ai-site-helping-with-software-production.jpg
date:   2024-10-24 22:10:05 -0500
categories: PY-Adventure
tags:
  - Python
  - Google Colab
author: nreyes
comments: true
---

## Introducción

Me gusta mucho la programación funcional, y cada vez que se toca el tema, es necesario entonces, hablar de las Lambda functions, map, filter, y reduce, cuatro bestias que nno tienen equivalente en los lenguajes imperativos clásicos de ayer. 

Hoy en dia, la situación es diferente, pues los lenguajes imperativos (Java, C#), son mas flexibles, han evolucionado para estar a la altura de los requeriientos de la industria actual. En este tutorial, exploraremos algunos conceptos y técnicas avanzadas de Python con Google Colab, por lo que te pido un poco de paciencia, ve por cafe y adelante.

## Sección 1: Técnicas avanzadas de Python

1. Lambda Functions
2. Map, Filter, and Reduce Functions
3. List Comprehensions
4. Generators
5. Itertools
6. Decorators
7. Context Managers
8. Multithreading and Multiprocessing
9. Working with Files (Reading and Writing)
10. Regular Expressions
11. Error Handling and Exceptions

***

## Lambda Functions

Las Lambda Functions, o funciones lambda, son funciones anónimas, que en el caso de Python, estan limitadas, pues estas se deben expresar en una linea. Estas funciones anonimas, se pueden crear con la palabra reservada **lambda**, y son de mucha utilidad, cuando se necesita una función sencilla durante un período breve y no se desea definir una función completa mediante **def**.

````python 
# Podemos almacenar las lambda functions en variables
add = lambda x, y: x + y

print(add(5, 3))  # Output: 8

# Un Lambda recursivo
fibo = lambda n: n if n <= 1 else fibo(n - 1) + fibo(n - 2)
for i, n in enumerate(range(10)):
    print(f'Fibonacci({i}) is: {fibo(n)}')
````

Las funciones lambda pueden aceptar cualquier cantidad de argumentos, pero solo pueden tener una expresión, ahora bien, es necesario tener siempre presente, que lo recomendado es no romperce la cabeza y crear una funcion convencional y usarla cuando y donde se amerite, todo sea a favor de la legibilidad del codigo.



## Map, Filter, and Reduce Functions

Dejame y te cuento un poco de historia, en tiempos preteritos, los lenguajes solo poseian los siguientes mecanismos:
- instrucciones secuenciales
- Mecanismos de decision (if-else)
- Bucles (for, while)

solo esas tres cosas son suficientes para desarrollar un programa exacto y legible, nada de intrucciones **go to, breack, continue**, ahora surge una pregunta, ¿ Es posible cambiar el estado de un programa sin recurrir a un bucle for o while?, aunque sinceramente, yo no pueda vivir sin un for in, te cuento que un mundo mejor si es posible, debes saber, que en el mundo de la programacion funcional pura no existen los bucles for ni while, todo resuelven con un maritllo y un yunque, todo lo resuelven con funciones de primer orden, funciones map, filter y reduce, evaluación peresoza, y ya que estamos, funciones anonimas, funciones parciales y monadas.

De momento solo quedemonos con la habilidad de componer funciones, si **f(g(x))**, no te suena, dejame y te lo explico mejor, puedes tomar funciones dentro de otra funciones, tambien quedemonos con map, filter y reduce, son funciones de orden superior, y esposible evadir los bucles for y while por medio de estas.

Map, filter y reduce, son funciones que operan sobre colecciones de datos, ya sean listas, tuplas, diccionarios, entre otras, tomando como entrada, primeramente una funcion, y luego, una coleccion de datos, para luego realizar operaciones específicas sobre ellas.

## Map

La función **map()**, matemáticamente, es es tener una funcion **f(x)** que se aplica sobre cada elemento de un conjunto de datos iterables **A = {x1, x2, x3, ...}**, y ya tecnicamente, devuelve como resultado un objeto map, el cual es iterable.

Ejemplo:

````python
numbers = [1, 2, 3, 4, 5]
squares = map(lambda x: x * x, numbers)
print(squares)
# output: <map object at 0x7e556d4ba9e0>

# Convert the iterator to a list
squares_list = list(squares)
print(squares_list)  # Output: [1, 4, 9, 16, 25]
````
Por tal motivo, en el ejemplo anterior se recurre a: **list**(squares). Ahora subamos un poquito el nivel:

````python
do_it = lambda f, *args: f(*args)
hello = lambda first, last: print("Hello", first, last)
bye = lambda first, last: print("Bye", first, last)

name = ['David','Jane']
last_name = ['Mertz','Doe']

data = map(do_it, [hello, bye], name, last_name)

for i in data:
    print(i)

# output:
Hello David Mertz
None
Bye Jane Doe
None
````

````python
for elem in collection:
    f(elem)

#lo podemos reemplazar por
map(f, collection)

````


## Filter

La función **filter()**, filtra elementos de un conjunto de datos, funcionando algo parecido a como lo haría un tamiz en la vida real, es decir, toma solo aquellos elementos capaces de pasar por el **"tamiz"**, es decir, toma como entrada una funcion **f(x)** que hará de tamiz, para ello, esta debe ser una función que solo pueda devolver **TRUE** o **FALSE** como resultado, pues al aplicar dicha funcion sobre cada elemento del conjunto **A = {x1, x2, x3, ...}** , nos quedaremos solo coon los elementos que cumplan con los requisitos especificados en nuestra función de filtrado.

Ejemplo:
````python 
numbers = [1, 2, 3, 4, 5]
even_numbers = filter(lambda x: x % 2 == 0, numbers)

# Convert the iterator to a list
even_numbers_list = list(even_numbers)
print(even_numbers_list)  # Output: [2, 4]
````

## Reduce

La función reduce() reduce una secuencia de datos a un único valor aplicando una función determinada de forma acumulativa a los elementos, de izquierda a derecha. La función reduce() está disponible en el módulo functools.

````python 
from functools import reduce

numbers = [1, 2, 3, 4, 5]
product = reduce(lambda x, y: x * y, numbers)
print(product)  # Output: 120 (1 * 2 * 3 * 4 * 5)
````

## List Comprehensions
Las listas por compresión, son una delicia matemática, la cual es tomada del mundo haskell, un lenguaje de programación funcional puro, el cual esta muy extendido en el mundo academico. Ahora, empecemos calentando un poco, sigan leyendo, a continuación tenemos el siguiente ejemplo:

````python
pares = [x ** 2 for x in range(10) if x%2 == 0]
print(pares)

# output: [0, 4, 16, 36, 64]
````
En el cual, podemos ver primeramente son una notación compacta que nos recuerda mucho a las matemática, pues lo anterior lo podemos lerr como:
***
**pares** es una **lista** (en matematicas se habla de conjuntos pero no nos compliquemos), formado por **f(x) = x^2** (una funcion que toma un elemento y lo eleva al cuadrado), para todo **elemento x** del conjunto **{0, 1, 2, 3. 4, 5, 6, 7, 8, 9}**  Si **x modulo 2 es 0**.
***

Segundo, podemos notar, que de un plumazo nos ocupamos tanto de un map como de un filter, pues lo anterior es similar a filtrar una lista para posteriormente mapear cada elemento de la colección, con una funcion de nuestro interes, veamos:

````python
pares_2 = list(map(lambda x: x**2, filter(lambda x: x%2 == 0, range(10))))
print(pares_2)

# output: [0, 4, 16, 36, 64]
````
Resumiendo, la lista por comprensión, es un mecanismo optimizado para python (son mas rapidas que un  **for in** convencional), y como vemos, estas nos proporcionan una forma concisa de crear listas, muy terrenalmente, son un mecanismo, el cual consiste en una expresión, seguida de una declaración for dentro de corchetes y si amerita el caso, sazonamos con un if y una expresión de filtrado, podemos anidar listas por compresion, usarlas con map, filter y en realidad cualquier cosa, los invito a ponerce creativos.

Ejercicio 1:
Use listas por comprensión para crear una lista de cubos de números impares del 1 al 20.

````python 
cubes = [x ** 3 for x in range(1, 21) if x % 2 != 0]

print(cubes)
# output: [1, 27, 125, 343, 729, 1331, 2197, 3375, 4913, 6859]
# muy facil che
````


````python 
do_all_funcs = lambda fns, *args: [map(fn, *arg) for n in fns]

hello = lambda first, last: print("Hello", first, last)
bye = lambda first, last: print("Bye", first, last)

name = ['David','Jane']
last_name = ['Mertz','Doe']

data = do_all_funcs([hello, bye], name, last_name)

print(data)

#output
Hello David Mertz
Hello Jane Doe
Bye David Mertz
Bye Jane Doe
[[None, None], [None, None]]
````
## Generators 

Los generadores son una forma sencilla de crear iteradores. Estos se definen como funciones normales, pero en lugar de devolver un valor, lo producen es un objeto el cual se puede recorrer, un iterador. Luego, cuando se llama al generador, lo que hacemos es consumir los elementos, uno por uno, del objeto iterador, tomando en cuenta que cada llamada empieza inmediatamente despues de donde quedó la vez anterior.

A continuación, se muestra un ejemplo de un generador que genera la secuencia de Fibonacci:

````python
# La función generadora
def fibonacci(count):
  a , b = 0, 1
  while count > 0:
    yield a
    a, b = b, a + b
    count -= 1

# Genera los primeros 5 números de Fibonacci
fib = fibonacci(5)

# consumimos los elementos uno a uno
print(next(fib)) # output: 0
print(next(fib)) # output: 1
print(next(fib)) # output: 1
print(next(fib)) # output: 2
print(next(fib)) # output: 3
print(next(fib)) # output: StopIteration


# Genera los primeros 10 números de Fibonacci
fib = fibonacci(10)

# recurrimo a un bucle for para consumir la totalidad de los datos
for i, num in enumerate(fib):
    print(f"Fibonacci number {i + 1} -> {num}")

"""
salida esperada:
Fibonacci number 1 -> 0
Fibonacci number 2 -> 1
Fibonacci number 3 -> 1
Fibonacci number 4 -> 2
Fibonacci number 5 -> 3
Fibonacci number 6 -> 5
Fibonacci number 7 -> 8
Fibonacci number 8 -> 13
Fibonacci number 9 -> 21
Fibonacci number 10 -> 34
"""
```

Una notación alternativa muy similar a las listas por compresión donde tambien podemos usar funciones filtrado, pero en vez de usar corchetes, usamos parentesis, por ejemplo:

````python
# una funcion lambda
fibo = lambda n: n if n <= 1 else fibo(n - 1) + fibo(n - 2) 

# generamos 10 numero de fibonacci
data = (fibo(n) for n in range(10))

# consumimos los datos
for i, num in enumerate(data):
    print(f'Fibonacci({i}) is: {num}') 

# otra funcion generadora
data = (x**2 for x in range(1, 10) if x%2 == 0)

# consuminos los datos
for i, num in enumerate(data):
    print(f'posicion {i + 1} -> {num}')
````

## Bibliográfia
- http://aprendehaskell.es
- https://github.com/aulasoftwarelibre
