# Análisis de Préstamos Kiva

Este proyecto realiza un análisis exploratorio de datos (EDA) y preprocesamiento sobre un dataset de préstamos de Kiva, una organización sin fines de lucro que permite a las personas prestar dinero a bajo interés a emprendedores y estudiantes en 77 países.


## Introducción
El objetivo principal de este proyecto es entender mejor la distribución y las características de los préstamos en la plataforma Kiva. Se exploran variables clave como montos de préstamos, países, sectores, y la relación entre el tiempo de publicación y desembolso del préstamo.

## Dataset
El dataset utilizado es `kiva_loans.csv`, que contiene información detallada sobre los préstamos otorgados a través de Kiva. Algunas de las columnas clave incluyen `funded_amount`, `loan_amount`, `activity`, `sector`, `country`, `posted_time`, `disbursed_time`, `term_in_months`, y `lender_count`.

## Preprocesamiento y Limpieza de Datos
Las siguientes operaciones de limpieza y preprocesamiento fueron realizadas:
-   **Manejo de Valores Nulos**: Se identificaron y visualizaron las columnas con valores nulos (`tags`, `region`, `funded_time`, `partner_id`, `use`, `borrower_genders`, `disbursed_time`, `country_code`).
-   **Eliminación de Columnas Irrelevantes/Redundantes**: Se eliminaron las columnas `country_code`, `tags`, `partner_id`, `borrower_genders`, `date`, `funded_time`, `region` y `use` debido a su redundancia, falta de valor informativo o alto porcentaje de valores nulos.
-   **Conversión de Tipos de Datos**: Las columnas de tiempo (`posted_time`, `disbursed_time`) se convirtieron a formato `datetime` y se normalizaron. Las columnas de tipo `object` se convirtieron a tipo `string`.
-   **Normalización de Texto**: Se aplicó la normalización de texto (eliminación de espacios y conversión a minúsculas) a todas las columnas de tipo `string` para asegurar consistencia.

## Ingeniería de Características
Se crearon nuevas características para enriquecer el análisis:
-   **`loan_type`**: Clasifica los préstamos en `pre_disbursed` (desembolsados antes de ser publicados) o `post_disbursed` (desembolsados después de ser publicados).
-   **`loan_amount_category`**: Categoriza los montos de los préstamos en 'micro', 'small', 'medium' y 'large' basándose en rangos definidos.
-   **`month`**: Extrae el mes de la columna `posted_time` para análisis temporal.

## Análisis Exploratorio de Datos (EDA) y Visualizaciones
Se realizaron diversas visualizaciones para entender las distribuciones, tendencias y relaciones en los datos:
-   **Histogramas**: Se utilizaron para visualizar la distribución de `loan_amount`, `funded_amount`, `term_in_months` y `lender_count`.
-   **Gráficos de Barras**: Se mostraron los 10 principales países por el total del monto financiado, el número de préstamos por sector y el promedio de prestamistas por tipo de préstamo (`loan_type`).
-   **Gráficos de Línea**: Se analizaron las tendencias del monto promedio de los préstamos y el monto total financiado a lo largo del tiempo (mensual).
-   **Gráficos Circulares**: Se utilizó para mostrar la proporción de préstamos por los 8 países principales.
-   **Detección de Outliers**: Se aplicó la regla de Turkey para identificar valores atípicos en `loan_amount` dentro de cada categoría de préstamo.
-   **Gráficos de Densidad**: Visualización de la distribución de `loan_amount` para cada categoría de préstamo (`micro`, `small`, `medium`, `large`).
-   **Mapas Coropléticos (Choropleth Map)**: Se creó un mapa geográfico para visualizar el `total_loan` por país, mostrando dónde se concentran los montos de préstamo.

## Conclusiones y Próximos Pasos
Este análisis inicial ha revelado patrones interesantes en los datos de Kiva, como la distribución de los montos de los préstamos, los países y sectores más activos, y la existencia de préstamos desembolsados antes de su publicación. 

Los próximos pasos podrían incluir:
-   Análisis más profundo de los outliers y su impacto.
-   Modelado predictivo para pronosticar montos de préstamos o la cantidad de prestamistas.
-   Análisis de sentimientos en la columna `use` (si no se hubiera eliminado).
