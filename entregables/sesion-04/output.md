# User Stories — FlowSync MVP

> Backlog derivado exclusivamente del PRD `docs/PRD.md` (v1.0, Q3 2026).
> Alcance limitado al MVP. No se incluyen funcionalidades "Nice to Have", épicas futuras ni sincronización inversa (Google → FlowSync), pendiente de spike técnico según el PRD.

---

# US-001 - Crear cuenta con email y contraseña

## User Story

Como visitante,

quiero registrarme con mi correo electrónico y una contraseña,

para tener una cuenta propia y acceder a las funcionalidades de FlowSync.

## Criterios de aceptación

- Dado que el visitante proporciona un email válido y una contraseña de al menos 8 caracteres,
  cuando completa el registro,
  entonces la cuenta se crea correctamente y el usuario queda autenticado.

- Dado que el visitante introduce un email con formato inválido,
  cuando intenta registrarse,
  entonces el sistema muestra un mensaje de error comprensible y no crea la cuenta.

- Dado que el visitante introduce una contraseña de menos de 8 caracteres,
  cuando intenta registrarse,
  entonces el sistema muestra un mensaje de error comprensible y no crea la cuenta.

- Dado que el email ya está registrado,
  cuando el visitante intenta registrarse,
  entonces el sistema lo indica y ofrece ir a la pantalla de inicio de sesión.

---

# US-002 - Iniciar sesión

## User Story

Como usuario registrado,

quiero iniciar sesión con mi correo electrónico y contraseña,

para acceder de forma segura a mis tareas.

## Criterios de aceptación

- Dado que el usuario tiene una cuenta registrada,
  cuando introduce credenciales válidas,
  entonces el sistema permite el acceso y mantiene la sesión mediante un token de acceso.

- Dado que las credenciales son incorrectas,
  cuando el usuario intenta iniciar sesión,
  entonces el sistema muestra un mensaje de error comprensible y no concede el acceso.

- Dado que el usuario está autenticado,
  cuando accede a la aplicación,
  entonces solo puede ver y operar sobre sus propias tareas y datos.

---

# US-003 - Cerrar sesión

## User Story

Como usuario autenticado,

quiero cerrar sesión,

para dejar de tener acceso activo a mi cuenta desde ese dispositivo.

## Criterios de aceptación

- Dado que el usuario tiene una sesión activa,
  cuando cierra sesión,
  entonces el sistema invalida el token de acceso y deja de mostrar información de la cuenta.

- Dado que el usuario ha cerrado sesión,
  cuando intenta acceder a una pantalla que requiere autenticación,
  entonces el sistema le redirige a iniciar sesión.

---

# US-004 - Pantalla de bienvenida tras el registro

## User Story

Como usuario recién registrado,

quiero ver una pantalla de bienvenida que explique brevemente qué hace FlowSync,

para entender el valor del producto y ser invitado a crear mi primera tarea.

## Criterios de aceptación

- Dado que el usuario acaba de completar el registro correctamente,
  cuando llega a la aplicación,
  entonces ve una pantalla de bienvenida con una frase que explica qué hace FlowSync.

- Dado que el usuario está en la pantalla de bienvenida,
  cuando la visualiza,
  entonces se le invita explícitamente a crear su primera tarea.

---

# US-005 - Crear tarea

## User Story

Como usuario autenticado,

quiero crear una tarea indicando al menos un título,

para registrar un pendiente que necesito gestionar.

## Criterios de aceptación

- Dado que el usuario proporciona un título,
  cuando crea la tarea,
  entonces la tarea se guarda correctamente y aparece en su listado.

- Dado que el usuario no proporciona título,
  cuando intenta crear la tarea,
  entonces el sistema muestra un mensaje de error comprensible y no crea la tarea.

- Dado que el usuario crea una tarea,
  cuando esta se guarda,
  entonces nace con estado `pending`.

- Dado que el usuario crea una tarea,
  cuando lo hace,
  entonces la descripción y la fecha límite son opcionales y la tarea se crea aunque no se rellenen.

---

# US-006 - Ver el listado de tareas

## User Story

Como usuario autenticado,

quiero ver el listado de mis tareas,

para saber qué pendientes tengo.

## Criterios de aceptación

