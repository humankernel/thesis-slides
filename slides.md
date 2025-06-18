---
theme: ./theme
title: Thesis
titleTemplate: "%s - Slides"
author: Joaquin
transition: slide-left
mdc: true
fonts:
  sans: Roboto
  serif: Roboto Slab
  mono: Maple Mono NF
---

<div class="flex flex-col justify-between h-[470px]">
  <div class="text-center flex flex-col justify-center gap-4">
    <span class=" font-bold opacity-60 text-md"> Universidad de las Ciencias Informáticas - 18/7/2025 </span>
  </div>

  <div class="text-5xl font-bold text-center">Desarrollo de una herramienta basada en LLM y RAG para asistir el análisis de artículos científicos.
  </div>

  <div class="flex justify-between text-sm">
    <span class="font-700 opacity-60">
      <span class="opacity-50"> Autor </span> <br>
      Joaquin E. Rivas Sánchez
    </span>
    <span class="font-700 opacity-60">
      <span class="opacity-50"> Tutores </span> <br>
       Msc. Angel Alberto Vazquez Sánchez <br>
       Msc. Lisset Salazar Gómez
    </span>
  </div>
</div>

<!--
Buenos días, en el dia de hoy se le dara presentación al trabajo de diploma titulado:

**LEER TITULO**

El autor es quien les habla y como tutores.

**LEER TUTORES**
-->

---
layout: image
image: "./assets/ai.webp"
---

<!--
En los últimos años, la inteligencia artificial generativa ha transformado profundamente diversas areas del saber como la investigación científica y académica.

Herramientas como Elicit o SciSpace **permiten analizar y sintetizar miles de artículos en minutos**, **acelerando descubrimientos** y **facilitando tareas** que antes resultaban inabordables por su volumen o complejidad.

Sin embargo, el acceso a estas herramientas presentan limitaciones significativas en entornos con recursos restringidos, como el cubano.
-->

---
layout: image
image: ./assets/homologos.webp
---

# Sistemas Homólogos

<!--
- Muchos servicios se encuentran bloqueados para usuarios en Cuba.

- Las opciones gratuitas son muy limitadas y el acceso a planes de pagos es inviable por restricciones económicas y políticas.

- Además, la mayoría de estas herramientas están enfocadas para un público angloparlante, lo que reduce su accesibilidad local.

Estas limitaciones generan una brecha tecnológica que limita la capacidad de los investigadores cubanos para competir en igualdad de condiciones en la ciencia global.
-->

---

# Problema de investigación

¿Cómo desarrollar una herramienta de IA accesible, efectiva y localizable que permita a investigadores cubanos analizar documentos científicos de forma semi-automatizada, aprovechando los modelos de lenguaje de gran tamaño y generación aumentada por recuperación (RAG), sin depender de infraestructura costosa o conexión a internet?

<!--
A partir de esta problematica surge como problema de investigación:

**LEER**
-->

---

# Objeto de Estudio

Modelos de Lenguaje de Gran Tamaño (LLM).

<br>
<br>

# Campo de Acción

Extensión de LLM basado en RAG.

---

# Objetivo General

Desarrollar una herramienta de código abierto, basada en LLM y RAG, para el análisis semiautomático de artículos científicos en PDF, adaptada al contexto tecnológico y lingüístico de Cuba.

<!-- 
Se propone como Objetivo General 
-->

---

# Tareas de investigación

+ Elaboración del marco teórico referente a modelos del lenguaje de gran tamaño y su extension utilizando generación aumentada por recuperación.
+ Análisis de sistemas homólogos para la identificación de los requisitos de software.
+ Implementación del sistema a partir de los requisitos de software.
+ Validación de la propuesta de solución.

<!-- 
Para dar cumplimiento al objetivo propuesto se proponen un conjunto de *tareas de investigación*:
-->

---
layout: image 
image: ./assets/ragg.webp
---

