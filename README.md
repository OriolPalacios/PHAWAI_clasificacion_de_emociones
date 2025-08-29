# Análisis Comparativo de Modelos para Clasificación de Emociones en EmoEvent

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/[URL_A_TU_NOTEBOOK_EN_GITHUB])

## 1. Descripción del Proyecto

Este repositorio contiene el notebook y los resultados del proyecto final sobre clasificación de emociones en texto. El objetivo es realizar un estudio exploratorio y comparativo de tres paradigmas distintos de Procesamiento de Lenguaje Natural (NLP) para determinar su eficacia en el dataset **EmoEvent**.

El dataset EmoEvent contiene 8,409 tweets en español, anotados con una de 8 emociones (`anger`, `sadness`, `joy`, `disgust`, `fear`, `surprise`, `offensive`, `other`) y asociados a eventos específicos.

El principal hallazgo de este estudio es que el rendimiento de todos los modelos está fuertemente limitado por la baja calidad y el severo desbalance de clases del dataset. Sorprendentemente, el modelo de razonamiento general (Mistral-7B en modo Zero-Shot) superó al modelo Transformer especializado (BETO), sugiriendo que en contextos de datos ruidosos, un enfoque sin entrenamiento puede ser más robusto.

## 2. Modelos Explorados

Se implementaron y compararon tres enfoques con una complejidad creciente:

1.  **Baseline Clásico (TF-IDF + SVM):** Un modelo de Machine Learning tradicional, computacionalmente eficiente, para establecer una base de rendimiento sólida.
2.  **Transformer Especializado (Fine-Tuning):** Se realizó un fine-tuning de **BETO** (`dccuchile/bert-base-spanish-wwm-uncased`), un modelo BERT pre-entrenado en español, representando el estándar actual de la industria.
3.  **LLM de Razonamiento General (Zero-Shot):** Se utilizó **Mistral-7B-Instruct-v0.2** desplegado localmente para clasificar tweets sin ningún entrenamiento previo, evaluando su capacidad de razonamiento "out-of-the-box".

## 3. Metodología

El flujo de trabajo seguido en el notebook es el siguiente:
1.  **Carga de Datos:** Importación directa del dataset desde su repositorio original en GitHub.
2.  **Análisis Exploratorio de Datos (EDA):** Visualización de la distribución de emociones y eventos para identificar el desbalance de clases y otras características clave.
3.  **Preprocesamiento de Texto:** Limpieza y normalización básica de los tweets.
4.  **Implementación y Evaluación:** Entrenamiento (cuando aplica) y evaluación de cada uno de los tres modelos sobre el mismo conjunto de prueba.
5.  **Análisis Comparativo:** Presentación de resultados agregados (F1-Macro), análisis por emoción (matriz de confusión) y análisis por evento.

## 4. Cómo Ejecutar el Notebook

### Requisitos Previos
- Una cuenta de Google con acceso a Google Colab.
- Una cuenta de Hugging Face.
- Un token de acceso de Hugging Face con permisos de lectura.

### Configuración del Entorno
1.  **Clonar el Repositorio (Opcional):**
    ```bash
    git clone [URL_DE_TU_REPO]
    ```
2.  **Abrir en Google Colab:** Haz clic en el badge "Open In Colab" al inicio de este README o abre el archivo `Clasificacion_Emociones_EmoEvent.ipynb` directamente en Colab.

3.  **Configurar el Acelerador de Hardware:**
    - En el menú de Colab, ve a `Entorno de ejecución` -> `Cambiar tipo de entorno de ejecución`.
    - Selecciona **GPU** (T4 o superior) como acelerador de hardware.

4.  **Configurar el Token de Hugging Face:**
    - En el panel izquierdo de Colab, haz clic en el ícono de la llave (🔑) para acceder a los "Secrets".
    - Crea un nuevo secret con el nombre `HF_TOKEN`.
    - Pega tu token de acceso de Hugging Face como valor.
    - Asegúrate de que el interruptor "Acceso desde el notebook" esté activado.

### Ejecución
- Una vez configurado el entorno, puedes ejecutar todas las celdas del notebook en orden (`Entorno de ejecución` -> `Ejecutar todo`).
- **Nota:** La descarga y carga del modelo Mistral-7B puede tardar varios minutos la primera vez. La inferencia sobre el conjunto de prueba completo también tomará un tiempo considerable.

## 5. Estructura del Repositorio
```
.
├── Clasificacion_Emociones_EmoEvent.ipynb  # El notebook principal con todo el análisis
└── README.md                             # Este archivo de documentación
```
