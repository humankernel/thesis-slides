<!-- # Homologos

<span class="absolute top-10 right-15"> Elicit </span>

<SlidevVideo autoplay controls class="rounded-xl">
  <source src="./assets/elicit.mp4" type="video/mp4" />
  <p>
    Your browser does not support videos. You may download it
    <a href="./assets/elicit.mp4">here</a>.
  </p>
</SlidevVideo> -->

<!--
1. **Elicit** es una herramienta de inteligencia artificial diseñada para ayudar en la investigación académica, está enfocado en la revisión y síntesis de literatura científica.

El usuario introduce la pregunta y el sistema realiza un proceso complejo de:
    - recoleccion de articulos relevantes.
    - extrae la informacion relevante de cada uno.
    - genera un articulo en forma de Survey resumiendo y citando lo encontrado.
-->
---
layout: image-right
image: ./assets/generator.svg
---

## Patrón Generador

<br>

```python {all|4-25}
def create_query_plan(
    query: str, plan: QueryPlan
) -> Generator[ChatMessageAndChunk, None, None]:
    yield (
        ChatMessage(
            role="assistant",
            content=f"Creating Query Plan for {query}",
            metadata={
                "title": "✍ Creating Query Plan",
                "status": "pending",
            },
        ),
        [],
    )
    # USEFUL STUFF ...
    yield (
        ChatMessage(
            role="assistant",
            content=str(plan),
            metadata={ # ... metadata ...},
        ),
        [],
    )
```

<!--
Se utilizo el patron de diseño generador: 

El cual permite pausar y reanudar la ejecucion del codigo e informar al usuario a travez de mensajes las acciones que se estan realizando.
-->

---
layout: image-right
image: ./assets/state-machine.svg
---

## Patrón State Machine

<br>

```python {all}
state = GenerationState()
while not state.complete and iterations < max_iterations:
    # planificación, recuperación, generación ...

    yield from validate_answer(plan, state)

    # Si el estado aún no es completo, se refina el plan para la siguiente iteración
    if not state.complete:
        yield from refine_query_plan(plan, state)

    iterations += 1

yield state.answer, chunks
```

<!--
Tambien el patron maquina de estado:

Un patron comunmente utilizado en la programacion procedural para orquestrar las transiciones de estado entre distintas funciones.
-->

---
layout: intro-image
image: ./assets/eval-tool.png
---

<h1 class="text-dark-500 text-center absolute top-2 left-2 right-2 text-shadow-xl"> Evaluación </h1>

<!--
Para la Evaluacion se creo una Herramienta para generar conjuntos de prueba de forma automatizada usando LLMs.
-->
