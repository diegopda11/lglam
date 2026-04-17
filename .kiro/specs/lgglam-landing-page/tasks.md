# Plan de Implementación: lg.glam_ Landing Page

## Descripción general

Implementar el archivo `index.html` completo con CSS y JS embebidos para la landing page del estudio de belleza lg.glam_. La implementación sigue el orden estructural del documento: primero la base del archivo, luego cada sección de arriba a abajo, y finalmente la lógica JavaScript con sus tests.

## Tareas

- [x] 1. Estructura base del archivo HTML
  - Crear `index.html` con `<!DOCTYPE html>`, `<html lang="es">`, `<head>` y `<body>` vacío
  - Agregar `<meta charset="UTF-8">` y `<meta name="viewport" content="width=device-width, initial-scale=1.0">`
  - Agregar metaetiquetas Open Graph: `og:title`, `og:description` e `og:image` (Hero)
  - Agregar `<link rel="preload" as="image" href="maquillaje.jpeg">` para optimizar CRP
  - Agregar `<link>` de Google Fonts con Montserrat pesos 400, 600, 700, 900 y `&display=swap`
  - Agregar script asíncrono de Google Analytics 4 (`G-XXXXXXXXXX`)
  - Abrir etiqueta `<style>` con reset CSS, variables de paleta (`#000`, `#FFF`, `#F5F5F5`), tipografía global Montserrat uppercase, `letter-spacing: 0.05em`, clase `.grayscale` con `filter: grayscale(100%)`, y estilos `:focus-visible` globales
  - Agregar `overflow-x: hidden` en `body` y `scroll-behavior: smooth` en `html`
  - _Requisitos: 1.1, 1.2, 1.3, 1.4, 1.5, 1.7, 9.1, 9.3_

- [x] 2. Navbar
  - [x] 2.1 Implementar HTML y CSS del Navbar
    - Crear `<nav id="navbar">` con `position: fixed; top: 0; z-index: 1000; background: #FFF; box-shadow`
    - Agregar logo `<img src="logo.jpeg" alt="lg.glam_ logo" height="40">`
    - Agregar tres `<a>` de navegación: `href="#hero"`, `href="#servicios"`, `href="#instagram"`
    - Agregar `<button class="btn-dark" data-message="Hola, me gustaría agendar una cita en lg.glam_" data-analytics="whatsapp-click-navbar">AGENDAR CITA</button>`
    - Agregar `<button class="hamburger" aria-label="Abrir menú">` y `<div class="nav-mobile">` oculto por defecto
    - CSS responsive: ocultar links y botón en `≤768px`, mostrar hamburguesa
    - _Requisitos: 2.1, 2.2, 2.3, 2.7, 2.9_

- [x] 3. Sección Hero
  - [x] 3.1 Implementar HTML y CSS del Hero
    - Crear `<section id="hero">` con `height: 100vh; background-image: url(maquillaje.jpeg); background-size: cover; background-position: center`
    - Agregar pseudo-elemento `::before` con `background: rgba(0,0,0,0.50)` como overlay
    - Contenido centrado con Flexbox: `<h1>¡LOS MEJORES CAMBIOS DE LOOK!</h1>` (mínimo `2.5rem`) y subtítulo
    - Botón outline: `border: 2px solid #FFF; background: transparent; color: #FFF` con `href="#servicios"`
    - Botón sólido: `background: #FFF; color: #000` con `data-message` y `data-analytics="whatsapp-click-hero"`
    - CSS responsive: `h1` mínimo `1.8rem` en móvil, botones apilados verticalmente
    - _Requisitos: 3.1, 3.2, 3.3, 3.4, 3.5, 3.6, 3.7, 3.8, 3.9_

- [x] 4. Sección Servicios con Tabs
  - [x] 4.1 Implementar HTML y CSS de tabs y grid de tarjetas
    - Crear `<section id="servicios">` con los cinco `<button class="tab" data-filter="...">`: TODOS, MAQUILLAJE, MANOS Y PIES, CABELLO, FACIALES
    - Tab activo inicial: `data-filter="todos"` con clase `active` (fondo negro, texto blanco)
    - Crear las 7 tarjetas `<div class="card" data-category="..." data-message="..." data-analytics="...">` con imagen, nombre y precio según la tabla del diseño
    - CSS grid: `grid-template-columns: repeat(3, 1fr); gap: 1.5rem` en escritorio, 1 columna en móvil
    - Clase `.fade-in` con `@keyframes fadeIn` de `0.4s ease`
    - Agregar `alt` descriptivo a cada imagen de tarjeta
    - _Requisitos: 4.1, 4.2, 4.4, 4.5, 4.6, 4.7, 1.5, 1.6_

