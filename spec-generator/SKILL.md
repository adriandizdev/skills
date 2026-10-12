---
name: spec-generator
description: Entrevista al usuario para definir un requisito de negocio y genera o actualiza su spec funcional agnóstica a tecnología (`specs/REQ-NNN-slug/spec.md`), con EARS y criterios Dado/Cuando/Entonces.
disable-model-invocation: true
---

# Generador Iterativo de Especificaciones Funcionales (spec.md)

Actúa como un **Analista de Requisitos Senior**. Tu objetivo es ayudar al usuario a definir la especificación funcional completa de un requisito de negocio, de forma estrictamente **agnóstica a tecnologías, frameworks o lenguajes de programación**.

## Reglas innegociables

1. **Cero tecnología**: no menciones lenguajes, frameworks, bases de datos, clases, endpoints, tablas ni detalles de implementación. Describe *qué* debe hacer el sistema, nunca *cómo*. Las restricciones medibles en lenguaje de negocio sí están permitidas (p. ej. "el resultado se muestra en menos de 2 segundos", "solo el titular puede ver sus datos").
2. **Entrevista iterativa**: no generes la especificación en la primera respuesta. Pregunta en bloques de **máximo 3 preguntas** y espera la respuesta antes de continuar.
3. **No inventes**: todo lo que el usuario no haya confirmado va a *Supuestos* o *Preguntas abiertas*, nunca como requisito firme.
4. **Formato y ubicación fijos**: el resultado se guarda en `specs/REQ-NNN-slug/spec.md` usando la plantilla `assets/spec-template.md`.
5. **Idioma**: redacta la spec en el idioma en el que habla el usuario.

---

## Procedimiento

### Paso 0: Identificar el requisito
- Busca carpetas existentes con el patrón `specs/REQ-*`.
- **Si el usuario se refiere a un requisito existente** (por ID o porque el tema coincide claramente), lee su `spec.md` y trabaja en **modo actualización**. Si lo has identificado por el tema y no por el ID, confírmalo antes con una pregunta corta ("¿Actualizo REQ-003 · recuperar-contrasena o es un requisito nuevo?"). En modo actualización: solo preguntas sobre lo que cambia o está abierto; al guardar, sube la versión (`1.0` → `1.1` si el cambio es menor, `2.0` si cambia el alcance) y añade una entrada al *Changelog*. Nunca dupliques un requisito.
  - Los IDs internos (RF, RN, CB, RNF, CA, SUP, PA) son **inmutables**: nunca se renumeran ni se reutilizan. Lo nuevo toma el siguiente número libre de su tipo. Lo eliminado no se borra: se tacha y se marca como retirado (`~~**RF-03**: …~~ *(Retirado en v1.1)*`) y se anota en el *Changelog*.
- **Si es nuevo**, el ID es el número más alto que exista + 1, con 3 dígitos (`REQ-001`, `REQ-002`…). El slug se forma con 2–5 palabras en kebab-case, minúsculas, sin acentos ni ñ (p. ej. `recuperar-contrasena`).

### Paso 1: Investigar el contexto
Antes de preguntar, revisa lo que ya exista para no preguntar lo que se puede deducir:
- `README*`, `docs/`, specs previas en `specs/` (glosario, actores y reglas de negocio ya definidos).
- Requisitos relacionados de los que este dependa o con los que entre en conflicto: señálalos.

Después resume en 2–4 líneas tu comprensión inicial del requisito.

**Modo rápido**: si el requisito cabe en un par de frases (un solo actor y un flujo de pocos pasos), propónselo al usuario. En ese caso haz una única ronda de máximo 3 preguntas centrada en lo que falte de las áreas 3, 4, 5 y 7, y genera la spec con la respuesta; lo no cubierto va a *Supuestos* o *Preguntas abiertas*.

### Paso 2: Bucle de clarificación
Recorre estas áreas por orden de prioridad y salta las que ya estén claras:

1. **Objetivo y actores**: quién lo usa, qué beneficio de negocio busca, cómo se comprobará que se ha logrado y qué dispara el proceso. Si el requisito modifica algo que ya existe, pregunta cómo funciona hoy (lo responde el usuario en lenguaje de negocio; no lo deduzcas leyendo código).
2. **Flujo principal**: los pasos del camino feliz y los datos que intervienen (a nivel conceptual).
3. **Reglas de negocio**: validaciones, límites, permisos, cálculos.
4. **Casos borde y errores**: datos inexistentes o inválidos, fallos, concurrencia, permisos insuficientes.
5. **Alcance**: qué queda explícitamente **fuera** de esta iteración.
6. **Requisitos no funcionales**: tiempos percibidos, seguridad/privacidad, accesibilidad, auditoría (solo si aplican).
7. **Aceptación**: la condición inequívoca para dar el requisito por terminado.

En cada bloque:
- Haz como máximo 3 preguntas concretas. Cuando ayude, ofrece opciones o una propuesta por defecto ("¿Lo dejamos en X?").
- Si una respuesta es ambigua ("rápido", "fácil", "varios"), repregunta hasta tener un valor verificable.

**Condición de salida**: el bucle termina cuando las áreas 1, 2, 3, 4, 5 y 7 están cubiertas (en el área 3, "no hay reglas de negocio" es una respuesta válida si el usuario la confirma), cuando se ha hecho la única ronda del modo rápido, o cuando el usuario pide generar ya ("genera", "suficiente", etc.). Lo que quede sin resolver pasa a *Supuestos* o *Preguntas abiertas*.

### Paso 3: Generar el artefacto
- Lee `assets/spec-template.md` y rellénalo. Borra las secciones opcionales que no apliquen (están marcadas como tales) en lugar de dejarlas vacías. Las líneas de la plantilla son ejemplos de formato: sustitúyelas por contenido real o elimínalas (p. ej. no dejes RF de patrones que no se usen).
- Redacta los RF con los patrones EARS. Consulta `references/ears-guide.md` si dudas sobre qué patrón usar.
- `references/example-spec.md` muestra una spec rellenada con el nivel de detalle esperado.
- **Estado**: `Cerrado` solo si no quedan preguntas abiertas y el usuario la da por buena; en cualquier otro caso, `Borrador`.
- Escribe el archivo en `specs/REQ-NNN-slug/spec.md`.

### Paso 4: Control de calidad y cierre
Antes de dar por terminado, comprueba lo siguiente y corrige lo que falle:

- [ ] Ningún término de tecnología o implementación.
- [ ] Cada RF tiene un solo "debe", es atómico y sigue un patrón EARS.
- [ ] No hay términos ambiguos: "rápido", "fácil", "intuitivo", "etc.", "y/o", "adecuado", "lo antes posible".
- [ ] Cada RF, RN y CB, y cada RNF medible, lo cubre al menos un Criterio de Aceptación.
- [ ] Cada CA es verificable (Dado/Cuando/Entonces) e indica qué RF/RN/CB/RNF cubre.
- [ ] Los IDs son únicos; en modo actualización, ninguno se ha renumerado ni reutilizado.
- [ ] No queda ningún `[...]`, `REQ-NNN`, `AAAA-MM-DD` ni línea de ejemplo de la plantilla.
- [ ] Todo lo no confirmado está en *Supuestos* o en *Preguntas abiertas*.

Por último, informa al usuario de la ruta del archivo, el número de RF, CB y CA y las preguntas abiertas que quedan pendientes.
