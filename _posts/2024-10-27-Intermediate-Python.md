---
layout: post
title:  "Intermediate Python I"
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
## Algorithms + Data Structures = Programs

Niklaus Wirth, En 1975, escribió el libro **Algorithms + Data Structures = Programs**, nunca he tenido ese libro en mis manos, pero ¡cuanta razon! no encuentro desperdicio en tal frase.

En mi opinion y parafraceando al gran Niklaus, considero que para diseñar un programa, es necesario conocer profundamente las estructuras de datos que nos ofrece nuestra herramienta favorita, llamese esta  Python, Java, C#, puede ser una biblioteca en particular, tal como Pandas con sus omniopresentes data frames, en fin, resulta que, nuestro deber primero es elegir y escoger, esa estrucutura de datos que mejor represente nuestro problema a resolver, esa estructura que mejor se ajuste a nuestras necesidades, pues dependiendo de la estructura elegida podremos optar por un camino u otro, esos camionos de eleccion son los algoritmos, que manipulando eficientemente los datos, es como finalmente se logra obtener un programa correcto.

Me gusta mucho Python, es verdad, pero programar puede hacerse en el lenguaje que prefieras o lo que te exija la universidad o el trabajo. Pues lo fundamental va más allá del lenguaje: consiste en, primeramente, es entender el problema en sí (nuestra ley cero de la termodinámica). Después, es necesario embonar los datos con las estructuras de datos adecuadas, es decir, seleccionar aquellas que permitan representar la información de manera eficiente, clara y concisa. Finalmente, el tercer paso es manipular estos bloques de datos de forma que se logre la funcionalidad deseada, optimizando así cada aspecto del programa.

Resumiendo, tenemos:

1. Entender el problema. (nuestra ley cero de la termodinámica)
2. Embonar Los datos con las estructuras de datos adecuadas.
3. Manipular los bloques de datos.
***

## Contenido
- Los Datos
    - mutable vs inmutable
    - homogeneo vs heterogeneo

- Colecciones
    - Listas
    - Tuplas
    - Diccionarios
- Range
- Enumerate 
- Zip
***


## Los Datos
Todo lenguaje de programación, ofrecen dos tipos de datos, los primitivos (numeros, caracteres, otros), y los civilizados, esos datos que les gusta agruparse alrededor de una fogata y fundar luego una civilización (se nos puso poetico el hombre 😝), esos datos los conocemos como colecciones, podemos crear nuevas estructuras de datos, como las clases de la programación orientda a objetos o OOP para los panas, y/o customizar las colecciones de datos que nos ofrece el lenguaje de programación con el que estemos trabajando.

Recordemos que las clases son moldes con las que luego se fabricaran objetos, y que cada clase agrupa una serie de datos o características, funcionalidades y condimentos varios. Luego tenemos los objetos, los cuales son fabricado a partir de una clase, y estos objetos interactuan entre si por medio de mensajes, por ultimo es OOP y no POO, pues no soy fan de Winny the POO (perdon no podía dejar pasar la oportunidad 🤣).

## Mutable vs Inmutable
Hace referencia a la capacidad de un dato o colección de daos, de cambiar o no su estado o valor. En la programación funcional pura, los datos son concevidos como inmutables, mas sin embargo, esto no es asi con el resto de lenguajes de programación actuales, pues estos son pragmáticos, es decir, los datos cambian constantemente de estado, pero si se requiere, suelen ofrecer algun mecanismo por medio del cual nuestro dato permanece estatico y no cambia de valor durante la ejecución del programa. En python, les adelanto, no existe tal key word, por lo que todo se reduce a un trato entre caballeros, un dato inmutable es declarado en una variable en mayusculas y eso es todo.

Por ejemplo en Java, un ArrayList, es una estrutura de datos, donde puedo agregar nuevos elementos, quitar elementos, cambiar el valor de los elementos almacenados, y por tanto, estamos ante una estructura de datos mutable, esto es asi, por su capacidad de cambiar de estado, lo mismo no sucede con las tuplas en Python, es verdad que su comportamiento es el de una lista, mas sin embargo, los datos que la conforman no pueden variar, no puedo agregar nuevos elementos o quitar los elementos ya existenetes, por lo que concluimos, que las tuplas de python son una estrutura de datos inmutable.

Por ultimo, trabajar con datos inmutables ofrece mes muy ventajoso, sobre todo a la hora de trabajar con concurrencia.

## homogeneo vs heterogeneo
Hace referencia a los datos agrupados dentro de una colección, ¿son todos acaso del mismop tipo?, por ejemplo en Java, un ArrayList, es una estrutura de datos donde todos los datos que la conforman necesariamente son del mismo tipo, en contraste,  las listas en Python, pueden contener cualquier variedad de elementos, pude ser numerico, otra lista, cualquier cosa que se requiera, hasta funciones.

## Colecciones
Python ofrece varias estructuras de datos, como los heaps o monticulos, los conjuntos, entre otros, mas en este momnento nos vamos a centrar en las listas, las Tuplas y los Diccionarios, los cuales son las estructuras de datos mas extendidas, y que veremos con mas frecuencia, a posteriori, podríamos hablar de los vectores de numpy y los data frame de Pandas.

