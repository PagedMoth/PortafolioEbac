# 📊 Proyecto: Rendimiento de Cultivos Agrícolas

El rendimiento de los cultivos agrícolas está influenciado por múltiples factores, siendo el **tipo de suelo** uno de los más determinantes.  
Este proyecto se enfoca en analizar cómo las características del terreno afectan la productividad medida en **toneladas por hectárea**, con el fin de identificar patrones que permitan optimizar decisiones agronómicas.

A través de la recopilación y procesamiento de datos históricos sobre cultivos y tipos de tierra, se busca construir un **modelo predictivo** que facilite estimaciones precisas del rendimiento esperado en distintas condiciones edáficas.

---

## 🎯 Objetivo del Proyecto
Desarrollar y entrenar un modelo de **Machine Learning** utilizando **Google Cloud Platform (GCP)**, capaz de predecir el rendimiento de cultivos en función del tipo de suelo.  

El modelo será diseñado para:
- Ser desplegado de forma remota en la nube.  
- Integrarse en sistemas de consulta agronómica.  
- Escalarse para futuras aplicaciones en entornos productivos.  

---

## 🛠️ Herramientas Utilizadas en GCP
Para comenzar en GCP se utilizaron las siguientes APIs:

- **Cloud Storage**:  
  Se subieron los datos a la plataforma, donde se almacenó la tabla de los datos utilizados.  

- **Big Query**:  
  Se creó una tabla de datos a partir de la información almacenada en Cloud Storage, para poder trabajar con ella en la nube.  

- **Vertex AI**:  
  Se usó para el desarrollo y entrenamiento del modelo de Machine Learning.  

Los datos provienen de **Kaggle**, una plataforma que ofrece múltiples conjuntos de datos para aprendizaje y práctica, incluyendo datos reales de recolecciones empíricas de individuos o instituciones.

---

## ⚙️ Flujo de Trabajo
1. **Cloud Storage** → Subida y almacenamiento de los datos.  
2. **Big Query** → Creación de la tabla de datos para análisis.  
3. **Vertex AI** → Desarrollo del modelo de Machine Learning.  

---

## 🚀 Desarrollo en Vertex AI
- Se inicializa en el apartado de **Desarrollo de modelos** dentro de Vertex AI (menú desplegable lateral).  
- Se selecciona **Conjunto de datos** y se crea el dataset a partir de la tabla creada en Big Query.  
- Una vez creado el conjunto de datos, se procede a **Implementación y Uso**.  
- Se selecciona **+ CREAR** y se siguen las instrucciones apoyadas en las imágenes del proyecto.  

---

Para entrenar un nuevo modelo debemos ponerle nombre y elegir entre clasificación y regresión. Para este proyecto se utilizó regresión para estimar las toneladas producidas por cultivo.
Abajo se seleccionó AutoML el método de aprendizaje que ofrece Google con sus modelos de forma sencilla, si quisiéramos utilizar las librerías de pythorch, tenosrflow, etc, se debe seleccionar entrenamiento personalizado.

<div align="center">
  <img src="Imagenes%20Git%20Hub/Imagen1.png" alt="Interfaz Vertex AI" width="600"/>
</div>


