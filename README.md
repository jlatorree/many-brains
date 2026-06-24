# system-md

Sistema estándar para organizar el contenido que generas en proyectos de Claude Cowork y Claude Code. Resuelve el problema de "voy generando documentos y se vuelve difícil mapear la información".

Este repo es una **plantilla**: lo clonas (o usas "Use this template" en GitHub) para arrancar cada proyecto nuevo con la estructura ya lista.

> **Nota:** este `README.md` y `docs/guia-de-uso.md` son documentación explicativa, no piezas operativas. El sistema funciona solo con `CLAUDE.md` y `manifest.md`. Una vez que configures un proyecto nuevo, puedes **borrar ambos sin problema**.

## Qué incluye

| Archivo | Rol |
| ------- | --- |
| `CLAUDE.md` | El motor. La regla que el agente lee para mantener el sistema vivo. **Andamiaje**: en Cowork se vuelca a las instrucciones del proyecto y se borra (con tu permiso); en Code se conserva. |
| `manifest.md` | El mapa. Índice del proyecto (esqueleto vacío, listo para llenar). Queda en la raíz. |
| `README.md` | Esta portada. **Andamiaje**: se borra al sembrar el proyecto (con tu permiso). |
| `docs/guia-de-uso.md` | La guía completa: cómo funciona el sistema y cómo aplicarlo. |
| `_decisiones/decisiones.md` | Bitácora cronológica de decisiones de rumbo. Carpeta CORE. |

## Cómo usarlo

### En Claude Code

1. Clona el template (o "Use this template" en GitHub) en la carpeta de tu proyecto nuevo.
2. Abre el proyecto en Claude Code. El `CLAUDE.md` se lee automáticamente.
3. Al empezar, el agente te preguntará qué cargar como contexto canónico. De ahí en adelante crea carpetas y mantiene el `manifest.md` solo.

### En Claude Cowork

1. Copia esta carpeta como base de tu proyecto nuevo en Cowork.
2. Abre `CLAUDE.md`, copia todo su contenido y pégalo en las **instrucciones del proyecto** (panel derecho → Instructions). En Cowork las instrucciones se editan desde la app; por debajo se guardan en un `claude.md` del proyecto.
3. Listo. Misma rutina de arranque y mantenimiento automático.

## La idea en una línea

Las conversaciones cristalizan en **canónicos** (tus fuentes, en carpetas temáticas) → los combinas para generar **derivados** (presentaciones, informes, en carpetas CORE) → el agente mantiene el `manifest.md` y las conexiones al día, sin que se lo pidas.

Inspirado en el MANIFEST.md de David Paluy y el patrón LLM Wiki de Andrej Karpathy, adaptado a un flujo generativo. Ver `docs/guia-de-uso.md`.
