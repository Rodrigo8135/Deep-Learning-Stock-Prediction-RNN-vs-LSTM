# Deep Learning Stock Prediction: RNN vs LSTM

> Implementación y análisis crítico del capítulo de series temporales  
> del libro *"Machine Learning for Financial Risk Management with Python"*

---

##  Descripción
Este proyecto compara RNN simple vs LSTM para predecir el precio de 
acciones de Apple (AAPL), replicando el código del libro, identificando 
sus errores técnicos y proponiendo correcciones. Se evalúan dos enfoques: 
predicción de cambio diario (`diff`) y predicción de precio directo.

---

##  Hallazgos principales
- El código del libro contiene **4 errores técnicos documentados**
- LSTM con precio directo supera a RNN (MAE $4.09 vs $7.37)
- Predecir cambios diarios (`diff`) produce modelos inútiles en ambos casos
- La Directional Accuracy es más relevante que el MAE en finanzas
- El propio libro concluye: *"estos modelos no sugieren una mejora significativa"*

---

## Errores encontrados en el libro

| Error | Libro | Corrección |
|-------|-------|------------|
| Activación LSTM | `relu` | `tanh` |
| Evaluación del modelo | Predicción recursiva | Ventanas reales |
| Tamaño del modelo | 512/256 neuronas | 64/32 neuronas |
| Tamaño de batch | 150 | 32 |

---

## Resultados comparativos

| Modelo | Enfoque | MAE | Dir. Accuracy | Resultado |
|--------|---------|-----|---------------|-----------|
| LSTM | diff (libro) | $1.57 | 50.3% | Línea plana  |
| RNN  | diff (libro) | $7.37 | 47.9% | Línea plana  |
| RNN  | Precio directo | $7.00 | ~50% | Sigue tendencia  |
| LSTM | Precio directo | $4.09 | 49.3% | Mejor modelo  |

---

## Gráficas

### LSTM con diff — resultado del libro
> Línea roja plana: el modelo predice ~$0 todos los días

### LSTM con precio directo — versión corregida  
> Las líneas siguen la misma tendencia en rango $120-$195

---

## Conceptos aplicados
- Redes Neuronales Recurrentes (RNN y LSTM)
- Ventanas deslizantes (Sliding Window)
- Data Leakage y cómo evitarlo
- Normalización con MinMaxScaler
- EarlyStopping y ReduceLROnPlateau
- Evaluación honesta vs predicción recursiva
- Métricas: MAE, RMSE, Directional Accuracy

---

## Tecnologías
![Python](https://img.shields.io/badge/Python-3.x-blue)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange)
![Keras](https://img.shields.io/badge/Keras-red)
![scikit-learn](https://img.shields.io/badge/scikit--learn-yellow)
![yfinance](https://img.shields.io/badge/yfinance-green)
![matplotlib](https://img.shields.io/badge/matplotlib-blue)

---
##  Referencia
> *Machine Learning for Financial Risk Management with Python*  
> Abdullah Karasan — O'Reilly Media
