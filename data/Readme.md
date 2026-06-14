
## Conclusión - Sprint 2

### Relación entre imágenes y datos tabulares

En este sprint integramos dos fuentes de datos: el dataset
de multas del Sprint 1 y las imágenes de los radares.
Cruzamos ambas usando OCR para determinar qué multas tienen
evidencia visual válida. Notamos que la relación no es
uno a uno: hay multas sin imagen asociada e imágenes que
no corresponden a ninguna multa del dataset.

### Pipeline de procesamiento implementado

Construimos un pipeline de cuatro etapas con OpenCV:
conversión a grises, suavizado gaussiano, detección de
bordes con Canny y extracción OCR con Tesseract.
Para mejorar la lectura de patentes agregamos cierre
morfológico rectangular, sharpening con kernel 3x3,
umbralización OTSU en múltiples variantes y filtrado
geométrico por área y relación de aspecto (2.0 a 6.5).
Recortamos el 20% superior en imágenes de tipo plates
para eliminar texto decorativo que confundía al OCR.

### Impacto de los registros con hora 00:00 y fecha 1932-01-01

Decidimos conservar estas filas porque representan multas
reales cuyo valor temporal no pudo parsearse en el Sprint 1.
Participan del cruce con imágenes y pueden tener
coincidencia visual, pero sus fechas y horas no son
confiables para análisis cronológico. Cualquier métrica
por franja horaria o período que las incluya debe
interpretarse con precaución.

### Dificultades encontradas

La principal dificultad fue la variedad de las imágenes:
patentes europeas, americanas, con distintos colores de
fondo, stickers superpuestos y texto de contexto sobre
la placa. También encontramos archivos .QOI y .JP2 que
OpenCV no puede leer y tuvimos que filtrarlos durante
la descompresión del dataset.

### Multas sin evidencia visual

Una parte del dataset no obtuvo coincidencia con ninguna
imagen. Las causas pueden ser: que la patente no figure
en el dataset, que el OCR no haya podido extraer texto
legible por condiciones de la imagen, o que el formato
detectado difiera del registrado (con o sin espacios
o guiones). El umbral de similitud del 80% por LCS
de izquierda a derecha fue el criterio de aceptación.

### Conclusión general

El trabajo de este sprint nos permitió vincular la
evidencia fotográfica con los registros administrativos.
La arquitectura de pipeline por etapas que desarrollamos
facilita iteraciones futuras: ajustando parámetros de
recorte, umbral de match o incorporando modelos OCR
especializados se puede mejorar la cobertura de forma
incremental.

## Conclusión - Sprint 2

### Relación entre imágenes y datos tabulares

En este sprint integramos dos fuentes de datos: el dataset
de multas del Sprint 1 y las imágenes de los radares.
Cruzamos ambas usando OCR para determinar qué multas tienen
evidencia visual válida. Notamos que la relación no es
uno a uno: hay multas sin imagen asociada e imágenes que
no corresponden a ninguna multa del dataset.

### Pipeline de procesamiento implementado

Construimos un pipeline de cuatro etapas con OpenCV:
conversión a grises, suavizado gaussiano, detección de
bordes con Canny y extracción OCR con Tesseract.
Para mejorar la lectura de patentes agregamos cierre
morfológico rectangular, sharpening con kernel 3x3,
umbralización OTSU en múltiples variantes y filtrado
geométrico por área y relación de aspecto (2.0 a 6.5).
Recortamos el 20% superior en imágenes de tipo plates
para eliminar texto decorativo que confundía al OCR.

### Impacto de los registros con hora 00:00 y fecha 1932-01-01

Decidimos conservar estas filas porque representan multas
reales cuyo valor temporal no pudo parsearse en el Sprint 1.
Participan del cruce con imágenes y pueden tener
coincidencia visual, pero sus fechas y horas no son
confiables para análisis cronológico. Cualquier métrica
por franja horaria o período que las incluya debe
interpretarse con precaución.

### Dificultades encontradas

La principal dificultad fue la variedad de las imágenes:
patentes europeas, americanas, con distintos colores de
fondo, stickers superpuestos y texto de contexto sobre
la placa. También encontramos archivos .QOI y .JP2 que
OpenCV no puede leer y tuvimos que filtrarlos durante
la descompresión del dataset.

### Multas sin evidencia visual

Una parte del dataset no obtuvo coincidencia con ninguna
imagen. Las causas pueden ser: que la patente no figure
en el dataset, que el OCR no haya podido extraer texto
legible por condiciones de la imagen, o que el formato
detectado difiera del registrado (con o sin espacios
o guiones). El umbral de similitud del 80% por LCS
de izquierda a derecha fue el criterio de aceptación.

### Conclusión general

El trabajo de este sprint nos permitió vincular la
evidencia fotográfica con los registros administrativos.
La arquitectura de pipeline por etapas que desarrollamos
facilita iteraciones futuras: ajustando parámetros de
recorte, umbral de match o incorporando modelos OCR
especializados se puede mejorar la cobertura de forma
incremental.

## Conclusión - Sprint 3

### Integración de persistencia relacional
En este sprint migramos de archivos CSV a una base de datos
relacional SQLite gestionada con el ORM SQLAlchemy. El modelo
contempla cuatro entidades: Vehiculo, Radar, Multa y Evidencia,
con relaciones 1:N y 1:0..1 según el dominio del problema.
Esto permite consultas estructuradas eficientes y garantiza
integridad referencial que los CSV no podían ofrecer.

### Control de versiones de datos con DVC
Los archivos binarios (imágenes y CSV pesados) se migraron
de Git a DVC apuntando a un remote local. Esta separación
es fundamental: Git gestiona el código y los metadatos
(.dvc), mientras DVC gestiona los datos. En producción
el remote sería S3 o GCS, pero el flujo es idéntico.

### Búsqueda vectorial con ChromaDB y OpenCLIP
Se implementó un pipeline de búsqueda por similitud visual:
OpenCLIP transforma cada imagen en un vector de 512 dimensiones
y ChromaDB permite consultas por distancia coseno. Esto
habilita identificar un vehículo a partir de una foto sin
depender de OCR, siendo más robusto ante imágenes de baja
calidad o patentes dañadas.

### Limitaciones y trabajo futuro
El dataset de imágenes con evidencia es reducido (14 matches).
Una colección vectorial mayor mejoraría la precisión de la
búsqueda. También sería valioso integrar ambas bases de datos
para actualizar automáticamente la BD relacional cuando se
encuentra un match vectorial nuevo.
