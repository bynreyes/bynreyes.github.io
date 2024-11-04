---
layout: post
title:  "code time I"
subtitle: dificultad ⭐
image: /assets/images/code.jpg
date:   2024-10-24 22:10:05 -0500
categories: PY-Adventure
tags:
  - Ejercicios
  - Python
  - Google Colab
author: nreyes
comments: true
---

# Claude AI

Te ayudaré con ejercicios de Python organizados por niveles de dificultad. Los he diseñado para cubrir conceptos importantes que suelen evaluarse en entrevistas para posiciones junior.

# NIVEL BÁSICO:

1. Escribe una función que determine si un número es par o impar
2. Crea un programa que calcule el factorial de un número
3. Desarrolla una función que cuente las vocales en una cadena de texto
4. Escribe un programa que genere la serie Fibonacci hasta n términos
5. Crea una función que invierta una cadena de texto sin usar métodos incorporados
6. Desarrolla un programa que determine si un año es bisiesto
7. Escribe una función que encuentre el número más grande en una lista
8. Crea un programa que convierta temperatura de Celsius a Fahrenheit y viceversa
9. Desarrolla una función que cuente las palabras en una oración
10. Escribe un programa que sume todos los números en una lista
11. rea una función que verifique si una palabra es palíndromo
12. Desarrolla un programa que genere una tabla de multiplicar
13. Escribe una función que elimine los espacios en blanco de una cadena
14. Crea un programa que calcule el área de diferentes figuras geométricas
15. Desarrolla una función que convierta un número decimal a binario

# Code TIME!!!

### determine si un número es par o impar

- un numero es par si este, es divisible por 2, es decir, **x mod 2 = 0**
- En python el operador modulo es:  %
````python
# determine si un número es par o impar: if ternario
n = int(input("digite un numero: "))
print(f'{n} es un numnero par') if x%2 == 0  else print(f'{n} es un numero impar')


# determine si un número es par o impar: lambda function
test = lambda x: True if x%2 == 0 else False
n = int(input("digite un numero: "))
print(f'{n} es un numnero par') if test(n) else print(f'{n} es un numero impar')

# determine si un número es par o impar: def
def es_par(x):
    print(f'{n} es un numnero par ') if x%2 == 0 else print(f'{n} es un numero impar ')

n = int(input("digite un numero: "))
es_par(n)
````
### Factorial de un número
- solo aplica para numeros positivos
````python
# factorial de un numero: solucion imperativa
def factorial(x):
    if x in (0, 1):
        return 1
    else:
        aux = 1
        for i in range(2, x + 1):
            aux = aux * i
        return aux
        

n = int(input("digite un numero: "))
print(f'el factorial de {n} es: {factorial(n)}')

# factorial de un numero: con reduce
from functools import reduce
n = int(input("digite un numero: "))
factorial = 1 if n in (0, 1) else reduce(lambda x, y: x * y, range(2, n + 1))
  
print(f'el factorial de {n} es: {factorial}')

#  factorial de un numero: con recurcion
def factorial(x):
    if x in (0, 1):
        return 1
    else:
        return x * factorial(x - 1)

