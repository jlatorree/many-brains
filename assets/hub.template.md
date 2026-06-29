# 00 — Hub del proyecto [NOMBRE]

*Mapa maestro de los documentos del proyecto. Última actualización: YYYY-MM-DD.*

Este archivo es el **índice vivo** del proyecto: la vista **global** de qué está vigente y qué deriva de qué. La vista **local** de cada documento (de qué depende, qué alimenta) vive dentro del propio archivo, en su sección `## Conexiones`.

> Al clonar este template, reemplaza `[NOMBRE]` y empieza a llenar las tablas. Las carpetas se crean solas a medida que generas contenido (ver `CLAUDE.md`).

---

## Reglas de gestión (las cinco consignas)

**1. Una fuente de verdad por tema.** Cada tema tiene un solo node. No se duplica contenido entre nodes.

**2. Versionado solo por cambio estructural.** La versión sube solo ante cambios de fundamento (premisa, modelo, arquitectura, alcance). Cambios incrementales solo actualizan la fecha. En la duda, no bumpear.

**3. Hub como mapa.** Este archivo es el único lugar donde se ve qué nodes están vigentes, cuándo se actualizaron y qué deriva de cada uno.

**4. Derivados citan su node.** Cada derivado lleva *"Basado en `archivo.md` (versión del YYYY-MM-DD)"*.

**5. Conexiones explícitas en wikilinks.** Cada node cierra con una sección `## Conexiones` (`[[...]]`) que declara de qué depende, qué alimenta y con qué se relaciona.

---

## Estructura de carpetas

**CORE (transversales — piso mínimo, extensible):**

| Carpeta          | Contenido                                                            |
| ---------------- | ------------------------------------------------------------------- |
| `_context/`      | Contexto del proyecto (visión, propósito, conceptos clave) |
| `_entregables/`      | Tus salidas, por tipo: `keynotes/`, `informes/`, `prototipos/`…                                 |
| `_design-system/`| Tokens, componentes, guías visuales del proyecto                    |
| `_referencias/`  | Bibliografía y fuentes                                              |
| `_historico/`    | Versiones congeladas (nodes llevados a instancias externas)     |
| `_decisiones/`   | Bitácora cronológica de decisiones de rumbo (`decisiones.md`)        |

En la raíz, solo `hub.md` (este índice). La regla de mantenimiento la instala el skill Many Brains en el handoff: en Cowork se pega en las instrucciones del proyecto; en Code vive en el `CLAUDE.md` del proyecto.

**MODULARES (temáticas — nacen de las conversaciones):**

| Carpeta      | Contenido     |
| ------------ | ------------- |
| _(vacío — se llena al crear el primer tema)_ | |

---

## Nodes vigentes

| Documento | Tema | Última actualización | Versión |
| --------- | ---- | -------------------- | ------- |
| _(vacío)_ | | | |

---

## Derivados activos

| Derivado | Construido sobre | Última actualización | Estado |
| -------- | ---------------- | -------------------- | ------ |
| _(vacío)_ | | | |

> **Estado**: `al día` o `requiere refresh`.

---

## Documentos pendientes de crear

- _(vacío)_

---

## Cómo se mantiene este hub

El agente lo mantiene automáticamente en cada sesión gracias a la regla en `CLAUDE.md`: actualiza fechas/versiones al tocar nodes, marca derivados como `requiere refresh`, agrega filas nuevas, y actualiza la fecha de cabecera con cada cambio. Ver `docs/guia-de-uso.md` para el detalle.
