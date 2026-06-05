# 📊 Proyecto: Análisis de Datos de Viviendas (USA Housing Dataset)

Este repositorio contiene el análisis exploratorio de datos (EDA) y la preparación de un dataset inmobiliario en Estados Unidos, enfocado en predecir o analizar el precio de las viviendas en función de sus características estructurales, ubicación y servicios.

---

## 📌 1. Configuración del Entorno

El análisis se ejecuta en un entorno de **Python 3.11+** utilizando las siguientes librerías principales:
* **Manipulación de Datos:** `pandas` (v3.0.2), `numpy` (v2.4.4)
* **Visualización:** `matplotlib`, `seaborn`, `plotly`
* **Cálculo Estadístico:** `scipy.stats`

---

## 📥 2. Dimensiones del Dataset (`train.csv`)

* **Registros:** 1,460 filas
* **Variables:** 81 columnas
* **Tamaño aproximado en memoria:** ~3.43 MB
* **Tipos de Datos:**
  * 🔢 **Numéricos Enteros (`int64`):** 35 columnas
  * 📉 **Numéricos Flotantes (`float64`):** 3 columnas
  * 🔤 **Categorías / Texto (`object` / `str`):** 43 columnas

---

## 📋 3. Diccionario de Datos (81 Columnas)

Para facilitar la exploración, las variables se han agrupado en los siguientes componentes clave de la propiedad. Haz clic en cada sección para desplegar los detalles:

<details>
<summary>🆔 Identificación y Clasificación General</summary>

* `Id`: Identificador único de la vivienda.
* `MSSubClass`: Tipo de vivienda construida (codificado numéricamente por diseño).
* `MSZoning`: Clasificación general de la zona (Residencial, Comercial, Industrial, etc.).
</details>

<details>
<summary>📐 Terreno y Ubicación Extensa</summary>

* `LotFrontage`: Pies lineales de calle conectados directamente a la propiedad.
* `LotArea`: Tamaño total del terreno en pies cuadrados.
* `Street`: Tipo de acceso vial (Pavimentado o Tierra).
* `Alley`: Tipo de acceso a callejones (si aplica).
* `LotShape`: Forma general de la propiedad (Regular o irregular).
* `LandContour`: Planicidad del terreno (Liso, ladera, depresión, etc.).
* `Utilities`: Tipos de servicios públicos disponibles (Agua, Electricidad, Gas).
* `LotConfig`: Configuración del lote (Lote de esquina, interior, etc.).
* `LandSlope`: Pendiente del terreno.
* `Neighborhood`: Ubicación física dentro de los límites de la ciudad (Barrio/Colonia).
* `Condition1`: Proximidad a diversas condiciones de infraestructura (vías de tren, avenidas, etc.).
* `Condition2`: Segunda condición de proximidad (si existe más de una).
</details>

<details>
<summary>🧱 Estructura, Materiales y Calidad</summary>

* `BldgType`: Tipo de vivienda (Familiar, Duplex, Casa adosada, etc.).
* `HouseStyle`: Estilo de construcción de la vivienda (1 piso, 2 pisos, niveles divididos).
* `OverallQual`: Calidad general del material y acabado de la casa (Escala del 1 al 10).
* `OverallCond`: Condición general actual de la casa (Escala del 1 al 10).
* `YearBuilt`: Año de construcción original de la vivienda.
* `YearRemodAdd`: Año de remodelación o adición más reciente (igual al año de construcción si no hubo cambios).
* `RoofStyle`: Tipo o estilo de techo.
* `RoofMatl`: Material de construcción del techo.
* `Exterior1st`: Cubierta exterior principal de la casa.
* `Exterior2nd`: Segundo material de la cubierta exterior (si aplica).
* `MasVnrType`: Tipo de chapa de mampostería.
* `MasVnrArea`: Área de la chapa de mampostería en pies cuadrados.
* `ExterQual`: Calidad actual del material exterior.
* `ExterCond`: Condición actual del material en el exterior.
* `Foundation`: Tipo de cimentación o base estructural (Bloque, Concreto, etc.).
</details>

<details>
<summary>🕳️ Sótano (Basement)</summary>

* `BsmtQual`: Altura evaluada del sótano.
* `BsmtCond`: Condición general del sótano.
* `BsmtExposure`: Paredes a nivel de jardín o grado de salida al exterior.
* `BsmtFinType1`: Calidad de la primera área terminada del sótano.
* `BsmtFinSF1`: Pies cuadrados terminados de la primera sección del sótano.
* `BsmtFinType2`: Calidad de la segunda área terminada (si aplica).
* `BsmtFinSF2`: Pies cuadrados terminados de la segunda sección.
* `BsmtUnfSF`: Pies cuadrados sin terminar dentro del sótano.
* `TotalBsmtSF`: Área total del sótano en pies cuadrados.
</details>

<details>
<summary>🎛️ Servicios, Climatización e Interiores</summary>

