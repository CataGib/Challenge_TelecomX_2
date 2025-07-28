# Challenge_TelecomX_2
Segundo desafío de TelexomX
# 📊 Modelo de Predicción de Churn en Clientes de Telecomunicaciones

## 🎯 Propósito del Proyecto

El objetivo principal de este análisis es **predecir la cancelación (churn)** de clientes de una empresa de telecomunicaciones utilizando un modelo de machine learning, y así identificar los factores que influyen en su decisión de abandonar el servicio. Esta información permite a la empresa diseñar **estrategias de retención más efectivas**, anticipándose a la fuga de clientes.

---

## 🗂️ Estructura del Proyecto

El proyecto está organizado de la siguiente forma:

├── churn_modeling.ipynb # Cuaderno principal del análisis y modelado
├── datos/
│ ├── datos_originales.csv # Dataset original sin procesar
│ ├── datos_normalizado.csv # Dataset después del preprocesamiento
├── visualizaciones/
│ ├── matriz_correlacion.png # Imagen de la matriz de correlación
│ ├── distribucion_tenure.png # Gráficos de EDA relevantes
├── README.md # Documentación del proyecto (este archivo)
└── requirements.txt # Bibliotecas necesarias


---

## Preparación de los Datos

### Clasificación de Variables

- **Numéricas**: `customer.tenure`, `account.Charges.Monthly`, `account.Charges.Total`, `Cuentas_Diarias`
- **Categóricas**: `Contract`, `PaymentMethod`, `InternetService`, entre otras

### Limpieza y Preprocesamiento

1. **Revisión de valores faltantes (NaN)**: Reemplazados por `0` en variables numéricas.
2. **Codificación de variables categóricas**: 
   - Se utilizó `LabelEncoder` para columnas binarias.
   - Se aplicó `OneHotEncoding` para variables con múltiples categorías.
3. **Normalización**: Se aplicó `MinMaxScaler` a variables numéricas para mejorar la eficiencia del modelo KNN.
4. **Conversión de la variable objetivo (`Churn`)**: Mapeada a valores binarios (`Yes` = 1, `No` = 0).

### División del Dataset

El dataset fue dividido en:
- **80% entrenamiento**
- **20% prueba**

Usando `train_test_split` con `stratify=y` para mantener balance en la variable `Churn`.

---

## Modelos Evaluados

Se probaron tres modelos supervisados:

- Árbol de Decisión
- Random Forest
- K-Nearest Neighbors (KNN)

Las métricas utilizadas fueron: **Accuracy, Recall, Precisión y F1-Score**.

*El Árbol de Decisión fue el modelo con mejor balance, especialmente en Recall, lo cual es clave para detectar clientes que realmente abandonan el servicio.*

---

## Insights del Análisis Exploratorio (EDA)

Se realizaron visualizaciones para entender el comportamiento de las variables clave. Ejemplos:

- `customer.tenure`: Clientes con menor antigüedad tienen mayor probabilidad de churn.
- `account.Charges.Total`: Clientes con menor gasto acumulado también presentan mayor riesgo.
- **Matriz de correlación**: Se identificaron relaciones significativas entre las variables numéricas y la variable objetivo.

Las visualizaciones se encuentran en la carpeta `/visualizaciones`.

---

## Instrucciones de Ejecución

### Requisitos

Instalar las siguientes bibliotecas de Python (puedes usar `requirements.txt`):

```bash
pip install -r requirements.txt
