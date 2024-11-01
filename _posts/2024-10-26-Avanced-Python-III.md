---
layout: post
title:  "Avanced Python III"
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
## Introduccion

En este tutorial, exploraremos algunos conceptos y técnicas avanzadas de Python con Google Colab, un poco de paciencia, ve por cafe 

## Sección 1: Técnicas avanzadas de Python

1. Lambda Functions
2. Map, Filter, and Reduce Functions
3. List Comprehensions
4. Generators
5. Decorators
6. Context Managers
7. Multithreading and Multiprocessing
8. Working with Files (Reading and Writing)
9. Regular Expressions
10. Error Handling and Exceptions

***

## Decorators (decoradores)

Los decoradores son una forma de modificar el comportamiento de funciones o clases. Permiten encapsular otra función para extender su comportamiento sin modificar su código.

A continuación, se muestra un ejemplo de un decorador simple que mide el tiempo de ejecución de una función:

````python
import time

def timing_decorator(func):
def wrapper(*args, **kwargs):
start_time = time.time()
result = func(*args, **kwargs)
end_time = time.time()
print(f"{func.__name__} tardó {end_time - start_time:.5f} segundos en ejecutarse.")
return result

return wrapper

@timing_decorator
def slow_function():
time.sleep(2)

slow_function()
````

## Context Manager (administradores dew contexto)

Los administradores de contexto se utilizan para administrar recursos, como identificadores de archivos o conexiones de red, que se deben adquirir y liberar. Por lo general, se utilizan con la declaración with para garantizar que los recursos se adquieran y liberen correctamente.

A continuación, se muestra un ejemplo de un administrador de contexto para trabajar con archivos:

````python

with open("file.txt", "r") as file:
content = file.read()
# Hacer algo con el contenido
````


En este ejemplo, la función open() devuelve un objeto de archivo, que es un administrador de contexto. Cuando se sale del bloque with, el archivo se cierra automáticamente.

Puede crear sus propios administradores de contexto utilizando el módulo contextlib:

````python
from contextlib import contextmanager

@contextmanager
def my_context():
print("Ingresando al contexto")
yield
print("Saliendo del contexto")

with my_context():
print("Dentro del contexto")
````

## Multithreading and Multiprocessing

Multiprocesamiento y subprocesamiento múltiple

Python proporciona los módulos de subprocesamiento y subprocesamiento para trabajar con subprocesos y procesos, respectivamente. Los subprocesos son livianos, pero tienen limitaciones debido al bloqueo de intérprete global (GIL) en CPython. Los procesos, por otro lado, pueden aprovechar al máximo los núcleos de CPU múltiples, pero tienen una mayor sobrecarga.

Aquí hay un ejemplo de uso de subprocesos para descargar varios archivos simultáneamente:

````python
import threading
import urllib.request

urls = [
"https://example.com/file1.txt",
"https://example.com/file2.txt",
"https://example.com/file3.txt",
]

def download_file(url):
urllib.request.urlretrieve(url, url.split("/")[-1])

# Crear e iniciar los subprocesos
threads = []
for url in urls:
t = threading.Thread(target=download_file, args=(url,))
t.start()
threads.append(t)

# Esperar a que finalicen todos los subprocesos
for t in threads:
t.join()

print("All files dropped.")
````

Y aquí hay un ejemplo de uso de procesos para calcular el factorial de varios números:

````python
import multiprocessing

def factorial(n, return_dict):
result = 1
for i in range(1, n + 1):
result *= i
return_dict[n] = result

numbers = [5, 7, 10]

# Crear e iniciar los procesos
processes = []
manager = multiprocessing.Manager()
return_dict = manager.dict()

for num in numbers:
p = multiprocessing.Process(target=factorial, args=(num, return_dict))
p.start()
processes.append(p)

# Esperar a que finalicen todos los procesos
for p in processes:
p.join()

print("Factorials:")
for num in numbers:
print(f"{num}: {return_dict[num]}")
````

## Trabajar con archivos (lectura y escritura)

Para leer y escribir archivos en Python, puede utilizar la función Función open(). La función open() toma dos argumentos: la ruta del archivo y el modo en el que se abre el archivo.

A continuación, se muestra un ejemplo de cómo escribir texto en un archivo:

````python
with open("file.txt", "w") as file:
file.write("Hello, World!")

Y aquí se muestra cómo leer el contenido de un archivo:

with open("file.txt", "r") as file:
content = file.read()
print(content)
````

## Expresiones regulares

Las expresiones regulares se utilizan para realizar operaciones de búsqueda, reemplazo y validación en datos de texto. El módulo re en Python proporciona funciones para trabajar con expresiones regulares.

Aquí hay un ejemplo de uso de expresiones regulares para verificar si una cadena es una dirección de correo electrónico válida:

````python
import re

email_pattern = r"^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$"

email = "user@example.com"

if re.match(email_pattern, email):
print("Dirección de correo electrónico válida")
else:
print("Dirección de correo electrónico no válida")
````

## Error Handling and Exceptions 

Manejo de errores y excepciones

El manejo de errores es una parte esencial de la programación. En Python, los errores se manejan a través de excepciones. Las excepciones son eventos que se activan cuando ocurre un error durante la ejecución de un programa. Puedes

````python

try:
    result = 1 / 2
except ZeroDivisionError:
    print("Error: Division by zero.")
finally:
    print("This will be executed no matter what.")

````

## Bibliográfia
- https://docs.python.org/3/library/itertools.html
- https://realpython.com/python-itertools/
- http://aprendehaskell.es
- https://github.com/aulasoftwarelibre
