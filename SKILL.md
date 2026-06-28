---
name: many-brains
description: >-
  Organiza y mantiene un proyecto bajo el sistema Many Brains: un manifest vivo,
  carpetas CORE/modulares, fuentes canónicas y derivados que citan su fuente.
  Detecta el estado del proyecto y actúa en consecuencia: siembra uno vacío,
  ADOPTA uno que ya tiene contenido (lo lee todo, propone una estructura en árbol
  y reordena solo con la aprobación del usuario, sin borrar nada), o reconcilia
  uno que ya usa Many Brains. Úsalo siempre que el usuario quiera ordenar,
  estructurar, migrar, limpiar o "aplicar Many Brains" a un proyecto —nuevo o ya
  avanzado— incluso si no nombra el sistema explícitamente pero pide poner orden
  en sus archivos, notas, carpetas o documentos.
---
# Many Brains

Este skill instala y mantiene el método **Many Brains** en un proyecto: en vez de
acumular archivos sueltos, se cultiva un "cerebro" por proyecto con fuentes
canónicas, derivados que citan su fuente, y un `manifest.md` que actúa como mapa.
Tu rol al usarlo es el de **bibliotecario, no autor**: ordenas y propones, pero la
curaduría y las decisiones son del usuario. **Nunca borras nada.**

## Qué hace este skill por dentro (orientación)

El sistema se apoya en tres ideas que debes conocer antes de tocar nada:

- **Canónicos**: archivos `.md` que son la *única fuente de verdad* de un tema.
  Viven en carpetas **modulares** (nombre del tema, sin prefijo).
- **Derivados**: presentaciones, informes, resúmenes generados *a partir de*
  canónicos. Viven en carpetas **CORE** (con prefijo `_`) y citan su fuente.
- **Manifest**: `manifest.md` en la raíz, el índice vivo de qué hay y qué deriva
  de qué.

Archivos que trae este skill (léelos cuando los necesites, no todos de golpe):

- `references/tutorial.md` — el resumen del sistema que le explicas al usuario
  **Léelo siempre antes de proponer u ordenar.**
- `references/clasificacion.md` — las señales para decidir qué es cada archivo.
  Léelo al entrar en modo Adoptar.
- `assets/manifest.template.md` — el esqueleto del `manifest.md` a crear.
- `assets/instrucciones-para-claude.md` — las reglas permanentes que el proyecto necesita para
  mantenerse vivo. Es lo que instalas en el handoff.

## Primero — Detecta el modo (no asumas)

Mira la raíz del proyecto e identifica en cuál de los tres estados estás:

| Estado | Modo | Ir a |
| --- | --- | --- |
| Hay un `manifest.md` estructurado en la raíz | **Reconciliar** | sección "Modo Reconciliar" |
| Casi sin contenido (solo config/ruido) | **Sembrar** | sección "Modo Sembrar" |
| Hay contenido real, pero no Many Brains | **Adoptar** | sección "Modo Adoptar" |

Ignora siempre el "ruido" (no cuenta como contenido y nunca lo tocas):
`.git/`, `.DS_Store`, `node_modules/`, `.obsidian/`, archivos de config del editor.

Detecta también el **entorno**, porque el handoff final cambia: ¿Cowork o Claude
Code? Si no estás completamente seguro, **pregúntaselo al usuario** antes del
handoff. No asumas.

## Antes de proponer u ordenar — Explica el sistema (siempre)

Antes de proponer una estructura o sembrar, lee `references/tutorial.md` y dale al
usuario un **resumen breve** (4-6 frases) de cómo funciona Many Brains y con qué
lógica vas a ordenar su proyecto. Esto importa porque el usuario debe entender el
criterio *antes* de ver su contenido reorganizado; si no, el orden le parecerá
arbitrario. No te saltes este paso aunque el usuario tenga prisa.

## Modo Adoptar (el corazón)

Garantía central: **no borras nada y no mueves nada hasta que el usuario apruebe.**

1. **Inventaria.** Lista todos los archivos (recursivo), ignorando el ruido.
2. **Lee / hojea.** Abre cada archivo lo suficiente para entender su rol. No lo
   modifiques.
3. **Clasifica (propuesta).** Para cada archivo decide un rol y un destino usando
   las señales de `references/clasificacion.md` (léelo ahora). Esfuérzate por
   ubicar todo dentro de la estructura; clasificar mal es preferible a rendirse,
   porque el usuario corrige el plan antes de que se ejecute.
   - **`_historico/` nunca se asigna automáticamente.** Solo va ahí lo que el
     usuario ordene congelar explícitamente. Al adoptar, no puedes saber qué
     versión se llevó a una instancia externa: eso es un evento del mundo real que
     solo el usuario conoce.
