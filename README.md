import numpy as np
import os
import msvcrt
# Funciones para operaciones con matrices
def ingresar_valores(mat):
    filas, columnas = mat.shape
    print(f'\n__________________ MATRIZ ________________')
    for f in range(filas):
        for c in range(columnas):
            mat[f][c] = float(input(f'Dato [{f}][{c}]: '))
def mostrar_matriz(mat):
    print(mat)
def suma_matrices(matA, matB):
    return np.add(matA, matB)
def resta_matrices(matA, matB):
    return np.subtract(matA, matB)
def multiplicacion_matrices(matA, matB):
    return np.dot(matA, matB)
def determinante_matriz(mat):
    return np.linalg.det(mat)
def traspuesta_matriz(mat):
    return np.transpose(mat)
def inversa_matriz(mat):
    return np.linalg.inv(mat)
def escalar_matriz(mat, escalar):
    return mat * escalar
def matrices():
    opcion = 0
    matA = None
    matB = None
    matC = None
    while opcion != 11:
        os.system('cls' if os.name == 'nt' else 'clear')
        print('Cálculo de Matrices S.A.\nSeleccione su opción:\n')
        print('1. Definir renglones y columnas')
        print('2. Ingresar valores a las matrices')
        print('3. Mostrar matrices')
        print('4. Suma de matrices')
        print('5. Resta de matrices')
        print('6. Multiplicación de matrices')
        print('7. Determinante de matrices')
        print('8. Traspuesta de matrices')
        print('9. Inversa de matrices')
        print('10. Escalar por matriz')
        print('11. Salir\n')
        opcion = int(input('Seleccione una opción: '))
        if opcion == 1:
            filas = int(input('FILAS: '))
            col = int(input('COLUMNAS: '))
            matA = np.zeros((filas, col))
            matB = np.zeros((filas, col))
            matC = np.zeros((filas, col))
        elif opcion == 2:
            print('Ingresar valores para la matriz A:')
            ingresar_valores(matA)
            print('Ingresar valores para la matriz B:')
            ingresar_valores(matB)
        elif opcion == 3:
            print('Matriz A:')
            mostrar_matriz(matA)
            print('Matriz B:')
            mostrar_matriz(matB)
            print('Presione una tecla para continuar...')
            msvcrt.getch()
        elif opcion == 4:
            matC = suma_matrices(matA, matB)
            print('Resultado de la suma de matrices:')
            mostrar_matriz(matC)
            print('Presione una tecla para continuar...')
            msvcrt.getch()
        elif opcion == 5:
            matC = resta_matrices(matA, matB)
            print('Resultado de la resta de matrices:')
            mostrar_matriz(matC)
            print('Presione una tecla para continuar...')
            msvcrt.getch()
        elif opcion == 6:
            try:
                matC = multiplicacion_matrices(matA, matB)
                print('Resultado de la multiplicación de matrices:')
                mostrar_matriz(matC)
            except ValueError as e:
                print(f'Error: {e}')
            print('Presione una tecla para continuar...')
            msvcrt.getch()
        elif opcion == 7:
            try:
                detA = determinante_matriz(matA)
                detB = determinante_matriz(matB)
                print('Determinante de la matriz A:', detA)
                print('Determinante de la matriz B:', detB)
            except np.linalg.LinAlgError as e:
                print(f'Error: {e}')
            print('Presione una tecla para continuar...')
            msvcrt.getch()
        elif opcion == 8:
            print('Traspuesta de la matriz A:')
            mostrar_matriz(traspuesta_matriz(matA))
            print('Traspuesta de la matriz B:')
            mostrar_matriz(traspuesta_matriz(matB))
            print('Presione una tecla para continuar...')
            msvcrt.getch()
        elif opcion == 9:
            try:
                invA = inversa_matriz(matA)
                invB = inversa_matriz(matB)
                print('Inversa de la matriz A:')
                mostrar_matriz(invA)
                print('Inversa de la matriz B:')
                mostrar_matriz(invB)
            except np.linalg.LinAlgError as e:
                print(f'Error: {e}')
            print('Presione una tecla para continuar...')
            msvcrt.getch()
        elif opcion == 10:
            escalar = float(input('Ingrese el escalar: '))
            print('Resultado de escalar la matriz A:')
            mostrar_matriz(escalar_matriz(matA, escalar))
            print('Resultado de escalar la matriz B:')
            mostrar_matriz(escalar_matriz(matB, escalar))
            print('Presione una tecla para continuar...')
            msvcrt.getch()
        elif opcion == 11:
            print('Hasta pronto')
        else:
            print('Opción no válida')
            print('Presione una tecla para continuar...')
            msvcrt.getch()
matrices()


