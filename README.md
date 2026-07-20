# pseudocodigo.txt.// ==========================================
// MÓDULO 1: Leer datos con validación (In-place)
// ==========================================
PROCEDIMIENTO leerDatos(temp_arr[], n)
    VARIABLES: i, nota
    PARA i DESDE 0 HASTA n - 1 HACER
        REPETIR
            IMPRIMIR "Ingrese la nota del estudiante ", i + 1, ":"
            LEER nota
            SI nota < 0 O nota > 10 ENTONCES
                IMPRIMIR "Nota inválida. Debe estar entre 0 y 10."
            FIN_SI
        HASTA QUE nota >= 0 Y nota <= 10
        temp_arr[i] = nota // Modificación in-place
    FIN_PARA
FIN_PROCEDIMIENTO

// ==========================================
// MÓDULO 2: Ordenamiento Bubble Sort Optimizado
// ==========================================
PROCEDIMIENTO ordenarDatos(temp_arr[], n)
    VARIABLES: i, j, aux, huboIntercambio
    PARA i DESDE 0 HASTA n - 2 HACER
        huboIntercambio = FALSO
        PARA j DESDE 0 HASTA n - i - 2 HACER
            SI temp_arr[j] > temp_arr[j + 1] ENTONCES
                // Intercambio de valores
                aux = temp_arr[j]
                temp_arr[j] = temp_arr[j + 1]
                temp_arr[j + 1] = aux
                huboIntercambio = VERDADERO
            FIN_SI
        FIN_PARA
        // Si no hubo intercambios, el arreglo ya está ordenado
        SI huboIntercambio == FALSO ENTONCES
            RETORNAR
        FIN_SI
    FIN_PARA
FIN_PROCEDIMIENTO

// ==========================================
// MÓDULO 3: Función de cálculo (Promedio)
// ==========================================
FUNCIÓN calcularPromedio(temp_arr[], n) : Real
    VARIABLES: i, suma, prom
    suma = 0.0
    PARA i DESDE 0 HASTA n - 1 HACER
        suma = suma + temp_arr[i]
    FIN_PARA
    prom = suma / n
    RETORNAR prom
FIN_FUNCIÓN

// ==========================================
// MÓDULO 4: Función de Búsqueda Binaria
// ==========================================
FUNCIÓN buscarNota(temp_arr[], n, elementoBuscado) : Entero
    VARIABLES: izq, der, centro
    izq = 0
    der = n - 1
    MIENTRAS izq <= der HACER
        centro = (izq + der) / 2
        SI temp_arr[centro] == elementoBuscado ENTONCES
            RETORNAR centro // Retorna el índice donde se encontró
        SINO
            SI elementoBuscado < temp_arr[centro] ENTONCES
                der = centro - 1
            SINO
                izq = centro + 1
            FIN_SI
        FIN_SI
    FIN_MIENTRAS
    RETORNAR -1 // Retorna -1 si no se encuentra
FIN_FUNCIÓN

// ==========================================
// MÓDULO 5: Procedimiento para mostrar reporte
// ==========================================
PROCEDIMIENTO mostrarReporte(temp_arr[], n, promedio, posBusqueda)
    VARIABLES: i
    IMPRIMIR "======= REPORTE FINAL DE CALIFICACIONES ======="
    IMPRIMIR "Notas ordenadas de menor a mayor:"
    PARA i DESDE 0 HASTA n - 1 HACER
        IMPRIMIR "Estudiante ", i + 1, ": ", temp_arr[i]
    FIN_PARA
    IMPRIMIR "-----------------------------------------------"
    IMPRIMIR "Promedio general del grupo: ", promedio
    SI posBusqueda != -1 ENTONCES
        IMPRIMIR "La nota buscada se encuentra en la posición: ", posBusqueda
    SINO
        IMPRIMIR "La nota buscada no fue registrada en el sistema."
    FIN_SI
    IMPRIMIR "==============================================="
FIN_PROCEDIMIENTO

// ==========================================
// ALGORITMO PRINCIPAL
// ==========================================
ALGORITMO Principal
    VARIABLES: N, promedioGrupo, posicion, notaABuscar
    IMPRIMIR "Ingrese la cantidad de estudiantes:"
    LEER N
    
    VARIABLES: misNotas[N] // Declaración del arreglo de tamaño N
    
    // Llamadas a los módulos en el orden correcto
    LEERDatos(misNotas, N)
    ordenarDatos(misNotas, N)
    promedioGrupo = calcularPromedio(misNotas, N)
    
    IMPRIMIR "Ingrese la nota exacta que desea buscar en el registro:"
    LEER notaABuscar
    posicion = buscarNota(misNotas, N, notaABuscar)
    
    mostrarReporte(misNotas, N, promedioGrupo, posicion)
FIN_ALGORITMO
code:Agregar pseudocódigo modular
