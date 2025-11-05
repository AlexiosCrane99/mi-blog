---
layout: default
title: "Análisis de Flujo de Datos Simulado con Spark"
---

# 🔥 Análisis de Flujo de Datos Simulado con Spark

> 💡 **Objetivo:**  
> Aplicar analítica avanzada con **Apache Spark** para procesar un flujo de clics simulado en una tienda online de lectura digital.  
> El propósito es comprender cómo los usuarios navegan e interactúan con la plataforma en tiempo real.

---

## ✅ 1. Escenario

Imagina una **página de lectura de libros en línea** que desea analizar el comportamiento de sus lectores.  
Cada clic representa una acción del usuario: abrir un libro, pasar de capítulo, marcar una página o cerrar sesión.

La tienda necesita detectar patrones de navegación para:

- 👥 Identificar usuarios activos  
- 🚀 Encontrar picos de interacción  
- ⚠️ Detectar comportamientos sospechosos  
- 🎯 Evaluar la eficiencia de campañas en tiempo real  

---

## 📊 2. Dataset

![Tabla Ejemplo del DataSet]({{ '/assets/images/Dataset_Clicks.png' | relative_url }})

**Columnas principales:**

| Columna | Descripción |
|----------|--------------|
| `Timestamp` | Fecha y hora del clic |
| `User_ID` | Identificador del usuario |
| `Clicks` | Número de clics por evento |

📈 **Tamaño del dataset:** 100 registros simulados (10 usuarios distintos).  

---

## ⚙️ 3. Proceso en Spark

El análisis se ejecutó en **Google Colab** con PySpark.  
Pasos del procesamiento:

1. Cargar el archivo CSV.  
2. Convertir la columna `Timestamp` a tipo fecha.  
3. Simular un flujo de datos en micro-lotes de 1 minuto.  
4. Contar los clics por usuario dentro de cada ventana temporal.  

Ejemplo de código:

```python
from pyspark.sql import SparkSession
from pyspark.sql.functions import sum as _sum

spark = SparkSession.builder.appName("Clickstream Analysis").getOrCreate()
df = spark.read.csv("clickstream_books.csv", header=True, inferSchema=True)
clicks_per_user = df.groupBy("User_ID").agg(_sum("Clicks").alias("Total_Clicks"))
clicks_per_user.show()

📈 4. Resultados del Análisis

Patrones observados:

🧭 Algunos usuarios realizan muchos clics en intervalos cortos → lectores muy activos.

⚡ Picos repentinos de clics → oportunidades para promociones o eventos.

⏱️ La distribución temporal revela los horarios de mayor actividad.

🧩 5. ¿Cómo ayuda esto a la tienda?

Los resultados permiten:

🎯 Mejor segmentación de usuarios según su actividad.

🤖 Detección de bots o comportamientos automatizados.

🧠 Optimización de recomendaciones de lectura.

💰 Toma de decisiones en tiempo real para campañas de marketing.

🏗️ 6. Arquitectura del Blog con Jekyll

Motor: Jekyll
Tema: Cayman

Estructura del proyecto:

/_posts/                  # Publicaciones Markdown
/_layouts/                # Plantillas HTML
/assets/images/           # Gráficos y visuales
_config.yml               # Configuración global
index.md                  # Página principal


Despliegue en GitHub Pages:

Instalar Ruby y Jekyll.

Crear blog: jekyll new mi-blog.

Editar _config.yml → theme: jekyll-theme-cayman.

Subir el proyecto a GitHub.

Activar GitHub Pages.

Agregar este post en _posts/2025-11-04-analisis-flujo-datos-spark.md.

![Gráfico de clics por usuario]({{ '/assets/images/clicks.png' | relative_url }})

💭 7. Reflexión Final
🔄 ¿Streaming o Batch?
Procesamiento por Lotes (Batch)	Procesamiento en Streaming
Procesa grandes volúmenes completos	Procesa datos en tiempo real
Mayor latencia	Baja latencia
Ideal para informes	Ideal para monitoreo
Ejemplo: ventas diarias	Ejemplo: clics en vivo

🚀 En 2025, la analítica en streaming es esencial para las empresas digitales.
Permite adaptarse rápidamente a las necesidades y hábitos de los usuarios.

<footer style="text-align:center; font-size:0.9em; color:#777;"> Hecho con ❤️ usando Jekyll + Spark | Proyecto de <strong>Alessandro Díaz M.</strong> </footer> ```
