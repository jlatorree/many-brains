# Many Brains

Skill para organizar y mantener un proyecto bajo el método **Many Brains**: en vez
de acumular archivos sueltos, cultivas un "cerebro" por proyecto con fuentes
canónicas, derivados que citan su fuente, y un `manifest.md` que actúa como mapa.
Resuelve el problema de "voy generando documentos y se vuelve difícil mapear la
información".

A diferencia de un template (que solo sirve para arrancar un proyecto vacío), este
skill también **adopta un proyecto que ya viene avanzando**: lee lo que existe,
propone una estructura y la ordena —sin borrar nada y solo con tu aprobación.

## Los tres modos

El skill detecta el estado del proyecto y actúa según corresponda:

| Estado | Modo | Qué hace |
| --- | --- | --- |
| Proyecto vacío | **Sembrar** | Crea el `manifest.md` y deja todo listo. |
| Proyecto con contenido, sin Many Brains | **Adoptar** | Lee todo, propone una estructura en árbol y reordena solo con tu OK. |
| Proyecto que ya usa Many Brains | **Reconciliar** | Ajusta desfases del manifest y corre el *lint*. |

## Qué incluye

| Archivo | Rol |
| ------- | --- |
| `SKILL.md` | El skill. Detección de modo, flujo plan-first y handoff. |
| `references/tutorial.md` | El resumen del sistema que el agente le explica al usuario antes de ordenar. |
| `references/clasificacion.md` | Las señales para decidir qué es cada archivo. |
| `assets/manifest.template.md` | Esqueleto del `manifest.md` que se siembra en el proyecto. |
| `assets/instrucciones-para-claude.md` | La regla permanente que mantiene el sistema vivo (se instala en el handoff). |
| `docs/guia-de-uso.md` | La guía conceptual completa del método. |

## Cómo se instala el mantenimiento (handoff)

Al terminar de ordenar, el skill deja el proyecto autosostenido instalando la regla
de `assets/instrucciones-para-claude.md` **a nivel de proyecto** (no global):

- **En Claude Code:** crea o actualiza el `CLAUDE.md` del proyecto.
- **En Claude Cowork:** te entrega el texto para que lo pegues en Settings del
  proyecto → Instructions (la app no permite escribirlo automáticamente).

## La idea en una línea

Las conversaciones cristalizan en **canónicos** (tus fuentes, en carpetas
temáticas) → los combinas para generar **derivados** (presentaciones, informes, en
carpetas CORE) → el agente mantiene el `manifest.md` y las conexiones al día, sin
que se lo pidas.

Inspirado en el MANIFEST.md de David Paluy y el patrón LLM Wiki de Andrej Karpathy,
adaptado a un flujo generativo. Ver `docs/guia-de-uso.md`.
