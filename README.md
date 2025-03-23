# Analisis-y-pronosticos-de-los-precios-de-Qualitas

**Nota** El proyecto se dividio en dos partes por la variedad de modelos aplicados. 
  * Parte 1. Modelos clásicos (AR, MA, ARMA, ARIMA, ARIMAX y SARIMA)
  * Parte 2. Modelos avanzados (Auto Arima, Prophet, LSTM)

## ⭐ Metodología STAR

### ⭐ **Situación:**  
En un contexto financiero, surge la necesidad de desarrollar un modelo para **pronosticar los precios de las acciones de Qualitas**, con el fin de explorar la precisión de distintos enfoques de series de tiempo. Dado que los precios bursátiles presentan volatilidad y patrones complejos, era esencial comparar modelos tradicionales con técnicas más avanzadas para identificar la mejor opción.

---

### 🔥 **Tarea:**  
El objetivo principal del proyecto fue:  
- Construir un modelo predictivo capaz de **pronosticar los precios de las acciones de Qualitas**, evaluando la precisión de diversos enfoques mediante la métrica **RMSE**.  
- Implementar tanto **modelos clásicos** de series de tiempo (*ARIMA, SARIMA, ARMA*) como técnicas avanzadas (*GARCH, Prophet, LSTM*).  
- Optimizar el modelo **LSTM** aplicando **validación cruzada** y **GridSearch** para ajustar sus hiperparámetros, asegurando un ajuste más riguroso del modelo.  

---

### ⚙️ **Acción:**  
1. **Obtención y preparación de datos:**  
   - Descargué los precios históricos de Qualitas desde `yfinance` e implementé una función para validar la existencia del archivo local antes de hacer una nueva descarga, evitando limitaciones por múltiples solicitudes.  
   - Realicé un análisis exploratorio para evaluar la estacionariedad mediante la **prueba de Dickey-Fuller**, aplicando transformaciones (*diferenciación*) cuando fue necesario.  
   - Utilicé técnicas de suavizado (**SMA, EWMA**) para visualizar la tendencia subyacente y apliqué **ACF** y **PACF** para identificar la estructura de autocorrelación.  

2. **Modelado:**  
   - **Modelos clásicos:**  
      - Implementé modelos **AR, MA, ARMA, ARIMA y SARIMA**, optimizando los parámetros mediante **GridSearch** y validando la significancia de los coeficientes.  
      - Incorporé variables exógenas con **ARMAX**, utilizando el índice IPC México, evidenciando la capacidad del modelo para captar correlaciones externas.  
   - **Modelos avanzados:**  
      - Utilicé **GARCH** para modelar la volatilidad de los retornos, evidenciando que la varianza presenta memoria a largo plazo.  
      - Implementé **Prophet**, que superó a ARIMA en precisión, logrando una mejora significativa del **28%** en el RMSE.  
      - Construí un modelo **LSTM**, ajustando la secuencia temporal a **20 días hábiles** para capturar patrones a corto plazo.  
      - Apliqué **validación cruzada** y **GridSearch** para optimizar el modelo **LSTM**, ajustando hiperparámetros como la cantidad de neuronas, la tasa de aprendizaje y el tamaño del lote, aunque el modelo original obtuvo un mejor RMSE.  
      - Utilicé predicción recursiva con **LSTM**, observando cómo el error acumulado reducía la precisión en horizontes largos.  

---

### ✅ **Resultado:**  
- El modelo **LSTM original** resultó ser el más preciso a corto plazo, con un RMSE de **5.974**, superando significativamente a todos los modelos tradicionales.  
- La optimización del **LSTM** con **validación cruzada** y **GridSearch** no mejoró el RMSE, pero evidenció la robustez del modelo base.  
- **Prophet** logró un RMSE de **25.146**, mejorando en un **28%** el error de ARIMA.  
- **GARCH(1,2)** modeló la volatilidad con éxito, mostrando que la varianza dependía de dos lags previos, lo que refleja memoria a largo plazo.  
- La predicción recursiva con **LSTM** acumuló error, resultando en menor precisión a largo plazo (RMSE de **60.8222** para un año).  