- Dado que el usuario tiene tareas creadas,
  cuando accede a su listado,
  entonces ve sus tareas con al menos su título, estado y fecha límite (si la tiene).

- Dado que el usuario tiene varias tareas,
  cuando se muestra el listado por defecto,
  entonces las tareas se presentan ordenadas de forma que las más relevantes para "hoy" aparecen primero.

- Dado que el usuario accede a su listado,
  cuando este se carga,
  entonces solo se muestran las tareas que pertenecen a ese usuario.

---

# US-007 - Editar una tarea

## User Story

Como usuario autenticado,

quiero editar cualquier campo de una tarea existente,

para mantener mis pendientes actualizados.

## Criterios de aceptación

- Dado que el usuario tiene una tarea,
  cuando modifica su título, descripción, fecha límite o estado,
  entonces los cambios se guardan y se reflejan en el listado.

- Dado que el usuario edita el título dejándolo vacío,
  cuando intenta guardar,
  entonces el sistema muestra un mensaje de error comprensible y no guarda el cambio.

---

# US-008 - Borrar una tarea

## User Story

Como usuario autenticado,

quiero borrar una tarea,

para eliminar los pendientes que ya no necesito.

## Criterios de aceptación

- Dado que el usuario tiene una tarea,
  cuando la borra,
  entonces la tarea deja de existir y desaparece de su listado.

- Dado que el usuario intenta borrar una tarea,
  cuando confirma la acción,
  entonces solo puede borrar tareas de su propiedad.

---

# US-009 - Cambiar el estado de una tarea

## User Story

Como usuario autenticado,

quiero cambiar el estado de una tarea entre pendiente, completada y archivada,

para reflejar en qué situación se encuentra cada pendiente.

## Criterios de aceptación

- Dado que el usuario tiene una tarea en estado `pending`,
  cuando la marca como completada,
  entonces la tarea pasa a estado `completed`.

- Dado que el usuario tiene una tarea,
  cuando la archiva,
  entonces la tarea pasa a estado `archived`.

- Dado que una tarea tiene un estado,
  cuando el usuario lo modifica,
  entonces el nuevo estado solo puede ser uno de los valores válidos: `pending`, `completed` o `archived`.

---

# US-010 - Filtrar tareas por estado

## User Story

Como usuario autenticado,

quiero filtrar mis tareas por estado,

para centrarme en un subconjunto de pendientes (por ejemplo, solo los pendientes o solo los completados).

## Criterios de aceptación

- Dado que el usuario tiene tareas en distintos estados,
  cuando aplica un filtro por estado,
  entonces el listado muestra únicamente las tareas de ese estado.

- Dado que el usuario tiene un filtro por estado aplicado,
  cuando lo quita,
  entonces el listado vuelve a mostrar las tareas según la vista por defecto.

---

# US-011 - Estado vacío del listado

## User Story

Como usuario autenticado sin tareas visibles,

quiero ver un estado vacío con una invitación a crear mi primera tarea,

para saber que la cuenta funciona y qué hacer a continuación.

## Criterios de aceptación

- Dado que el usuario no tiene ninguna tarea (cuenta nueva),
  cuando accede a su listado,
  entonces ve un estado vacío con una invitación a crear la primera tarea.

- Dado que todas las tareas del usuario están archivadas y no hay ninguna visible,
  cuando accede a su listado,
  entonces ve el estado vacío con la invitación a crear una tarea.

---

# US-012 - Exportar tareas a CSV

## User Story

Como usuario autenticado,

quiero exportar mis tareas a un archivo CSV,

para poder llevarme mis datos fuera de FlowSync.

## Criterios de aceptación

- Dado que el usuario tiene tareas,
  cuando solicita la exportación,
  entonces obtiene un archivo CSV que incluye, como mínimo, el título, la descripción, el estado y la fecha límite de cada tarea.

- Dado que el usuario solicita la exportación,
  cuando se genera el archivo,
  entonces solo contiene tareas de su propiedad.

---

# US-013 - Conectar la cuenta de Google

## User Story

Como usuario autenticado,

quiero conectar mi cuenta de Google a FlowSync mediante autorización OAuth,

para que mis tareas puedan sincronizarse con mi Google Calendar.

## Criterios de aceptación

