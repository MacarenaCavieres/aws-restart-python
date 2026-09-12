# Módulo de Fundamentos de Programación con Python

![Python Version](https://img.shields.io/badge/python-3.6+-blue.svg)
![AWS Cloud9](https://img.shields.io/badge/IDE-AWS%20Cloud9-orange.svg)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen.svg)

Este repositorio contiene el conjunto de prácticas y laboratorios desarrollados durante el módulo de programación en Python. Los ejercicios abarcan desde el manejo de tipos de datos básicos y estructuras sintácticas, hasta el procesamiento de información biológica, automatización de comandos del sistema operativo y depuración de código.

## Resumen de Laboratorios

### 1. Tipos de Datos Primarios y Operaciones Básicas

- **Interacción con la consola y REPL:** Uso del shell interactivo de Python (`python3`) para la ejecución de operaciones aritméticas elementales y validación de expresiones[cite: 1].
- **Tipos de datos numéricos y booleanos:** Declaración de variables de tipo entero (`int`), flotante (`float`), complejo (`complex`) y booleano (`bool`), inspeccionando sus tipos mediante la función integrada `type()` y formateando cadenas con `str()`[cite: 1].
- **Manejo de cadenas de texto (Strings):** Concatenación de cadenas, lectura de datos desde la entrada estándar mediante `input()` y formateo de salidas dinámicas utilizando el método `.format()` y f-strings[cite: 1].

### 2. Estructuras de Datos Compuestas

- **Colecciones (Listas, Tuplas y Diccionarios):** Manipulación de listas mutables, acceso por índice y modificación de elementos; uso de tuplas inmutables; e implementación de diccionarios para la gestión de datos mediante pares clave-valor[cite: 1].
- **Listas de tipos mixtos:** Creación de colecciones con múltiples tipos de datos heterogéneos e iteración sobre estas para validar dinámicamente sus tipos[cite: 1].

### 3. Control de Flujo e Iteración

- **Estructuras condicionales:** Implementación de decisiones lógicas mediante bloques `if`, `elif` y `else` para procesar entradas e iteraciones condicionales del usuario[cite: 1].
- **Bucles `while` y `for`:** Construcción de un juego interactivo de adivinanza numérica con generación de valores aleatorios (`random`) usando `while`, e iteraciones secuenciales controladas con `for` y `range()`[cite: 1].

### 4. Procesamiento de Archivos y Secuencias Biológicas

- **Lectura y procesamiento de CSV:** Parsing e importación de datos tabulares desde un archivo `.csv` a estructuras en memoria mediante los módulos `csv` y `copy` (uso de `deepcopy` para evitar copias superficiales)[cite: 1].
- **Limpieza y manipulación de texto:** Procesamiento y limpieza manual y programática de secuencias de aminoácidos de la preproinsulina humana descargadas desde NCBI[cite: 1].
- **Cálculos bioquímicos:** Procesamiento de cadenas proteicas, cálculo aproximado del peso molecular de la insulina a partir del conteo de aminoácidos, determinación del porcentaje de error respecto al valor real y evaluación de la carga neta según variaciones del pH[cite: 1].

### 5. Modularidad y Cifrado de Información

- **Funciones definidas por el usuario:** Diseño e implementación de un algoritmo de Cifrado César modularizado en funciones especificas (`getDoubleAlphabet`, `getMessage`, `getCipherKey`, `encryptMessage`, `decryptMessage`)[cite: 1].
- **Manejo de alfabetos y desplazamiento:** Transformación de caracteres mediante operaciones sobre cadenas de texto e índices para encriptar y desencriptar mensajes[cite: 1].

### 6. Administración de Sistemas y Depuración

- **Ejecución de comandos Bash:** Interacción con el sistema operativo invocando comandos del Shell (`ls`, `uname`, `ps`) desde el código utilizando los módulos `os` (mediante `os.system`) y `subprocess` (mediante `subprocess.run`)[cite: 1].
- **Depuración de código (Debugging):** Uso del entorno de depuración interactivo de AWS Cloud9 para establecer puntos de interrupción (breakpoints), inspeccionar variables y rastrear errores de tipos de datos (_Traceback_)[cite: 1].

## Mención Especial: Desafío de Números Primos

Como parte de los desafíos prácticos del módulo, se implementó un algoritmo dinámico en Python para identificar y filtrar números primos en un rango determinado (1 al 250), persistiendo los resultados formateados en un archivo plano.

**Lógica y Solución Desarrollada:**

- **Evaluación con Early Exit:** La función `is_prime(x)` evalúa los divisores en orden descendente y detiene la ejecución inmediatamente (`return False`) en cuanto el conteo de divisores supera los 2 elementos, optimizando las iteraciones innecesarias.
- **Procesamiento de Rango e I/O:** La función `evaluation(a, b)` recorre dinámicamente los valores en sentido inverso, formatea la colección resultante separada por comas y gestiona la escritura del archivo `results.txt` mediante el uso de gestores de contexto (`with open`).

```python
def is_prime(x):
    nums = []
    for i in range(x, 0, -1):
        if x % i == 0:
            nums.append(i)
            size = len(nums)
            if size > 2:
                return False
    return True


def evaluation(a, b):
    prime_numbers = []
    for y in range(b, a, -1):
        if is_prime(y):
            prime_numbers.append(y)
    prime_numbers.append(1)
    prime_numbers.sort()
    result = " , ".join(str(n) for n in prime_numbers)
    with open("results.txt", "w") as file:
        file.write(result)
    return prime_numbers


print(evaluation(1, 250))
```

## Requisitos del Entorno

- Python 3.6 o superior
- Módulos estándar requeridos (incluidos en la biblioteca estándar de Python):
    - `csv`
    - `copy`
    - `random`
    - `os`
    - `subprocess`
