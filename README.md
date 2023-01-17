# Homework_clase1
# Práctica Clase 1 
1) Crear una función capaz de convertir números enteros de base 10 a base 2. Debe recibir como parámetro el número a convertir<br>
Consideraciones:<br> 
a. Tratar de resolverlo sin usar la función format(nro,"b")<br>
b. El pdf "conversion-de-decimal-a-binario.pdf" puede servir de ayuda.

def NumeroBinario(numero):
    '''
    Esta función recibe como parámetro un número entero mayor ó igual a cero y lo devuelve en su 
    representación binaria. Debe recibir y devolver un valor de tipo entero.
    En caso de que el parámetro no sea de tipo entero y mayor a -1 retorna nulo.
    '''
    if type(numero)!= int or numero < 0: return None
    if numero < 2:
        return numero
    else:
        return int(str(NumeroBinario(numero//2)) + str(numero%2)) 
        


##Otra manera

def NumeroBinario(numero):
    if type(numero) != int or numero<=-1:
        return None
    if numero <1:
        return numero
    binario = ''
    while numero >= 1:
      binario = str(numero%2) + binario
      numero //=2
    return int(binario)
    


2) Convertir de decimal a binario las fracciones 1/2, 1/3, 1/4, 1/5, 1/6, 1/7, 1/8, 1/9. Luego analizar los resultados y observar
qué particularidad se encuentra en los mismos. Se puede usar Python o una calculadora, lo importante es ver si hay algo que podemos notar...

Salida esperada:
* Fraccion 1 / 2 :  0.5  y En binario:  0.1
* Fraccion 1 / 3 :  0.3333333333333333  y En binario:  0.010101010101010101010101
* Fraccion 1 / 4 :  0.25  y En binario:  0.01
* Fraccion 1 / 5 :  0.2  y En binario:  0.001100110011001100110011
* Fraccion 1 / 6 :  0.16666666666666666  y En binario:  0.001010101010101010101010
* Fraccion 1 / 7 :  0.14285714285714285  y En binario:  0.001001001001001001001001
* Fraccion 1 / 8 :  0.125  y En binario:  0.001
* Fraccion 1 / 9 :  0.1111111111111111  y En binario:  0.000111000111000111000111

def binarizar_punto_flotante(numero):
    flotante = numero-int(numero)
    pos = 1
    salida = 0.0
    while flotante < 1:
        flotante *=2
        salida = salida + int(flotante)*10**(-1*pos)
        if flotante >1: 
            flotante -=1
        pos+=1
        if pos==20: break
    return NumeroBinario(int(numero))+ salida