- Dado que el usuario no tiene su cuenta de Google conectada,
  cuando inicia la conexión y autoriza el acceso vía OAuth,
  entonces FlowSync queda autorizado para leer y escribir en su Google Calendar.

- Dado que el usuario completa la autorización de Google,
  cuando esta finaliza correctamente,
  entonces sus tokens de Google se almacenan de forma segura y no son accesibles por otros usuarios.

- Dado que el usuario cancela o rechaza la autorización de Google,
  cuando vuelve a FlowSync,
  entonces la cuenta de Google no queda conectada y el sistema lo indica de forma comprensible.

---

# US-014 - Reflejar tareas con fecha límite como eventos de calendario

## User Story

Como usuario con la cuenta de Google conectada,

quiero que mis tareas con fecha límite aparezcan como eventos en mi Google Calendar,

para no tener que copiarlas a mano y ver todo en un solo sitio.

## Criterios de aceptación

- Dado que el usuario tiene su cuenta de Google conectada,
  cuando crea una tarea con fecha límite,
  entonces se genera el evento correspondiente en su Google Calendar.

- Dado que el usuario tiene una tarea sin fecha límite,
  cuando le añade una fecha límite,
  entonces se genera el evento correspondiente en su Google Calendar.

- Dado que el usuario crea una tarea sin fecha límite,
  cuando la guarda,
  entonces no se genera ningún evento en el calendario.

---

# US-015 - Actualizar el evento al cambiar la fecha de una tarea

## User Story

Como usuario con la cuenta de Google conectada,

quiero que al cambiar la fecha límite de una tarea se actualice su evento en Google Calendar,

para que mi calendario siga reflejando la fecha correcta sin trabajo manual.

## Criterios de aceptación

- Dado que una tarea con fecha límite ya tiene un evento en Google Calendar,
  cuando el usuario cambia la fecha límite de la tarea,
  entonces el evento correspondiente se actualiza a la nueva fecha.

---

# US-016 - Eliminar el evento al borrar una tarea

## User Story

Como usuario con la cuenta de Google conectada,

quiero que al borrar una tarea se elimine su evento en Google Calendar,

para que mi calendario no muestre pendientes que ya no existen.

## Criterios de aceptación

- Dado que una tarea con fecha límite tiene un evento en Google Calendar,
  cuando el usuario borra la tarea,
  entonces el evento correspondiente se elimina del calendario.

---

# US-017 - Actualizar el evento al completar una tarea

## User Story

Como usuario con la cuenta de Google conectada,

quiero que al completar una tarea su evento en Google Calendar se elimine o se marque según corresponda,

para que mi calendario refleje que ese pendiente ya está resuelto.

## Criterios de aceptación

- Dado que una tarea con fecha límite tiene un evento en Google Calendar,
  cuando el usuario marca la tarea como completada,
  entonces el evento correspondiente se elimina o se marca según corresponda.

---

# US-018 - Desconectar la cuenta de Google

## User Story

Como usuario con la cuenta de Google conectada,

quiero poder desconectar mi cuenta de Google en cualquier momento,

para dejar de sincronizar mis tareas con el calendario cuando lo desee.

## Criterios de aceptación

- Dado que el usuario tiene su cuenta de Google conectada,
  cuando la desconecta,
  entonces FlowSync deja de sincronizar tareas con Google Calendar.

- Dado que el usuario desconecta su cuenta de Google,
  cuando la desconexión se completa,
  entonces las tareas ya creadas en FlowSync no se borran y siguen disponibles.

---

# US-019 - Sincronización resiliente ante fallos de la API de Google

## User Story

Como usuario con la cuenta de Google conectada,

quiero que mis tareas se guarden aunque la sincronización con Google falle,

para no perder información cuando la API de Google no está disponible.

## Criterios de aceptación

- Dado que el usuario crea o modifica una tarea,
  cuando la API de Google no está disponible o devuelve un error,
  entonces la tarea se guarda igualmente en FlowSync.

- Dado que una operación de sincronización con Google ha fallado,
  cuando el sistema lo detecta,
  entonces la operación se reintenta más tarde.

- Dado que se realiza una operación de sincronización con Google,
  cuando esta se ejecuta,
  entonces queda registrada en los logs para poder diagnosticar fallos.
