# Guion de Grabación del Video (5 Minutos) + Guía de Defensa Breve · Equipo 3
**Evidencia:** EVI3-U1: Proyecto de limpieza y exploración de datos (40 % de la Unidad I)  
**Archivo de video a generar:** `EVI3_Equipo-3_Video.mp4` (o enlace de Drive/YouTube «No listado»)  
**Cuaderno a proyectar en pantalla:** `EVI3_Equipo-3_Cuaderno.ipynb` (con todas las celdas ya ejecutadas)  

---

## Recomendaciones antes de grabar (OBS Studio / Zoom / Meet)
1. **Abran `EVI3_Equipo-3_Cuaderno.ipynb` en Jupyter / VS Code / Google Colab con un zoom de 110 % – 125 %** para que las tablas y gráficos se lean con nitidez en el video.
2. **Regla de oro del docente:** **Muestren los resultados (tablas renderizadas y gráficos), NO lean ni desplacen el código línea por línea.** Solo hagan una pausa breve sobre la firma de la función `limpiar_reniec(original)` y el bloque `assert` en la Sección 4.
3. **Distribución equitativa de los 3 integrantes (5:00 minutos exactos):**
   - **Integrante 1 – Edward Mamani Zapana (`00:00 – 01:30` · 1,5 min):** Bloque 1 (Problema y preguntas, `0,5 min`) + Bloque 2 (Datos y diagnóstico de calidad, `1,0 min`).
   - **Integrante 2 – Roger Golber Mamani Panca (`01:30 – 03:15` · 1,75 min):** Bloque 3 (Decisiones de limpieza y reproducibilidad, `1,0 min`) + primera mitad del Bloque 4 (Estadísticas descriptivas y Figuras 1, 2 y 3, `0,75 min`).
   - **Integrante 3 – Kevin Diego Gutierrez Arratia (`03:15 – 05:00` · 1,75 min):** Segunda mitad del Bloque 4 (Evolución temporal, foco en Región Puno y correlaciones de Spearman, `0,75 min`) + Bloque 5 (Conclusiones para decidir, correlación vs. causalidad y limitaciones, `1,0 min`).

---

## Guion Cronometrado Paso a Paso (Qué mostrar y Qué decir)

### BLOQUE 1: Problema y Preguntas de Análisis (`00:00 – 00:30` · 0,5 minutos)
**Narra:** Integrante 1 (Edward Mamani Zapana)

| Tiempo | Qué mostrar en pantalla (Acción visual) | Qué decir (Guion hablado) |
| :---: | :--- | :--- |
| `00:00 – 00:15` | Mostrar el encabezado del cuaderno `EVI3_Equipo-3_Cuaderno.ipynb` (integrantes del Equipo 3 y tabla de ubicación del FO1) y bajar suavemente a la **Sección 1.1 y 1.2**. | *"Buen día, ingeniero. Somos el **Equipo 3**, conformado por Edward Mamani, Roger Mamani y Kevin Gutierrez. Presentamos nuestro proyecto de limpieza y exploración de datos para el **RENIEC – Dirección de Servicios Registrales**, con alcance nacional y foco territorial en la **Jefatura Regional de Puno**."* |
| `00:15 – 00:30` | Enfocar en pantalla las **4 preguntas de análisis (Sección 1.2)** y la **tabla del proceso CRISP-DM (Salida de la Celda [1], Sección 1.3)**. | *"El problema operativo que abordamos es la fuerte asimetría de carga entre oficinas urbanas saturadas y sedes periféricas entre 2023 y 2026. Siguiendo las 6 fases de **CRISP-DM**, planteamos responder: qué departamentos y qué provincias de Puno concentran la demanda, qué peso tienen los trámites de DNI frente a Registros Civiles, cuál es su estacionalidad y cómo se correlacionan los servicios por oficina."* |

---

### BLOQUE 2: Datos y Diagnóstico de Calidad (`00:30 – 01:30` · 1,0 minuto)
**Narra:** Integrante 1 (Edward Mamani Zapana)

