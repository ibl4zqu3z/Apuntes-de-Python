# Variables

Ya hemos visto cómo podemos crear y asignar un valor a una variable: basta con escribir su nombre, un signo igual y, a continuación, el valor o la expresión que define el valor.

Por ejemplo, podemos crear dos variables m y n, asignarles el valor 3 y 4 respectivamente, crear una nueva variable, p, y asignar a ésta la suma de m y n.

Observa a continuación que la función **print** imprime el valor de la variable que se incluya como argumento:


```python
m = 3
n = 4
p = m + n
print(p)
```

    7
    

Una variable tiene siempre un tipo asignado. Las variables m, n y p anteriores son, por ejemplo, de tipo "**número entero**" (representado como "*int*" en Python). Podemos visualizar el tipo de una variable con la función **type**:


```python
type(p)
```




    int



Pero hay otros tipos de variables. Dentro del bloque de variables numéricas tenemos, además de los números enteros, los **números reales** ("float") y los **números complejos** ("complex").

Por cierto, fíjate que el separador decimal es el punto, no la coma. La coma está reservada para separar elementos.


```python
a = 5.7
type(a)
a
```




    5.7




```python
b = 3 - 2j
type(b)
```




    complex



## Impresión de variables

Otro aspecto a destacar es que, en las dos celdas anteriores, se está imprimiendo el tipo de la variable sin que estemos usando la función print. Por defecto, la función type no imprime el tipo de la variable, solo lo identifica. Así, teóricamente, si quisiéramos crear una variable e imprimir su tipo deberíamos ejecutar el siguiente código:


```python
a = 5.7
print(type(a))
```

    <class 'float'>
    

Sin embargo, en Jupyter se imprime siempre por defecto la última expresión que haya en cada celda. O, dicho con otras palabras, si queremos mostrar, por ejemplo, el contenido de la variable a, podemos usar cualquiera de los dos métodos siguientes:


```python
a
```




    5.7




```python
print(a)
a
b
```

    5.7
    




    (3-2j)



Pero recuerda que el método de no incluir la función print solo funciona cuando la expresión es la última de una celda. Y, en todo caso, ten en cuenta también que el resultado devuelto por la celda no es exactamente el mismo si usamos la función print o si no la usamos. Por ejemplo:


```python
type(a)
```




    float




```python
print(type(a))
```

    <class 'float'>
    

Podemos distinguir estos dos tipos de salidas en Jupyter gracias al mensaje "Out" que se muestra cuando no hay un **print** explícito. 

## Otros tipos de variables (texto, booleanas)

Tenemos variables tipo **texto** ("str"):


```python
c = "Python"
type(c)
```




    str



También hay variables tipo **booleano** (que solo pueden tomar los valores True/False):


```python
d = True
type(d)
```




    bool



# Tipos complejos (listas, tuplas, conjuntos y diccionarios)

Hasta aquí hemos visto tipos simples (**números enteros, números reales, números complejos, textos y booleanos**) pero Python también proporciona tipos más complejos, como **las listas, las tuplas, los conjuntos y los diccionarios**. Aunque veremos estos tipos con más profundidad un poco más adelante, echemos un vistazo a algunos ejemplos.

Una lista es una agrupación ordenada de elementos de cualquier otro tipo:


```python
esta_es_mi_primera_lista = [1, 2.3, "Python", True]
type(esta_es_mi_primera_lista)
```




    list




```python
print(esta_es_mi_primera_lista)
```

    [1, 2.3, 'Python', True]
    


```python
esta_es_mi_primera_lista[4] = "a todos"
```


    ---------------------------------------------------------------------------

    IndexError                                Traceback (most recent call last)

    Cell In[19], line 1
    ----> 1 esta_es_mi_primera_lista[4] = "a todos"
    

    IndexError: list assignment index out of range



```python
esta_es_mi_primera_lista.append("ECI")
esta_es_mi_primera_lista
```




    [1, 2.3, 'Python', True, 'ECI']



Un tipo semejante a la lista es la tupla. La mayor diferencia es que los elementos de una lista pueden ser modificados, mientras que la tupla es inmutable (no se puede modificar):


```python
f = (1, 2.3, "Python", True)
type(f)
```




    tuple




```python
print(f)
f[0]=1
```

    (1, 2.3, 'Python', True)
    


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    Cell In[26], line 2
          1 print(f)
    ----> 2 f[0]=1
    

    TypeError: 'tuple' object does not support item assignment


Las listas y las tuplas son agrupaciones ordenadas de elementos en las que, por ejemplo, un mismo elemento puede aparecer varias veces. El conjunto es diferente en estos aspectos: no hay un orden en los elementos que lo componen, y éstos solo pueden aparecer una vez:


```python
g = {1, 2.3, "Python", True}
type(g)
```




    set




```python
print(g)
```

    {1, 2.3, 'Python'}
    


```python
g.add(5)
g
```




    {1, 2.3, 5, 'Python'}



Por último, un diccionario es una especie de lista cuyos elementos (a los que se llama "valores") tienen asignados un nombre (a los que se llama "claves"):


```python
dias = {"enero": 31, "febrero": 28, "marzo": 31}
type(dias)
```




    dict




```python
print(dias)
dias["febrero"]
```

    {'enero': 31, 'febrero': 28, 'marzo': 31}
    




    28



## Creación de variables

Hay que destacar el hecho de que, para usar una variable, no hace falta declararla previamente, ni tampoco es necesario indicar el tipo: si asignamos un valor a una variable, se crea -si no existía-, o se modifica su valor -si ya existía- y, en ambos casos, se le asigna el tipo adecuado.

También debes tener en cuenta que las mayúsculas y las minúsculas son consideradas letras diferentes y que, por lo tanto, dos nombres como ventas y Ventas representarían variables distintas.

A la hora de dar un nombre a una variable, deberás tener en cuenta algunas reglas:

* El primer carácter deberá ser una letra minúscula, una letra mayúscula o "_". Esto significa que, por ejemplo, no podemos usar variables cuyo nombre comience por un número.
* Los caracteres "$" y "?" no están permitidos.
* Los nombres de variables no pueden comenzar ni terminar por dos caracteres "_" (este tipo de nombres están reservados por Python).
* Tampoco podrán usarse como nombres aquellos identificadores reservados de Python como "for" o "break".
Se muestra a continuación el conjunto de palabras reservadas de Python:

![image.png](attachment:image.png)

## Tipado dinámico

Otra de las características de las variables en Python es que pueden tomar valores de distinto tipo a lo largo del código, propiedad que se conoce como tipado dinámico. En el siguiente ejemplo la variable a comienza siendo de tipo entero:


```python
a = 0.1
print(a)
print(type(a))
```

    0.1
    <class 'float'>
    

Ahora pasa a ser una cadena de texto:


```python
a = "Tipado dinámico"
print(type(a))
```

    <class 'str'>
    

A continuación, un booleano (recibe el resultado de evaluar la expresión 4 > 3, lo que devuelve el valor *True*):


```python
a = 4 < 3
print(a)
print(type(a))
```

    False
    <class 'bool'>
    

... y, por último, en pasa a ser de tipo "número complejo":


```python
a = 3 - 4j
print(a)
print(type(a))
```

    (3-4j)
    <class 'complex'>
    