- [x] 5. Sección Premium 50/50
  - [x] 5.1 Implementar HTML y CSS de la sección Premium
    - Crear `<section id="premium">` con `display: grid; grid-template-columns: 1fr 1fr`
    - Columna izquierda: `<img src="peinado.jpeg" class="grayscale" alt="Peinado especial en lg.glam_">` con `object-fit: cover; min-height: 500px; width: 100%`
    - Columna derecha con fondo `#F5F5F5`: título "SERVICIOS PREMIUM", lista de ≥5 servicios con nombre y precio en `justify-content: space-between`
    - Botón `data-message="Hola, me interesa conocer los servicios premium de lg.glam_"` y `data-analytics="whatsapp-click-premium"`
    - CSS responsive: columnas apiladas en móvil (foto primero, lista después)
    - _Requisitos: 5.1, 5.2, 5.3, 5.4, 5.5, 5.6_

- [x] 6. Franja CTA
  - [x] 6.1 Implementar HTML y CSS de la franja CTA
    - Crear `<section id="cta">` con `background: #000; color: #FFF; text-align: center; padding: 4rem 2rem`
    - Encabezado "CITA DE VALORACIÓN GRATUITA" y texto secundario descriptivo
    - Botón outline blanco: `border: 2px solid #FFF; background: transparent; color: #FFF` con `data-message` y `data-analytics="whatsapp-click-cta"`
    - CSS responsive: centrar elementos, ajustar tamaño de encabezado en móvil
    - _Requisitos: 6.1, 6.2, 6.3, 6.4, 6.5, 6.6_

- [x] 7. Feed de Instagram
  - [x] 7.1 Implementar HTML y CSS del feed
    - Crear `<section id="instagram">` con grid `grid-template-columns: repeat(4, 1fr)`
    - Cuatro `<img>` cuadradas con `aspect-ratio: 1/1; object-fit: cover; filter: grayscale(100%)` usando `cejas.jpeg`, `pestañas.jpeg`, `peinado.jpeg`, `tinte.jpeg`
    - Hover overlay via `::after` con ícono SVG de Instagram centrado y fondo `rgba(0,0,0,0.5)`
    - Botón/enlace "SEGUIR EN INSTAGRAM" con `href="https://www.instagram.com/lg.glam_/" target="_blank"`
    - CSS responsive: 2 columnas en móvil
    - _Requisitos: 7.1, 7.2, 7.3, 7.4, 7.5_

- [x] 8. Footer
  - [x] 8.1 Implementar HTML y CSS del Footer
    - Crear `<footer id="footer">` con `background: #000; color: #FFF; display: grid; grid-template-columns: 1fr 1fr`
    - Columna izquierda: logo, dirección, teléfono, email, enlaces a redes sociales
    - Columna derecha: `<iframe>` de Google Maps con `filter: grayscale(100%); pointer-events: none`
    - Fallback de texto dentro del `<iframe>` para cuando esté bloqueado: enlace directo a Google Maps
    - Botón "CÓMO LLEGAR" con `href="https://maps.google.com/?q=..." target="_blank"`
    - Franja inferior con `© 2025 lg.glam_ — Todos los derechos reservados` centrado
    - CSS responsive: columnas apiladas en móvil (info primero, mapa después)
    - _Requisitos: 8.1, 8.2, 8.3, 8.4, 8.5, 8.6, 8.7_

- [x] 9. Checkpoint — Verificar estructura visual completa
  - Asegurarse de que todas las secciones renderizan correctamente, los estilos grayscale se aplican, el layout responsivo funciona en 375px y 1440px, y no hay scroll horizontal. Consultar al usuario si hay dudas.

