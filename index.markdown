---
layout: default
title: "Inicio"
---

# 📘 Blog de Análisis de Datos

Bienvenido a mi blog creado con **Jekyll + Spark**.  
Aquí encontrarás el proyecto:  
**“Análisis de Flujo de Datos Simulado con Spark”**

---

{% for post in site.posts %}
### 🗓️ [{{ post.title }}]({{ post.url }})
Publicado el {{ post.date | date: "%d %B %Y" }}
{% endfor %}
