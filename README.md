

# Clasificación temática automática de proyectos de investigación

Este proyecto implementa un pipeline en **R** para la **clasificación temática automática de proyectos de investigación**, a partir del análisis de texto no estructurado contenido en sus títulos, palabras clave y campos descriptivos.

El objetivo es identificar qué **área temática prioritaria** aborda cada proyecto, utilizando un enfoque basado en **diccionarios de palabras clave** y reglas explícitas de decisión.

---

##  Objetivo

- Filtrar una base de proyectos a partir de su contenido textual.
- Asignar a cada proyecto una o más **áreas temáticas prioritarias**.
- Garantizar robustez ante variaciones ortográficas (tildes, mayúsculas).
- Generar una base final lista para análisis o uso institucional.

---

##  Metodología

### 1. Normalización del texto
Todo el texto es normalizado mediante:
- conversión a minúsculas
- eliminación de tildes y caracteres especiales (Unicode → ASCII)

Esto permite detectar coincidencias independientemente de cómo estén escritas.

---

### 2. Definición del diccionario temático
Se definieron **8 áreas temáticas**, cada una representada por un conjunto de entre 10 y 15 palabras clave.

Las palabras clave fueron seleccionadas a partir del análisis exploratorio del **corpus real de títulos y palabras clave de proyectos**, priorizando términos frecuentes y discriminantes por área, e ignorando clasificaciones administrativas preexistentes.

Las áreas consideradas son:
1. Innovación tecnológica aplicada a los principales sectores productivos  
2. Sistemas de transporte y logística de cargas  
3. Energías renovables, ambiente y desarrollo sustentable  
4. Gestión de los recursos hídricos  
5. Gestión de gobierno  
6. Comercio Exterior y Relaciones Internacionales  
7. Industrias Culturales y Creativas  
8. Gestión Turística  

---

### 3. Clasificación automática
Para cada proyecto:
- se concatenan todos sus campos textuales
- se cuentan las coincidencias con las palabras clave de cada área
- se asigna:
  - una única área si tiene mayor cantidad de coincidencias
  - múltiples áreas si existe empate (separadas por `;`)
  - `"Sin clasificación"` si no se detectan coincidencias

---

##  Estructura del proyecto

1. Colocar la base original en:
data_raw/Base_Proyectos_Consolidada.xlsx
2. Abrir el proyecto en RStudio (`.Rproj`)
3. Ejecutar el script principal:
`r` `source("main.R")`
4. El archivo clasificado se generará en:

´data_processed/Base_Proyectos_Clasificada.xlsx
