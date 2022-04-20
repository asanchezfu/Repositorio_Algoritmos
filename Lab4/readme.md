### Lab 4 - Algoritmos UNAL - 

Este laboratorio grupal consistió en implementar dos tipos de algoritmos: *Fuerza Bruta* y *Algoritmo Voraz de bisección*  para encontrar la raíz de la función:
**x^5 - 59x^4 + 35x^3 - 250x^2 + x - 70**

##### Análisis y cálculo de complejidad

###### Algoritmo de Fuerza Bruta

```
def func(x):                                                         O(1)
  y = x^5 - 59·x^4 + 35·x^3 - 250·x^2 + x - 70
  return y

#Brute Force
def f_bruta(i, f):                                                   **O(n)**  
x = i                                                                 O(1)
  while x <= f:                                                       O(n)
    value = func(x)                                                   O(1)
    if value == 0:                                                    O(1)
      return x                                                        O(1)
    prev_val = func(round(x - 0.0001,4))                              O(1)
    if (prev_val·value < 0):                                          O(1)
      return x                                                        O(1)                                
    x += 0.0001                                                       O(1)
    x = round(x,4)                                                    O(1)
  return "No tiene raíz"                                              O(1)
```

Vemos que el algoritmo de *fuerza bruta* tiene complejidad **O(n)**, donde n es la longitud de valores a evaluar en el intervalo. En este caso n correspondería a  2000 (enteros en el intervalo)·10000(precisión) = 20'000.000. Así, este algoritmo depende tanto de la longitud del intervalo como de la precisión que se desee manejar en la respuesta y tiene complejidad lineal.
Con ayuda de la librería time de python, se calculó que la ejecución de este algoritmo fue de *33.2 s* aprox.

###### Algoritmo Voraz (Bisección)

```
def biseccion_alg (xi, xf, er):                                       **O(log n)**                                
  x = sym.Symbol('x')                                                 O(1)
  func = x^5 - 59·x^4 + 35·x^3 - 250·x^2 + x - 70                     O(1)
  if (func.subs(x,xi) * func.subs(x,xf) >= 0):                        O(1)
        print("No hay raíz en el intervalo seleccionado")             O(1)
        return                                                        O(1)
  while True:                                                         O(log n)
    xm = (xi+xf)/2                                                    O(1) --- Aquí se produce la bisección y se reduce la complejidad del algoritmo a log base 2 de n
    mid_val = func.subs(x,xm)                                         O(1)
    if mid_val == 0:                                                  O(1)
      return xm                                                       O(1)
      break                                                           O(1)
    elif abs((xm-xi)) <= er or abs(mid_val) <= er:                    O(1)
      return xm                                                       O(1)
      break                                                           O(1)
    if (func.subs(x,xi) * mid_val < 0):                               O(1)
      xf=xm                                                           O(1)
    elif (func.subs(x,xf) * mid_val < 0):                             O(1)
      xi=xm                                                           O(1)
```

Por otro lado, el algoritmo voraz de bisección resulta ser más óptimo para encontrar la raíz de una función, pues su complejidad es **O(log n)**, logarítmica. Sin embargo, la precisión deseada también puede incrementar el tiempo de ejecución.
Para este algoritmo se obtuvo un tiempo de ejecución de *0.006086 s* aprox.
