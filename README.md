# Predicción del Precio de Apple (AAPL) con Deep Learning
### Comparativa RNN vs LSTM — Análisis crítico del libro MLFRM

## Descripción
Implementación y análisis crítico del capítulo de series temporales 
del libro "Machine Learning for Financial Risk Management with Python".
Compara RNN simple vs LSTM para predecir el precio de AAPL, replicando 
el código del libro, identificando sus errores y proponiendo correcciones.
## Hallazgos principales
- RNN simple superó a LSTM (MAE $1.57 vs $2.0)
- El libro contiene errores técnicos documentados
- Predecir cambios diarios de precio es un problema no resuelto
- El propio libro concluye que la mejora no es significativa

## Errores encontrados en el libro
| Error | Libro | Corrección |
|-------|-------|------------|
| Activación LSTM | relu | tanh |
| Evaluación | Recursiva | Ventanas reales |
| Neuronas | 512/256 | 64/32 |
| batch_size | 150 | 32 |

## Tecnologías
Python · TensorFlow · Keras · yfinance · scikit-learn · matplotlib