# ¿Qué es RAG y por qué es importante?

<!--
Primero es importante entender que es RAG:

Generación Aumentada por Recuperación (RAG) es una técnica que combina lo mejor de dos mundos:

1. La habilidad de **buscar y recuperar información específica** y actualizada de fuentes externas, como bases de datos, documentos o repositorios de datos.
2. La capacidad generativa de los LLM para sintetizar información.
-->

---

# Limitaciones de los LLM

| **Característica** | **LLM** | **LLM + RAG** |
|-----------|-----------|-----------|
| **Acceso a la información** | ❌ Conocimiento estático. | ✅ Acceso a información actualizada y en tiempo real. |
| **Verificación de respuestas**| ❌ Respuestas no verificables | ✅ Control y filtrado de la información  |
| **Manejo del contexto** | ❌ Bajo rendimiento en textos extensos. | ✅ El contexto contiene únicamente los fragmentos relevantes para cada consulta. |

<!--
Esto resuelve tres limitaciones clave de los LLM tradicionales:

- Los LLM por sí solos tienen un conocimiento estático, limitado a los datos con los que fueron entrenados, sin acceso a información posterior a ese entrenamiento.

- La verificación y control de la información generada es limitada, lo que puede provocar respuestas incorrectas o "alucinaciones"

- Tienen un limite de informacion de entrada y a menudo presentan un bajo rendimiento en textos largos o complejos, lo que puede afectar la coherencia y precisión de las respuestas.


En el prototipo, **este enfoque permite** al usuario: 

- Integrar conocimiento nuevo proveniente de documentos externos al sistema.
-->

---
layout: two-cols
---

<template v-slot:default>

<SlidevVideo autoplay muted loop class="h-[500px]">
  <source src="./assets/video-send-pdf.mp4" type="video/mp4" />
</SlidevVideo>

</template>

<template v-slot:right>

<img src="./assets/step-indexing.webp" />

</template>

<!--
El prototipo realizado consiste del siguiente flujo:

1. El usuario puede iniciar una conversación e introducir documentos en formato PDF:

2. El sistema los procesara, dividiendo el contenido en secciones de texto.
    - estas son transformados del lenguaje natural a una representación numérica (forma de vectores) que mantiene el significado semántico de estas.

3. estos vectores son guardados en una base de datos.
-->

---
layout: two-cols
---

<template v-slot:default>

<SlidevVideo autoplay muted loop class="h-[450px] absolute top-15 left-2">
  <source src="./assets/video-query.mp4" type="video/mp4"  />
</SlidevVideo>

</template>

<template v-slot:right>

<img src="./assets/step-querying.webp" />

</template>

<!--
Posteriormente, al usuario introducir una consulta

1. El sistema puede descomponer la misma en múltiples sub-preguntas.
2. Luego son convertidas a la misma representación numérica.
3. Posteriormente se realiza una búsqueda utilizando múltiples métodos de recuperación para obtener los documentos mas relevantes a la consulta.
4. los mismos son reordenados basados en la relevancia.
5. luego estos sirven de contexto para responder la pregunta utilizando el LLM.
-->

---
layout: image
image: "./assets/tech.webp"
---
# Tecnologías

<!--
Las tecnologias y herramientas utilizadas fueron las siguientes:

- vLLM como biblioteca para ejecutar los modelos de IA.

- Python como lenguaje de programación.

- Se utilizo `Qwen3-4B` como modelo LLM y `BGE-M3`, `BGM-M3-reranker` como modelo de generacion de embeddings y como modelo reranker.

- RAGAS como biblioteca para realizar las evaluaciones automatizadas.

- PyTorch para algunos algoritmos de comparación que requerian el uso de tensores.

- Gradio como biblioteca para construir la interfaz grafica.
-->

---

# Metodología de Desarrollo

La metodología "Programación Extrema" (XP) generó los siguientes artefactos:

- Historias de Usuario (12).