* `Heating`: Tipo de calefacción central instalada.
* `HeatingQC`: Calidad y condición del sistema de calefacción.
* `CentralAir`: Disponibilidad de aire acondicionado central (`Y` / `N`).
* `Electrical`: Tipo de sistema eléctrico instalado.
* `1stFlrSF`: Pies cuadrados del primer piso.
* `2ndFlrSF`: Pies cuadrados del segundo piso.
* `LowQualFinSF`: Pies cuadrados terminados con baja calidad (en todos los niveles).
* `GrLivArea`: Área habitable total sobre el nivel del suelo (pies cuadrados).
* `BsmtFullBath`: Baños completos ubicados en el sótano.
* `BsmtHalfBath`: Medios baños ubicados en el sótano.
* `FullBath`: Baños completos en los pisos superiores.
* `HalfBath`: Medios baños en los pisos superiores.
* `BedroomAbvGr`: Número de dormitorios sobre el nivel del sótano.
* `KitchenAbvGr`: Número de cocinas instaladas.
* `KitchenQual`: Calidad de los acabados de la cocina.
* `TotRmsAbvGrd`: Total de habitaciones sobre el nivel del suelo (no incluye baños).
* `Functional`: Clasificación de la funcionalidad y daños de la vivienda.
* `Fireplaces`: Cantidad de chimeneas funcionales.
* `FireplaceQu`: Calidad de la chimenea (si aplica).
</details>

<details>
<summary>🚗 Estacionamiento (Garage)</summary>

* `GarageType`: Ubicación del garaje (Adosado, empotrado, independiente, etc.).
* `GarageYrBlt`: Año en que se construyó el garaje.
* `GarageFinish`: Estado de acabado interior del garaje.
* `GarageCars`: Capacidad de vehículos que caben en el garaje.
* `GarageArea`: Tamaño total del garaje en pies cuadrados.
* `GarageQual`: Calidad de construcción del garaje.
* `GarageCond`: Condición actual del garaje.
* `PavedDrive`: Estado de la calzada vehicular o entrada (Pavimentada, tierra, etc.).
</details>

<details>
<summary>🌳 Terrazas, Piscinas y Características Extra</summary>

* `WoodDeckSF`: Área de la terraza o plataforma de madera en pies cuadrados.
* `OpenPorchSF`: Área del porche abierto en pies cuadrados.
* `EnclosedPorch`: Área del porche cerrado en pies cuadrados.
* `3SsnPorch`: Área del porche de tres estaciones en pies cuadrados.
* `ScreenPorch`: Área del porche con mosquitero/pantalla en pies cuadrados.
* `PoolArea`: Área de la piscina en pies cuadrados.
* `PoolQC`: Calidad de la piscina (si aplica).
* `Fence`: Calidad de la cerca o vallado perimetral de protección.
* `MiscFeature`: Características especiales adicionales no cubiertas (cobertizos, canchas, etc.).
* `MiscVal`: Valor monetario estimado de la característica especial.
</details>

<details>
<summary>💰 Datos de Venta y Variable Objetivo</summary>

* `MoSold`: Mes en el que se realizó la venta (1-12).
* `YrSold`: Año en el que se vendió la propiedad.
* `SaleType`: Tipo de contrato o transacción de venta.
* `SaleCondition`: Condición particular de la venta (Venta normal, adjudicación, transferencia familiar).
* 🎯 **`SalePrice`:** El precio de venta de la propiedad en dólares. **Esta es la variable objetivo a predecir.**
</details>

---

## ⚠️ 4. Estrategia Inicial para Datos Faltantes (`NaN`)

Durante la inspección inicial, se identifican variables con un volumen alto de valores nulos. Es importante notar que en este dataset, la mayoría de los `NaN` **no son errores de captura**, sino indicadores de que la propiedad no cuenta con dicha amenidad:

1. **Variables con >80% de nulos (`Alley`, `PoolQC`, `Fence`, `MiscFeature`):** Se evaluará su eliminación o codificación como variables categóricas binarias (ej: `HasPool` 0 o 1).
2. **Variables de Garaje y Sótano:** Los nulos coinciden entre columnas del mismo tipo, confirmando la ausencia de sótano o garaje. Se imputarán con `'No Basement'` / `'No Garage'` para categóricas y `0` para numéricas.
3. **Variables Numéricas Continuas (`LotFrontage`):** Se requiere imputar utilizando la mediana agrupada por sectores (`Neighborhood`) para evitar sesgos estructurales.


# Análisis de Precios de Viviendas

## Descripción del Proyecto
Este proyecto realiza un análisis de datos sobre los precios de viviendas, utilizando técnicas de ciencia de datos para explorar tendencias, factores influyentes y predicciones. El objetivo es proporcionar insights valiosos sobre el mercado inmobiliario basado en datos históricos y actuales.

## Tecnologías Utilizadas
- **Lenguaje de Programación**: Python
- **Bibliotecas**: Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn
- **Herramientas**: Jupyter Notebook, Git

## Estructura del Proyecto
- `data/`: Carpeta con los datasets utilizados.
- `notebooks/`: Notebooks de Jupyter con el análisis paso a paso.
- `scripts/`: Scripts de Python para procesamiento y modelado.
- `results/`: Gráficos, reportes y modelos generados.

## Instalación
1. Clona el repositorio:
    ```
    git clone https://github.com/YezuzCama/An-lisis-de-precios-de-viviendas.git
    ```
2. Instala las dependencias:
    ```
    pip install -r requirements.txt
    ```

## Uso
Ejecuta los notebooks en orden para reproducir el análisis. Comienza con `notebooks/01_exploracion_datos.ipynb`.

## Contribuciones
Las contribuciones son bienvenidas. Por favor, abre un issue o pull request en el repositorio.
