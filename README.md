# 🚀 Taller Práctico: MLflow + Docker 🐳
# Del dato al modelo desplegado

# Autor: Juan Sebastián Varón Arenas 👨‍💻

# 1. Descripción 📝
Este material documenta la ejecución y comprensión del taller práctico MLflow + Docker, basado en el tutorial Machine Learning Model Serving for Newbies with MLflow.

El objetivo es comprender el ciclo de vida completo de un modelo de Machine Learning, desde el entrenamiento hasta el despliegue como servicio de inferencia, garantizando reproducibilidad y facilidad de ejecución mediante Docker. Exploramos conceptos clave de MLOps:

📊 Entrenamiento de modelos.

📉 Registro de métricas.

📦 Gestión de versiones.

🗄️ Model Registry.

🌐 Model Serving.

🔗 Inferencia mediante API.

# 2. ¿Qué es MLflow? 🤖
MLflow es la plataforma open source para gestionar el ciclo de vida completo de modelos ML, permitiendo rastrear experimentos, almacenar versiones y desplegar modelos de forma consistente.

# Fases principales:
Tracking 🔍: Registro de parámetros, métricas y artefactos para asegurar la reproducibilidad.

Models 💾: Formato estándar para almacenar modelos independientemente de su implementación.

Registry 🏷️: Gestión centralizada de versiones, trazabilidad y control de ambientes.

Serving 🚀: Exposición del modelo como servicio REST.

# 3. Ejecución sin Registry 📂
Implementado mediante clf-train.py y docker-compose-no-registry.yml.

# Proceso: Carga del dataset Breast Cancer → StandardScaler + RandomForest → Almacenamiento local (clf-model/).

✅ Ventajas: Simplicidad, bajo consumo de recursos y fácil comprensión.

⚠️ Desventajas: Sin control de versiones, sin historial de experimentos y escalabilidad limitada.

# 4. Ejecución con Registry 🏗️
Implementado mediante clf-train-registry.py y docker-compose.yml. Incorpora un servidor dedicado para gestionar experimentos y versiones.

# Características:

Uso de mlflow.set_experiment("my-experiment").

Registro de métricas (accuracy_train, accuracy_test).

Asignación de alias (@Staging) para despliegue independiente.

✅ Ventajas: Versionamiento, trazabilidad total, historial y alta capacidad de colaboración.

⚠️ Desventajas: Mayor complejidad y necesidad de gestionar más componentes (Tracking Server).

# 5. Acceso al modelo e inferencias 📡
El modelo se expone como API REST mediante el endpoint POST /invocations.

Sin Registry: Sirve desde la carpeta local clf-model/.

Con Registry: Consulta directa vía models:/clf-model@Staging.

Prueba: Ejecuta ./predict.sh para enviar datos mediante curl y recibir predicciones.

# 6. Conclusiones 💡
MLflow es esencial para escalar de experimentos locales a procesos profesionales de MLOps. Mientras que el flujo local es ideal para aprendizaje, el uso del Model Registry es indispensable para la trazabilidad y el trabajo en entornos empresariales.

# 7. Data Lifecycle vs ML Lifecycle 🔄
El Machine Learning Lifecycle es una extensión natural del Data Lifecycle.

EtapaData      LifecycleML       Lifecycle

Inicio	       Ingestión         Preparación

Medio	         Transformación	   Entrenamiento & Evaluación

Final          Consumo           Registro, Despliegue & Inferencia

# El flujo integral que logramos implementar:
Ingestión ➡️ Transformación ➡️ Entrenamiento ➡️ Evaluación ➡️ Registro ➡️ Despliegue ➡️ Inferencia 🚀

# Documentación creada como parte del entrenamiento en MLOps.
