# Clasificación — cómo decidir qué es cada archivo (modo Adoptar)

Esta es tu guía para proponer un destino por archivo. Son **señales, no reglas
rígidas**: usa criterio y, en la duda, propón tu mejor hipótesis y márcala "(confianza baja)" en el plan (el usuario
corrige el plan antes de que se ejecute). El principio rector: **un archivo es
*node* si es una fuente de verdad sobre un tema; es *derivado* si se generó a
partir de otra cosa para presentarla o resumirla.**

## La pregunta clave: ¿fuente o representación?

Antes de mirar la extensión, pregúntate: *¿este archivo es donde vive el
conocimiento original, o es una versión hecha para mostrar/entregar algo que ya
existe en otro lado?*

- Donde vive el conocimiento → **node** (carpeta modular del tema).
- Una versión para mostrar/entregar → **derivado** (carpeta CORE).

La extensión ayuda pero no manda: un `.html` suele ser derivado, pero un `.md`
largo de notas crudas es node aunque esté desordenado.

## Tabla de señales

| Lo que ves en el archivo | Rol | Destino propuesto |
| --- | --- | --- |
| Visión, propósito, misión, conceptos clave, "filosofía", glosario del proyecto | Contexto | `_context/` |
| `.md` con sustancia sobre **un tema** (investigación, segmentos, propuesta, notas de trabajo, análisis) | Node | carpeta **modular** con nombre del tema |
| `.pptx` / `.html` / `.docx` / PDF generado por ti / resumen / one-pager / pitch | Derivado | `_entregables/` en subcarpeta por tipo (`keynotes/`, `informes/`, `prototipos/`…) |
| Tokens, paleta, tipografía, guías o componentes visuales | Design system | `_design-system/` |
| Bibliografía, papers de terceros, PDFs externos, enlaces fuente, capturas de referencia | Referencia | `_referencias/` |
| Bitácora/log de decisiones del proyecto | Decisiones | `_decisiones/decisiones.md` |
| Archivo de sistema o config (`.DS_Store`, `.gitignore`, `.obsidian/`, `node_modules/`) | Ruido | **no se toca, se ignora** |
| Genuinamente sin encaje tras agotar lo anterior | — | `_por-clasificar/` (último recurso) |

## Carpetas modulares: cómo agruparlas

Una carpeta modular agrupa **un tema**, con nombre descriptivo y sin prefijo
(`investigacion-usuarios/`, `segmentos/`, `modelo-negocio/`). Reglas prácticas:

- Si hay varios `.md` sobre el mismo tema, agrúpalos en una sola carpeta modular.
- Si un tema tiene un único archivo, igual puede tener su carpeta (o esperar: en
  la duda, propónla y deja que el usuario decida si fusionar).
- Si un `.md` mezcla dos temas, **no lo partas tú**: proponlo en el tema dominante
  y anota que quizá convenga separarlo más adelante (eso es decisión del usuario).

## Distinciones que suelen confundirse

- **Contexto vs. node temático.** `_context/` es para lo *transversal* a todo
  el proyecto (visión, propósito, conceptos). Un tema específico (un segmento, un
  hallazgo) es node modular, no contexto.
- **Referencia vs. node.** Una referencia es material *de terceros* que
  consultas (un informe de mercado ajeno). Un node es conocimiento *del
  proyecto*, aunque cite fuentes externas.
- **Derivado vs. node.** Si el archivo dice "basado en…", o claramente resume/
  presenta algo, es derivado. Si dudas, mira si su contenido existe ya en otro
  archivo más completo: si sí, este es el derivado.

## Reglas duras (no las rompas)

- **`_historico/` nunca se asigna automáticamente.** Solo se congela ahí una
  versión cuando el usuario lo ordena explícitamente, porque depende de un evento
  externo (se presentó a un comité, a dirección) que solo él conoce.
- **`_por-clasificar/` es el último recurso (la ambigüedad de categoría NO cuenta: para eso, ubícalo en tu mejor hipótesis y márcalo "confianza baja").** Agota todas las opciones antes de
  mandar algo ahí. Cada archivo que caiga ahí lleva una nota de por qué y **se le
  reporta al usuario**. La meta es que la carpeta quede vacía.
- **Ruido se ignora, no se borra.** No elimines `.DS_Store` ni nada: el sistema
  nunca borra.
- **Nada se mueve sin OK.** Todo esto es una *propuesta* hasta que el usuario
  aprueba el plan.