- Tareas de ingeniería (12).

- Pruebas Unitarias.

- Plan de Iteración (2).

- Estándares de Codificación

  - Patrón arquitectónico <span class="opacity-50"> (Arquitectura por Capas) </span>

  - Patrones de diseño.

<!-- 
El proyecto siguió la metodología ágil Programación Extrema (XP), gracias a:

Su enfoque en **ciclos iterativos cortos** y **pruebas constantes** ayuda a garantizar que cada avance sea funcional y **alineado con los objetivos del proyecto**.

Esta genero los siguientes artefactos ingenieriles.
 -->

---

# Requisitos funcionales

- **HU1: Enviar consultas**
- **HU2: Enviar archivos PDF**
- **HU3: Generar respuestas**
- **HU4: Procesar archivos**
- **HU5: Buscar documentos relevantes**
- **HU6: Mostrar documentos recuperados y sus puntuaciones**
- HU7: Regenerar respuesta
- HU8: Dar retroalimentación de una respuesta
- HU9: Editar una consulta previa
- HU10: Ajustar los parámetros del sistema
- HU11: Crear múltiples conversaciones
- HU12: Limpiar el chat

<!-- 
Entre los requisitos funcionales principales se encuentran:
 -->

---
layout: image
image: "./assets/performance.webp"
---

## Resultados y evaluación

<!--
En cuanto a los resultados obtenidos:

- Las pruebas de rendimiento fueron satisfactorias, arrojando resultados alentadores.

  - Con tiempos que no superan los 3.5 seg en las pruebas realizadas a la generación de respuestas.

  - y los 2 seg a la creación de embeddings
-->

---
layout: image
image: ./assets/ragas.webp
---

## Resultados y evaluación

<!--
Para las evaluaciones se utilizaron las métricas definidas por RAGAS:

Los resultados obtenidos fueron **LEER**, valores que se alinean con lo esperado. 

El rendimiento en Faithfulness y Factual Correctness está condicionado por el tamaño reducido del modelo LLM utilizado. 

Dado que la **investigación se enfoca** en el uso de LLM y RAG en entornos con recursos limitados, estos resultados reflejan un **balance adecuado entre precisión y eficiencia**, proporcionando una base sólida para futuras mejoras.
-->

---
layout: image
image: ./assets/rag.webp
---

<!-- 
En pantalla se puede ver el prototipo generado. 

A la izquierda, se encuentran los ajustes avanzados
  - como opciones de configuración del modelo
  - opciones de indexado avanzado, etc

En el centro, se muestra el área de conversación donde el usuario realiza consultas. 

A la derecha, se visualizan los documentos o fragmentos relevantes recuperados, junto a sus identificadores, lo que permite entender cómo el modelo selecciona la información utilizada para generar la respuesta.
 -->

---

# Conclusiones

- Se logró una revisión integral de los LLM y su extensión mediante RAG, lo cual permitió sustentar conceptualmente la herramienta propuesta.

- La metodología XP facilitó el desarrollo incremental, resultando en un prototipo funcional acorde al objetivo general planteado.

- El prototipo demostró viabilidad en hardware modesto, proporcionando una base sólida para futuras mejoras en generación y actualización documental continua.

<!-- 
Con el desarrollo de la herramienta se puede afirmar que:
-->

---

# Recomendaciones

- **Extender las fuentes de información mediante agentes web** que se conecten a repositorios académicos locales e internacionales.

- **Explorar lenguajes y técnicas de programación de alto rendimiento** para optimizar recursos.

- **Mejorar el preprocesamiento** de documentos con OCR y detección de estructuras complejas como fórmulas matemáticas.

- Investigar la incorporación de grafos de conocimiento (**GraphRAG**) para aumentar la precisión y contextualización.

---

