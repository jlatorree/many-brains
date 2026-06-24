# Mantenimiento del manifest (obligatorio)

Este proyecto usa un `manifest.md` en la raíz como índice vivo de todos los
documentos. Es tu mapa: léelo al inicio de cada sesión para orientarte sobre
qué archivo es la fuente de verdad de cada tema y qué deriva de qué.

**Arranque (primera vez en el proyecto).** Este archivo es andamiaje de
template: una vez que sus reglas están activas, sobra. Al iniciar un proyecto
recién clonado del template, ejecuta esta secuencia:

1. Lee e internaliza estas reglas.
2. **Limpieza del andamiaje, con consentimiento:**
   - **Primero, identifica el entorno.** Si no estás completamente seguro de si
     corres en Cowork o en Code, PREGÚNTALE al usuario antes de hacer nada
     ("¿Estás usando Cowork o Claude Code?"). No asumas.
   - Si estás en **Cowork**: confirma al usuario que ya cargaste las reglas y
     pídele que las pegue (o que confirme que las pegó) en las instrucciones del
     proyecto. Luego pide permiso explícito para borrar el andamiaje y la
     documentación explicativa: `CLAUDE.md`, `README.md` y `docs/guia-de-uso.md`.
     Solo bórralos si el usuario lo autoriza.
   - Si estás en **Code**: NO borres este `CLAUDE.md` — aquí es el mecanismo
     permanente que lees cada sesión. Sí puedes ofrecer borrar la documentación
     explicativa (`README.md` y `docs/guia-de-uso.md`), con consentimiento.
   - Nunca borres nada sin confirmación explícita del usuario.
3. Pregúntale: "¿Hay alguna fuente, documento o información que deba cargar como
   contexto canónico en `_context/` antes de empezar?". Con su respuesta, siembra
   el proyecto.

No crees carpetas vacías por adelantado: créalas solo cuando llegue el primer
archivo que va en ellas. Las decisiones de rumbo se registran en
`_decisiones/decisiones.md` (crea la carpeta y el archivo al registrar la
primera).

El flujo del proyecto es generativo: las conversaciones cristalizan en
canónicos temáticos (carpetas modulares), y esos canónicos son las fuentes con
las que generas derivados (presentaciones, informes) que viven en las carpetas
CORE. Mantén el sistema vivo SIN que el usuario te lo pida, aplicando estas
cinco consignas:

1. **Una fuente de verdad por tema.** Cada tema tiene un solo archivo canónico.
   No dupliques contenido entre canónicos. Si necesitas una representación
   (presentación, resumen, informe), créala como derivado, no como copia.

2. **Versionado solo por cambio estructural.** Sube versión (v0.2 → v0.3) solo
   ante un cambio de fundamento (premisa, modelo, arquitectura, alcance). Cambios
   incrementales (agregar sección, refinar, reordenar) NO suben versión: solo
   actualizan la fecha de cabecera. En la duda, no bumpees.

3. **Manifiesto como mapa.** Cuando crees, muevas, renombres o modifiques un
   canónico o un derivado, actualiza de inmediato la fila correspondiente en
   `manifest.md` (ruta, fecha, versión, estado) y la fecha de su cabecera.

4. **Derivados citan su canónico.** Todo derivado que generes (HTML, .docx,
   .pptx, resumen) debe llevar en cabecera o pie: "Basado en `archivo.md`
   (versión del YYYY-MM-DD)". Al generar un derivado, lee primero su(s)
   canónico(s) como fuente — nunca inventes contenido que debería venir del
   canónico.

5. **Conexiones explícitas en wikilinks.** Cada canónico cierra con una sección
   `## Conexiones` que declara con enlaces `[[...]]` de qué depende, qué alimenta
   y con qué se relaciona. Mantenla actualizada al crear o modificar canónicos.
   Es tu mapa de navegación: al abrir un archivo, lee sus Conexiones para saber
   qué otros canónicos leer antes de responder o generar un derivado.

## Operaciones que debes ejecutar

- **Cristalizar.** Cuando una conversación produzca conocimiento que vale la
  pena retener (un hallazgo, una decisión, un análisis), PROPÓN proactivamente
  guardarlo — no esperes solo a que el usuario lo pida. La decisión final de
  guardar es suya. Si acepta, guárdalo como canónico temático en su carpeta
  modular (créala si no existe), nunca dejes morir lo valioso en el chat. No
  guardes la conversación entera, solo lo que vale. Al crearlo, agrégalo al
  manifest y dale su sección `## Conexiones`.

- **Registrar decisión.** Cuando se tome una decisión que cambia el rumbo del
  proyecto (un pivote, un cambio de premisa, descartar un enfoque), añade una
  entrada al final de `_decisiones/decisiones.md` (crea la carpeta CORE
  `_decisiones/` y el archivo si no existen) con el formato `## [YYYY-MM-DD]
  Título` y
  un párrafo breve con el QUÉ y el PORQUÉ. Es append-only: no edites entradas
  pasadas. Registra solo decisiones de rumbo, no operaciones mecánicas (crear un
  derivado o actualizar una fecha NO van aquí).

- **Derivar.** Cuando el usuario pida un derivado a partir de canónicos
  ("con X.md y Y.md genera una presentación"), lee primero esos canónicos como
  fuente, genera el derivado en la carpeta CORE que corresponda, ponle la cita
  "Basado en..." y registra la fila en la tabla de derivados del manifest.

- **Lint (cuando el usuario lo pida).** Haz un health-check del proyecto y
  reporta: canónicos sin sección `## Conexiones`; wikilinks `[[...]]` que apuntan
  a archivos que no existen; derivados marcados `requiere refresh` desde hace
  tiempo; contradicciones entre canónicos; conceptos mencionados varias veces
  que merecerían su propio canónico. Propón correcciones, no las apliques sin
  confirmar.

## Reglas operativas adicionales

- Al modificar un canónico, marca como `requiere refresh` en el manifest todo
  derivado que dependa de él.
- No pre-crees carpetas vacías. Crea cada carpeta (CORE o modular) solo cuando
  llegue el primer archivo que va en ella.
- Carpetas CORE base (piso mínimo, no renombrar): `_context/`, `_keynote/`,
  `_design-system/`, `_referencias/`, `_historico/`, `_decisiones/`. Las CORE
  son transversales (sirven a todo el proyecto, no a un tema).
- Las CORE son extensibles: si aparece una necesidad transversal que no encaja
  en las existentes (ej. `_assets/`, `_templates/`), propón crear una nueva CORE
  con prefijo `_` y regístrala en la tabla de estructura del manifest.
- Carpetas MODULARES: créalas por tema y con nombre descriptivo (sin prefijo `_`)
  cuando aparezca contenido temático nuevo. Regla de decisión: si la carpeta
  agrupa un TEMA → es modular; si es transversal a todo el proyecto → es CORE.
  Agrégalas a la tabla de estructura del manifest.
- Solo se entra a `_historico/` para congelar la versión exacta de un canónico
  que se llevó a una instancia externa (comité, dirección). Nombre:
  `nombre_YYYY-MM-DD_audiencia.md`. No es para borradores.
- Si detectas que el manifest quedó desactualizado respecto al estado real de
  las carpetas, corrígelo y avisa al usuario qué reconciliaste.
