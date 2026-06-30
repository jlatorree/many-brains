# Many Brains

Skill para organizar y mantener un proyecto bajo el método **Many Brains**: en vez
de acumular archivos sueltos, cultivas un "cerebro" por proyecto con nodes,
outputs que citan su fuente, y un `_hub.md` que lo conecta todo.
Resuelve el problema de "voy generando documentos y se vuelve difícil mapear la
información".

A diferencia de un template (que solo sirve para arrancar un proyecto vacío), este
skill también **adopta un proyecto que ya viene avanzando**: lee lo que existe,
propone una estructura y la ordena —sin borrar nada y solo con tu aprobación.

## Instalación

> **Nota:** este repo es un **plugin de Claude Code** y está pensado para usarse en
> Code. Claude Cowork no admite plugins: los usuarios de Cowork usan la **edición
> derivada de un solo archivo** (ver abajo), pegándola en las Instructions del proyecto.

**Claude Code — como plugin** (recomendado: se auto-actualiza):

```sh
/plugin marketplace add jlatorree/many-brains
/plugin install many-brains@jlatorree
```

**Claude Code — como skill personal** (clonando el repo, sin marketplace):

```sh
git clone https://github.com/jlatorree/many-brains.git ~/.claude/skills/many-brains
```

**Claude Cowork:** no se instala desde GitHub (Cowork no admite plugins). Usa la
edición derivada de un solo archivo
[`cowork/many-brains-cowork.md`](cowork/many-brains-cowork.md) y pégala en Settings
del proyecto → Instructions (ver "Cómo se instala el mantenimiento" más abajo).

## Los tres modos

El skill detecta el estado del proyecto y actúa según corresponda:

| Estado | Modo | Qué hace |
| --- | --- | --- |
| Proyecto vacío | **Sembrar** | Crea el `_hub.md` y deja todo listo. |
| Proyecto con contenido, sin Many Brains | **Adoptar** | Lee todo, propone una estructura en árbol y reordena solo con tu OK. |
| Proyecto que ya usa Many Brains | **Reconciliar** | Ajusta desfases del hub y corre el *lint*. |

## Qué incluye

| Archivo | Rol |
| ------- | --- |
| `SKILL.md` | El skill. Detección de modo, flujo plan-first y handoff. |
| `references/tutorial.md` | El resumen del sistema que el agente le explica al usuario antes de ordenar. |
| `references/clasificacion.md` | Las señales para decidir qué es cada archivo. |
| `assets/hub.template.md` | Esqueleto del `_hub.md` que se siembra en el proyecto. |
| `assets/instrucciones-para-claude.md` | La regla permanente que mantiene el sistema vivo (se instala en el handoff). |
| `docs/guia-de-uso.md` | La guía conceptual completa del método. |

## Cómo se instala el mantenimiento (handoff)

Al terminar de ordenar, el skill deja el proyecto autosostenido instalando la regla
de `assets/instrucciones-para-claude.md` **a nivel de proyecto** (no global):

- **En Claude Code:** crea o actualiza el `CLAUDE.md` del proyecto.
- **En Claude Cowork:** te entrega el texto para que lo pegues en Settings del
  proyecto → Instructions (la app no permite escribirlo automáticamente).

## La idea en una línea

Las conversaciones cristalizan en **nodes** (tus fuentes, planos en `_nodes/`) →
los combinas para generar **outputs** (presentaciones, informes, en `_outputs/`)
que citan su fuente → el agente mantiene el `_hub.md` y las conexiones al día, sin
que se lo pidas.

Inspirado en el MANIFEST.md de David Paluy y el patrón LLM Wiki de Andrej Karpathy,
adaptado a un flujo generativo. Ver `docs/guia-de-uso.md`.