<div class="flex flex-col justify-between h-[470px]">
  <div class="text-center flex flex-col justify-center gap-4">
    <span class=" font-bold opacity-60 text-md"> Universidad de las Ciencias Informáticas - 18/7/2025 </span>
  </div>

  <div class="text-5xl font-bold text-center">Desarrollo de una herramienta basada <br> en LLM y RAG para optimizar el análisis <br> de artículos científicos.
  </div>

  <div class="flex justify-between text-sm">
    <span class="font-700 opacity-60">
      <span class="opacity-50"> Autor </span> <br>
      Joaquin E. Rivas Sánchez
    </span>
    <span class="font-700 opacity-60">
      <span class="opacity-50"> Tutores </span> <br>
       Msc. Angel Alberto Vazquez Sánchez <br>
       Msc. Lisset Salazar Gómez
    </span>
  </div>
</div>


---

# PREGUNTAS DEL OPONENTE

a. ¿Qué prácticas de XP (ej: pair programming, TDD) adaptó u omitió en este contexto unipersonal, y cómo afectó esto la calidad o eficiencia del proceso?


---

# Respuesta

Las prácticas adoptadas que permitieron iterar rápidamente y mejorar el código de forma continua:

<v-clicks>

- ✅ Mantener un diseño simple

- ✅ Refactorización constante

Las prácticas que se omitieron fueron:

- ❌ Propiedad colectiva del código

- ❌ Programación en parejas

</v-clicks>

<!-- 
- Mantener el diseño del sistema lo más simple posible, implementando solo lo necesario para cumplir los requisitos actuales.

- Se realizo refactorizacion constante para mejorar continuamente el código sin cambiar su funcionalidad, para mantenerlo limpio y fácil de entender.

Se omitieron las prácticas como **LEER**, lo que hizo que la **detección de errores fuera más lenta**, ya que no contaba con una revisión inmediata de otro desarrollador. 
-->

---

# PREGUNTAS DEL OPONENTE

b. Para proyectos futuros de similar escala individual, ¿recomendaría XP u optaría por otra metodología ágil (ej: Scrum simplificado)? Justifique.

---
layout: image
image: ./assets/kanban.webp
---

# Respuesta

<!-- 
Para futuros proyectos individuales, recomendaria una metodologia hibrida que **combine las prácticas** utilizados de XP, junto con la metodologia Kanban 

la cual utiliza un tablero visual para **gestionar el flujo de trabajo** y **limitar el trabajo en curso**. 

Esto permite visualizar claramente el estado de cada tarea y detectar cuellos de botella, mejorando la eficiencia y la productividad.
 -->

---

# PREGUNTAS DEL OPONENTE

a. ¿Existe un diseño o prototipo para integrar esta retroalimentación en un ciclo de refinamiento automático (ej: fine-tuning con datos etiquetados) o manual (ej: priorización de correcciones)?

b. De no existir tal plan, ¿qué estrategia sugeriría para convertir estos reportes en acciones concretas que incrementen la precisión del sistema?

<!-- 
El plan consiste en recopilar los reportes de retroalimentación y utilizarlos en el futuro para aplicar técnicas de fine-tuning supervisado con datos etiquetados, alineando así el modelo a partir de ejemplos reales y mejorando su precisión en tareas específicas.
-->

---

# PREGUNTAS DEL OPONENTE

a. En futuras iteraciones del sistema, si el objetivo fuera su adopción por usuarios reales (investigadores, académicos), ¿qué métricas cualitativas y procesos de retroalimentación recomendaría incorporar para evaluar su usabilidad, adaptación al contexto local e impacto en flujos de trabajo?

---
layout: image 
image: ./assets/feedback.webp
---

# Respuesta

<!-- 
Para futuras iteraciones, recomendaría incorporar varias métricas subjetivas y mecanismos de retroalimentación directa para asegurar que el sistema cumpla con las expectativas del público objetivo:

- Sistema de feedback integrado: Similar al utilizado en plataformas como ChatGPT, donde los usuarios pueden calificar la utilidad o claridad de cada respuesta y dejar comentarios específicos.
-->

