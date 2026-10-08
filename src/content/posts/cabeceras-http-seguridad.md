---
title: "Cabeceras HTTP de Seguridad: Primera Línea Defensiva en el Navegador"
description: "Configurar correctamente las directivas en el servidor previene vulnerabilidades críticas como XSS, Clickjacking e inyecciones. Analizamos el impacto de CSP, HSTS y directivas clave para proteger el cliente web."
pubDate: 2026-03-20
---

Configurar correctamente las directivas en la respuesta HTTP del servidor web o CDN previene vectores de ataque críticos como Cross-Site Scripting (XSS), Clickjacking, robo de tokens de sesión e inyecciones de contenido malicioso.

### 1. Content Security Policy (CSP) 

La cabecera `Content-Security-Policy` restringe de forma declarativa qué orígenes y recursos (scripts, imágenes, estilos, conexiones WebSocket) pueden ser ejecutados por el cliente:

```http
Content-Security-Policy: default-src 'self'; script-src 'self'; style-src 'self' 'unsafe-inline'; object-src 'none'; base-uri 'self';
```

Al deshabilitar `unsafe-eval` y controlar los orígenes de script, se neutraliza la ejecución de código inyectado a través de parámetros no saneados.

### 2. HTTP Strict Transport Security (HSTS)

La directiva `Strict-Transport-Security` obliga al navegador a comunicarse exclusivamente mediante HTTPS durante el tiempo indicado en `max-age`, impidiendo ataques de degradación de protocolo (SSL Stripping):

```http
Strict-Transport-Security: max-age=31536000; includeSubDomains; preload
```

### 3. Protección contra Clickjacking y Sniffing

Complementariamente, dos directivas esenciales garantizan la integridad de la vista y del tipo de contenido:

- **X-Frame-Options:** Con valor `DENY` o `SAMEORIGIN`, previene que la página sea incrustada en un `<iframe>` invisible para engañar al usuario.
- **X-Content-Type-Options:** Con valor `nosniff`, impide que el navegador intente adivinar el tipo MIME ignorando la cabecera `Content-Type`.