4. **Presenta el PLAN como árbol.** Muestra la estructura propuesta en el esquema
   clásico de carpetas y subcarpetas (árbol), porque así se entiende de un
   vistazo. Debajo, una tabla `origen → destino → por qué` para el detalle. **Aún
   no has movido nada.** El plan va **solo en el chat**; ofrece guardarlo como
   `plan-de-orden.md` y hazlo solo si el usuario lo confirma. Pide aprobación (por
   lote o archivo por archivo).
5. **Lo que no encaja (último recurso).** Solo si un documento *de verdad* no tiene
   encaje en ninguna carpeta, ponlo en `_por-clasificar/`, con una nota de por qué,
   y **comunícaselo al usuario** para decidir juntos. La meta es que esa carpeta
   quede vacía: no es un buzón de descarte, es la excepción.
6. **Ejecuta (solo con OK).** Mueve los archivos a su destino (mover, no copiar,
   para no dejar duplicados). Crea las carpetas a medida que las necesitas (no
   pre-crees vacías). Crea `manifest.md` a partir de `assets/manifest.template.md`
   y llena sus tablas con lo recién ordenado.
7. **Handoff.** Ve a la sección "Handoff del mantenimiento".

> Mover vs. copiar: como el usuario ve el plan completo antes de que toques nada,
> el riesgo de mover (romper enlaces externos, p. ej. un vault de Obsidian) queda
> controlado. Si en algún proyecto el usuario prefiere copiar, trátalo como
> excepción y díselo.

> **La adopción solo reubica, no modifica contenido.** Al mover un archivo a su
> carpeta no cambias lo que hay dentro. Los canónicos llevan `## Conexiones` y los
> derivados una cita "Basado en…", pero **no se las agregues durante la
> adopción**: mover no es momento de editar. Propón añadirlas como un paso aparte y
> opcional, *después* de ordenar, archivo por archivo y con el OK del usuario.

## Modo Sembrar

Para un proyecto vacío o casi vacío:

1. **Explica el sistema** (tutorial breve, como en la sección anterior).
2. Pregunta: "¿Hay alguna fuente, documento o información que deba cargar como
   contexto canónico en `_context/` antes de empezar?".
3. Crea `manifest.md` desde `assets/manifest.template.md` (reemplaza `[NOMBRE]`).
4. No pre-crees carpetas: nacen cuando llega su primer archivo.
5. **Handoff** del mantenimiento.

## Modo Reconciliar

El proyecto ya usa Many Brains (hay `manifest.md`). No re-siembres.

- Compara el `manifest.md` con la realidad de las carpetas y corrige desfases
  (filas que faltan, rutas movidas, fechas). Avisa qué reconciliaste.
- Corre el **lint** si el usuario lo pide: canónicos sin sección `## Conexiones`,
  wikilinks `[[...]]` rotos, derivados marcados `requiere refresh` hace tiempo,
  contradicciones entre canónicos, conceptos repetidos que merecerían su propio
  canónico. **Propón** correcciones; no las apliques sin confirmar.

## Handoff del mantenimiento (cierre de Sembrar y Adoptar)

El objetivo es dejar el proyecto **autosostenido**: que el `manifest.md` se
mantenga vivo en cada sesión futura sin que el usuario lo pida. El mecanismo es la
regla permanente de `assets/instrucciones-para-claude.md`, y **va siempre a nivel de proyecto**
(no a las instrucciones globales — esa regla habla de `manifest.md` y carpetas que
otros proyectos no tienen).

- **En Cowork:** no puedes escribir el panel de instrucciones (es UI de la app).
  Entrégale al usuario el contenido de `assets/instrucciones-para-claude.md` y dile:
  "pega esto en Settings del proyecto → Instructions". Confirma que lo hizo.
- **En Claude Code:** crea o actualiza el `CLAUDE.md` del proyecto con el contenido
  de `assets/instrucciones-para-claude.md`.

Si no sabes en qué entorno estás, pregúntalo antes de hacer el handoff.

## Reglas invariables (lo que el skill promete)

- **Nunca borres.** Ni siquiera el ruido: lo ignoras, no lo eliminas.
- **Propón, decide el humano.** Nada se mueve sin OK. Eres bibliotecario, no autor.
- **Explica antes de actuar** (siempre, antes de proponer u ordenar).
- **Adoptar reubica, no modifica contenido.** Añadir Conexiones o citas a archivos
  existentes es un paso aparte, propuesto y opcional.
- **`_por-clasificar/` es último recurso, no buzón.** Reporta lo que cae ahí.
- **`_historico/` solo por orden explícita del usuario.**
- **Idempotente.** Si te corren de nuevo, detectas el `manifest.md` y reconcilias;
  no re-siembras ni duplicas.