---
layout: image
image: ./assets/human-in-the-loop.webp
---

# Respuesta

<!--
- Sistema Human-in-the-Loop (HITL): Integrar un proceso donde usuarios expertos puedan revisar, corregir y validar las respuestas generadas por el sistema. 

Esto no solo mejora la calidad final, sino que también proporciona datos valiosos para ajustar el modelo y priorizar correcciones futuras


- Encuestas de aceptación y satisfacción: Aplicar cuestionarios periódicos para medir la satisfacción general, facilidad de uso, relevancia de las respuestas y posibles áreas de mejora.
-->

---

# PREGUNTAS DEL OPONENTE

a. Además de los desafíos técnicos documentados, ¿qué problema no previsto (ej.: incompatibilidad de bibliotecas, calidad de datos de prueba) surgió durante la codificación o pruebas, y cómo se resolvió?

---
layout: image 
image: ./assets/development.webp
---

# Respuesta

<!-- 
El principal desafío no previsto fue la lentitud en el ciclo de iteración durante el desarrollo, causada por la necesidad de reiniciar la aplicación tras cada cambio para recargar modelos pesados en memoria (entre 10-20 minutos por reinicio). Esto limitaba la capacidad de depuración rápida y testeos incrementales, especialmente al integrar componentes interdependientes.
-->

---
layout: image
image: ./assets/logs.webp
---

# Respuesta

<!--
La solución implementada incluyó la implementacion de un sistema de logging que registra:
  - Estados internos del sistema en cada etapa de procesamiento
  - Entradas/salidas de cada módulo con marcas temporales

Este enfoque se alinea con prácticas recomendadas en debugging de ML, donde la visibilidad del estado interno y la modularidad son críticas para sistemas complejos. Sin embargo, la solución requirió ajustar el balance entre precisión (modelos completos) y velocidad de desarrollo.
-->

---

# PREGUNTAS DEL OPONENTE

b. Tras la experiencia adquirida, ¿qué fase del plan original (ej.: diseño de arquitectura, pruebas RAGAS) demandó más/menos tiempo del estimado, y cómo ajustaría su distribución en futuras réplicas?


---
layout: image
image: ./assets/eval-tool.webp
---

# Respuesta

<!--
La fase que demandó más tiempo del estimado fue el diseño de las evaluaciones, ya que se requería una forma que permitiera crear pruebas en múltiples áreas del conocimiento para evaluar el sistema de manera general. 

Para abordar este desafío, se desarrolló una herramienta externa e independiente que, que utilizando artículos de Wikipedia, generó automáticamente conjuntos de datos de prueba. Esta solución automatizada facilitó la creación de evaluaciones diversas y representativas.

Para futuras réplicas, ajustaría la distribución del tiempo destinando más recursos y planificación temprana a la fase de diseño y generación de evaluaciones, considerando la complejidad de cubrir múltiples dominios. Además, integraría desde el inicio herramientas automatizadas similares para acelerar este proceso y evitar retrasos en etapas posteriores del proyecto.
-->

---

# Respuesta

| Área | Temas |
| --- | --- |
| Matemáticas | Números Primos, Álgebra lineal, Cálculo, Probabilidad |
| Ciencias de la Computación | Algoritmo, Estructura de datos, Inteligencia artificial, Programación de computadoras |
| Biología | Célula (biología), Genética, Evolución, Ecología |
| Física | Mecánica clásica, Electromagnetismo, Mecánica cuántica, Termodinámica |
| General | Batman, Perro salchicha, Teoría conspirativa, Religión |

<!-- 
- Incluye un total de 80 pares pregunta respuesta (4 pares por cada tema).

- Las preguntas fueron generadas de forma automática (usando un LLM), y están orientadas
a distintos dominios (ver Tabla 28).

- El dataset fue conformado de diferentes artículos de Wikipedia en versión inglés y español
 -->
