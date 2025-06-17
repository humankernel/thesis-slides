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
Buenos días, en el dia de hoy se le dara presentacion al trabajo de diploma titulado:

**LEER TITULO**

El autor es quien les habla y los tutores.

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

¿Cómo desarrollar una herramienta de IA accesible, eficiente y localizable que permita a investigadores cubanos analizar documentos científicos de forma semi-automatizada, aprovechando los modelos de lenguaje de gran tamaño y generación aumentada por recuperación (RAG), sin depender de infraestructura costosa o conexión a internet?

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

---

# Tareas de investigación

+ Elaboración del marco teórico referente a modelos del lenguaje de gran tamaño y la extension utilizando generación aumentada por recuperación.
+ Análisis de sistemas homólogos para la identificación de los requisitos de software.
+ Implementación del sistema a partir de los requisitos de software.
+ Validación de la propuesta de solución.

<!-- 
Para dar cumplimiento al objetivo propuesto se proponen un conjunto de *tareas de investigación*:
-->

---

# ¿Qué es RAG y por qué es importante?

<!--
Primero es importante entender que es RAG:

Generacion Aumentada por Recuperacion (RAG) es una técnica que combina lo mejor de dos mundos:

1. La habilidad de buscar y recuperar información específica y actualizada de fuentes externas, como bases de datos, documentos o repositorios de datos.
2. La capacidad generativa de los LLM para sintetizar información.
-->

---

# Limitaciones de los LLM

| **Característica** | **LLM** | **LLM + RAG** |
|-----------|-----------|-----------|
| **Acceso a la información** | Conocimiento estático. | Acceso a información actualizada y en tiempo real. |
| **Verificación de respuestas**| Respuestas no verificables | Control y filtrado de la información con citas verificables  |
| **Manejo del contexto** | Pérdida o limitación del contexto. | Enfoque en fragmentos relevantes para cada consulta. |

<!--
Esto resuelve tres problemas clave de los LLMs tradicionales:

- Con los LLM el conocimiento esta limitado a los datos con los que fue entrenado \
- RAG permite integrar información nueva y en tiempo real.

- ... \
- con RAG se tiene un mayor control y filtrado sobre la información que se utiliza para generar la respuesta.

- los LLM a menudo tienen un pobre rendimiento cuando la entrada es demasiado grande. \
- RAG permite utilizar solo la informacion relevante para responder la pregunta. 

En el prototipo desarrollado, este enfoque permite al usuario: 

Integrar conocimiento nuevo proveniente de documentos externos al sistema.
-->


---
layout: two-cols
---

<template v-slot:default>

<SlidevVideo autoplay class="h-[500px]">
  <source src="./assets/video-send-pdf.mp4" type="video/mp4" />
</SlidevVideo>

</template>

<template v-slot:right>

<img src="./assets/step-indexing.webp" />

</template>

<!--
El prototipo realizado consiste del siguiente flujo:

El usuario puede iniciar una conversacion e introducir documentos en formato `.pdf`
El sistema los procesara:
    - dividiento el contenido en secciones de texto.
    - estas son transformados del lenguaje natural a una representacion numerica (forma de vectores) que mantiene el significado semantico de esta.
    - estos vectores son guardados en una base de datos.
-->

---
layout: two-cols
---

<template v-slot:default>

<SlidevVideo autoplay class="h-[450px] absolute top-15 left-2">
  <source src="./assets/video-query.mp4" type="video/mp4"  />
</SlidevVideo>

</template>

<template v-slot:right>

<img src="./assets/step-querying.webp" />

</template>
<!--
Posteriormente, al usuario introducir una consulta
El sistema:
    - convierte esta a la misma representacion numerica (utilizando un modelo especializado).
    - luego realiza una busqueda utilizando multiples metodos de recuperacion
        para obtener los documentos mas relevantes a la consulta.
    - los mismos son reordenados basados en la relevancia.
    - luego estos sirven de contexto para responder la consulta utilizando el LLM.
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

