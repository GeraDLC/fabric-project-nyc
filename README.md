# 🚖 Ingeniería de Datos - Taxis NYC con Microsoft Fabric

Proyecto de ingeniería de datos enfocado en la automatización de ingesta, transformación y visualización de datos públicos de taxis en la ciudad de Nueva York, utilizando Microsoft Fabric como plataforma principal.

---

## 🧠 Objetivo

El propósito de este proyecto es demostrar cómo implementar un flujo moderno de datos de extremo a extremo sobre Microsoft Fabric, aplicando buenas prácticas de **ingeniería de datos**. El flujo incluye automatización de ingesta desde una API, procesamiento con notebooks y visualización en Power BI.

---

## 🧱 Arquitectura de la Solución

![Arquitectura](assets/arquitectura_solucion.png)

1. **Landing / Bronze**  
   - Descarga automatizada de archivos `.parquet` desde una API pública (NYC Taxi & Limousine Commission).  
   - Los archivos se almacenan en la capa *bronze* del Lakehouse.

2. **Staging / Silver**  
   - Transformaciones iniciales: limpieza de columnas, tipos de datos, nulos.  
   - Enriquecimiento con *lookup tables* como zonas de taxi.

3. **Presentation / Gold**  
   - Agregaciones y estructura final para análisis.  
   - Preparación de datos para consumo por herramientas BI.

4. **Reporting**  
   - Conexión del modelo semántico desde Power BI a las tablas *gold*.  
   - Dashboards dinámicos con KPIs, gráficos y mapas interactivos.

---

## ⚙️ Automatización y Flujo de Trabajo

- La ingesta se realiza automáticamente con un notebook programado (PySpark).
- El notebook se conecta a la API, descarga el archivo correspondiente al mes actual y lo guarda en el Lakehouse.
- Luego, otro notebook transforma los datos y los mueve de bronze a gold.
- Este flujo puede ejecutarse manualmente o como tarea recurrente.

---

## 📂 Estructura del Repositorio

├── notebooks/
│ ├── 01_ingesta_api_nyc.ipynb # Ingesta automática desde API
│ └── 02_transformaciones_taxi.ipynb # Transformaciones y carga a gold
│
├── powerbi/
│ └── dashboard_taxi_nyc.pbix # Reporte final en Power BI
│
├── data/
│ └── ejemplo_datasets/ # Parquets de ejemplo
│
├── assets/
│ └── arquitectura_solucion.png # Diagrama de arquitectura
│
├── README.md
└── LICENSE


---

## 📊 Visualizaciones en Power BI

- **Total de Viajes y Tarifas** por mes y por tipo de taxi  
- **Mapas de Calor** con zonas de recogida y destino  
- **KPIs Clave** como distancia total, viajes promedio, ingresos  
- **Filtros** por año, mes, zona, tipo de taxi  

---

## 🔧 Tecnologías Usadas

| Herramienta          | Descripción                                          |
|----------------------|------------------------------------------------------|
| **Microsoft Fabric** | Plataforma central del proyecto                      |
| **Lakehouse**        | Almacenamiento estructurado (bronze, silver, gold)  |
| **Notebooks (PySpark)** | Automatización de ingesta y procesamiento       |
| **Power BI**         | Visualización de datos y análisis interactivo       |
| **API NYC TLC**      | Fuente de datos abiertos (.parquet por mes)         |

---

## 🚀 Cómo Ejecutar el Proyecto

1. **Clona el repositorio:**
   ```bash
   git clone https://github.com/tu_usuario/proyecto-nyc-taxi-fabric.git
   cd proyecto-nyc-taxi-fabric