| Tiempo | Qué mostrar en pantalla (Acción visual) | Qué decir (Guion hablado) |
| :---: | :--- | :--- |
| `00:30 – 00:55` | Desplazar a la **Sección 2.2** y enfocar la **tabla `diccionario_datos` (Salida de la Celda [2])** donde se ven las 8 variables y sus tipos antes y después. | *"En la Sección 2 documentamos nuestra fuente oficial de Datos Abiertos de RENIEC, que cumple la Ley 29733 al no contener datos personales. El conjunto original tiene **122,527 filas brutas y 8 variables**: variables cualitativas nominales como `LOCAL`, `DEPARTAMENTO`, `PROVINCIA`, `DISTRITO` y `TIPO_TRANSACCION`; `MES` como cualitativa ordinal; y `TRANSACCIONES` como cuantitativa discreta, la cual inicialmente fue mal asignada como texto (`object`) por contener comas de miles y filas de subtotales."* |
| `00:55 – 01:30` | Desplazar a la **Sección 3** y enfocar la **tabla `diagnostico_calidad` (Salida de la Celda [3])** señalando con el cursor la columna `Faltantes (%)` y `Mecanismo de Faltantes`. | *"En el diagnóstico de calidad en la Sección 3 identificamos tres problemas críticos: Primero, más del **53 % de valores faltantes** en `LOCAL`, `DEPARTAMENTO` y `PROVINCIA` bajo un mecanismo **MAR estructural**, causado porque los reportes Excel originales tenían celdas combinadas verticalmente. Segundo, en `DISTRITO` (`55.74 %` de nulos) se combina MAR en 2023–2024 con un mecanismo **MNAR** en 2025–2026, años en los que RENIEC dejó de publicar el distrito. Y tercero, detectamos caracteres corruptos de codificación (`¢` en lugar de `Ó`), **33,943 filas separadoras o subtotales**, y **13,052 valores atípicos por IQR**."* |

---

### BLOQUE 3: Decisiones de Limpieza y Reproducibilidad (`01:30 – 02:30` · 1,0 minuto)
**Narra:** Integrante 2 (Roger Golber Mamani Panca)

| Tiempo | Qué mostrar en pantalla (Acción visual) | Qué decir (Guion hablado) |
| :---: | :--- | :--- |
| `01:30 – 02:00` | Mostrar brevemente la firma de la función `def limpiar_reniec(original)` en la **Sección 4.1 (Celda [4])** y pasar de inmediato al resultado del test `assert` y la **tabla Antes vs. Después en la Sección 4.2 (Salida de la Celda [5])**. | *"Gracias, compañero. En la Sección 4 encapsulamos toda la limpieza en la función modular `limpiar_reniec()` verificada con pruebas `assert` y `np.allclose`. Cada decisión responde al mecanismo diagnosticado: primero aplicamos **forward-fill agrupado por año** para restituir el 100 % de las celdas combinadas sin arrastrar datos de un año a otro; segundo, convertimos `TRANSACCIONES` a entero positivo eliminando las **33,943 filas vacías y subtotales**, quedándonos con **88,584 registros reales**; y tercero, imputamos `'NO REGISTRADO'` en los distritos faltantes de 2025–2026 para no inventar ubicaciones."* |
| `02:00 – 02:30` | Con el cursor sobre la **tabla Antes vs. Después (Salida de la Celda [5])**, señalar las filas `Filas totales`, `Faltantes`, `Media y Mediana` y `Volumen total acumulado`. | *"Respecto a los **13,052 valores atípicos mayores a 745.5 trámites/mes** detectados por IQR, decidimos **conservarlos y etiquetarlos** en la variable `ES_ATIPICO_IQR`, porque no son errores sino sedes metropolitanas reales como Lima o Juliaca; eliminarlos borraría más del 75 % de los trámites del país. Además, creamos variables temporales (`PERIODO`, `TRIMESTRE`), escalados Min-Max, Z-Score y Log10, logrando reducir los faltantes a **0.0 %** y consolidar **51,216,206 trámites** exportados en `EVI3_Equipo-3_Datos_Limpio.csv`."* |

---

### BLOQUE 4: Hallazgos con Estadísticas, Gráficos y Patrones (`02:30 – 04:00` · 1,5 minutos)
**Narran:** Integrante 2 (Roger Mamani · `02:30 – 03:15`) e Integrante 3 (Kevin Gutierrez · `03:15 – 04:00`)

