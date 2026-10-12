# Guía rápida de EARS (Easy Approach to Requirements Syntax)

Cada requisito tiene esta forma: `[precondición] [disparador] el sistema debe [respuesta]`. Lleva **un único "debe"** y tiene que poder verificarse.

| Patrón | Plantilla | Cuándo usarlo | Ejemplo |
|---|---|---|---|
| **Ubicuo** | El sistema debe [respuesta]. | Comportamiento que se cumple siempre, sin disparador. | El sistema debe asociar cada pedido a un único cliente. |
| **Evento** | Cuando [disparador], el sistema debe [respuesta]. | Reacción a una acción o suceso. | Cuando el usuario solicita recuperar su contraseña, el sistema debe enviar un enlace de restablecimiento al correo registrado. |
| **Estado** | Mientras [estado], el sistema debe [respuesta]. | Comportamiento que dura mientras se cumple una condición. | Mientras la cuenta esté bloqueada, el sistema debe rechazar cualquier intento de acceso. |
| **No deseado** | Si [condición anómala], entonces el sistema debe [respuesta]. | Errores, fallos y entradas inválidas (sección Casos Borde). | Si el enlace de restablecimiento ha caducado, entonces el sistema debe informar al usuario y ofrecerle solicitar uno nuevo. |
| **Opcional** | Donde [característica], el sistema debe [respuesta]. | Comportamiento que depende de una variante del producto (una funcionalidad que puede estar incluida o no). Un ajuste del propio usuario es un *Estado*. | Donde el producto incluya el envío a domicilio, el sistema debe pedir la dirección de entrega antes de confirmar el pedido. |
| **Complejo** | Mientras [estado], cuando [disparador], el sistema debe [respuesta]. | Combinación de los anteriores. | Mientras la sesión esté activa, cuando el usuario cambie su contraseña, el sistema debe cerrar el resto de sesiones abiertas. |

## Antipatrones (y cómo corregirlos)

| ❌ Mal | Problema | ✅ Bien |
|---|---|---|
| El sistema debe ser rápido. | No se puede verificar. | Cuando el usuario envía el formulario, el sistema debe mostrar el resultado en menos de 2 segundos. |
| El sistema debe validar el email y enviar una notificación. | Dos "debe" en uno. | Divídelo en RF-01 (validar) y RF-02 (notificar). |
| El sistema debe guardar el token en la tabla `users`. | Detalle de implementación. | El sistema debe asociar el enlace de restablecimiento a una única cuenta. |
| El usuario podrá exportar datos, etc. | Alcance abierto. | Enumera los datos concretos y pasa el resto a *Fuera de Alcance*. |
| El sistema debería permitir… | Modal débil. | Usa siempre "debe". Si es deseable pero no obligatorio, va a *Fuera de Alcance* o a *Preguntas abiertas*. |
