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
  <img src="Imagenes%20Git%20Hub/Imagen1.png" alt="Imagen 1" width="600"/>
</div>

En el paso 2 se seleccionó la columna objetivo, este paso es muy importante porque es la que indicamos que es lo que el modelo queremos que calcule.

<div align="center">
  <img src="Imagenes%20Git%20Hub/Imagen2.png" alt="Imagen 2" width="600"/>
</div>

Las funciones son si queremos agregar más datos conectados a la tabla que tenemos para el entrenamiento. Para este proyecto se omitió y siguió con la creación del modelo.

<div align="center">
  <img src="Imagenes%20Git%20Hub/Imagen3.png" alt="Imagen 3" width="600"/>
</div>

En el paso 4 podemos revisar nuevamente la tabla y seleccionar los datos que queremos que utilice solamente para el entrenamiento, al igual que podemos cambiar el tipo de columna de categórica o numérica si es que existe alguna discrepancia.

<div align="center">
  <img src="Imagenes%20Git%20Hub/Imagen4.png" alt="Imagen 4" width="600"/>
</div>

Para esta sección 5 también tiene un peso importante porque aquí depende el tiempo y el dinero que nosotros vamos a destinar que se utilice para que se entrene el modelo de ML, y esto afecta directamente en el tiempo de desarrollo del modelo y en el costo que implica entrenarlo. Para este proyecto se utilizó un nodo/hora.

<div align="center">
  <img src="Imagenes%20Git%20Hub/Imagen5.png" alt="Imagen 5" width="600"/>
</div>

Ya que comienza el entrenamiento se puede ver en la sección de Desarrollo de Modelos > Entrenamiento. Para este proyecto se requirieron 2 horas con 1 min.

<div align="center">
  <img src="Imagenes%20Git%20Hub/Imagen6.png" alt="Imagen 6" width="600"/>
</div>

Ya que esté listo se verá de igual forma en la sección de Implementación y Uso > Registro de Modelos. 

<div align="center">
  <img src="Imagenes%20Git%20Hub/Imagen7.png" alt="Imagen 7" width="600"/>
</div>

Ya con el modelo entrenado los resultados fueron los siguientes:

<div align="center">
  <img src="Imagenes%20Git%20Hub/Imagen8.png" alt="Imagen 8" width="700"/>
</div>

Posteriormente se necesita hacer un despliegue de modelo, nosotros podemos usar un contenedor o usar un extremo (servidor) que Google nos proporciona donde igual podemos seleccionar el tipo de procesamiento que puede tener, la zona en el mundo donde podemos correr el servidor, así como los iconos para utilizar un servidor bajo en CO_2

<div align="center">
  <img src="Imagenes%20Git%20Hub/Imagen9.png" alt="Imagen 9" width="600"/>
</div>

<div align="center">
  <img src="Imagenes%20Git%20Hub/Imagen10.png" alt="Imagen 10" width="600"/>
</div>

Algo que se puede apreciar es que al entrar en la información del modelo como los logs de uso de GCP podemos notar qué tipo de entrenamiento utilizó, en este caso hizo un ordenamiento aleatorio de los datos en 80/10/10 esto quiere decir que utilizó 80 entrenamiento, 10 validación y 10 de prueba.

<div align="center">
  <img src="Imagenes%20Git%20Hub/Imagen11.png" alt="Imagen 11" width="400"/>
</div>

Y dentro de los logs de la consola también podemos observar que utilizó 25 combinaciones de hiper parámetros y fundamentalmente utilizó el modelo de tipo decisiones de árbol aumentado. 

<div align="center">
  <img src="Imagenes%20Git%20Hub/Imagen12.png" alt="Imagen 12" width="400"/>
</div>

<div align="center">
  <img src="Imagenes%20Git%20Hub/Imagen13.png" alt="Imagen 13" width="600"/>
</div>

Para finalizar los resultados del modelo fueron bastante buenos con una r^2= 0.998 y un error porcentual y absoluto muy bajos, por lo que podemos decir que es un buen modelo de predicción. También al sacar la importancia de los atributos con las configuraciones de Google podemos notar que el valor más importante para saber si un cultivo va a darme mucho o poco en rendimiento de toneladas es el tipo de cultivo, es decir si es de arroz, trigo, papa, etc.

<div align="center">
  <img src="Imagenes%20Git%20Hub/Imagen14.png" alt="Imagen 14" width="600"/>
</div>

<div align="center">
  <img src="Imagenes%20Git%20Hub/Imagen15.png" alt="Imagen 15" width="700"/>
</div>

<div align="center">
  <img src="Imagenes%20Git%20Hub/Imagen16.png" alt="Imagen 16" width="700"/>
</div>

Un último dato importante es el costo, con este proyecto se utilizó el dinero que Google provee por utilizar su plataforma en el lapso inicial de 3 meses aproximadamente regalando MXN $5500 para practicas o uso intensivo. Ahora para terminar con este documento me gustaría resaltar que, si se utiliza para este tipo de caso de 1 nodo/hora, servicios de almacenamiento y de despliegue digital con una base de datos de aproximadamente 10k registros se necesitó una inversión de $1,040.59 pesos con un tiempo inicial de 2hr de entrenamiento del modelo más el tiempo que se invierta para su uso manejo, mejoramiento, despliegue, distribución, etc. Puede variar, aunque con esto podemos tener una comprensión simple del costo de un proyecto básico. 

<div align="center">
  <img src="Imagenes%20Git%20Hub/Imagen17.png" alt="Imagen 17" width="1000"/>
</div>

<div align="center">
  <img src="Imagenes%20Git%20Hub/Imagen18.png" alt="Imagen 18" width="1000"/>
</div>

<div align="center">
  <img src="Imagenes%20Git%20Hub/Imagen19.png" alt="Imagen 19" width="1000"/>
</div>

Gracias por leer mi documento, espero que haya sido de ayuda para cualquier profesional de Ciencia de Datos o Análisis de Datos en la nube de GCP.
