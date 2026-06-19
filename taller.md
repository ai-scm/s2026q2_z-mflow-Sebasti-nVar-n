# 🚀 Taller Hands-On: MLflow + Docker 🐳
Del dato al modelo desplegado

# Autor: Sebastián Varón 👨‍💻

# Repositorio: s2026q2_z-mflow-Sebasti-nVar-n

# 🎯 Objetivo
Aplicar los conceptos del Data Lifecycle al ciclo de vida de un modelo de Machine Learning.
Utilizamos un clasificador sobre el dataset breast_cancer de sklearn como vehículo 
pedagógico para explorar la conversión de datos en modelos, su versionado y despliegue.

# 🏗️ Estructura del Taller

# Fase             Actividad

# 0	               Introducción y conexión MLOps

# 1	               Exploración local del dataset

# 2	               Entrenamiento + Serving sin registry (Docker)

# 3                MLflow Registry, UI y Versionado (Docker)

# 4	               Inferencia vía REST API

# 5	               Cierre y escalabilidad a entornos Cloud

# 🔍 Evidencias de Resultados
# 1. Exploración de Datos 📊
Se validó el dataset con 569 observaciones y 30 variables (features). El objetivo está desbalanceado (357 benignos, 212 malignos), lo que justifica el uso de class_weight='balanced'.

# 2. Comparación de Versiones ⚖️
Implementamos el entrenamiento con versionado. Observamos la importancia del overfitting al comparar modelos:

v1 (100 árboles): Mejor generalización (accuracy_test ~0.9649).

v2 (200 árboles): Ligero overfitting en entrenamiento (accuracy_train ~0.9978).

Conclusión: Gracias a MLflow Registry, pudimos identificar que la v1 era superior para producción.

3. Registro y Despliegue 🚀
UI MLflow: Implementada en http://localhost:8000.

Serving: El modelo expone la API REST en http://localhost:1234/invocations.

Inferencia: Validada mediante curl con datos de prueba, obteniendo probabilidades precisas.

# 🔄 Data Lifecycle vs. ML Lifecycle
Durante el taller, conectamos ambos mundos:

Ingestión: Carga desde sklearn.

Transformación: Normalización con StandardScaler (Pipeline).

Entrenamiento: Clasificación con RandomForest.

Evaluación: Registro de accuracy en MLflow.

Registro: Almacenamiento en Model Registry con alias Staging.

Despliegue/Inferencia: API REST consumible por cualquier servicio.

# 🛠️ Tecnologías Utilizadas
Python 3.12 🐍 (Exploración)

MLflow 2.16.2 🧪 (Tracking, Registry, Serving)

Docker & Docker Compose 🐳 (Reprodutibilidad del entorno)

# 📋 Resumen de Comandos

# Levantar el stack completo
docker compose -f docker-compose.yml up --build

# Realizar inferencia
./predict.sh test.csv

# Limpiar entorno
docker compose down