n = int(input("digite un numero: "))
print(f'el factorial de {n} es: {factorial(n)}'

# mas recurción
factorial = lambda x: 1 if x in (0, 1) else x * factorial(x - 1)
n = int(input("digite un numero: "))
print(f'el factorial de {n} es: {factorial(n)}')
````

### contar las vocales en una cadena de texto
````python
# contar las vocales en una cadena de texto: solución imperativa
# word.lower(), transforma word en minusculas (lower case).
vocales = ("a", "e", "i", "o", "u")
word = str(input("digite una palabra: "))

def contar_vocales(x):
    aux = 0
    for x in word.lower():
        if x in vocales:
            aux += 1
    return aux

print(f'la palabra {word} tiene {contar_vocales(aux)} vocales')
````

A continuación  contar las vocales en una cadena de texto: sum()  y count() function, 

word.count(x) retorna cuantas veces aparece x dentro de word, luego, por lo general, todo for lo puedo reemplazar por un list compresion
considero esta es la solucion mas coherente, o mas natural, contar cuantas veces aparece la a, luego cuantas veces aparece la vocal e, y asi sucesivamente, para finalmente, sumar todo.
````python
# contar las vocales en una cadena de texto: sum()  y count() function
vocales = ("a", "e", "i", "o", "u")
word = str(input("digite una palabra: "))
cantidad_vocales = sum(word.lower().count(x)  for x in vocales)
print(f'la palabra {word}, tiene  {cantidad_vocales} vocales')

# contar las vocales en una cadena de texto: len() function
vocales = ("a", "e", "i", "o", "u")
word = str(input("digite una palabra: "))
cantidad_vocales = len([x for x in word.lower() if x in vocales])
print(f'la palabra {word}, tiene  {cantidad_vocales} vocales')

# se me ocurrio llenar una lista con ceros y unos.
# donde si se coincide con una vocal, agrego uno a la lista
# luego sumo toda los unos almacenados en la lista
vocales = ("a", "e", "i", "o", "u")
word = str(input("digite una palabra: "))
cantidad_vocales = sum((1 for x in word.lower() if x in vocales))
print(f'la palabra {word}, tiene  {cantidad_vocales} vocales')
````

### Escribe un programa que genere la serie Fibonacci hasta n términos
supongo que si **n=10**, no se me pide hallar **f(10)**, mas bien, lo que se me pide son los diez primeros numeros de la serie
````python
# serie Fibonacci hasta n términos: solución imperativa 
n = 12
def fibonacci(count):
    a, b, count = 0, 1, 0
    while count < n:
        a, b = b, a + b
        count += 1
        print(f"Fibonacci number {count} -> {a}")

fib = fibonacci(n)

# serie Fibonacci hasta n términos: solución imperativa + función generadora
n = 12
def fibonacci(count):
    a, b = 0, 1
    while count > 0:
        a, b = b, a + b
        yield a
        count -= 1

fib = fibonacci(n)

for i, num in enumerate(fib, 1):
    print(f"Fibonacci number {i} -> {num}")

# función generadora por compresión
stop = 12
fibo = lambda n: 1 if n <= 1 else fibo(n - 1) + fibo(n - 2)
data = (fibo(n) for n in range(stop))
for i, num in enumerate(data, 1):
    print(f"Fibonacci number {i} -> {num}")
````

### Crea una función que invierta una cadena de texto

````python
# inviertir una cadena de texto: forma imperativa
word = 'Ají traga la lagartija'
def mirror(word):
    for c in reversed(word):
        print(c, end="")

mirror(word)

# inviertir una cadena de texto: slice
word = str(input("ingrese un texto: "))
mirror = lambda word: print(f'{word} reves: {word[::-1]}')
mirror(word)
````

### Desarrolla un programa que determine si un año es bisiesto
ni idea, tengo que investigar porque un año es bisiesto

### Escribe una función que encuentre el número más grande en una lista
se puede abordar con max, no veo mayor dificultad, exploraremos varios acercamientos

````python
# el número más grande en una lista: forma imperativa
from random import randint
data = [randint(1, 100) for _ in range(10)]

def max_custom(data):
    c = 0
    for i in data:
        if i > c:
            c = i
    return c

print(f'max: {max_custom(data)} de la lista original: {data}')
````
````python
# el número más grande en una lista: max function
from random import randint
data = [randint(1, 100) for _ in range(10)]
print(f'max: {max(data)} de la lista original: {data}')
````
````python
# el número más grande en una lista: reduce function
from random import randint
from functools import reduce
data = [randint(1, 100) for _ in range(10)]

test = lambda x, y: x if x > y else y
max_custom = lambda data: reduce(test, data)

print(f'max: {max_custom(data)} de la lista original: {data}')
````
````python
# el número más grande en una lista: sorted function
from random import randint

data = [randint(1, 100) for _ in range(10)]
print(f'max: {sorted(data)[-1]} de la lista original: {data}')

data = [randint(1, 100) for _ in range(10)]
print(f'max: {sorted(data, reverse = True)[1]} de la lista original: {data}')
````

### Crea un programa que convierta temperatura de Celsius a Fahrenheit y viceversa

Investigando:
````math
C = (F -32) * 5/9
````
````math
F = 9/5 * C + 32
````
por tanto el 90% del problema ya esta resuelto
````python
to_celcius = lambda x: (x -32) * 5/9
to_farenheit = lambda x: 9/5 * x + 32

print(f'-50 C -> {to_farenheit(-50)} F')
print(f'0 C -> {to_farenheit(0)} F')
print(f'100 C -> {to_farenheit(100)} F')
print(f'212 F -> {to_celcius(212)} C')
print(f'32 F -> {to_celcius(32)} C')
````
### Desarrolla una función que cuente las palabras en una oración
lo ideal sería leer un archivo de texto, bueno, esa es mi opinión.
````python
# cuente las palabras en una oración: solución iterativa
file = "README.md"
path = "/content/sample_data/" + file

def palabras(path):
    acc = 0
    with open(path, "r") as f:
        for line in f:
            for word in line.split():
                acc += 1
                
    return acc

print(f'el archivo {file} tiene {palabras(path)} palabras')
````

````python
# cuente las palabras en una oración: sum y len function
file = "README.md"
path = "/content/sample_data/" + file

def palabras(path):
    with open(path, "r") as f:
        return sum(len(line.split()) for line in f)
````
Al final, contar las palabras en una oración se reduce a:
````python
# un bucle for
for word in line.split():
    acc += 1

# len function
len(line.split())
````

es importante tener una noción, de como trabajar con archivos, intentaré profundizar en el tema en publicaciones posteriores.

### Escribe un programa que sume todos los números en una lista
````python
# sume todos los números en una lista: version iterativa
from random import randint
data = [randint(1, 100) for _ in range(10)]
def suma_custom(data):
    aux = 0
    for i in data:
        aux += i
    return aux

print(f'suma: {suma_custom(data)} de la lista original: {data}')
````

````python
# sume todos los números en una lista: reduce function
from random import randint
from functools import reduce
suma = lambda x, y: x + y
data = [randint(1, 100) for _ in range(10)]
print(f'suma: {reduce(suma, data)} de la lista original: {data}')
````

````python
# sume todos los números en una lista: sum function
from random import randint
data = [randint(1, 100) for _ in range(10)]
print(f'suma: {sum(data)} de la lista original: {data}')
````

````python
# sume todos los números en una lista: accumulate function
from random import randint
from itertools import accumulate

data = [randint(1, 100) for _ in range(10)]
s = list(accumulate( data))
print(s)
print("=======================================")
print(f'suma: {s[-1]} de la lista original: {data}')
````

### Crea una función que verifique si una palabra es palíndromo
"aji traga la lagartija", "ojo", son ejemplos de palindromos, ahora, pudieramos aboradar el problema de la siguiente forma:

1. obtener la palabra o oracion
2. eleiminar espacios en blanco: line.split()
3. juntar todo: "".join(line.split())
4. convertir a minusculas: "".join(line.split()).lower()
5. reverse 
6. comparar

y una vez mas, si lo puedes escribir, ya tienes el 90% del problema resuelto
````python
line_1 = "This directory includes a few sample datasets to get you started"
line_2 = "aji traga la lagartija"
line_3 = "ojo"

data = [line_1, line_2, line_3]

pre = lambda line: "".join(line.split()).lower()
palindromo = lambda line: pre(line)[::-1]
es_palindromo = lambda line: pre(line) == palindromo(line)

for line in data:
    print(f'{line} es palindromo') if es_palindromo(line) else print(f'{line} no es palindromo')
````
### Desarrolla un programa que genere una tabla de multiplicar

````python
def tabla(a):
    for i in range(1, 11):
        print(f'{a} x {i} = {a*i}')

tabla(5)
````
### Escribe una función que elimine los espacios en blanco de una cadena
````python
cadena = "This directory includes a few sample datasets to get you started"
print(cadena.split())
print("".join(cadena.split())
````
se puede trabajar con bucles for y whiles tradicionales, pero es mas importante, considero yo, dominar split, join y demas metodos que aplican sobre type string

### Crea un programa que calcule el área de diferentes figuras geométricas
las diferentes figuras seran:
- circulo
- triangulo
- rectangulo
- cuadrados

ajuste de patrones match-case para los panas.

````python
def circulo():
    r = int(input("digite el radio del circulo: "))
    return "circulo", 3.1416 * r**2

def cuadrado():
    l = int(input("digite el lado del cuadrado: "))
    return "cuadrado", l**2
    
def triangulo():
    b = int(input("digite la base del triangulo: "))
    h = int(input("digite la altura del triangulo: "))
    return "triangulo", (b*h)/2

def rectangulo():
    b = int(input("digite la base del rectangulo: "))
    h = int(input("digite la altura del rectangulo: "))
    return "rectangulo", b*h

    acciones = {
    1: cirdulo,
    2: cuadrado,
    3: triangulo,
    4: rectangulo
}

def menu_area():
    while True:
        print("1. Circulo")
        print("2. Cuadrado")
        print("3. Triangulo")
        print("4. Rectangulo")
        print("5. Salir")
        print("digite una opcion: ", end="")
        opcion = int(input())

        match opcion:
            case opcion if opcion in acciones:
                fig, area = acciones.get(opcion)() 
                print(f'el area del {fig} es: {area}') 
                print("==============================")
            case 5:
                break
            case _:
                print("opcion invalida")
                print("==============================")

menu_area()
````

````python
def circulo():
    r = int(input("digite el radio del circulo: "))
    return "circulo", 3.1416 * r**2

def cuadrado():
    l = int(input("digite el lado del cuadrado: "))
    return "cuadrado", l**2
    
def triangulo():
    b = int(input("digite la base del triangulo: "))
    h = int(input("digite la altura del triangulo: "))
    return "triangulo", (b*h)/2

def rectangulo():
    b = int(input("digite la base del rectangulo: "))
    h = int(input("digite la altura del rectangulo: "))
    return "rectangulo", b*h

acciones = {
    1: circulo,
    2: cuadrado,
    3: triangulo,
    4: rectangulo
}

def menu_area():
    while True:
        print("1. Circulo")
        print("2. Cuadrado")
        print("3. Triangulo")
        print("4. Rectangulo")
        print("5. Salir")
        print("digite una opcion: ", end="")
        opcion = int(input())
        if opcion == 5:
            break
        elif opcion in acciones:
            fig, area = acciones.get(opcion)() 
            print(f'el area del {fig} es: {area}') 
            print("==============================")
        else:
            print("opcion invalida")
            print("==============================")
       

menu_area()
````

### Desarrolla una función que convierta un número decimal a binario

````python
# decimal a binario: forma imperativa
n = int(input("digite un numero"))
count = 0
def to_binario (decimal):
    count = 0
    binario = 0
    while decimal > 0:
        binario += (decimal % 2) * 10**count
        decimal //= 2
        count += 1
    return binario

print(bin(n))
print(f'el numero {decimal} en binario es: {to_binario(n)}')
````


````python
# decimal a binario: forma imperativa
n = int(input("digite un numero"))
def to_binario(decimal):
    binario = ""
    while decimal > 0:
        binario += "0" if decimal % 2 == 0 else "1"
        decimal //= 2
  
    return binario[::-1]
    
print(f'el numero {n} en binario es: {to_binario(n)}')
````
Otra forma de llevar un numero de decimal a binario, y que meparece práctico y  divertido, es por medio de restas sucesivas de potencias de dos, ejemplo:

dado un numero decimal 
````math
d = 14 
````
que lo podemos reescribir como
````math
d = 14 = 8 + 4 + 2 = 1*2^3 + 1*2^2 + 1*2^1 + 0*2^0
````
````math
binary(14) = 11110
````
Si se fijan, lo que estamosa haciendo es, encender y apagar bits en un orden, segun corresponda, para luego en el mismo orden en que encendí o apgue los bits, ir anotando dichos bits

````python 
from itertools import count, takewhile, repeat
from functools import reduce

n = int(input("digite un numero"))
d, b = n, '0b'
# genero las potencias de dos
base = takewhile(lambda x: x<=n,(2**x for x in count(0)))

# la operaión de apagar y encender bits 
op = lambda acc, x: (acc[0] - x[0], acc[1] + '1') if acc[0] >= x[0] else (acc[0], acc[1] + '0')

# la magia
binario = reduce (op, zip(reversed(list(base)), repeat('')), [d, b])
print(binario)
print(bin(n))
print("====================================")
print(f'el numero {n} en binario es: {binario[1]}')
````
