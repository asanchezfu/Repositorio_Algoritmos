Se realiza un algoritmo en Python 3.6 
Con el objetivo de encontrar la posicion 
de un segmento de un genoma de por medio
de "fuerza bruta" (se comparo por cada 
caracter si la cadena correspondia con
el segmento asignado)

//Complejidad
def find(secuence, target):                     O(1)
  
  initial = 0                                   O(1)
  final = len(target)                           O(1)
  for i in range(len(secuence) - len(target)):  O(n)
    if secuence[i:i+len(target)] == target:	O(n)
      initial = i				O(1)
      final = len(target) + i - 1		O(1)
    break					O(1)
  return initial, final				O(1)

Tenemos O(n)*O(n)*O(1)=O(n^2), complejidad cuadratica