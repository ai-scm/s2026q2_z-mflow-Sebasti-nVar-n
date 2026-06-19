# 🔗 Conexión: Data Lifecycle → ML Lifecycle
Documentación técnica del taller práctico Autor: Sebastián Varón | Proyecto: s2026q2_z-mflow-Sebasti-nVar-n

# 🧠 Introducción
Este documento detalla cómo los principios del Data Lifecycle (que ya conocemos) se integran
y expanden en el Machine Learning Lifecycle. No son flujos aislados; el entrenamiento de 
modelos es, en esencia, una fase avanzada de consumo y transformación de datos.

# 📊 Comparativa: Data Lifecycle vs. ML Lifecycle

EtapaData             LifecycleML            Lifecycle¿Qué                        cambia?

Inicio	              Ingestión	             Ingestión + Exploración              Se añade EDA (Exploratory Data Analysis) 
                                                                                  para entender distribuciones.

Proceso              	Transformación       	 Preprocesamiento	                    Ahora debe ser reproducible y empaquetado 
                                                                                  (Pipeline).

Almacenamiento	      Almacenamiento	       Registro de modelo	                  Se guardan artefactos 
                                                                                  (modelos, métricas, dependencias).

Consumo	              Consumo	               Despliegue + Inferencia	            Se convierte en un endpoint REST de tiempo real.

 
Gobierno	            Gobernanza	           Gobernanza + MLOps	                  Gestión de lineage, comparación y transiciones.


# ⚙️ ¿Qué se mantiene y qué evoluciona?
✅ Lo que se mantiene
Reproducibilidad: Si el pipeline de datos exige consistencia,
el pipeline de ML exige resultados idénticos ante el mismo input.

Versionado: Auditoría estricta tanto de los datos
base como de los modelos generados.

Separación: La distinción entre entorno de desarrollo (laptop) y producción 
(servidor/nube) sigue siendo crítica. Docker es nuestro puente aquí.


# 🚀 Lo que se amplía (El aporte de MLflow)
Tracking de Experimentos: No solo versionamos código; versionamos
hiperparámetros, métricas (accuracy) y datasets específicos.

Gestión de Ciclo de Vida: Los modelos tienen "vida" (Staging → Production).
MLflow Registry permite esta gobernanza mediante aliases.

Reproducibilidad del Entorno: La predictibilidad del modelo depende de versiones exactas de sklearn o numpy. 
Archivos como conda.yaml y requirements.txt son ahora obligatorios.


# 📉 Flujo Integral Ejecutado (Breast Cancer Dataset)
El taller implementó este flujo completo, transformando datos estáticos en un servicio vivo:

Exploración: Análisis de 569 registros y balanceo de clases.

Transformación: Normalización (StandardScaler) empaquetada en Pipeline.

Entrenamiento: Clasificación con RandomForestClassifier.

Registro: Gestión de versiones v1/v2 con alias @Staging.

Despliegue: API REST activa en localhost:1234.

Inferencia: Predicciones en tiempo real mediante curl.

# 💡 Reflexión Final
El Data Lifecycle nos enseñó que los datos son un activo que debe gobernarse desde la fuente. El ML Lifecycle extiende esta responsabilidad: ahora el "consumo" no es un reporte estático, sino un modelo que toma decisiones.

"En el mundo de los datos, un error falla rápido. En el mundo de ML, un error es silencioso."

Esta es la razón por la que herramientas como MLflow y prácticas de MLOps son fundamentales: nos permiten auditar, comparar y revertir cambios en el comportamiento de nuestros modelos con la misma precisión con la que gobernamos nuestros datos.

Documentación técnica preparada por Sebastián Varón para el semillero s2026q2z.

