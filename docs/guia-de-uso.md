# Guía de uso — Sistema de organización de proyectos

Sistema estándar para organizar el contenido que generas en proyectos de Claude Cowork y Claude Code. Resuelve el problema de "voy generando documentos y es difícil mapear la información".

> **Nota:** esta guía y el `README.md` son documentación del *skill* para entender el método; no se copian a tus proyectos. Dentro de un proyecto, el sistema funciona con dos cosas: el `hub.md` y la regla de mantenimiento (en el `CLAUDE.md` del proyecto si usas Code, o en las instrucciones del proyecto si usas Cowork).

## Las dos piezas

El sistema son **tres archivos que trabajan juntos**:

1. **`hub.md`** — el mapa (el *presente*). Índice vivo de qué documento es la fuente de verdad de cada tema, qué deriva de qué, y en qué estado está todo. Lo lees tú para orientarte; lo lee el agente para no duplicar ni perderse.
2. **La regla de mantenimiento** — el motor. Un bloque de instrucciones en el `CLAUDE.md` (Code) o en las instrucciones del proyecto (Cowork) que ordena al agente mantener todo vivo en cada sesión, sin que se lo pidas.
3. **`_decisiones/decisiones.md`** — la bitácora (el *cómo llegamos aquí*). Registro cronológico append-only de las decisiones que cambiaron el rumbo, con fecha y porqué. Vive en la carpeta CORE `_decisiones/`. El hub dice qué hay ahora; la bitácora cuenta la secuencia que llevó hasta ahí.

Sin la pieza 2, el sistema se desactualiza apenas dejas de hacerlo a mano. Con ella, el mantenimiento es automático.

> **Buena práctica de longitud.** El `CLAUDE.md` rinde mejor por debajo de ~200 líneas (es contexto que el agente carga cada sesión); mantén ahí solo la regla de mantenimiento. El `hub.md` el agente lo lee bajo demanda, así que puede ser más largo — pero si pasa de ~150 líneas, suele ser señal de archivar derivados viejos en `_historico/` o dividir el proyecto.

## La idea central: el flujo de conocimiento

El sistema tiene una sola dirección de flujo:

**conversación → node temático (módulo) → fuente → derivado (CORE)**

1. Conversas con el agente y algo cristaliza (un segmento, una propuesta de valor, un hallazgo).
2. Eso se guarda como **node** en una carpeta MODULAR (`segmentos/`, `propuesta-valor/`). Tus módulos *son* tus fuentes de conocimiento, y nacen de las conversaciones.
3. Cuando pides un **derivado**, combinas nodes: *"con `segmentos.md` y `propuesta-de-valor.md` genera una presentación para stakeholders"*. El derivado se guarda en **`_entregables/`** (por tipo: `keynotes/`, `informes/`…) y cita sus fuentes.

Las carpetas:

- **CORE** (con prefijo `_`, nacen cuando llega su primer archivo): `_context/`, `_entregables/` (tus salidas, por tipo: `keynotes/`, `informes/`, `prototipos/`…), `_design-system/`, `_referencias/`, `_decisiones/`, `_historico/`. Aquí viven los **derivados** y el material de apoyo.
- **MODULARES** (crecen con tus conversaciones): una por tema, nombre descriptivo. Aquí viven los **nodes** (tus fuentes).

Cada node cierra con una sección `## Conexiones` en wikilinks (`[[...]]`) que dice de qué depende y qué alimenta. No es para un grafo bonito: es **navegación para el agente** — al abrir un archivo ve qué más leer — y la base del *lint*. Como ya usas Obsidian, el grafo aparece gratis; pero los `[[...]]` son texto plano, así que el sistema no queda atado a ningún plugin.

## Aplicarlo en un proyecto

Ya no traes una carpeta: **invocas el skill**. Una vez instalado (ver `README.md`), *Many Brains* detecta en qué estado está tu proyecto y actúa en consecuencia, sin pre-crear carpetas (cada una nace cuando llega su primer archivo):

- **Proyecto vacío → Sembrar.** Crea el `hub.md` y te pregunta qué cargar como contexto.
- **Proyecto con contenido, sin Many Brains → Adoptar.** Lee todo lo que existe, te explica el método, propone una estructura en árbol y reordena **solo con tu aprobación, sin borrar nada**.
- **Proyecto que ya usa Many Brains → Reconciliar.** Ajusta los desfases del `hub.md` y, si lo pides, corre el *lint*.

Al cerrar, el skill instala la **regla de mantenimiento** a nivel de proyecto para que el `hub.md` se mantenga vivo solo en cada sesión futura:

- **En Claude Code:** crea o actualiza el `CLAUDE.md` del proyecto (en Code el archivo es el mecanismo permanente, se queda).
- **En Claude Cowork:** te entrega el texto para pegarlo en las instrucciones del proyecto (panel → Instructions), porque la app no lo escribe por ti.

> **Diferencia clave:** en Code la regla vive en el archivo `CLAUDE.md`; en Cowork vive en el panel de la app. En ambos casos el skill **nunca borra nada sin tu consentimiento**.

## El flujo diario

1. **Empiezas una sesión** → el agente lee el hub y se orienta. (La primera vez en un proyecto, te pregunta qué cargar como contexto.)
2. **Conversas y algo cristaliza** → el agente te *propone* guardarlo como node en su módulo (operación *cristalizar*), con su sección `## Conexiones`. Tú decides; no se queda en el chat.
3. **Tomas una decisión de rumbo** → el agente la registra en `_decisiones/decisiones.md` con fecha y porqué.
4. **El agente actualiza el hub** → fecha, versión, estado de derivados. Sin que lo pidas.
5. **Pides un derivado** → "usa `[modulo]/[archivo].md` como fuente". El agente lee el node (y sus Conexiones), no inventa, y lo guarda en CORE.
6. **De vez en cuando pides un *lint*** → el agente revisa la salud del proyecto: nodes sin Conexiones, wikilinks rotos, derivados desactualizados, contradicciones.

## Las cinco consignas (lo que nunca cambia)

1. Una fuente de verdad por tema.
2. Versionado solo por cambio estructural (en la duda, no bumpear).
3. Hub como mapa (único lugar donde se ve todo de un vistazo).
4. Derivados citan su node.
5. Conexiones explícitas en wikilinks (navegación para el agente, base del lint).

## Relación con `CLAUDE.md` / `AGENTS.md`

No confundas dos capas:

- **`CLAUDE.md`** = contexto e instrucciones para el *agente* (cómo comportarse, qué reglas seguir). Aquí vive la regla de mantenimiento.
- **`hub.md`** = mapa del *contenido* para humanos y agente (qué documento es qué).

Son complementarios. Si en algún proyecto usas también `AGENTS.md` (estándar multi-herramienta), la regla de mantenimiento puede ir ahí en lugar de `CLAUDE.md` — el agente la lee igual.

---

*Inspirado en el MANIFEST.md de David Paluy y en el patrón LLM Wiki de Andrej Karpathy, adaptados a un flujo generativo. De Paluy: la idea de un archivo-mapa. De Karpathy: las tres capas (fuentes / contenido que el agente mantiene / schema en CLAUDE.md), la operación de archivar buenos hallazgos (aquí, "cristalizar"), el lint periódico, y los wikilinks como navegación. Lo que NO se tomó: su grafo es convergente (muchas fuentes externas → síntesis) y a gran escala (cientos de páginas, motor de búsqueda, log cronológico); este sistema es generativo (pocos nodes propios → muchos derivados) y a escala humana, donde el hub y la memoria del proyecto bastan sin log aparte.*
