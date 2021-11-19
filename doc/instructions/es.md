[![](https://img.shields.io/badge/IBM%20Cloud-powered-blue.svg)](https://cloud.ibm.com)
[![](https://img.shields.io/discord/734849242153222221?logo=discord)](https://discord.gg/yJYmTGDWKH)

# Desafio 01 | Bantotal

- [1. Sobre Bantotal](#1-sobre-bantotal)
  - [1.1. Introducción](#11-introducción)
  - [1.2. Premiación](#12-premiación)
- [2. Desafio de negocio](#2-desafio-de-negocio)
- [3. Objetivo](#3-objetivo)
- [4. Tecnologias aplicadas](#4-tecnologias-aplicadas)
- [5. Desarrollo de la Solución](#5-desarrollo-de-la-solución)
- [5.1. Pre-requisitos](#51-pre-requisitos)
- [5.2. Resumen de Tareas](#52-resumen-de-tareas)
- [5.3. Desarollo](#53-desarollo)
  - [Importación de un proyecto a Watson Studio](#importación-de-un-proyecto-a-watson-studio)
- [6. Envío](#6-envío)
- [7. Sobre la evaluación](#7-sobre-la-evaluación)

## Para ayudarte

- [Material de Apoyo](#materiales-de-apoyo)

## 1. Sobre Bantotal

### 1.1. Introducción

Bantotal es la plataforma bancaria líder en América Latina, que resuelve la operativa de misión crítica de las Instituciones Financieras en forma simple y precisa.

La plataforma bancaria Bantotal ingresa al mercado en 1991 y se convierte en líder para América Latina. Su casa central se encuentra en Uruguay, donde también se ubican su Departamento de I+D, su Centro de Servicios de Mantenimiento global y su Centro de Capacitación. Cuenta con oficinas comerciales y de servicios en: Argentina, Chile, Colombia, México, Perú y Uruguay. Sus Centros de Desarrollo de Software están ubicados en Perú y Uruguay.

### 1.2. Premiación

Bantotal entregará como premio un voucher de compra por valor de USD 500 (quinientos dólares) a las dos personas mejor puntuadas en su desafío.

## 2. Desafio de negocio

Cada vez que un cliente solicita un crédito a una institución financiera se activan varios procesos y controles internos, necesarios para la evaluación de la solicitud recibida. De esta forma, se analizan manualmente mucha información vinculada al perfil del cliente, destinos del crédito, actividad laboral, ingresos, condiciones de la vivienda, entre otros datos demográficos.

Adicionalmente, la institución hace uso de los denominados Buró de créditos para conocer el historial crediticio del cliente con el fin de definir su perfil crediticio. Junto con otros historiales propios, información proveniente de otros créditos, nivel de cumplimiento y comportamiento en sus productos contratados, la institución aprueba un monto a prestar y un plazo para su devolución, o rechaza la solicitud.

## 3. Objetivo

El desafío consiste en crear un modelo de inteligencia artificial capaz de realizar un análisis de riesgo para predecir si se debe o no realizarse un préstamo a un cliente. Para ello, se espera el uso de un modelo de Machine Learning capaz de realizar una clasificación.

El modelo se puede desarrollar en la plataforma [Watson Studio](https://cloud.ibm.com/catalog/services/watson-studio) y debe publicarse en una instancia de [Watson Machine Learning](https://cloud.ibm.com/catalog/services/machine-learning).

El modelo debe entrenarse con el conjunto de datos disponible en este repositorio, que contiene datos de clientes bancarios como datos demográficos, sus cuentas y préstamos realizados.

## 4. Tecnologias aplicadas

Para este desafío se utilizarán los siguientes servicios de IBM Cloud:

- [Watson Studio](https://cloud.ibm.com/catalog/services/watson-studio), también conocido como Cloud Pak for Data as a Service. Este servicio permite el uso de una variedad de herramientas relacionadas con la ciencia de datos, incluida la ejecución de Jupyter Notebooks con procesadores en la nube.

- [Watson Machine Learning](https://cloud.ibm.com/catalog/services/machine-learning) (WML). Este servicio proporciona una serie de recursos para crear, capacitar y publicar modelos de aprendizaje automático. Para la validación del desafío, solicitamos a los participantes que envíen sus modelos en forma de publicación WML. De esta manera, será posible validar el modelo mediante llamadas HTTP.

Recomendamos usar el lenguaje [Python](https://www.python.org/), con [Jupyter Notebooks](https://jupyter.org/), por lo que que proporcionamos ejemplos de código con estas herramientas, para usarlos en Watson Studio.

Sin embargo, el participante es libre de usar el lenguaje y la herramienta que desee para resolver el desafío, siempre que pueda publicar el modelo en [Watson Machine Learning](https://cloud.ibm.com/catalog/services/machine-learning).

Pueden consultarse los _frameworks_ compatibles [en esta página](https://dataplatform.cloud.ibm.com/docs/content/wsj/analyze-data/pm_service_supported_frameworks.html?context=analytics&audience=wdp).

## 5. Desarrollo de la Solución

### 5.1. Pre-requisitos

Para realizar este desafío, debe cumplir con los siguientes requisitos previos:

- Registrarse en la [Maratón Behind the Code](https://maratona.dev/?register=true) y confirmar su correo electrónico de registro;
- Tener una [cuenta de IBM Cloud](https://ibm.biz/Bdf8dW), que puede ser Lite o Pay-As-You-Go (no es necesario registrarse para el evento con la misma dirección de correo electrónico utilizada para crear su cuenta de IBM Cloud).

### 5.2. Resumen de Tareas

1. Cree una instancia de los servicios del desafío en IBM Cloud: Watson Machine Learning (obligatorio). Object Storage y Watson Studio (opcionales);
2. Si utiliza Watson Studio, descargue [el proyecto](../../assets/project.zip) e impórtelo a su servicio;
3. Lea y ejecute las instrucciones contenidas en el [Jupyter Notebook](../../assets/notebooks);
4. Cambie, valide y pruebe su modelo de Machine Learning, hasta que esté satisfecho con el resultado;
5. Cree un deployment de Watson Machine Learning con su modelo;
6. Submita su solución en la [página del desafío](https://maratona.dev/challenge/1).

### 5.3. Desarollo

El desafío es desarrollar un modelo de Machine Learning para predecir el riesgo de un préstamo, basado en la información bancaria. Deberá explorar los datos, procesarlos y crear el modelo para la predicción.

El modelo debe recibir los siguientes datos como entrada:

```python
[
  "ID",                             # Número identificador del cliente
  "CHECKING_BALANCE",               # Saldo que posee el cliente en su cuenta corriente
  "PAYMENT_TERM",                   # Cantidad de días que el cvliente posee para pagar el préstamo
  "CREDIT_HISTORY",                 # Situación crediticia pasada del cliente
  "LOAN_PURPOSE",                   # Motivo del préstamo
  "LOAN_AMOUNT",                    # Monto del préstamo
  "EXISTING_SAVINGS",               # Saldo de cuenta de ahorros
  "EMPLOYMENT_DURATION",            # Cuántos años ha permanecido el cliente en su empleo
  "INSTALLMENT_PERCENT",            # Cantidad de cuotas en las que el préstamo debe ser pagado
  "SEX",                            # Sexo del cliente
  "OTHERS_ON_LOAN",                 # Denota la existencia de un garante u otro solicitante del préstamo
  "CURRENT_RESIDENCE_DURATION",     # Años que el cliente ha permanecido en su última residencia
  "PROPERTY",                       # Indica si el cliente posee alguna propiedad a su nombre
  "AGE",                            # Edad del cliente
  "INSTALLMENT_PLANS",              # Plan de financiamiento, que puede ser del banco, externo o ninguno
  "HOUSING",                        # Indica si el cliente posee una casa propia
  "EXISTING_CREDITS_COUNT",         # Número de préstamos que le han sido concedidos al cliente en el pasado
  "JOB_TYPE",                       # Tipo de empleo: 0 - desempleado, 1 - no calificado, 2 - autónomo, 3 - calificado
  "DEPENDENTS",                     # Número de personas con acceso a la cuenta
  "TELEPHONE",                      # Denota si el cliente tiene un número de teléfono registrado
  "FOREIGN_WORKER"                  # Denota si el cliente trabaja en un país fuera del banco
]
```

Y como salida un valor binario que representa si se debe permitir o no el préstamo (0 para no, 1 para sí).

**Atención**: los datos proporcionados en este desafío son ficticios, cualquier correlación con la realidad es mera coincidencia.

Para comenzar, sigue el paso a paso a continuación para importar el proyecto del desafío con los datos y el Notebook en Watson Studio. Alternativamente, también puedes ejecutar el [Notebook](../../assets/notebooks/notebook-es.ipynb) en otros entornos. En el Notebook encontrarás todas las instrucciones para crear un modelo de Machine Learning y publicarlo en Watson Machine Learning.

#### Importación de un proyecto a Watson Studio

Primero, [cree una instancia de Watson Studio](https://cloud.ibm.com/catalog/services/watson-studio) en su cuenta de IBM Cloud, si aún no la tiene, e ingrese a [página de inicio de IBM Cloud Pak for Data as a Service](https://dataplatform.cloud.ibm.com/) a través de la instancia.

Descargue el archivo [project.zip](../../assets/project.zip) que se encuentra en este repositorio.

En la página de inicio, en la sección `Work with data`, haga clic en `Create a project`.

![creando-proyecto](https://s3.br-sao.cloud-object-storage.appdomain.cloud/maratona-static/create-project.png)

Después de abrir la nueva página, haga clic en `Create a project from a sample or file`.

![creando](https://s3.br-sao.cloud-object-storage.appdomain.cloud/maratona-static/creating.png)

Haga clic en `Drop a file here or browse for file to upload` o arrastra tu archivo al área resaltada.

![seleccionar-archivo](https://s3.br-sao.cloud-object-storage.appdomain.cloud/maratona-static/select-file.png)

Después de cargarlo, dale un nombre a tu proyecto y una descripción, si así lo deseas.

![naming](https://s3.br-sao.cloud-object-storage.appdomain.cloud/maratona-static/name.png)

¡Listo!

Ahora simplemente ve a la pestaña `Assets` de tu proyecto para ver la lista de archivos y Notebooks.

![assets.png](https://s3.br-sao.cloud-object-storage.appdomain.cloud/maratona-static/assets.png)

Desde aquí, podrás abrir el Notebook en tu proyecto y seguir las instrucciones para llevar a cabo el desafío.

## 6. Envío

Una vez tenga el modelo listo, el último paso es realizar el envío. Recuerde que **sólo se aceptará un envío para el desafío**, así que pruébelo bien antes de enviarlo.

🚨 CAMBIO EN EL MECANISMO DE ENVÍO 🚨

Debido a problemas con los límites del plan gratuito de Watson Machine Learning, cambiamos el sistema de envío para solicitar un archivo CSV. Para entregar el desafío, debe cambiar el [archivo con la tabla de respuestas](../../assets/data/ANSWERS.csv) disponible en ese repositorio, completando el valor de la columna `ALLOW` en las 1000 líneas del archivo con las predicciones de su modelo (valores 0 o 1). Evaluaremos su solución en función de las respuestas en el archivo CSV.

Para enviar, debe acceder a la página de desafío: [https://maratona.dev/challenge/1](https://maratona.dev/challenge/1) y enviar el archivo CSV con las respuestas, junto con un archivo `.zip`, hasta 10 MB, que contiene el código fuente de la solución (recuerde eliminar las dependencias y los conjuntos de datos para que no ocupen espacio). La página probará el archivo CSV para verificar que se encuentra en el formato correcto.

Podrá seguir el estado de la entrega accediendo a la [página del desafío](https://maratona.dev/challenge/1), iniciando sesión en su cuenta.

## 7. Sobre la evaluación

Una semana después del inicio del desafío, nuestro sistema de evaluación automatizado iniciará las evaluaciones. Utilizará los datos para calcular una puntuación numérica del 1 al 100, basado en la métrica [F<sub>1</sub>](https://en.wikipedia.org/wiki/F-score). El archivo `.zip` enviado debe contener todo el código utilizado para obtener la solución. De lo contrario, la puntuación será cero.

Si el desafío se entrega dentro del plazo de envío (hasta el 21 de noviembre), el participante recibirá una bonificación del 10% de la puntuación total (10 puntos), independientemente del resultado de su desafío. Por tanto, la puntuación máxima posible es 110 (puntuación de 100 + bonificación de 10).

Después del plazo de envío, el participante aún puede realizar su envío hasta el 12 de diciembre, pero sin recibir el bono.

**Atención**: nos reservamos el derecho de darle a um envío cero de puntuación si:

- El código fuente enviado no es consistente con los resultados obtenidos de las pruebas en el modelo.
- Se detecta plagio, de uno o más participantes. En este caso, se dará cero puntos al desafio entregado por todos los participantes con la misma solución.

## Materiales de apoyo

- [Documentación de Watson Machine Learning](https://dataplatform.cloud.ibm.com/docs/content/wsj/analyze-data/ml-overview.html)
- [Introducción a IBM Watson Studio](https://developer.ibm.com/es/articles/introduction-watson-studio/)
- [Toma el control de tus datos con Watson Studio](https://developer.ibm.com/es/series/learning-path-watson-studio/)
- [Visualizar datos con Python](https://developer.ibm.com/es/patterns/visualize-data-with-python/)
- [Generar un Python notebook para modelos de pipeline usando AutoAI](https://developer.ibm.com/es/patterns/autoai-code-generation/)
- [Automatizando Machine Learning como un campeón con Watson AutoAI](https://developer.ibm.com/es/tutorials/automatizando-machine-learning-como-un-campeon-con-watson-autoai/)
- [Despliega tu modelo de Machine Learning en la nube con Watson](https://developer.ibm.com/es/tutorials/despliega-tu-modelo-de-machine-learning-en-la-nube-con-watson/)
- [¿Qué es la Analítica predictiva?](https://developer.ibm.com/es/articles/ba-predictive-analytics1/)
- [Cree una solución predictiva](https://developer.ibm.com/es/articles/ba-predictive-analytics3/)
- [Introducción a IBM Cloud Pak for Data](https://developer.ibm.com/es/articles/get-started-with-ibm-cloud-pak-for-data/)
- [Desarrollar modelos de machine learning con y sin AutoML](https://developer.ibm.com/es/articles/compare-model-building-with-and-without-automated-machine-learning/)
- [Ponga en marcha una solución predictiva](https://developer.ibm.com/es/articles/ba-predictive-analytics4/)
- [Ética de Datos: 5 razones de sesgo en modelos de Machine Learning y cómo evitarlos](https://developer.ibm.com/es/articles/datos-vs-modelo-reduciendo-sesgos-en-conjuntos-de-datos/)
- [Cómo resolver un problema de negocio y pronosticar la rotación de clientes utilizando un conjunto de datos de pérdida de clientes](https://developer.ibm.com/es/patterns/solve-a-business-problem-and-predict-customer/)
- [Crea un modelo predictivo de machine learning de manera rápida y sencilla con IBM SPSS Modeler](https://developer.ibm.com/es/tutorials/build-a-predictive-machine-learning-model-quickly-and-easily-with-ibm-spss/)
- [Construir un predictor del mercado de valores](https://developer.ibm.com/es/patterns/predicting-the-stock-market-in-watson-studio/)

Recuerda que puedes acceder al Discord oficial del Maratón 2021 para hacer preguntas y/o interactuar con otros participantes: [Discord](https://discord.gg/yJYmTGDWKH).

## License

Copyright 2021 Maratona Behind the Code

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
