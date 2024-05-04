# Operaciones con variables

Hemos visto ya algún ejemplo de operaciones con variables en el que sumábamos dos de ellas:


```python
m = 2
n = 3.2
r = n + m
print(r)
type(r)
```

    5.2
    




    float



Python ofrece, en todo caso, un buen número de operadores que podemos usar en nuestros programas. Echémosles un vistazo.

## Operadores algebraicos

Python incluye los cuatro operadores aritméticos: suma (+), resta (-), multiplicación (*) y división (/). Se muestran a continuación algunos ejemplos:


```python
m = 3 + 1
n = 2
r = m / n
print(r)
type(r)
```

    2.0
    




    float




```python
m = 5
n = 3
r = ((m - n) * 2)
print(r)
```

    4
    

Obsérvese que en la primera celda estamos creando variables de tipo "número entero" (m y n, variables a las que se asignan los valores 4 y 2, respectivamente) y, sin embargo, el resultado contenido en r es 2.0 -un número real-. Esto es así porque el resultado de una expresión en la que existe alguna división siempre es considerado un número real, aun cuando la parte decimal pueda ser cero (como en este caso).

Otro comentario interesante: en la segunda celda hemos utilizado paréntesis para especificar el orden en el que deseamos que se ejecuten las operaciones: queremos que, en primer lugar, se calcule la resta de m y n y, solo después, que el resultado se multiplique por dos. Si no hubiéramos usado los paréntesis el resultado hubiera sido distinto, como puede comprobarse a continuación:


```python
r = (m - n) * 2
print(r)
```

    4
    


```python
r = m - n * 2
print(r)
```

    -1
    

En ésta última celda se calcula primero la multiplicación n * 2 (lo que devuelve como resultado 6) y después se realiza la resta 5 (valor de m) menos 6 (valor de n * 2), dando como resultado el -1 que vemos en la imagen. Esto es así debido a la precedencia de los operadores, es decir, a la diferente prioridad que tienen unos operadores con respecto a otros.

Hay tres operadores algebraicos adicionales:

### Operador //

El operador // divide dos valores y devuelve el número entero más próximo que sea menor o igual al resultado. Esto, cuando el resultado es un número positivo no tiene demasiada complejidad: simplemente se devuelve la parte entera de la división:


```python
7 // 2
```




    3



Sin embargo, cuando el resultado es un número negativo, lo que se devuelve es el entero más próximo pero inferior al resultado:


```python
-7 // 2
```




    -4



En este caso, el resultado de la división es -3.5, por lo que se devuelve el valor -4.

### Operador %

Este operador también divide dos números, pero devuelve el resto de la división -lo que se conoce como *módulo*-. Por ejemplo:


```python
7 % 3
7 - (7 // 3) * 3
```




    1




```python
30 % 3
```




    0



En el primer caso (7 % 3) la parte entera del resultado de la división es 2 y el resto es 1. La segunda expresión es lo mismo, hecho con. otros operadores.

En el segundo caso (30 % 3) la parte entera del resultado de la división es 10 y el resto es 0.

### Operador **

Por último, el operador exponenciación devuelve el resultado de elevar un número a otro. Por ejemplo:


```python
2 ** 3
```




    8




```python
5 ** -1
```




    0.2




```python
7 ** 0
```




    1



## Operadores de comparación

Otro conjunto de operadores son aquellos que se aplican a dos elementos comparándolos y devuelven un resultado booleano (un Verdadero o Falso, o, en lenguaje Python, True o False). Entre estos operadores nos encontramos con la igualdad (==), desigualdad (!=), mayor que (>), menor que (<), mayor o igual que (>=) y menor o igual que (<=).

Algunos ejemplos:


```python
a = 1
print(a)
a == 1
```

    1
    




    True




```python
a != 1
```




    False



Obsérvese que la igualdad se comprueba con dos signos de igualdad ("==") pues, como ya hemos visto, un único signo de igualdad ("=") está reservado para asignar un valor a una variable. La desigualdad se comprueba con el operador "!=", no con "<>" como ocurre en otros lenguajes de programación.


```python
4 > 2
```




    True




```python
5 <= 2
```




    False



## Operadores lógicos

Python también incluye varios operadores lógicos: and, or y not. El primero devuelve True cuando ambos valores son True, el segundo devuelve True cuando algún valor es True, y el tercero devuelve True cuando el valor al que se aplica toma el valor False:


```python
(5 < 4) and (5 > 3) and (5 < 6)
```




    False




```python
(5 > 4) or (5 > 3) or (5 < 6)
```




    True




```python
a = 2
(a < 5) and (a != 3)
```


```python
not (a == 5)
```

## Operadores de pertencia

Este tipo de operadores evalúan si un objeto pertenece a otro. Hay dos: **in** y **not in**, que es el complementario del anterior. El primero (*in*) devuelve *True* cuando el elemento pertenece al segundo. Por ejemplo, si estamos utilizando cadenas de texto:


```python
"Data" in "Python for Data Science"
```




    True




```python
"data" in "Python for Data Science"
```




    False



En este caso las mayúsculas y las minúsculas son consideradas letras distintas, de ahí que en el primer ejemplo se devuelva *True* (pues "*Data*" se encuentra incluido en "*Python for Data Science*") y en el segundo no.

Otro ejemplo utilizando conjuntos (tipo de variable que veremos más adelante): en el primer ejemplo de los dos que siguen se comprueba si el valor 3 pertenece al conjunto s (lo que es cierto). En el segundo se comprueba si el valor 8 pertenece al mismo conjunto s (lo que no es cierto):


```python
s = set([1, 2, 3, 4, 5])
```


```python
3 in s
```




    True




```python
8 in s
```




    False




```python
8 not in s
```




    True



## Operadores de identidad

Esta categoría de operadores comprueban si las dos variables representan el mismo objeto, lo que no es igual que decir que toman el mismo valor. Los dos operadores de identidad disponibles son is y not is. Veamos algunos ejemplos:

Que dos variables tomen el mismo valor las convierte en iguales, pero no necesariamente en idénticas. Si estamos comparando variables enteras, si son iguales, también son idénticas:


```python
m = 3
n = 3
```


```python
m == n
```




    True




```python
m is n
```




    True



Esto es así porque el número 3 al que "apuntan" ambas variables es el mismo. No hay más que un "número tres" en Python. No sabemos dónde se almacena, pero allí donde esté, es único.

Pero si estamos trabajando con listas, por ejemplo, la cosa cambia:


```python
m = ["a", "b"]
n = m
```


```python
m == n
```




    True




```python
m is n
```




    True



En este ejemplo vemos cómo m y n son iguales (ambas variables representan listas que contienen los mismos elementos) pero no son idénticas, porque los elementos que forman la variable m están contenidos en una parte de la memoria del ordenador, y los elementos que forman la variable n están contenidos en otra parte de la memoria del ordenador. Coincide que en ambas partes de la memoria están almacenados los mismos valores, pero se trata de diferentes objetos en diferentes zonas de la memoria al fin y al cabo.

Sin embargo, véase el siguiente ejemplo:


```python
m = ["a", "b"]
n = m
```


```python
m == n
```


```python
m is n
```

Aquí también estamos trabajando con listas, pero ahora m y n son iguales e idénticas ¿por qué? Porque cuando ejecutamos la instrucción n = m estamos diciéndole a Python "haz que n apunte al mismo objeto al que representa m". Podríamos decir que la variable n es un alias de m.
