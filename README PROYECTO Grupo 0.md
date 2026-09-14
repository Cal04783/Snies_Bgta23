# 📊 Análisis de Matriculados en Educación Superior — Bogotá 2023

Proyecto de análisis exploratorio y predictivo sobre la matrícula de primer curso en programas de educación superior en Bogotá D.C. durante el año 2023.

## 🎯 Objetivo

Este proyecto busca caracterizar y explicar la matrícula de primer curso en Bogotá D.C. (2023), respondiendo tres preguntas centrales:

1. **¿Cómo se distribuyen los matriculados por nivel de formación?** (técnico, tecnólogo, universitario, etc.)
2. **¿Cómo se distribuyen los matriculados por sexo?**
3. **¿Qué relación existe entre el área de conocimiento y el nivel de formación?**

Sobre esta última pregunta se aplica una prueba estadística formal (Chi-cuadrado) para determinar si la relación observada es significativa. Finalmente, se construye un modelo de Machine Learning (Random Forest) que predice el número de matriculados y permite identificar qué variables influyen más en esa predicción.

## 🧩 Metodología

| Etapa | Descripción |
|---|---|
| 1. Limpieza de datos | Normalización de texto (tildes, mayúsculas, caracteres especiales) para evitar categorías duplicadas |
| 2. Filtrado | Restricción del conjunto de datos a Bogotá D.C., año 2023 |
| 3. Análisis exploratorio | Visualizaciones por nivel de formación, sexo, y cruce área–nivel |
| 4. Prueba estadística | Chi-cuadrado de independencia sobre la tabla cruzada |
| 5. Modelado predictivo | Random Forest Regressor, con métricas de evaluación e importancia de variables |

## 📁 Estructura del repositorio

```
.
├── README.md                     # Este archivo
├── data/
│   └── matriculados.xlsx         # Base de datos de matrícula (ver sección "Datos")
├── notebooks/
│   └── PrFinalDataExp.ipynb      # Notebook principal con todo el análisis
├── outputs/
│   └── figuras/                  # Gráficos exportados del análisis
└── requirements.txt              # Dependencias de Python
```

## 📦 Datos

El notebook recibe un archivo de Excel con la información de matrícula:

```python
df = pd.read_excel(NOMBRE_ARCHIVO, sheet_name=HOJA, engine="openpyxl")
```

Antes de ejecutar, deben definirse:

- `NOMBRE_ARCHIVO`: ruta al archivo `.xlsx` (por ejemplo, `data/matriculados.xlsx`)
- `HOJA`: nombre de la hoja de Excel que contiene los datos

**Columnas requeridas:**

`MUNICIPIO DE OFERTA DEL PROGRAMA` · `DEPARTAMENTO DE OFERTA DEL PROGRAMA` · `NIVEL DE FORMACIÓN` · `SEXO` · `ÁREA DE CONOCIMIENTO` · `INSTITUCIÓN DE EDUCACIÓN SUPERIOR (IES)` · `SECTOR IES` · `MODALIDAD` · `SEMESTRE` · `AÑO` · `MATRICULADOS PRIMER CURSO`

## ⚙️ Requisitos

- Python 3.9 o superior
- Jupyter Notebook, JupyterLab, VS Code o Google Colab

**Dependencias** (`requirements.txt`):

```
pandas
matplotlib
numpy
scipy
scikit-learn
openpyxl
```

## ▶️ Cómo ejecutar el proyecto

### Opción A — Google Colab

1. Abrir [Google Colab](https://colab.research.google.com/) y subir `PrFinalDataExp.ipynb`.
2. Subir el archivo de datos `.xlsx` a la sesión (panel de archivos → "Subir").
3. Definir `NOMBRE_ARCHIVO` (por ejemplo, `/content/matriculados.xlsx`) y `HOJA` en la celda de carga.
4. Ejecutar todas las celdas: `Entorno de ejecución` → `Ejecutar todas`.

### Opción B — Entorno local

```bash
# 1. Clonar el repositorio
git clone <url-del-repositorio>
cd <nombre-del-repositorio>

# 2. Crear y activar entorno virtual
python -m venv venv
source venv/bin/activate      # En Windows: venv\Scripts\activate

# 3. Instalar dependencias
pip install -r requirements.txt

# 4. Ejecutar el notebook
jupyter notebook notebooks/PrFinalDataExp.ipynb
```

Antes de correr las celdas, colocar el archivo de datos en `data/` y ajustar `NOMBRE_ARCHIVO` y `HOJA` según corresponda. Se recomienda ejecutar con `Kernel` → `Restart & Run All` para garantizar reproducibilidad.

## 📈 Resultados esperados

Al ejecutar el notebook de principio a fin se obtienen:

- Gráfico de barras: matriculados por nivel de formación
- Gráfico circular: distribución por sexo
- Mapa de calor y barras apiladas: relación área de conocimiento – nivel de formación
- Resultado de la prueba Chi-cuadrado (estadístico, valor p, grados de libertad)
- Métricas del modelo Random Forest (MAE, RMSE, R²)
- Gráfico de valores reales vs. predichos
- Ranking de importancia de variables

## 🔁 Reproducibilidad

Tanto la partición de datos (entrenamiento/prueba) como el modelo Random Forest utilizan `random_state=42`, por lo que los resultados son reproducibles al ejecutar el notebook completo.

## 👤 Autoría

Proyecto desarrollado por Carlos Enrique Alvarez Morales, Johan Sebastián Cuan Ramírez, Joan Nicolas Ávila, Juan Sebastián Fonseca Parra como parte de un ejercicio de análisis de datos aplicado a información educativa oficial de Colombia.