| Tiempo | Qué mostrar en pantalla (Acción visual) | Qué decir (Guion hablado) |
| :---: | :--- | :--- |
| `02:30 – 02:55` | **(Roger Mamani)** Mostrar la **tabla de Estadísticas Descriptivas Nacional vs. Región Puno (Sección 5.1, Salida de Celda [6])** y luego las **Figuras 1 y 2 (Sección 6.1 y 6.2)**. | *"En la Sección 5 vemos por qué era indispensable usar estadística robusta: la media nacional es de **578.17 trámites**, pero la **mediana es de solo 81 trámites** (y **56 en la región Puno**), con un coeficiente de variación de **4.37**. En la **Figura 1** comprobamos que Lima concentra el **38.8 %** del país con **19.88 millones** de trámites. Y en la **Figura 2** hallamos que **Entrega de DNI (44.5 %)** y **Trámite de DNI (34.8 %)** absorben el **79.3 %** de toda la carga operativa de RENIEC."* |
| `02:55 – 03:15` | **(Roger Mamani)** Mostrar la **Figura 3 (Histograma Log10 y Boxplot, Sección 6.3)**. | *"La **Figura 3** en escala logarítmica muestra claramente la brecha entre la mediana de 81 y la media de 578, confirmando en el boxplot que la línea de Identificación DNI supera por un orden de magnitud en mediana y dispersión a los Registros Civiles."* |
| `03:15 – 03:40` | **(Kevin Gutierrez)** Mostrar la **Figura 4 (Evolución anual y mensual, Sección 6.4)** y luego la **Figura 5 (Zoom Regional Puno, Sección 6.5)**. | *"Continuando con el análisis temporal en la **Figura 4**, el volumen anual supera de forma sostenida los **12.6 millones de trámites**, con picos estacionales en **enero, febrero y agosto** donde la mediana sube a 98–100 trámites. Al hacer foco en nuestra **Región Puno (Figura 5)**, que suma **1,642,478 trámites**, descubrimos un patrón clave: solo dos provincias, **San Román con 708,998 trámites (43.2 %)** y **Puno con 421,514 (25.7 %)**, concentran el **68.8 % de toda la demanda regional**, siendo la **Agencia San Román en Juliaca (520 mil)** la sede con mayor carga de todo el departamento."* |
| `03:40 – 04:00` | **(Kevin Gutierrez)** Mostrar la **Tabla Dinámica de Puno (Sección 7.1)** y la **Figura 6 (Matriz de Correlación de Spearman, Sección 7.2)**. | *"Finalmente, en la Sección 7 evaluamos asociaciones con la **correlación por rangos de Spearman**, elegida por su robustez ante atípicos. En la **Figura 6** demostramos una correlación muy fuerte de **+0.848** entre Trámite de DNI y Entrega de DNI por oficina, pero una correlación levemente inversa de **-0.131** con Actas Registrales, ya que las oficinas auxiliares ORAF en hospitales y municipios se dedican casi exclusivamente a nacimientos y defunciones."* |

---

### BLOQUE 5: Conclusiones para Decidir, Causalidad y Limitaciones (`04:00 – 05:00` · 1,0 minuto)
**Narra:** Integrante 3 (Kevin Diego Gutierrez Arratia)

| Tiempo | Qué mostrar en pantalla (Acción visual) | Qué decir (Guion hablado) |
| :---: | :--- | :--- |
| `04:00 – 04:35` | Mostrar la **tabla `hallazgos_decisiones` en la Sección 8.1 (Salida de la Celda [15])**. | *"En la Sección 8 traducimos nuestros hallazgos en **tres decisiones concretas** sin confundir correlación con causalidad: Primero, la alta correlación entre Trámite y Entrega de DNI (+0.848) y la concentración en Juliaca no son causadas por ineficiencia de otras sedes, sino por una **variable confusora demográfica y comercial**; por ello recomendamos **reasignar ventanillas y tótems de entrega automática a la Agencia San Román y al PAP San Miguel en Juliaca**, que hoy superan a la sede de Puno capital. Segundo, dado que la Entrega de DNI representa el **50 % de las atenciones en Puno**, recomendamos **separar ventanillas exclusivas de entrega rápida** de las ventanillas de captura biométrica. Y tercero, reforzar personal temporal en los picos de **enero–febrero y agosto**."* |
| `04:35 – 05:00` | Mostrar la **Sección 8.2 (Limitaciones técnicas y metodológicas)**. | *"Como limitaciones transparentamos tres puntos: primero, la omisión oficial de la columna `DISTRITO` en 2025–2026 (mecanismo MNAR), por lo que las comparaciones de los 4 años deben hacerse a nivel de departamento, provincia y local; segundo, que el año 2026 comprende hasta el tercer trimestre; y tercero, que los datos son conteos mensuales agregados sin tiempos individuales de espera en cola. Con esto concluimos la presentación del Equipo 3. Muchas gracias."* |

