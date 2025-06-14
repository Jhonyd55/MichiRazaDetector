# 🐾 MichiRazaDetector

**MichiRazaDetector** es una herramienta creada por un amante de los gatitos, sin experiencia formal en razas de gatos, pero con el deseo de aprender y crear algo útil y bonito para la comunidad gatuna. Esta aplicación te permite clasificar imágenes de gatos por raza a través de modelos de machine learning y también limpiar tu dataset eliminando imágenes no deseadas.

Este proyecto tiene como objetivo principal la **clasificación automática de razas de gatos** utilizando técnicas de aprendizaje profundo, específicamente *Transfer Learning* con un modelo basado en `MobileNetV2`. Está diseñado para ser **escalable**, de manera que se puedan incorporar nuevas razas o técnicas sin necesidad de rehacer todo el pipeline.

---

## 🚀 Características

- 🔍 **Transfer Learning** con redes preentrenadas (MobileNetV2).
- 📁 Dataset con **más de 50 razas de gatos**.
- 📊 Métricas de evaluación completas (Precision, Recall, F1-score).
- 📉 Curvas ROC individuales para cada clase.
- 📈 Matriz de confusión y visualización del rendimiento.
- 📦 Preparado para ampliación futura (más datos, técnicas, o salidas).
- 🖼️ Uso de imágenes con licencia pública (con fines educativos).
- ⚖️ Consideraciones sobre el desbalance de clases incluidas.

---

## 🖼️ Dataset