## Listas
Es una colección de datos, mutable y heterogenea, basada en un lista enlazada (linkend list), donde podemos acceder a los elementos de dicha lista por medio de un subindice. Podemos crear una lista, con un para de corchetes y dentro colocar los elementos que querramos, eso si, los elementos deben estar separados por comas.

Por otro lado, en Java tenemos los arreglos y las listas enlazadas, ambas colecciones mutables y homogeneas.

## Tuplas
Son estructuras de datos inmutables, es decir una vez intanciada, no puedo modificar sus parametros, del resto, son estructuras muy similares a las listas,  es heterogenea, puedo almacenar datos de distintos tipos y comparten los mismos metodos de manipulación exeptuando aquellos que provoquen un cambio de estado. Podemos crear una tupla por medio de un par de parentesis, y colocxando dentro los elementos que querramos almacenar, separados por coma.

## Diccionarios
son estructuras de datos clave-valor, los puedes conseguir en otros lengujes, como Java, C#, bajo el nombre HashMap. Los diccionarios son colleciones de datos  de pares clave-valor, estan desordenados, tienen barbaridad de metodos, mas empecemos por el principio:

  - La clave pude ser cualquier cosa que sea inmutable (que no cambia)
  - El valor puede se ser cualquier cosa. (alguien dijo funciones?).
  - Podemos usar un par de llaves (curly brakes) para crear un diccionario.
  - utlilizamos un par de puntos para separar una clave de su valor, y una coma para separarar las parejas clave-valor dentro de la colección
  - Son estructuras de datos mutables, al poder eliminar o adicionar nuevas parejas clave-valor, modificar el valor de uina clave, etc.
## Range

Es una funcion que devuelve una secuencia de numeros, por defecto comienza en cero y con paso uno, incrementa hasta donde le indiquemos.
***
range(start = 0, stop, step = 1)
***
## Enumerate
Es una funcion que toma un iterable y retorna un objeto enumetrate, un objeto iterable.

***
enumerate(iterable, start = 0)
***
## Zip

zip es una función que recibe de entrada uno o mas objetos iterables y devuelve un objeto zip iterable, por lo que debemos recurrir a la función **next()**, para consumir uno a uno los elementos del iterable, un bucle **for in** de toda la vida, o tambien podemos usar la función **list()**, veamos a continuación un ejemplo:

````python
materias = ['Pensamiento Algoritmico', 'Algebra Superior', 'Sistemas Digitales']
notas = [4.5, 4.2, 3.5]

print(zip(materias, notas)) 
print()

#output:
<zip object at 0x780f42f760c0>
````

````python
data = list(zip(materias, notas))
print(f'data sin procesar: \n{data}')
print()

# output:
data sin procesar: 
[('Pensamiento Algoritmico', 4.5), ('Algebra Superior', 4.2), ('Sistemas Digitales', 3.5)]
````

````python
for materia, nota in data:
    print(f'{materia} fue aprobado con: {nota} puntos.')

# output:
Pensamiento Algoritmico fue aprobado con: 4.5 puntos.
Algebra Superior fue aprobado con: 4.2 puntos.
Sistemas Digitales fue aprobado con: 3.5 puntos.
````

Como vemos, zip por si solo, nos devuelve un objeto para nada legible al ojo humano, y como no hablo taka taka, es necesario recurrir a **list()**, para ver que ha pasado, recurrir a **nex()** tambien hubiera funcionado, y ¿que es lo que observamos?, bueno te puedo responder que observamos lo esperado, **zip()** toma dos listas y combina los elementos uno a uno en una tupla, toma los elementos en el mismo orden y empezando por el indice 0. Ahora, cabe acotar, que si los elementos a combinar no guardan la misma cantidad de elementos, creanme que zip termina donde cuando la coleccion mas pequeña no tenga mas elementos que combinar.

 A xontinuación un par de ejemplos mas:

````python
# create a list of names
names = ['sravan', 'bobby', 'ojaswi', 'rohith', 'gnanesh']

# create a list of subjects
subjects = ['java', 'python', 'R', 'cpp', 'bigdata']

# create a list of marks
marks = [78, 100, 97, 89, 80]

# use enumerate() and zip() function
# to iterate the lists
for i, (names, subjects, marks) in enumerate(zip(names, subjects, marks), 1):
    print(i, names, subjects, marks)

# output:
1 sravan java 78
2 bobby python 100
3 ojaswi R 97
4 rohith cpp 89
5 gnanesh bigdata 80
````

````python
names = ['John', 'Jane', 'Alice', 'Bob']
ages = [20, 22, 25]

zipped = zip(names, ages)
print(zipped)
print()
print(f'zipped.__next__() -> {zipped.__next__()}')
print(f'next(zipped) -> {next(zipped)}')
print()

zipped = zip(names, ages)
print(list(zipped))
print()

for name, age in zip(names, ages):
    print(f'{name} is {age} years old')
````
````python
zipped = [('John', 20), ('Jane', 22), ('Alice', 25)]
names, ages = zip(*zipped)

print()
print(names)  # ('John', 'Jane', 'Alice')
print(ages)   # (20, 22, 25)

````


## Bibliografía
- https://es.wikipedia.org/wiki/Niklaus_Wirth
- https://docs.python.org/3/tutorial/controlflow.html#match-statements