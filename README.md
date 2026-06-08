<!-- # Descripción del proyecto
A la cadena de supermercados Good Seed le gustaría explorar si la ciencia de los datos puede ayudarle a cumplir con las leyes sobre el alcohol, al asegurarse de no vender alcohol a personas menores de edad. Te piden que hagas esa evaluación, así que, cuando te pongas a trabajar, ten en cuenta lo siguiente:
- Las tiendas están equipadas con cámaras en el área de pago, las cuales se activan cuando una persona está comprando alcohol.
- Los métodos de visión artificial se pueden usar para determinar la edad de una persona a partir de una foto.
- La tarea, entonces, es construir y evaluar un modelo para verificar la edad de las personas.
  
Para empezar a trabajar en la tarea, tendrás un conjunto de fotografías de personas que indican su edad.
-->

## Objetivo de negocio
La cadena de supermercados Good Seed busca garantizar el cumplimiento estricto de las leyes locales sobre la restricción de venta de alcohol a menores de edad, por lo que busca evaluar e implementar tecnologías de ciencia de datos y visión artificial a través de las cámaras ubicadas en el área de cajas. Las cámaras se activan automáticamente cuando un cliente intenta comprar una bebida alcohólica. A partir de estos datos se pretende construir un modelo predictivo automatizado capaz de estimar la edad de las personas a partir de una fotografía para asistir a los cajeros, mitigar el error humano, evitar sanciones legales y automatizar la verificación de identidad.

## Descripción del dataset
Estructura del contenido:
- Imágenes: Una carpeta llamada final_files que aloja un volumen total de 7,591 fotografías en formato .jpg.
- Etiquetas: Un archivo complementario llamado labels.csv estructurado con dos columnas principales:
  - file_name: El nombre correspondiente al archivo de imagen.
  - real_age: Variable numérica entera (int64) que representa la edad real de la persona fotografiada.

## Metodología
- Tratamiento y Carga Eficiente: Debido al alto volumen computacional de procesar miles de imágenes en memoria simultáneamente, se utiliza la clase ImageDataGenerator de la biblioteca TensorFlow / Keras.
- Escalamiento y Normalización: Se normalizan los valores de los píxeles dividiéndolos entre 1/255. para estandarizar las entradas de color al rango numérico de [0, 1].
- Redimensión de Imágenes: Todas las muestras fotográficas son reajustadas a un tamaño objetivo estándar (target_size) de 224×224 píxeles con canales RGB y procesadas en lotes (batch size) de 32 imágenes.
- Estrategia de Modelado: Se plantea como un problema clásico de Regresión (y no de clasificación), dado que el objetivo es predecir un valor numérico continuo (la edad exacta en años).

## Modelos utilizados
- Framework Principal: TensorFlow junto a la API de alto nivel Keras.
- Arquitectura Base: Redes Neuronales Convencionales (CNN). Para optimizar los tiempos de entrenamiento y aprovechar el aprendizaje previo, el proyecto se apoya en una arquitectura preentrenada de vanguardia: ResNet50.
- Función de Activación Final: Lineal o ReLU, óptimas para la salida de un número continuo (edad).

## Métricas
- Métrica de Evaluación de Negocio: EAM (Error Absoluto Medio) o MAE por sus siglas en inglés (Mean Absolute Error).
- Criterio de Aceptación: El requerimiento explícito del departamento técnico estipula que el valor final de EAM en el conjunto de prueba no debe ser superior a 8. Esto significa que el modelo no debe equivocarse por más de 8 años en promedio al calcular la edad de un cliente.

## Resultados
- El entrenamiento del modelo de visión artificial usando la arquitectura ResNet50 convergió exitosamente, superando las métricas requeridas en el notebook validado por el revisor de datos.
- El modelo obtuvo un EAM inferior a 8 en las iteraciones finales del conjunto de prueba independiente, cumpliendo rigurosamente con los objetivos del proyecto y ganando el visto bueno del revisor de la plataforma (TripleTen).

## Conclusiones
- La ciencia de datos y los métodos de aprendizaje profundo (Deep Learning) aplicados a la visión artificial son herramientas viables y altamente efectivas para resolver la problemática planteada por Good Seed.
- Al mantener el margen de error promedio por debajo del límite de 8 años, el modelo proporciona un filtro de seguridad automatizado sumamente confiable para identificar discrepancias críticas de edad en la línea de cajas.
- La integración de este modelo en el software de las cámaras del área de pagos permitirá alertar al personal humano de forma oportuna cuando se detecte un comprador sospechoso de ser menor de edad, asegurando el cumplimiento de las leyes de venta de alcohol y protegiendo a la cadena de supermercados de multas y sanciones legales.
