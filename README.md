# Examen Práctico: Machine Learning I
**Estudiante:** Fabián Manaut Araya  
**Institución:** Escuela de Ingeniería - Universidad Mayor  
**Asignatura:** Machine Learning I  

---

## 1. Enlaces del Proyecto
* **Repositorio GitHub:** https://github.com/Fabianmanaut/ML1_ExamenAplicado_Manaut_Fabian
* **Video de Defensa:** https://drive.google.com/file/d/1DiJTJjsa0k4L1USb85uTd7k4bgCMgl14/view?usp=sharing

---

## 2. Descripción del Dataset
* **Nombre:** California Housing Dataset (Pace & Barry, 1997)
* **Fuente:** [Repositorio GitHub - California Housing](https://raw.githubusercontent.com/akmand/datasets/main/california_housing.csv)
* **Registros:** 20.640 observaciones y 10 variables.
* **Variable Objetivo:** `MedHouseVal` (Valor mediano de las viviendas).
* **Tipo de Tarea:** Regresión supervisada y agrupamiento no supervisado.

---

## 3. Metodología Aplicada
1. **Limpieza y Outliers:** Auditoría de valores faltantes (imputación por mediana en `total_bedrooms`) y winsorización de valores atípicos mediante rango intercuartílico (IQR 1.5).
2. **Preprocesamiento sin Data Leakage:** Separación 80/20 train/test (`random_state=42`), estandarización z-score y codificación One-Hot para `ocean_proximity` ajustados exclusivamente sobre el conjunto de entrenamiento.
3. **PCA y K-Means:** Reducción dimensional con 3 componentes principales (80,52% de varianza explicada acumulada) y segmentación en $k=3$ clústeres mediante Método del Codo y Coeficiente de Silueta.
4. **Modelamiento:** Comparación de modelos lineales (Full, Backward, Forward), regularización Ridge y ensamble Random Forest Regressor optimizados con `GridSearchCV` ($cv=5$).

---

## 4. Resultados Comparativos

| Modelo | RMSE | MAE | $R^2$ | MAPE (%) |
| :--- | :---: | :---: | :---: | :---: |
| **Ridge Regression** | 70.080,71 | 51.454,26 | 0,6252 | 30,13% |
| **Random Forest Regressor** | **49.328,77** | **31.955,75** | **0,8143** | **17,90%** |

* **Modelo Ganador:** Random Forest Regressor, debido a que captura de forma no lineal la interacción entre la ubicación geográfica (`longitude`, `latitude`) y el ingreso medio (`median_income`).

---

## 5. Instrucciones de Reproducción
```bash
# Clonar repositorio
git clone [https://github.com/Fabianmanaut/ML1_ExamenAplicado_Manaut_Fabian.git](https://github.com/Fabianmanaut/ML1_ExamenAplicado_Manaut_Fabian.git)

# Instalar dependencias
pip install -r requirements.txt

# Ejecutar el notebook
jupyter notebook F_Manaut_ML_Examen.ipynb

---

## 6. Declaración de Uso de IA Generativa
Se declara el uso ético y transparente de herramientas de Inteligencia Artificial Generativa (Gemini / ChatGPT) como apoyo metodológico en la redacción de documentación y depuración de sintaxis de código, habiendo sido los análisis, ejecuciones e interpretaciones revisadas y validadas por el autor.
