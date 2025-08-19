
---

## 🛠️ Tecnologías Utilizadas
- **Python 3**
- Librerías principales:
  - `pandas`, `numpy` → manipulación y análisis de datos
  - `matplotlib`, `seaborn` → visualización
  - `scikit-learn` → preprocesamiento, modelos y métricas
  - `imblearn` → balanceo de clases con SMOTE

---

## 📑 Fase 1: Exploración y Limpieza de Datos (EDA)
- Importación de datos desde JSON.  
- Conversión a **DataFrame de Pandas**.  
- Verificación de valores nulos, duplicados e inconsistencias.  
- Creación de nuevas variables como **Cuentas_Diarias** (derivada de cargos mensuales).  
- Estandarización de categorías (`Sí/No → 1/0`).  
- Análisis descriptivo y visualización de patrones iniciales.

**Principales hallazgos:**
- Mayor tasa de cancelación en clientes con **contratos mensuales**.  
- Los clientes con **método de pago Electronic Check** muestran más evasión.  
- **Permanencia corta** se asocia con mayor riesgo de churn.  

---

## 🤖 Fase 2: Modelado Predictivo
### 🔹 Preparación
- Eliminación de columnas irrelevantes (ej. IDs).  
- Codificación de variables categóricas con **One-Hot Encoding**.  
- Balanceo de clases con **SMOTE** para evitar sesgo hacia la clase mayoritaria.  
- División de datos en **train (70%)** y **test (30%)**.  
- Escalado de variables numéricas para modelos sensibles a la escala.

### 🔹 Modelos Entrenados
1. **Regresión Logística** (requiere normalización).  
2. **Random Forest** (no requiere normalización).  

### 🔹 Resultados
- **Regresión Logística**
  - Accuracy: ~0.80
  - Recall: mejor capacidad para identificar clientes que cancelan.
  - Modelo más **interpretable** y con buena generalización.
- **Random Forest**
  - Accuracy: ~0.78 en test, pero ~0.99 en train → **overfitting**.
  - Importancia de variables confirma patrones observados.

---

## 📊 Factores Clave Identificados
- **Meses de permanencia**: clientes con más tiempo en la compañía tienen menor probabilidad de churn.  
- **Tipo de contrato**: mensual → mayor churn; anual/bianual → menor churn.  
- **Método de pago (Electronic Check)**: fuertemente asociado con cancelaciones.  
- **Tipo de internet (Fibra Óptica)**: clientes con este servicio cancelan más que otros.  
- **Cargos Totales**: altos montos acumulados se relacionan con mayor evasión.  

---

## 💡 Recomendaciones Estratégicas
1. **Incentivar contratos largos** (1 o 2 años) con descuentos o beneficios.  
2. **Revisar calidad del servicio de Fibra Óptica**, dado su vínculo con mayor churn.  
3. **Gestionar clientes con altos cargos totales** con planes flexibles.  
4. **Promover métodos de pago automáticos/seguros** en lugar de Electronic Check.  
5. **Destacar soporte técnico y servicios adicionales** como diferenciadores de retención.  

---

## 📌 Ejecución del Proyecto

### 1️⃣ Instalar dependencias
```bash
pip install pandas numpy matplotlib seaborn scikit-learn imbalanced-learn
