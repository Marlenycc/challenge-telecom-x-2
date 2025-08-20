# 📊 Telecom X – Predicción de Cancelación de Clientes (Churn)

## 📌 Introducción

Este proyecto forma parte del desafío de **Data Science - Alura Latam | ONE - Oracle Next Education**.  
El objetivo es **predecir qué clientes tienen más probabilidad de cancelar (Churn)** y proponer estrategias de retención basadas en los resultados.

---

## 🎯 Objetivos del Desafío

- Preparar los datos para el modelado (limpieza, codificación y normalización).
- Realizar un análisis exploratorio y de correlación.
- Entrenar distintos modelos de clasificación.
- Evaluar el rendimiento de los modelos con métricas clave.
- Identificar los factores más influyentes en la cancelación.
- Proponer acciones estratégicas de retención de clientes.

---

## 🛠️ Preprocesamiento de Datos

- Se eliminó la columna **`customerID`**, ya que no aporta información predictiva.
- Se definió la variable objetivo **`Churn`** (map: Yes=1, No=0).
- Se aplicó **One-Hot Encoding** a variables categóricas.
- Se verificó y trató el desbalance de clases (26% Sí vs 74% No).
- Para modelos sensibles a la escala, se aplicó **StandardScaler** únicamente a variables numéricas continuas:
  - `tenure`
  - `Charges.Monthly`
  - `Charges.Total`
  - `Cuentas_Diarias`

---

## 🔎 Análisis Exploratorio (EDA)

- Se exploró la proporción de clientes que cancelan: **26.5% (minoría)**.
- Se generó una **matriz de correlación** para identificar relaciones.
- Variables con mayor correlación con `Churn`:
  - `Contract`, `tenure`, `TotalCharges` (negativas).
  - `InternetService_Fiber optic`, `PaymentMethod_Electronic check` (positivas).

### Análisis dirigido

- **Tenure vs Churn**: clientes con poca antigüedad presentan mayor riesgo.
- **TotalCharges vs Churn**: clientes con mayor gasto acumulado tienden a quedarse.
- **Contract vs Churn**: contratos largos reducen notablemente la cancelación.

---

## 🤖 Modelado Predictivo

### Separación de datos

- 70% entrenamiento y 30% prueba.
- Se aplicó **estratificación** para mantener la proporción de churn.

### Modelos entrenados

1. **Regresión Logística** (con normalización).
2. **KNN (k=5)** (con normalización).
3. **Random Forest** (sin normalización).

---

## 📊 Evaluación de Modelos

Se evaluaron con **Accuracy, Precision, Recall y F1-score**:

| Modelo              | Accuracy | Precision | Recall | F1-score |
| ------------------- | -------- | --------- | ------ | -------- |
| Regresión Logística | 0.80     | 0.69      | 0.72   | 0.70     |
| KNN (k=5)           | 0.78     | 0.66      | 0.68   | 0.67     |
| Random Forest       | 0.84     | 0.73      | 0.77   | 0.75     |

👉 **Random Forest** fue el mejor modelo, destacando en recall y F1, lo que lo hace más confiable para detectar clientes en riesgo de cancelación.

---

## 📌 Factores Clave en la Cancelación

### Factores de riesgo

- Contratos **Month-to-Month**.
- Método de pago **Electronic Check**.
- **Baja antigüedad** (tenure bajo).
- Servicio de **Fiber Optic**.

### Factores protectores

- Contratos **1 o 2 años**.
- **Mayor gasto acumulado (TotalCharges)**.
- Servicios adicionales como **Tech Support** y **Online Security**.

---

## 🎯 Estrategias de Retención

1. **Migrar contratos mensuales** hacia planes anuales con incentivos.
2. **Promover pagos automáticos**, reduciendo electronic check.
3. **Fidelización temprana**: soporte y beneficios en los primeros meses.
4. **Optimizar la experiencia de Fiber Optic**, reforzando la calidad percibida.
5. **Ofrecer paquetes de valor** con servicios adicionales que fortalezcan la permanencia.

---

## ✅ Conclusión Final

El proyecto permitió **predecir el churn con buena precisión** y, sobre todo, entender los factores que lo impulsan.  
El modelo de **Random Forest** se consolidó como la mejor herramienta predictiva, mientras que los hallazgos sobre contratos, métodos de pago y antigüedad sirven como base para **estrategias de retención efectivas**.  
Con estas acciones, Telecom X puede anticiparse a la pérdida de clientes y mejorar su lealtad a largo plazo.