- Las imágenes fueron obtenidas desde internet, específicamente de fuentes de **licencia pública y uso educativo** ya que no queremos tener problemas de **copyright**.
 
  ![gato1](https://github.com/user-attachments/assets/aae4d348-184b-4821-ac39-e73247441d0c) ![image](https://github.com/user-attachments/assets/2c5091ae-fad5-4c20-baa5-0da19f9daf50).
  *imágenes tomadas de internet con **licencia pública***


- Se identificaron **problemas de desbalance**, ya que algunas razas tienen muchas más imágenes que otras. Esto se dejó así por fines prácticos del entrenamiento y análisis del modelo, no obstante, se plantea como una línea de mejora futura.

---
## 🧽 Limpieza de imágenes

Una de las funcionalidades más prácticas de **MichiRazaDetector** es la capacidad de eliminar imágenes directamente desde la interfaz:

<div align="center">

  <img src="https://github.com/user-attachments/assets/aae4d348-184b-4821-ac39-e73247441d0c" alt="interfaz de imagenes" width="70%">

  <p><em>Herramienta para la eliminación de las imágenes no deseadas.</em></p>

</div>
  
- Se muestra una galería con las imágenes de entrenamiento y prueba.
- Puedes seleccionar múltiples imágenes (haciendo clic en ellas).
- Luego, presionas el botón **Eliminar imágenes seleccionadas** y las imágenes se eliminan físicamente del disco.

Esto permite depurar el conjunto de datos de forma visual y rápida, eliminando imágenes borrosas, repetidas o con errores.

---

## 🧠 Resultados del modelo

Tras entrenar el modelo, se obtuvo un **accuracy general del 55%** sobre el conjunto de prueba. A continuación, se muestran algunos de los resultados más relevantes por raza:

- 🐱 **Bombay cat**: 0.82 precision, 0.90 recall, 0.86 f1-score
- 🐱 **Lykoi cat**: 0.83 precision, 1.00 recall, 0.91 f1-score
- 🐱 **Selkirk Rex cat**: 1.00 precision, 0.70 recall, 0.82 f1-score

Algunas razas con bajo desempeño:

- ❌ **Balinese cat**: 0.22 precision
- ❌ **Ragamuffin cat**: 0.12 precision
- ❌ **Colorpoint Shorthair cat**: 0.20 precision

Esto se puede deber a la baja cantidad o baja calidad de imágenes para esas clases, por lo cual la limpieza del dataset puede mejorar estos resultados.

📊 **Resumen general:**

- Accuracy total: **0.55**
- Precision media (macro): **0.57**
- Recall media (macro): **0.54**
- f1-score medio (macro): **0.54**

## 🔍 Matriz de Confusión

Esta matriz muestra cómo se distribuyen las predicciones correctas y erróneas entre las distintas razas:

<p align="center">
  <img src="https://github.com/user-attachments/assets/tu_imagen_matriz_confusion.png" alt="Matriz de Confusión" width="70%">
</p>

<p align="center"><em>Nota: Esta visualización es útil para identificar razas que se confunden fácilmente entre sí.</em></p>

---

## 📈 Rendimiento del Modelo

A continuación se muestra la evolución de la precisión y la pérdida durante el entrenamiento y validación del modelo:

<p align="center">
  <img src="./4b291e2d-371c-4626-8ee2-5bfc076f42bb.png" alt="Precisión y pérdida del modelo" width="90%">
</p>

Durante las primeras épocas, se observa un rápido incremento en la precisión del entrenamiento, mientras que la precisión de validación se estabiliza más pronto, lo cual puede ser indicativo de **sobreajuste**.  
De igual manera, la pérdida de validación deja de disminuir significativamente tras cierto punto, lo cual refuerza la necesidad de técnicas de regularización o parada temprana si se desea mejorar la generalización del modelo.

<p align="center"><em>Estas gráficas permiten monitorear el desempeño del modelo y detectar posibles problemas como el sobreentrenamiento.</em></p>


---

## 📈 Curvas ROC

Se calcularon y visualizaron las curvas ROC para cada una de las clases utilizando `OneVsRestClassifier` y codificación binaria `LabelBinarizer`. 

A continuación, los resultados visuales por clase:

| Clase | Curva ROC |
|-------|-----------|
| Clase 1 | ![ROC Clase 1](sandbox:/mnt/data/242c7734-7c19-4a90-a8b2-1b03482d2780.png) |
| Clase 2 | ![ROC Clase 2](sandbox:/mnt/data/01442769-abbb-460f-b6c9-8dff4fdd4f80.png) |
| Clase 3 | ![ROC Clase 3](sandbox:/mnt/data/26d9fa02-b2ae-433f-ab1e-4e0a029ed122.png) |
| Clase 4 | ![ROC Clase 4](sandbox:/mnt/data/5e934711-31ab-4da9-b1f4-90c54e10948d.png) |
| Clase 5 | ![ROC Clase 5](sandbox:/mnt/data/0c17f4d0-f0c1-4946-a00b-40f96bca3088.png) |
| Clase 6 | ![ROC Clase 6](sandbox:/mnt/data/1c117029-5fb9-4d56-a41a-e90fcda1eebb.png) |

**Observaciones:**
- Algunas clases (por ejemplo, *Bombay cat* o *Lykoi cat*) muestran curvas con alta AUC (> 0.9), lo cual indica buen rendimiento.
- Otras razas como *Balinese cat* o *Ragamuffin cat* presentan curvas más cercanas a la línea diagonal (AUC ≈ 0.5), lo que implica que el modelo tiene dificultad para diferenciarlas correctamente.
- Este fenómeno está directamente relacionado con el desbalance de datos y la posible similitud visual entre ciertas razas.

---

## 📊 Reporte de Clasificación

```text
                          precision    recall  f1-score   support

          Abyssinian cat       0.65      0.73      0.69        15
    American Bobtail cat       0.82      0.64      0.72        14
       American Curl cat       0.67      0.75      0.71         8
  American Shorthair cat       0.59      0.87      0.70        15
   American Wirehair cat       1.00      0.25      0.40         8
            Balinese cat       0.22      0.17      0.19        12
              Bengal cat       0.64      0.60      0.62        15
              Birman cat       0.45      0.60      0.51        15
              Bombay cat       0.82      0.90      0.86        10
    British Longhair cat       0.64      0.64      0.64        14
   British Shorthair cat       0.47      0.60      0.53        15
             Burmese cat       0.60      0.40      0.48        15
            Burmilla cat       0.48      0.80      0.60        15
           Chartreux cat       0.50      0.14      0.22        14
Colorpoint Shorthair cat       0.20      0.12      0.15         8
         Cornish Rex cat       0.58      0.50      0.54        14
              Cymric cat       0.50      0.47      0.48        15
           Devon Rex cat       0.47      0.47      0.47        15
        Egyptian Mau cat       0.62      0.45      0.53        11
    European Burmese cat       0.43      0.30      0.35        10
    Exotic Shorthair cat       0.83      0.45      0.59        11
        Havana Brown cat       0.70      0.64      0.67        11
           Himalayan cat       0.67      0.67      0.67        12
    Japanese Bobtail cat       0.60      0.43      0.50         7
          Khao Manee cat       0.62      0.50      0.56        10
               Korat cat       0.60      0.60      0.60        15
              LaPerm cat       0.75      0.80      0.77        15
               Lykoi cat       0.83      1.00      0.91        15
          Maine Coon cat       0.67      0.50      0.57        12
                Manx cat       0.58      0.47      0.52        15
    Norwegian Forest cat       0.50      0.57      0.53        14
              Ocicat cat       0.58      0.47      0.52        15
            Oriental cat       0.50      0.73      0.59        15
             Persian cat       0.67      0.67      0.67        15
            Pixiebob cat       0.56      0.75      0.64        12
          Ragamuffin cat       0.12      0.13      0.12        15
             Ragdoll cat       0.36      0.36      0.36        14
        Russian Blue cat       0.38      0.53      0.44        15
            Savannah cat       0.57      0.80      0.67        10
       Scottish Fold cat       0.71      0.50      0.59        10
         Selkirk Rex cat       1.00      0.70      0.82        10
             Siamese cat       0.42      0.53      0.47        15
            Siberian cat       0.43      0.40      0.41        15
           Singapura cat       0.46      0.55      0.50        11
            Snowshoe cat       0.64      0.58      0.61        12
              Somali cat       0.67      0.36      0.47        11
              Sphynx cat       0.62      0.77      0.69        13
           Tonkinese cat       0.31      0.33      0.32        15
              Toyger cat       0.60      0.64      0.62        14
      Turkish Angora cat       0.25      0.22      0.24         9
         Turkish Van cat       0.50      0.64      0.56        11

                accuracy                           0.55       652
               macro avg       0.57      0.54      0.54       652
            weighted avg       0.56      0.55      0.54       652
```

#### 📌 Interpretación General:

- La mayoría de las clases tienen un **AUC (Área bajo la curva)** superior a 0.9.
- En particular, las clases 1, 2 y 6 muestran una capacidad de clasificación **muy alta**, con curvas cercanas al óptimo.
- Clases como la 4 y 5 presentan una **ligera disminución** de rendimiento, posiblemente debido a menor cantidad de datos o similitud visual con otras clases.
- Esto sugiere que **el modelo generaliza bien**, pero se puede mejorar balanceando el dataset o ajustando hiperparámetros.

---

## 🚀 Escalabilidad del Proyecto

Este proyecto fue diseñado con **modularidad y escalabilidad** en mente. Algunas formas en que puede crecer:

- 🔄 Añadir más razas (simplemente agregando nombres al array y reentrenando).
- 📈 Mejorar el balance del dataset.
- 🌎 Soporte multilingüe en la interfaz Gradio.
- 📱 Integración con aplicaciones móviles o clínicas veterinarias.
- 💾 Implementación como API REST para producción.

---
## 🎲 Predicción Aleatoria sobre Imagen de Validación

El programa incluye una funcionalidad que selecciona **aleatoriamente una imagen** del conjunto de validación para evaluarla con el modelo previamente entrenado.

Esta herramienta permite observar cómo el modelo se comporta en condiciones reales sobre imágenes no vistas durante el entrenamiento.

### 🛠 ¿Cómo funciona?

- Se elige una **clase aleatoria** (por ejemplo: `beagle`, `poodle`, etc.).
- Dentro de esa clase, se selecciona **una imagen al azar**.
- La imagen se carga, se preprocesa (ajuste de tamaño y normalización), y luego se pasa al modelo para hacer la predicción.
- Se muestra la imagen con:
  - La clase **real**.
  - La clase **predicha** por el modelo.
  - El **nivel de confianza** del modelo para esa predicción.

### 📷 Ejemplos de visualización

A continuación se presentan cinco ejemplos de imágenes de validación seleccionadas aleatoriamente y evaluadas por el modelo:

<p align="center">
  <img src="random1.png" width="30%" style="margin: 5px;">
  <img src="random2.png" width="30%" style="margin: 5px;">
  <img src="random3.png" width="30%" style="margin: 5px;"><br>
  <img src="random4.png" width="30%" style="margin: 5px;">
  <img src="random5.png" width="30%" style="margin: 5px;">
</p>

<p align="center"><em>Cada imagen fue seleccionada y evaluada aleatoriamente desde el conjunto de validación. Se muestra la clase verdadera, la clase predicha y el nivel de confianza.</em></p>


## 🌐 Interfaz de Usuario

Se incluye una interfaz web con Gradio donde puedes:

- Subir una imagen de un gato.
- Ver las probabilidades de predicción.

  ### 📷 Ejemplo de visualización

<p align="center">
  <img src="https://github.com/user-attachments/assets/imagen_random_predicha.png" alt="Predicción aleatoria" width="60%">
</p>

<p align="center"><em>La imagen cargada es evaluada en tiempo real y visualizada con su clase predicha y el nivel de confianza.</em></p>

---
## 📱 Modelo para Móviles

El modelo fue convertido a formato `.tflite` para su integración en aplicaciones Android mediante TensorFlow Lite. Esto permite ejecutar inferencias localmente sin necesidad de conexión a internet. (En desarrollo)

---

## 🗃️ Archivos Importantes

- `michi_model.h5`: Modelo entrenado en formato Keras.
- `michi_model.tflite`: Modelo optimizado para Android.
- `dataset_original.zip`: Imágenes predescargadas y listas para uso.
- `README.md`: Este archivo.

---
## 🔄 Escalabilidad

La arquitectura del proyecto ha sido diseñada para facilitar su extensión y mantenimiento. Algunas características clave incluyen:

- ✅ **Agregación sencilla de nuevas clases**: solo es necesario incluirlas en la estructura del dataset y entrenar nuevamente.
- 🧠 **Cambio de backbone flexible**: permite reemplazar el modelo base (como ResNet, MobileNet, EfficientNet, etc.) con ajustes mínimos.
- 🧪 **Integración de nuevas métricas**: se pueden añadir fácilmente otros métodos de evaluación o aplicar validación cruzada.
- 🔁 **Soporte para técnicas de mejora**: como *data augmentation*, *class balancing*, y preprocesamiento más sofisticado.

---

## 📌 Consideraciones Finales

- ⚠️ Las imágenes del dataset no fueron normalizadas en cuanto a color, iluminación o proporción. Se decidió mantenerlas así como parte de un enfoque realista y práctico.
- 🧩 Se planea incluir técnicas de **data augmentation** para mejorar la capacidad de generalización del modelo y compensar desbalances en el dataset.
- 🚀 Próximos pasos:
  - Optimización del entrenamiento y fine-tuning.
  - Despliegue del modelo como **API REST** o **aplicación web interactiva**.
  - Curación y mejora del dataset para futuras versiones del proyecto.


## 👨‍💻 Autor

**Jhony Michael Durán Ramírez**  
*Ingeniero de electrónico | Master en Inteligencia Artificial*  
[Villa del Rosario, Norte de Santander]  
Proyecto realizado como parte del estudio de técnicas de visión por computador.
