# Changelog

## [Sprint 1] - Ejercicio 01
### Added
- Inicializacion del repositorio Git en rama Sprint_1.
- Creacion de la estructura de directorios del proyecto.
- Creacion de README.md con objetivo e introduccion.
- Creacion de CHANGELOG.md.

## [Sprint 1] - Ejercicio 04
### Added
- Clase FineAnalyzer con encapsulamiento del DataFrame limpio.
- Metodo ranking_patentes: top 5 patentes mas multadas.
- Metodo ranking_horarios: top 5 horarios con mas multas.
- Metodo exceso_promedio: exceso medio como % sobre velocidad maxima.
- Metodo exceso_real_promedio: exceso medio en km/h.
- Metodo multas_por_ubicacion: conteo de multas por ubicacion.

## [Sprint 1] - Punto 07
### Added
- Redaccion de la conclusion del analisis en README.md.

## [Sprint 2] - Ejercicio 01
### Added
- Rama Sprint_2 creada desde Sprint_1.
- Estructura de directorios Sprint 2.
- Descarga y descompresión de urban_flow_plates.zip.
- README.md actualizado con objetivo Sprint 2.

## [Sprint 2] - Ejercicio 02
### Added
- Listado de imágenes con nombre y tamaño en KB.
- Separación en grupos 'plates' y 'completes'.
- Guardado de group_images.json en data/interim/.
- Función mostrar_muestras reutilizable.

## [Sprint 2] - Ejercicio 03
### Added
- Conversión a grises en 03_01_gray_scale/.
- Suavizado gaussiano en 03_02_blur/.
- Detección de bordes Canny en 03_03_canny/.
- Grillas de muestras por etapa de procesamiento.

## [Sprint 2] - Ejercicio 04
### Added
- Pipeline OCR: denoising, sharpening, cierre morfologico.
- 7 variantes de preprocesamiento por imagen.
- Seleccion por rango 4-10 chars alfanumericos.
- Filtrado geometrico con margen asimetrico en completes.
- Cruce LCS con ratio >= 0.80 (izq a der).
- speeding_fines_image.csv en data/processed/.

## [Sprint 2] - Ejercicio 05
### Added
- Métricas: multas sin/con imagen e imgs sin match.
- Métricas: multas pendientes totales y con imagen.
- multas_imagen.jpg: distribución con/sin evidencia.
- top10_patentes_imagen.jpg: top 10 con match.

## [Sprint 2] - Ejercicio 06
### Added
- Conclusión del Sprint 2 en data/Readme.md.
- Análisis impacto datos inválidos 00:00 y 1932-01-01.

## [Sprint 2] - Ejercicio 04
### Added
- Pipeline OCR: denoising, sharpening, cierre morfologico.
- 7 variantes de preprocesamiento por imagen.
- Seleccion por rango 4-10 chars alfanumericos.
- Filtrado geometrico con margen asimetrico en completes.
- Cruce LCS con ratio >= 0.80 (izq a der).
- speeding_fines_image.csv en data/processed/.

## [Sprint 2] - Ejercicio 05
### Added
- Métricas: multas sin/con imagen e imgs sin match.
- Métricas: multas pendientes totales y con imagen.
- multas_imagen.jpg: distribución con/sin evidencia.
- top10_patentes_imagen.jpg: top 10 con match.

## [Sprint 2] - Ejercicio 01
### Added
- Rama Sprint_2 creada desde Sprint_1.
- Estructura de directorios Sprint 2.
- Descarga y descompresión de urban_flow_plates.zip.
- README.md actualizado con objetivo Sprint 2.

## [Sprint 2] - Ejercicio 02
### Added
- Listado de imágenes con nombre y tamaño en KB.
- Separación en grupos 'plates' y 'completes'.
- Guardado de group_images.json en data/interim/.
- Función mostrar_muestras reutilizable.

## [Sprint 2] - Ejercicio 03
### Added
- Conversión a grises en 03_01_gray_scale/.
- Suavizado gaussiano en 03_02_blur/.
- Detección de bordes Canny en 03_03_canny/.
- Grillas de muestras por etapa de procesamiento.

## [Sprint 2] - Ejercicio 04
### Added
- Pipeline OCR: denoising, sharpening, cierre morfologico.
- 7 variantes de preprocesamiento por imagen.
- Seleccion por rango 4-10 chars alfanumericos.
- Filtrado geometrico con margen asimetrico en completes.
- Cruce LCS con ratio >= 0.80 (izq a der).
- speeding_fines_image.csv en data/processed/.

## [Sprint 2] - Ejercicio 05
### Added
- Métricas: multas sin/con imagen e imgs sin match.
- Métricas: multas pendientes totales y con imagen.
- multas_imagen.jpg: distribución con/sin evidencia.
- top10_patentes_imagen.jpg: top 10 con match.

## [Sprint 2] - Ejercicio 06
### Added
- Conclusión del Sprint 2 en data/Readme.md.
- Análisis impacto datos inválidos 00:00 y 1932-01-01.

## [Sprint 3] - Ejercicio 01
### Added
- Rama Sprint_3 creada desde Sprint_2.
- Verificación de acceso a datasets previos.
- README.md actualizado con contexto Sprint 3.

## [Sprint 3] - Ejercicio 02
### Added
- DVC inicializado con remote local /content/remote_dvc.
- speeding_fines_image.csv migrado de Git a DVC.
- Directorio imgs migrado de Git a DVC.

## [Sprint 3] - Ejercicio 03
### Added
- Clase Vehiculo con atributo patente y lista multas.
- Clase Radar con atributo radar_id y ubicacion.
- Clase Evidencia con imagen, patente_imagen y ratio.
- Clase Multa vinculando Vehiculo, Radar y Evidencia.
- Método __repr__ en todas las clases.

## [Sprint 3] - Ejercicio 04
### Added
- Función procesar_fila_csv: mapeo de dict a Multa.
- Creación de jerarquía Vehiculo/Radar/Evidencia.

## [Sprint 3] - Ejercicio 05
### Added
- VehiculoORM: tabla vehiculos con PK y relacion multas.
- RadarORM: tabla radares con PK y relacion multas.
- EvidenciaORM: tabla evidencias con FK a multa.
- MultaORM: tabla multas con FK a vehiculo y radar.
- __repr__ en todos los modelos ORM.

## [Sprint 3] - Ejercicio 06
### Added
- BD transito.db creada con SQLAlchemy.
- Tablas generadas automáticamente.
- Datos migrados desde speeding_fines_image.csv.

## [Sprint 3] - Ejercicio 07
### Added
- Consulta: top 10 patentes con más multas.
- Consulta: top 10 multas sin evidencia asc por fecha.
- Consulta: radares con mayor volumen de infracciones.
- Consulta: top 10 reincidentes en período dado.
- Consulta: porcentaje de multas con evidencia visual.

## [Sprint 3] - Ejercicio 08
### Added
- Modelo OpenCLIP ViT-B-32 cargado para embeddings.
- Función obtener_embedding: vectoriza imagen con CLIP.
- BD vectorial patente_vectorial creada en ChromaDB.
- Colección poblada con vectores de imágenes de evidencia.

## [Sprint 3] - Ejercicio 09
### Added
- Función buscar_patente_imagen: búsqueda por similitud.
- Retorna datos completos del vehículo desde la BD relacional.
- Validación con 3 imágenes de muestra.

## [Sprint 3] - Ejercicio 10
### Added
- Conclusión Sprint 3 en data/Readme.md.
