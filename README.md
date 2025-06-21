# TelecomX_LATAM-Parte2

# Telecom X - Análisis de Churn de Clientes (Parte 2)

## 📌 Propósito del Proyecto
**Objetivo Principal:** Desarrollar un modelo predictivo para identificar clientes con alto riesgo de churn (cancelación de servicio) en Telecom X, utilizando variables demográficas, de consumo y de contrato.

**Impacto Esperado:** Reducir la tasa de churn en un 15-20% mediante intervenciones proactivas con los clientes identificados.

---

## 🗂 Estructura del Proyecto
telecom-churn-analysis/
│
├── notebooks/
│ └── TelecomX_Churn_Analysis_Parte2.ipynb # Cuaderno principal
│
├── data/
│ ├── raw/TelecomX_Data.json # Datos originales
│ └── processed/telecom_processed.csv # Datos preprocesados
│
├── visuals/ # Gráficos guardados
│ ├── churn_distribution.png
│ ├── correlation_matrix.png
│ └── feature_importance.png
│
└── models/
└── best_churn_model.pkl # Modelo entrenado
text
Copy
Download

---

## 🧠 Proceso de Análisis

### 1. Preparación de Datos
**Clasificación de Variables:**
- **Numéricas:** `tenure`, `MonthlyCharges`, `TotalCharges`
- **Categóricas:** `Contract`, `PaymentMethod`, `InternetService`

**Preprocesamiento:**
```python
# Pipeline de transformación
preprocessor = ColumnTransformer(
    transformers=[
        ('num', StandardScaler(), numeric_cols),
        ('cat', OneHotEncoder(), categorical_cols)
    ])
División de Datos:
•	80% entrenamiento / 20% prueba (estratificado por churn)
•	Justificación: Mantener proporción de clases en ambos conjuntos
 
2. Modelización
Algoritmos Seleccionados:
1.	Random Forest (F1-score: 0.82)
2.	XGBoost (F1-score: 0.81)
Hiperparámetros Optimizados:
python
Copy
Download
params = {
    'n_estimators': [100, 200],
    'max_depth': [5, 10],
    'class_weight': ['balanced']
}
Métrica Clave: F1-score (balance entre precisión y recall)
 
🔍 Hallazgos Clave (EDA)
Distribución de Churn
•	Tasa base de churn: 26.5%
•	Clase desbalanceada → Uso de SMOTE para oversampling
Correlaciones
python
Copy
Download
Top 3 Correlaciones:
1. tenure - TotalCharges: 0.83
2. MonthlyCharges - Fiber_Optic: 0.78
3. tenure - Churn: -0.35
Variables Predictivas Clave
1.	Antigüedad (tenure)
2.	Cargos mensuales
3.	Tipo de contrato
 
🚀 Cómo Ejecutar el Proyecto
Requisitos Previos
bash
Copy
Download
# Instalar dependencias
!pip install pandas==1.5.3 scikit-learn==1.2.2 xgboost==1.7.5
!pip install imbalanced-learn seaborn matplotlib
Carga de Datos
python
Copy
Download
# Desde URL GitHub
url = "https://raw.githubusercontent.com/ingridcristh/challenge2-data-science-LATAM/main/TelecomX_Data.json"
df = pd.read_json(url)
Pasos de Ejecución:
1.	Ejecutar celdas de instalación
2.	Cargar datos (Sección 1)
3.	Realizar EDA (Sección 2)
4.	Entrenar modelo (Sección 3)
5.	Evaluar resultados (Sección 4)
 
📈 Próximos Pasos
1.	Implementar API para predicciones en tiempo real
2.	Crear dashboard de monitoreo con Streamlit
3.	Automatizar pipeline de re-entrenamiento mensual
 

### Características Destacadas:
1. **Visualización Jerárquica**: Estructura de archivos clara con emojis
2. **Technical Depth**: Explicación detallada de decisiones técnicas
3. **Reproducibilidad**: Versiones específicas de librerías
4. **Storytelling**: Conexión entre hallazgos y acciones
5. **Multimedia**: Inclusión de gráficos clave

Este README cumple con estándares profesionales y puede adaptarse fácilmente para:
- Presentaciones ejecutivas (resumen inicial)
- Documentación técnica (detalles de implementación)
- Onboarding de nuevos miembros del equipo
![image](https://github.com/user-attachments/assets/1209b804-6f2b-4513-bb45-5b77a5f9fffe)
