# Poke Holes — US-001 (Crear cuenta con email y contraseña)

> Análisis de huecos: edge cases, supuestos implícitos, escenarios faltantes y dependencias/riesgos no mencionados.
> No se reescribe la historia; solo se lista lo que falta o lo que se ha asumido.

---

## Edge cases (casos límite no cubiertos)

- **Normalización del email**: no se define si `Fernando@Gmail.com` y `fernando@gmail.com` son la misma cuenta. Falta especificar normalización (minúsculas, trim de espacios) antes de comprobar duplicados. Riesgo de cuentas duplicadas percibidas como distintas.
- **Espacios y caracteres invisibles**: email o contraseña con espacios al inicio/final, o contraseña de 8 espacios (cumple "≥8 caracteres" pero es inútil).
- **Límite superior de longitud**: no hay tope máximo para email ni contraseña (payloads enormes, posible DoS o truncado en BD).
- **Contraseña de exactamente 8 caracteres**: el borde exacto no tiene AC explícito (se asume que "al menos 8" incluye 8).
- **Complejidad de contraseña**: solo se exige longitud. Nada sobre requerir número/mayúscula/símbolo ni sobre bloquear contraseñas comunes ("12345678").
- **Emails válidos pero raros**: subdirecciones (`user+tag@`), unicode/IDN, TLDs largos. ¿Qué validador se usa? El veredicto "email inválido" depende de ello.
- **Campos vacíos o ausentes**: no hay AC explícito para email en blanco o contraseña ausente (se solapan parcialmente con "formato inválido" y "<8").

## Supuestos implícitos (lo que se asumió)

- La validación de longitud y formato ocurre **también en backend** (VineJS), no solo en frontend; el AC no lo ata aunque el RNF de errores claros lo insinúa.
- El **email es el identificador único** de la cuenta (no hay username separado).
- "Queda autenticado" implica emitir un **access token de `@adonisjs/auth`** y entrar sin re-login.
- Tras el registro, el usuario aterriza en la **pantalla de bienvenida** (dependencia con US-004).
- La contraseña se almacena **hasheada**, nunca en claro (RNF de privacidad no reflejado en el AC).
- No hay verificación de email por enlace ni "recordar contraseña": excluido explícitamente en el PRD §3.1 (supuesto confirmado, no omisión).

## Escenarios faltantes (sin AC)

- **Colisión concurrente**: dos registros simultáneos con el mismo email (carrera). ¿Unicidad garantizada con constraint único en BD?
- **Comportamiento de "ofrecer ir a login"**: ¿enlace, redirección automática, email prerellenado? No especificado.
- **Errores simultáneos**: email inválido *y* contraseña corta a la vez — ¿se muestran todos los errores o solo el primero?
- **Feedback de éxito**: no se describe qué ve el usuario al registrarse correctamente más allá de "queda autenticado".
- **Rate limiting / abuso**: nada sobre limitar intentos de registro (bots, creación masiva de cuentas).
- **Enumeración de cuentas (seguridad)**: el AC de "email ya registrado" revela que ese email existe (*account enumeration*). Puede ser aceptable en el MVP, pero es una decisión de seguridad no declarada.
- **Estado tras error**: ¿se conservan los datos del formulario tras un error de validación? (UX).
- **Accesibilidad / responsive**: el RNF §4 exige web usable en móvil, pero no hay AC de accesibilidad para el formulario.

## Dependencias y riesgos no mencionados

- **Dependencia con US-002 (login)**: el flujo "email ya registrado → ir a inicio de sesión" requiere que la pantalla de login exista.
- **Dependencia con US-004 (onboarding)**: destino post-registro.
- **Seguridad del hashing y de los tokens**: RNF de privacidad §4 aplica aquí pero no está atado a esta historia.
- **Timestamps de creación / zona horaria**: menor, pero conviene registrar `created_at` de forma consistente (ligado al riesgo de TZ del §7).
- **Deuda por política de contraseñas**: si más adelante se endurece la política, las cuentas MVP con contraseñas débiles quedan como deuda.
- **Cumplimiento/privacidad**: no se menciona consentimiento, términos ni tratamiento de datos personales (email); puede ser relevante según jurisdicción, aunque el PRD no lo pide.
