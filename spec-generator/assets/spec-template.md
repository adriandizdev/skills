# spec.md: REQ-NNN - [Nombre del Requisito]

| Campo | Valor |
|---|---|
| **ID** | REQ-NNN |
| **Estado** | Borrador · Cerrado |
| **Versión** | 1.0 |
| **Fecha** | AAAA-MM-DD |
| **Depende de** | REQ-XXX · Ninguno |

## 1. Contexto

[2–4 líneas: quién lo usa, qué problema resuelve y qué beneficio busca.]

- **Comportamiento actual** *(opcional)*: [Cómo se resuelve hoy, si el requisito modifica algo que ya existe.]
- **Medida de éxito** *(opcional)*: [Cómo se comprobará que se ha logrado el beneficio, distinto de la aceptación.]

## 2. Actores *(opcional: solo si hay más de uno o con permisos distintos)*

| Actor | Descripción | Permisos relevantes |
|---|---|---|
| [Actor] | [Quién es] | [Qué puede / no puede hacer] |

## 3. Requisitos Funcionales (Sintaxis EARS)

- **RF-01** (Ubicuo): El sistema debe [capacidad].
- **RF-02** (Evento): Cuando [disparador], el sistema debe [respuesta].
- **RF-03** (Estado): Mientras [estado], el sistema debe [respuesta].
- **RF-04** (Opcional): Donde [característica presente], el sistema debe [respuesta].
- **RF-05** (Complejo): Mientras [estado], cuando [disparador], el sistema debe [respuesta].

## 4. Reglas de Negocio

- **RN-01**: [Validación, límite, cálculo o política que el sistema debe respetar.]

## 5. Datos y Entidades (conceptual) *(opcional)*

| Entidad | Atributos relevantes | Notas |
|---|---|---|
| [Entidad de negocio] | [atributo, atributo] | [obligatoriedad, unicidad, ciclo de vida] |

## 6. Casos Borde y Comportamientos de Error

- **CB-01** (No deseado): Si [condición anómala], entonces el sistema debe [respuesta].

## 7. Requisitos No Funcionales *(opcional)*

- **RNF-01** (Rendimiento percibido): [Restricción medible.]
- **RNF-02** (Seguridad / Privacidad): [Restricción.]
- **RNF-03** (Accesibilidad): [Restricción.]

## 8. Fuera de Alcance

- [Funcionalidad descartada para esta iteración.]

## 9. Criterios de Aceptación

- **CA-01** → RF-01, RF-02
  - **Dado** [contexto inicial]
  - **Cuando** [acción]
  - **Entonces** [resultado observable]
- **CA-02** → RN-01, CB-01
  - **Dado** [contexto inicial]
  - **Cuando** [acción]
  - **Entonces** [resultado observable]

## 10. Supuestos y Preguntas Abiertas

**Supuestos**
- **SUP-01**: [Lo que se da por cierto sin haberlo confirmado.]

**Preguntas abiertas**
- **PA-01**: [Duda pendiente.]

## 11. Glosario *(opcional)*

| Término | Definición |
|---|---|
| [Término] | [Definición en lenguaje de negocio] |

## Changelog

| Versión | Fecha | Cambio |
|---|---|---|
| 1.0 | AAAA-MM-DD | Versión inicial. |
