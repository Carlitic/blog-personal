---
title: "Semántica en HTML5 y Accesibilidad (a11y): Más Allá del Div"
description: "El uso riguroso de elementos semánticos es la base para construir interfaces accesibles y comprensibles por lectores de pantalla. Repasamos cómo estructurar el árbol de accesibilidad sin caer en el Div Soup."
pubDate: 2026-03-12
---

El uso riguroso de elementos semánticos de HTML5 no es solo una buena práctica de maquetación estética; es el pilar para construir interfaces accesibles y optimizadas tanto para usuarios de tecnologías de asistencia como para indexadores web.

### 1. El problema del "Div Soup"

La proliferación indiscriminada de contenedores `<div>` sin valor semántico destruye el árbol de accesibilidad del navegador. Los lectores de pantalla no pueden inferir jerarquías ni regiones clave si todo el contenido se presenta dentro de divisiones genéricas.

### 2. Regiones semánticas principales

HTML5 introduce etiquetas que poseen roles ARIA implícitos nativos, haciendo innecesaria la sobrecarga de atributos manuales:

- `<header>`: Representa el encabezado introductorio de una página o sección.
- `<nav>`: Contenedor explícito de navegación. Permite al usuario de teclado o lector de pantalla saltar directamente a los enlaces.
- `<main>`: Contenido primario y único del documento (solo debe existir uno por página).
- `<article>`: Contenido autónomo y reutilizable de manera independiente (como una entrada de blog o noticia).
- `<aside>`: Información tangencialmente relacionada con el contenido principal (biografía, enlaces laterales, índices).

### 3. Navegación por teclado y foco visible

Una interfaz verdaderamente usable debe asegurar que todo elemento interactivo (`<a>`, `<button>`) sea alcanzable mediante tabulación y conserve un indicador visual claro (`:focus-visible`), sin eliminarse nunca por motivos meramente visuales.
