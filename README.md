# Sistema de Gestión y Análisis de Calificaciones

Este sistema resuelve el problema de la administración, ordenamiento y análisis estadístico de las calificaciones finales de un grupo de estudiantes. El sistema está compuesto por cinco módulos interconectados que se ejecutan de manera secuencial. 

En primer lugar, el módulo de lectura recibe y valida las notas ingresadas por el usuario. Posteriormente, el módulo de ordenamiento organiza las calificaciones de forma ascendente para facilitar su visualización. A continuación, el módulo de cálculo procesa los datos para obtener el promedio general del grupo. Luego, el módulo de búsqueda permite localizar una calificación específica dentro del arreglo. Finalmente, el módulo de reporte genera un resumen detallado con los resultados en la pantalla.

Las entradas del sistema consisten en un arreglo de números flotantes que representan las notas y el valor específico a buscar. Las salidas corresponden al arreglo completamente ordenado, el promedio del grupo, la posición del elemento buscado y el reporte final en texto.## 3. Análisis de Complejidad Big O

| Módulo | Complejidad | Justificación |
| :--- | :--- | :--- |
| `leerDatos` | $O(n)$ | Contiene un único ciclo `PARA` que recorre y valida los datos exactamente $n$ veces, donde $n$ es la cantidad de estudiantes. |
| `ordenarDatos` | $O(n^2)$ | Utiliza el método Bubble Sort que en el peor de los casos posee dos ciclos anidados iterando sobre el tamaño del arreglo. |
| `calcularPromedio`| $O(n)$ | Recorre de manera lineal el arreglo mediante un ciclo para acumular la suma de todos los elementos. |
| `buscarNota` | $O(\log n)$ | Implementa búsqueda binaria, la cual reduce a la mitad el espacio de búsqueda en cada iteración del ciclo `MIENTRAS`. |
| `mostrarReporte` | $O(n)$ | Posee un bucle lineal para imprimir secuencialmente cada uno de los elementos del arreglo ordenado. |

---

## 4. Tabla de Pruebas

| Caso de Prueba | Categoría | Datos de Entrada | Resultado Esperado | Resultado Obtenido |
| :--- | :--- | :--- | :--- | :--- |
| **Caso 1** | Flujo Típico / Normal | Cantidad: `3`<br>Notas: `[8.5, 6.0, 9.0]`<br>Buscar: `6.0` | Notas ordenadas: `[6.0, 8.5, 9.0]`<br>Promedio: `7.83`<br>Posición búsqueda: `0` | Exitoso. Muestra el reporte ordenado y la posición correcta en el arreglo. |
| **Caso 2** | Caso Límite (Extremos) | Cantidad: `2`<br>Notas: `[0.0, 10.0]`<br>Buscar: `10.0` | Notas ordenadas: `[0.0, 10.0]`<br>Promedio: `5.0`<br>Posición búsqueda: `1` | Exitoso. Valida correctamente las notas en los extremos permitidos (0 y 10). |
| **Caso 3** | Caso Error (Sin resultado) | Cantidad: `3`<br>Notas: `[7.0, 5.5, 8.0]`<br>Buscar: `4.0` | Notas ordenadas: `[5.5, 7.0, 8.0]`<br>Promedio: `6.83`<br>Posición búsqueda: `-1` | Exitoso. Identifica que el elemento no existe y el módulo de búsqueda retorna `-1`. |Doc: Agregar descripción y tablas de pruebas
