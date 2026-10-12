# spec.md: REQ-001 - Registrar préstamos de libros

| Campo | Valor |
|---|---|
| **ID** | REQ-001 |
| **Estado** | Borrador |
| **Versión** | 1.0 |
| **Fecha** | 2026-10-12 |
| **Depende de** | Ninguno |

## 1. Contexto

Presto libros a amigos con frecuencia y pierdo la pista de quién tiene cada uno. Quiero registrar cada préstamo y saber en todo momento qué libros están fuera, con quién y desde cuándo, para recuperarlos.

- **Comportamiento actual**: anoto los préstamos en una nota de texto libre; a menudo olvido apuntarlos o marcar la devolución.
- **Medida de éxito**: tras tres meses de uso, no hay ningún libro prestado del que desconozca quién lo tiene.

## 3. Requisitos Funcionales (Sintaxis EARS)

- **RF-01** (Evento): Cuando el usuario registra un préstamo, el sistema debe guardar el libro, la persona y la fecha del préstamo.
- **RF-02** (Evento): Cuando el usuario marca un préstamo como devuelto, el sistema debe guardar la fecha de devolución.
- **RF-03** (Ubicuo): El sistema debe mostrar la lista de préstamos activos ordenada del más antiguo al más reciente.
- **RF-04** (Estado): Mientras un préstamo supere el plazo máximo, el sistema debe destacarlo en la lista de préstamos activos.

## 4. Reglas de Negocio

- **RN-01**: Un libro solo puede tener un préstamo activo a la vez.
- **RN-02**: El plazo máximo de un préstamo es de 30 días naturales desde la fecha del préstamo.

## 6. Casos Borde y Comportamientos de Error

- **CB-01** (No deseado): Si el usuario registra un préstamo de un libro que ya tiene un préstamo activo, entonces el sistema debe rechazarlo e indicar con quién está el libro.
- **CB-02** (No deseado): Si el usuario registra un préstamo sin indicar la persona, entonces el sistema debe rechazarlo e indicar el dato que falta.

## 8. Fuera de Alcance

- Avisos automáticos a la persona que tiene el libro.
- Historial de lectura o valoraciones de los libros.

## 9. Criterios de Aceptación

- **CA-01** → RF-01, RF-03
  - **Dado** que no hay préstamos activos
  - **Cuando** registro el préstamo de "Dune" a Lucía con fecha de hoy
  - **Entonces** la lista de préstamos activos muestra "Dune", Lucía y la fecha de hoy
- **CA-02** → RF-02
  - **Dado** un préstamo activo de "Dune" a Lucía
  - **Cuando** lo marco como devuelto
  - **Entonces** desaparece de la lista de préstamos activos y conserva la fecha de devolución
- **CA-03** → RF-04, RN-02
  - **Dado** un préstamo activo con fecha de hace 31 días y otro con fecha de hace 30 días
  - **Cuando** consulto la lista de préstamos activos
  - **Entonces** solo aparece destacado el de hace 31 días
- **CA-04** → RN-01, CB-01
  - **Dado** un préstamo activo de "Dune" a Lucía
  - **Cuando** intento registrar un préstamo de "Dune" a Marcos
  - **Entonces** el préstamo se rechaza con un mensaje que indica que "Dune" está con Lucía
- **CA-05** → CB-02
  - **Dado** el formulario de nuevo préstamo con el libro indicado
  - **Cuando** lo envío sin indicar la persona
  - **Entonces** el préstamo se rechaza con un mensaje que indica que falta la persona

## 10. Supuestos y Preguntas Abiertas

**Supuestos**
- **SUP-01**: Cada libro se identifica por su título; no tengo dos ejemplares del mismo libro.

**Preguntas abiertas**
- **PA-01**: ¿Conviene permitir ampliar el plazo de un préstamo concreto?

## Changelog

| Versión | Fecha | Cambio |
|---|---|---|
| 1.0 | 2026-10-12 | Versión inicial. |
