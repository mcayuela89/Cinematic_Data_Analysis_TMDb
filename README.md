# Análisis Exploratorio de Datos Cinematográficos a partir de la API de TMDb

## 1. Descripción general

Este proyecto forma parte del módulo de análisis de datos del bootcamp de **Hack a Boss**.

El objetivo ha sido construir un pequeño pipeline **ETL + análisis exploratorio** a partir de datos de películas obtenidos de la API pública de **The Movie Database (TMDb)**, y responder a una serie de preguntas sobre popularidad, géneros, ingresos, votos y patrones de estrenos.

---

## 2. Miembros del equipo

- **Christian Monzon**
- **Miguel Cayuela**
- **Daniel Nedelcu**

---

## 3. Objetivos del proyecto

Los objetivos generales del proyecto son:

1. **Diseñar e implementar un proceso ETL básico**:
   - Extraer información de películas desde la API de TMDb.
   - Transformar y limpiar los datos para que sean analizables.
   - Guardar los datos en ficheros `.csv` para uso posterior.

2. **Realizar un análisis exploratorio de datos (EDA)** sobre el dataset de películas para:
   - Entender la distribución de popularidad, votación media, géneros, idiomas y años de lanzamiento.
   - Analizar qué géneros e idiomas tienden a funcionar mejor.
   - Estudiar la relación entre presupuesto, taquilla y duración.

3. **Responder a un conjunto de preguntas concretas**, entre ellas:
   - ¿Cuáles son las películas más populares y qué comparten?
   - ¿Qué géneros tienen mejor y peor votación media?
   - ¿Qué patrones hay en los estrenos a lo largo del tiempo?
   - ¿Qué géneros recaudan más?
   - ¿Cómo se relacionan la duración, el presupuesto y la taquilla?

4. **Documentar el trabajo de forma reproducible** para que cualquier persona que clone el repositorio pueda seguir el análisis paso a paso.

---

## 4. Datos utilizados y proceso ETL

Los datos que utilizamos en este proyecto provienen de la API pública de **The Movie Database (TMDb)**.  
A partir de las respuestas de la API construimos nuestro propio dataset y lo guardamos en formato `.csv` para poder trabajar de forma más cómoda en los notebooks.

### 4.1. Ficheros de datos

En la carpeta `data/` se encuentran los ficheros principales:

- `datos_originales_v6.csv`: dataset principal con todas las películas ya limpias y preparadas.
- `datos_backup_v6.csv`: copia de seguridad del dataset limpio.

Cada fila del dataset corresponde a una película e incluye, entre otras, las siguientes columnas:

- `ID`, `Titulo`, `Titulo_original`
- `Idioma_original`, `Pais_origen`
- `Lanzamiento` (fecha)
- `Presupuesto`, `Taquilla_recaudada`
- `Genero`
- `Duracion` (en minutos)
- `Votacion_media`, `Cantidad_votos`
- `Popularidad` y `Estado`

### 4.2. Proceso ETL (extract, transform, load)

El proceso ETL se realiza en el notebook `exportacion_limpieza.ipynb` y consta de tres pasos:

1. **Extracción**  
   - Llamamos a la API de TMDb usando `requests`.
   - Cargamos las respuestas en un DataFrame de `pandas`.

2. **Transformación**  
   - Renombramos columnas al español.
   - Convertimos tipos de datos (fechas, números, etc.).
   - Tratamos valores nulos.
   - Preparamos la columna de géneros para poder analizarlos.
   - Nos quedamos solo con las columnas relevantes para el análisis.

3. **Carga**  
   - Guardamos el resultado final en los ficheros `datos_originales_v6.csv` y `datos_backup_v6.csv`, que son los que luego se utilizan en `analisis_exploratorio.ipynb`.

---

## 5. Estructura del repositorio y orden de notebooks

Propuesta de estructura:

```text
.
├── proyecto-cine-tmdb/
│   ├── exportacion_limpieza.ipynb
│   └── analisis_exploratorio.ipynb
├── data/
│   ├── datos_originales_v6.csv
│   └── datos_backup_v6.csv
├── .gitignore
