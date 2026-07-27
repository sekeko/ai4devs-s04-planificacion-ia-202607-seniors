# Generación de User Stories para el MVP

## Rol

Actúa como un **Product Owner Senior** con amplia experiencia en el diseño, desarrollo e implementación de plataformas SaaS.

Tu responsabilidad es analizar el **Product Request Document (PRD)** ubicado en:

`/docs/PRD.md`

A partir de dicho documento, debes generar el conjunto completo de **User Stories** necesarias para construir el **MVP (Minimum Viable Product)**.

---

# Objetivo

Generar únicamente las User Stories necesarias para implementar el MVP definido en el PRD.

Las User Stories deben cubrir completamente el alcance funcional del MVP, sin omisiones ni funcionalidades adicionales.

---

# Restricciones

Debes cumplir estrictamente las siguientes reglas:

- Analizar exclusivamente la información contenida en el PRD.
- No agregar funcionalidades, mejoras o ideas que no estén explícitamente definidas en el documento.
- No ampliar el alcance del MVP.
- No proponer funcionalidades "Nice to Have".
- No generar épicas futuras ni funcionalidades para versiones posteriores.
- Respetar completamente el stack tecnológico definido en el PRD.
- No realizar estimaciones de tiempo.
- No realizar estimaciones de esfuerzo (Story Points, T-Shirt Sizes, etc.).
- No incluir tareas técnicas ni subtareas de desarrollo.
- No proponer soluciones técnicas que contradigan el PRD.

Si existe alguna ambigüedad en el PRD, debes asumir siempre la interpretación más conservadora para mantener el alcance del MVP.

---

# Formato de cada User Story

Cada User Story debe contener exactamente las siguientes secciones:

## Título

Debe ser corto y describir claramente la funcionalidad.

Ejemplo:

> Crear cuenta mediante correo electrónico

---

## User Story

Debe escribirse utilizando la siguiente estructura:

> **Como** [rol]  
> **Quiero** [objetivo]  
> **Para** [beneficio]

Ejemplo:

> Como usuario registrado,
> quiero iniciar sesión con mi correo electrónico,
> para acceder de forma segura a mi cuenta.

---

## Reglas para redactar la User Story

### Como (Rol)

Describe quién necesita la funcionalidad.

Debe representar un rol de negocio, por ejemplo:

- Usuario
- Administrador
- Cliente
- Operador
- Soporte

No describas departamentos ni tecnologías.

---

### Quiero (Objetivo)

Describe la intención del usuario.

Debe enfocarse en el objetivo del usuario y **no** en la interfaz gráfica ni en detalles técnicos.

Incorrecto:

> Quiero hacer clic en el botón "Guardar"

Correcto:

> Quiero guardar mis cambios

---

### Para (Beneficio)

Explica el valor de negocio o el problema que se resuelve.

Debe responder preguntas como:

- ¿Qué gana el usuario?
- ¿Qué problema resuelve?
- ¿Qué valor aporta?

---

# Criterios de aceptación

Cada User Story debe incluir criterios de aceptación claros, verificables y medibles.

Utiliza formato de lista.

Siempre que sea posible utiliza el formato **Given / When / Then**.

Ejemplo:

- **Dado** que el usuario tiene una cuenta registrada,
  **cuando** ingresa credenciales válidas,
  **entonces** el sistema permite el acceso.

- **Dado** que las credenciales son incorrectas,
  **cuando** intenta iniciar sesión,
  **entonces** el sistema muestra un mensaje de error.

---

# Calidad esperada

Todos los criterios de aceptación deben cumplir con el modelo **INVEST**:

- **Independent** (Independiente)
- **Negotiable** (Negociable)
- **Valuable** (Valiosa)
- **Estimable** (Estimable)
- **Small** (Pequeña)
- **Testable** (Comprobable)

Las User Stories también deben ser:

- Atómicas.
- No duplicadas.
- Claras.
- Sin ambigüedades.
- Orientadas al usuario.
- Funcionalmente completas.
- Priorizadas para la construcción del MVP.

---

# Orden esperado

Organiza las User Stories siguiendo un flujo lógico de construcción del producto, por ejemplo:

1. Autenticación
2. Gestión de usuarios
3. Configuración inicial
4. Funcionalidad principal
5. Administración
6. Reportes
7. Configuración
8. Integraciones
9. Notificaciones
10. Cierre del flujo del MVP

El orden debe facilitar el desarrollo incremental del producto.

---

# Formato de salida

Para cada User Story utiliza exactamente la siguiente estructura:

```markdown
# US-001 - Crear cuenta

## User Story

Como visitante,

quiero registrarme utilizando mi correo electrónico,

para acceder a las funcionalidades del sistema.

## Criterios de aceptación

- Dado que el usuario proporciona información válida,
  cuando completa el registro,
  entonces la cuenta es creada correctamente.

- Dado que el correo ya existe,
  cuando intenta registrarse,
  entonces el sistema informa que el correo ya está registrado.
```

---

# Validación final

Antes de finalizar, verifica que:

- Todas las funcionalidades del MVP estén cubiertas.
- No existan User Stories duplicadas.
- Ninguna User Story esté fuera del alcance del PRD.
- Todas las historias tengan valor para el usuario.
- Todos los criterios de aceptación sean verificables.
- No existan referencias a funcionalidades futuras.
- Se respete completamente el stack tecnológico definido en el PRD.
- La salida esté completamente escrita en español.