- Tareas de ingenieria (12).

- Pruebas Unitarias.

- Plan de Iteración (2).

- Estándares de Codificación

  - Patrón arquitectónico <span class="opacity-50"> (Arquitectura por Capas) </span>

  - Patrones de diseño.

<!-- 
El proyecto siguió la metodología ágil XP, la cual genero los siguientes artefactos ingenieriles.
 -->


---
layout: image
image: "./assets/performance.webp"
---

## Resultados y evaluación

<!--
- Las pruebas de rendimiento fueron satisfactorias, arrojando resultados alentadores.

  - Con tiempos que no superan los 3.5 seg en las pruebas realizadas a la generacion de respuestas.

  - 2 seg a la creacion de embeddings
-->

---
layout: image
image: ./assets/ragas.webp
---

## Resultados y evaluación

<!--
Las evaluaciones realizadas validaron que el prototipo cumple con los objetivos planteados:

- Proporciona respuestas precisas y contextualizadas, que situan al prototipo como una base robusta para ser extendida en el futuro.
- Y ofrecen datos valiosos que permiten enfocar futuras mejoras.

A continuacion se muestran los resultados de utilizar las metricas definidas por RAGAS para evaluar el sistema:

- Faithfulness: respuesta generada vs informacion recuperada.
    -> La respuesta generada no se adiere en la mayoria de los casos a la informacion recuperada.
    -> Lo cual puede deberse al modelo LLM utilizado.

- Context Recall: porciento de informacion relevante recuperada / toda la informacion recuperada.
    -> El prototipo en la mayoria de los casos probados recupera la informacion relevante.

- Factual Correctness: respuesta generada vs la de referencia.
    -> La respuesta representa la mayoria de los hechos en la respuesta de referencia.

Los resultados obtenidos fueron los esperados y marcan el camino para enfocar futuras mejoras.


Esto nos da a entender que si bien los documentos relevantes se encuentran en su mayoria, hay presencia de mucho ruido lo cual lleva a que el modelo ignore la mayoria de esta.
-->


---
layout: image
image: ./assets/unit-test-results.webp
---

## Pruebas de Unidad

<!--
Las pruebas de unidad se encargan de validar el comportamiento correcto de
componentes individuales de forma aislada.

Estos fueron los resultados en las 2 iteraciones del desarrollo.
-->

---
layout: image
image: ./assets/rag.webp
---

<!-- 
En pantalla se puede ver la aplicacion 
 -->

---

# Conclusiones

- Se logró una revisión integral de los LLM y su extensión mediante RAG, lo cual permitió sustentar conceptualmente el diseño de la herramienta propuesta.

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
layout: section
---

# Preguntas ...

<!-- 
Experiencia con metodología XP en un proyecto individual
Q: ¿Qué prácticas de XP resultaron más desafiantes o menos aplicables en un contexto unipersonal?
A: Programacion por duos

Q: La HU_8 permite calificar respuestas (ej.: "alucinación", "inapropiado"), pero no se detalla cómo estos datos se utilizarían para mejorar el sistema. ¿Planea implementar un ciclo de refinamiento basado en esta retroalimentación?
A: alineacion del modelo mediante fine-tuning

Q: ¿Consideró métricas de satisfacción de usuario más allá de las técnicas (RAGAS)?


Desafíos inesperados durante el desarrollo
Q: Más allá de las limitaciones técnicas previstas (baja conectividad, hardware), ¿qué obstáculo no anticipado surgió durante la implementación y cómo lo resolvió?
A: Debugabilidad y Logs 

Q: Si tuviera que repetir el proyecto, ¿qué fase acortaría o ampliaría en el plan de iteraciones?
A: ampliaria la fase de pruebas
-->

---
layout: image
image: ./assets/eval-tool.webp
---


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
