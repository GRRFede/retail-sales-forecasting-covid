# Análisis Contrafactual de Ventas Retail — COVID-19

**¿Qué hubiera pasado con las ventas de ropa en EE.UU. si no hubiera existido la pandemia?**

Este proyecto construye un análisis contrafactual usando datos mensuales de ventas de ropa y accesorios del sector minorista de Estados Unidos (1992–2023), comparando dos enfoques de predicción: un modelo estadístico clásico de series temporales y un modelo de machine learning.

---

## Pregunta de investigación

> *¿Cómo habrían evolucionado las ventas de ropa y accesorios en EE.UU. si no hubiera ocurrido el cierre económico por COVID-19 en 2020?*

---

## Metodología

### Datos
- **Fuente:** U.S. Census Bureau — Monthly Retail Trade Survey (MARTS)
- **Período:** Enero 1992 – Diciembre 2023 (384 observaciones mensuales)
- **Variable:** Ventas mensuales en millones de dólares (categoría NAICS 448)

### Modelos utilizados

| Modelo | Librería | Descripción |
|--------|----------|-------------|
| **SARIMAX** | `statsmodels` | Modelo estadístico para series con estacionalidad. Captura tendencia, ciclos y patrón mensual. Parámetros optimizados via Grid Search (criterio AIC). |
| **ForecasterAutoreg + Random Forest** | `skforecast` + `scikit-learn` | Convierte el problema temporal en regresión supervisada usando los últimos 30 meses como predictores. |

### Evaluación
Los modelos se evalúan sobre el 20% final de los datos (período de prueba) usando:
- **RMSE** (Root Mean Squared Error): error en millones USD
- **MAPE** (Mean Absolute Percentage Error): error porcentual promedio

---

## Estructura del repositorio

```
├── series_temporales_retail.ipynb   # Notebook principal con análisis completo
├── FusionCharts.csv                 # Datos de ventas (U.S. Census Bureau)
└── README.md
```

---

## Resultados principales

- El contrafactual modelado predice una trayectoria **por debajo de las ventas reales post-pandemia**, lo que sugiere que el crecimiento observado tras el COVID-19 fue superior a lo que habría ocurrido en un escenario sin pandemia.
- Una explicación plausible: las políticas fiscales expansivas (transferencias directas, subsidios) generaron demanda reprimida que impulsó el consumo por encima de la tendencia histórica al levantarse las restricciones.
- El SARIMAX optimizado superó al Random Forest en precisión, siendo más adecuado para esta serie con estacionalidad fuerte y estructura predominantemente lineal.

---

## Cómo ejecutar

1. Abrir el notebook en [Google Colab](https://colab.research.google.com/) o Jupyter
2. Subir el archivo `FusionCharts.csv` al entorno
3. Ejecutar las celdas en orden

```bash
# Dependencia adicional necesaria
pip install skforecast
```

---

## Tecnologías

![Python](https://img.shields.io/badge/Python-3.10-blue)
![Pandas](https://img.shields.io/badge/Pandas-2.0-blue)
![statsmodels](https://img.shields.io/badge/statsmodels-SARIMAX-green)
![scikit-learn](https://img.shields.io/badge/scikit--learn-RandomForest-orange)
![skforecast](https://img.shields.io/badge/skforecast-ForecasterAutoreg-purple)

---

## Autor

**Richard Federico Gil Romero**  
Estudiante de Economía — Universidad Autónoma de Santo Domingo (UASD)  
[LinkedIn](www.linkedin.com/in/richard-federico-gil-romero-508286271) · github.com/GRRFede