---

## Guía de Preparación para la Defensa Breve (Jueves 05/11 · 16:40 a 17:00 h)
El docente elegirá **al azar a uno de los 3 integrantes** y le hará una pregunta sobre cualquier decisión del cuaderno. Aquí tienen las respuestas exactas listas:

1. **«¿Por qué había más de 50 % de valores faltantes en `LOCAL` y `DEPARTAMENTO` y por qué usaron `ffill` en vez de eliminarlos o imputar la moda?»**
   - **Respuesta:** Porque en los reportes originales de Excel de RENIEC las celdas estaban combinadas verticalmente (el nombre del departamento y la oficina solo aparece en la primera fila de su bloque y queda en blanco debajo). Es un mecanismo **MAR estructural**. Si eliminábamos los nulos perdíamos más de la mitad del dataset, y si imputábamos con la moda (Lima) asignábamos trámites de provincias a Lima. El `ffill()` agrupado por `ANIO` restituye exactamente el encabezado de cada bloque.
2. **«¿Por qué en `DISTRITO` imputaron `'NO REGISTRADO'` en vez de usar `ffill` en 2025 y 2026?»**
   - **Respuesta:** Porque en 2025 y 2026 la Dirección de Servicios Registrales dejó de publicar la columna `DISTRITO` en sus archivos CSV (mecanismo **MNAR**). Como nuestro `ffill` está agrupado por `ANIO` (`df.groupby('ANIO')[col].ffill()`), evitamos que el último distrito de diciembre de 2024 se arrastre falsamente a las 22,193 filas de 2025 y 2026, y las etiquetamos honestamente como `'NO REGISTRADO'`.
3. **«¿Cuántos valores atípicos detectaron en `TRANSACCIONES` y por qué no los eliminaron?»**
   - **Respuesta:** Con el criterio de Tukey ($Q_3 + 1.5 \times \text{IQR} = 306 + 1.5 \times 293 = 745.5$) detectamos **13,052 registros atípicos** (y **954** con $|z| > 3$). No los eliminamos porque verificamos que pertenecen a oficinas registrales metropolitanas reales (como Lima, Trujillo, Arequipa o la Agencia San Román en Juliaca). Eliminarlos borraría más del 75 % de los trámites reales del país. En su lugar, creamos la bandera `ES_ATIPICO_IQR`, aplicamos $\log_{10}$ y usamos la **mediana (`81.0`) e IQR (`293.0`)**.
4. **«¿Por qué usaron la correlación de Spearman ($r_s$) y no la de Pearson ($r$)?»**
   - **Respuesta:** Porque `TRANSACCIONES` tiene una asimetría positiva extrema ($\text{skew} = 35.84$, $\text{CV} = 4.37$) con valores que van de 1 a 199,485. Pearson evalúa linealidad estricta y se sesga gravemente con esos valores extremos; en cambio, **Spearman ($r_s$)** trabaja sobre los **rangos ordenados**, midiendo asociación monótona de forma robusta a los outliers.
5. **«¿Qué hace la prueba `assert np.allclose(...)` en la Sección 4.2 de su cuaderno?»**
   - **Respuesta:** Verifica automáticamente la **reproducibilidad**: comprueba que la serie numérica producida por nuestra función modular `limpiar_reniec(df_raw)` coincide exactamente con el archivo limpio exportado `EVI3_Equipo-3_Datos_Limpio.csv`, que tiene exactamente `88,584` filas, `0` nulos y `51,216,206` trámites.

