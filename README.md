# Parcial 3: Predicción de CO2 Anual

-----

## 📌 Resumen del Proyecto

Este proyecto tiene como objetivo predecir la cantidad de **CO2 anual** a partir de los datos observados por el Observatorio Mauna Loa en Hawaii. El análisis se basa en una serie de tiempo, que incluye la lectura y el preprocesamiento de datos, el análisis de estacionariedad, y la búsqueda de los parámetros óptimos para un modelo ARIMA.

**Autores:** Juliana Bermúdez y Valentina Herrera

-----

## 📊 Conjunto de Datos

El conjunto de datos contiene mediciones de CO2 y otras características, como el promedio, el decimal de la fecha, etc.

Características clave del conjunto de datos:

  * `year`: El año de la observación.
  * `month`: El mes de la observación.
  * `decimal date`: La fecha en formato decimal.
  * `average`: El promedio de CO2.
  * `deseasonalized`: Promedio de CO2 sin estacionalidad.
  * `ndays`: Número de días de la observación.
  * `sdev`: La desviación estándar de la observación.
  * `unc`: La incertidumbre de la observación.

Antes de comenzar, se eliminaron las últimas tres variables (`ndays`, `sdev`, `unc`) ya que no eran relevantes para el análisis, así como las variables `year` y `month` porque `decimal date` era suficiente para la serie de tiempo.

-----

## ⚙️ Estructura del Proyecto

```
├── Parcial3.ipynb   # Jupyter notebook con el análisis completo
├── co2_mm_mlo.csv   # Archivo CSV del conjunto de datos
├── README.md        # Documentación del proyecto
```

-----

## 🔧 Instalación y Requisitos

Para ejecutar este proyecto, necesitarás:

  * Python 3.8+

  * Jupyter Notebook / JupyterLab

  * Las siguientes librerías:

    ```bash
    pip install numpy pandas statsmodels matplotlib scikit-learn
    ```

-----

## 🚀 Uso

1.  Coloca el archivo `co2_mm_mlo.csv` en la misma carpeta que el notebook.
2.  Abre el notebook `Parcial3.ipynb` en tu entorno de Jupyter.
3.  Ejecuta todas las celdas para reproducir el análisis y las predicciones.

-----

## 🔍 Metodología

El proyecto se centra en la construcción de un modelo de series de tiempo para predecir los niveles de CO2.

1.  **Lectura y Preprocesamiento:** Se leen los datos, se descartan las columnas irrelevantes y se convierte la fecha a un formato adecuado para series de tiempo, estableciéndola como el índice.
2.  **Visualización y Análisis de la Serie Temporal:** Se crearon series de tiempo con las variables `average` y `deseasonalized`. Se eligió la variable `average` ya que muestra la estacionalidad, lo que la hace adecuada para el análisis de series de tiempo.
3.  **Prueba de Estacionariedad:** Se realizó una prueba de Dickey-Fuller aumentada (ADF) para confirmar que la serie de tiempo no es estacionaria. El p-valor resultante fue de 1.0, lo cual es mayor que 0.05, confirmando que la serie tiene que ser diferenciada.
4.  **Diferenciación:** Se aplicó la diferenciación dos veces para eliminar la tendencia y la estacionalidad, logrando que la serie de tiempo sea estacionaria.
5.  **Identificación de Parámetros del Modelo ARIMA:** Se realizaron gráficas de autocorrelación y autocorrelación parcial para identificar los posibles valores de los parámetros (p y q) para el modelo ARIMA.
6.  **Entrenamiento y Validación:** Se dividió la serie en conjuntos de entrenamiento (80%) y prueba (20%). A partir de la división para entrenamiento se buscaron los mejores parámetros (p y q) utilizando validación cruzada y el criterio de información de Akaike (AIC). Los mejores parámetros encontrados fueron p=12 y q=12.

-----

## 🤝 Reconocimientos

Gracias a nuestros instructores y compañeros por su guía durante este proyecto.

-----

## 📜 Licencia

Este proyecto es para fines académicos. Siéntete libre de utilizarlo como referencia para aprender.