- [x] 10. Implementar lógica JavaScript — WhatsAppService y UIController
  - [x] 10.1 Implementar objeto CONFIG y clase WhatsAppService
    - Definir `const CONFIG` con `whatsappNumber`, `defaultMessage`, `instagramUrl`, `googleMapsUrl`, `ga4MeasurementId`
    - Implementar `class WhatsAppService` con constructor, `buildUrl(message)` que retorna `https://wa.me/<número>?text=<encodeURIComponent(message)>`, y `sanitize(message)`
    - Manejar el caso de `CONFIG.whatsappNumber` vacío: `console.warn` y retornar `null`
    - _Requisitos: 10.1, 10.2, 10.3, 10.4_

  - [ ]* 10.2 Escribir property test — Property 1: Construcción de URL de WhatsApp
    - Crear archivo `test.html` (solo entorno de desarrollo, NO subir a producción) que importe fast-check vía CDN: `<script src="https://cdn.jsdelivr.net/npm/fast-check/lib/bundle/fast-check.min.js"></script>`
    - Copiar únicamente `WhatsAppService` y `CONFIG` en el `<script>` de `test.html` para aislarlos del DOM
    - Usar fast-check: para cualquier número y mensaje no vacíos, la URL SHALL comenzar con `https://wa.me/<número>?text=`
    - Ejecutar abriendo `test.html` en el navegador localmente; los resultados se muestran en consola
    - **Property 1: Construcción de URL de WhatsApp**
    - **Valida: Requisitos 10.2, 10.3**

  - [ ]* 10.3 Escribir property test — Property 2: Fallback de mensaje genérico
    - Agregar al mismo `test.html` de desarrollo
    - Usar fast-check: para cualquier llamada a `buildUrl` con mensaje vacío o `undefined`, la URL SHALL usar `CONFIG.defaultMessage` y nunca tener `text=` vacío
    - **Property 2: Fallback de mensaje genérico**
    - **Valida: Requisito 10.4**

  - [x] 10.4 Implementar UIController — tabs y filtrado de tarjetas
    - Implementar `initTabs()`: al hacer clic en un tab, ocultar tarjetas cuyo `data-category` no coincida con `data-filter`, mostrar las que sí coincidan con clase `.fade-in`, y actualizar clase `active` en tabs
    - Para `data-filter="todos"` mostrar todas las tarjetas
    - _Requisitos: 4.2, 4.3, 4.4_

  - [ ]* 10.5 Escribir property test — Property 3: Filtrado de tarjetas por tab
    - Agregar al mismo `test.html` de desarrollo; simular el DOM con un array de objetos `{ category, visible }` en lugar de nodos reales
    - Usar fast-check: para cualquier filtro distinto de "todos", todas las tarjetas visibles SHALL tener `data-category` igual al filtro
    - **Property 3: Filtrado de tarjetas por tab**
    - **Valida: Requisito 4.3**

  - [ ]* 10.6 Escribir property test — Property 4: Tab TODOS muestra todas las tarjetas
    - Agregar al mismo `test.html` de desarrollo
    - Usar fast-check: desde cualquier estado previo, activar "todos" SHALL hacer visibles todas las tarjetas
    - **Property 4: Tab TODOS muestra todas las tarjetas**
    - **Valida: Requisitos 4.2, 4.3**

  - [ ]* 10.7 Escribir property test — Property 5: Unicidad del tab activo
    - Agregar al mismo `test.html` de desarrollo; modelar los tabs como un array de strings y `setActiveTab` como función pura
    - Usar fast-check: tras cualquier clic en un tab, exactamente un tab SHALL tener la clase `active`
    - **Property 5: Unicidad del tab activo**
    - **Valida: Requisito 4.3**

  - [x] 10.8 Implementar UIController — botones WhatsApp y analítica
    - Implementar `initWhatsAppButtons()`: delegar a `WhatsAppService.buildUrl()` leyendo `data-message` del botón o tarjeta clicada
    - Implementar `initAnalytics()`: leer `data-analytics` y disparar `gtag('event', 'whatsapp_click', { button_id: value })` antes de abrir la URL
    - Aplicar a todos los botones de agendar: Navbar, Hero, tarjetas, Premium, CTA
    - _Requisitos: 10.1, 10.2, 10.3, 10.4_

  - [x] 10.9 Implementar UIController — hamburguesa y menú móvil
    - Implementar `initHamburger()`: toggle de clase visible en `.nav-mobile` al hacer clic en `.hamburger`
    - Cerrar el menú al hacer clic en cualquier enlace del menú móvil
    - _Requisitos: 2.9, 2.10_

  - [x] 10.10 Conectar UIController — punto de entrada DOMContentLoaded
    - Instanciar `WhatsAppService` y `UIController` dentro de `document.addEventListener('DOMContentLoaded', ...)`
    - Llamar `ui.init()` que invoca todos los `init*()` en orden
    - _Requisitos: 10.1_

- [x] 11. Checkpoint final — Asegurarse de que todos los tests pasan
  - Abrir `test.html` localmente y verificar que las 5 propiedades pasan en consola (100 iteraciones cada una)
  - Confirmar que los atributos `alt`, `data-message` y `data-analytics` están presentes en todos los elementos interactivos de `index.html`
  - Verificar que `test.html` NO está referenciado desde `index.html` y no se incluye en el despliegue a producción

## Notas

- Las tareas marcadas con `*` son opcionales (property-based testing) y se ejecutan **exclusivamente en desarrollo** abriendo `test.html` en el navegador local
- `test.html` importa fast-check vía CDN y contiene solo las funciones puras extraídas de `index.html`; nunca se sube al servidor de producción
- `index.html` no importa fast-check ni ninguna librería de testing — cero peso extra en producción
- Cada tarea referencia requisitos específicos para trazabilidad
- El archivo `index.html` final debe poder abrirse directamente en el navegador sin servidor
