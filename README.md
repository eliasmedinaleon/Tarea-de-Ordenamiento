# Tarea-de-Ordenamiento

4. Resultados
----------------------------------------------------------------------------------------
Tamaño de entrada      Búsqueda Líneal     Búsqueda Binaria     Búsqueda Trinaria
10^5                   15.44               0.158                0.153
10^6                   185.52              0.258                0.214
10^7                   2,092.05            0.586                0.390
10^8                   41,006.80           2.286                1.303
----------------------------------------------------------------------------------------

6. Análisis de resultados
Comportamiento observado
La búsqueda lineal crece de forma proporcional a n, al pasar de 10⁵ a 10⁸ elementos, su tiempo promedio pasa de 15.44 a 41 006.80, es decir, un incremento de aproximadamente 2 656×, consistente con un crecimiento O(n). Las búsquedas binaria y trinaria, en cambio, crecen de forma mucho más lenta, al mismo incremento de n (×1000), la búsqueda binaria pasa de 0.158 a 2.286 (×14.5) y la trinaria de 0.153 a 1.303 (×8.5), ambos incrementos cercanos al comportamiento logarítmico esperado, no al lineal.

Análisis matemático
Para n = 10⁸, log₂(n) = 26.6 comparaciones en el peor caso para la búsqueda binaria, mientras que log₃(n) = 16.8 iteraciones para la trinaria, sin embargo, cada iteración de la trinaria requiere hasta 4 comparaciones (dos de igualdad y dos de orden) contra 1-2 de la binaria. Esto hace que el número total de comparaciones en el peor caso sea del mismo orden de magnitud entre ambas, aproximadamente 2·log₂ n para la binaria frente a 4·log₃ n para la trinaria. O sea, la binaria indica menos comparaciones totales en el peor caso teórico.

Diferencias
Aunque ambos algoritmos son O(log n), en esta implementación y en este entorno de ejecución la búsqueda trinaria resultó más rápida en tiempo que la binaria en los cuatro tamaños probados (por ejemplo, en n = 10⁸: 1.303 trinaria vs. 2.286 binaria). Esto muestra que el orden asintótico (Big-O) no es suficiente para predecir el desempeño real de dos algoritmos que pertenecen a la misma clase de complejidad.
El resultado real depende de factores que el conteo de comparaciones por sí solo no captura, el número de iteraciones realizadas, la localidad de referencia y el comportamiento de la caché del procesador al acceder a los datos, las optimizaciones que aplica el compilador, y la predicción de saltos de la CPU, que penaliza de forma distinta cada patrón de comparaciones.
Conclusión

Es una pregunta trampa porque no tiene una única respuesta absoluta, depende de qué se esté comparando. Si el criterio es la complejidad asintótica, la búsqueda lineal siempre pierde frente a las otras dos para n grande, y binaria y trinaria son asintóticamente equivalentes (ambas O(log n)), por lo que la más rápida no puede determinarse sólo con Big-O. Si el criterio es el tiempo real medido, en esta implementación y hardware la búsqueda trinaria fue la más rápida en los cuatro tamaños evaluados, seguida de la binaria y muy por detrás la lineal. La lección central es que la complejidad computacional predice cómo escala el tiempo con n, pero no predice con precisión el tiempo absoluto entre dos algoritmos de la misma clase asintótica: eso depende de la implementación concreta y del comportamiento del hardware en tiempo de ejecución, por lo que la experimentación es indispensable para elegir un algoritmo en la práctica.

