# Requirements Document

## Introduction

Landing page de una sola página (SPA estática) para el estudio de belleza **lg.glam_**. El sitio debe transmitir un estilo editorial de lujo / alta moda mediante una paleta monocromática, tipografía geométrica en mayúsculas y fotografías desaturadas. Todo el código se entrega en un único archivo `index.html` que incluye CSS y JS embebidos. La página debe ser completamente responsiva y todos los puntos de conversión redirigen al usuario a WhatsApp para agendar una cita.

---

## Glossary

- **Landing_Page**: El archivo `index.html` que contiene toda la interfaz del sitio.
- **Navbar**: Barra de navegación fija en la parte superior de la página.
- **Hero**: Sección de portada a pantalla completa con imagen de fondo.
- **Servicios_Grid**: Cuadrícula de tarjetas de servicios filtrable por categoría mediante tabs.
- **Seccion_Premium**: Sección dividida 50/50 que muestra una fotografía vertical y una lista de servicios premium con precios.
- **CTA_Franja**: Franja de fondo negro con llamada a la acción para agendar una cita de valoración gratuita.
- **Feed_Instagram**: Cuadrícula de cuatro imágenes cuadradas que simulan el feed de Instagram del estudio.
- **Footer**: Pie de página dividido 50/50 con información de contacto y mapa.
- **WhatsApp_API**: Enlace `https://wa.me/<número>` que abre una conversación de WhatsApp con el estudio.
- **Overlay**: Capa semitransparente oscura superpuesta sobre una imagen de fondo.
- **Tab**: Botón de filtro que activa una categoría de servicios en el Servicios_Grid.
- **Tarjeta_Servicio**: Componente visual que muestra imagen, nombre y precio de un servicio.
- **Breakpoint_Movil**: Ancho de ventana igual o inferior a 768 px.
- **data-message**: Atributo HTML personalizado en cada botón de agendar que contiene el mensaje contextual prellenado para WhatsApp (ej. `data-message="Hola, me interesa el servicio de Tintes de Cabello"`).
- **Open_Graph**: Conjunto de metaetiquetas `og:title`, `og:description` e `og:image` que controlan la previsualización del enlace al compartirlo en redes sociales o mensajería.

---

## Requirements

### Requirement 1: Estructura general del archivo

**User Story:** Como visitante, quiero que el sitio cargue desde un único archivo HTML, para que no necesite dependencias externas ni un servidor especial.

#### Acceptance Criteria

1. THE Landing_Page SHALL estar contenida en un único archivo `index.html` que incluya todo el CSS en una etiqueta `<style>` y todo el JavaScript en una etiqueta `<script>`.
2. THE Landing_Page SHALL importar la fuente Montserrat desde Google Fonts mediante una etiqueta `<link>` en el `<head>`.
3. THE Landing_Page SHALL aplicar la paleta monocromática: fondo blanco `#FFFFFF`, gris claro `#F5F5F5`, negro `#000000` como únicos colores base.
4. THE Landing_Page SHALL aplicar `font-family: 'Montserrat', sans-serif` como tipografía global con `text-transform: uppercase` y `letter-spacing` mínimo de `0.05em` en todos los textos de interfaz.
5. THE Landing_Page SHALL aplicar un filtro CSS `grayscale(100%)` a todas las imágenes de contenido para mantener la estética desaturada.
6. THE Landing_Page SHALL incluir un atributo `alt` descriptivo en todas las etiquetas `<img>` para garantizar accesibilidad y posicionamiento en buscadores locales.
7. THE Landing_Page SHALL incluir en el `<head>` las metaetiquetas Open_Graph: `og:title`, `og:description` e `og:image`, de modo que al compartir el enlace en WhatsApp o redes sociales se muestre una previsualización elegante con el nombre del estudio, una descripción breve y la imagen del Hero.

---

### Requirement 2: Navbar

**User Story:** Como visitante, quiero una barra de navegación clara y fija, para que pueda acceder a cualquier sección del sitio en todo momento.

#### Acceptance Criteria

1. THE Navbar SHALL permanecer fija en la parte superior de la ventana (`position: fixed`) durante el desplazamiento de la página.
2. THE Navbar SHALL mostrar el logotipo "lg.glam_" alineado a la izquierda usando la imagen `logo.jpeg`.
3. THE Navbar SHALL mostrar tres enlaces de navegación centrados con las etiquetas INICIO, SERVICIOS e INSTAGRAM.
4. WHEN el visitante hace clic en INICIO, THE Navbar SHALL desplazar la vista suavemente (`scroll-behavior: smooth`) hasta la sección Hero.
5. WHEN el visitante hace clic en SERVICIOS, THE Navbar SHALL desplazar la vista suavemente hasta la sección Servicios_Grid.
6. WHEN el visitante hace clic en INSTAGRAM, THE Navbar SHALL desplazar la vista suavemente hasta la sección Feed_Instagram.
7. THE Navbar SHALL mostrar un botón "AGENDAR CITA" alineado a la derecha con fondo negro y texto blanco.
8. WHEN el visitante hace clic en el botón "AGENDAR CITA" del Navbar, THE Navbar SHALL abrir el enlace WhatsApp_API en una nueva pestaña del navegador.
9. WHILE el ancho de la ventana es igual o inferior al Breakpoint_Movil, THE Navbar SHALL ocultar los enlaces de navegación y el botón, y mostrar un ícono de menú hamburguesa.
10. WHEN el visitante hace clic en el ícono hamburguesa, THE Navbar SHALL mostrar u ocultar un menú desplegable vertical con los mismos enlaces y botón.

---

### Requirement 3: Sección Hero

**User Story:** Como visitante, quiero una portada impactante a pantalla completa, para que perciba inmediatamente el estilo de lujo del estudio.

#### Acceptance Criteria

1. THE Hero SHALL ocupar el 100% del ancho y el 100% de la altura de la ventana (`100vw × 100vh`).
2. THE Hero SHALL usar `maquillaje.jpeg` como imagen de fondo con `background-size: cover` y `background-position: center`.
3. THE Hero SHALL aplicar un Overlay de color negro con opacidad entre `0.45` y `0.60` sobre la imagen de fondo.
4. THE Hero SHALL mostrar el encabezado principal "¡Los mejores cambios de look!" en tipografía blanca, tamaño mínimo de `2.5rem` en escritorio.
5. THE Hero SHALL mostrar un subtítulo descriptivo del estudio en tipografía blanca con tamaño menor al encabezado principal.
6. THE Hero SHALL mostrar dos botones: "VER SERVICIOS" con borde blanco y fondo transparente, y "AGENDAR CITA" con fondo blanco y texto negro.
7. WHEN el visitante hace clic en "VER SERVICIOS", THE Hero SHALL desplazar la vista suavemente hasta la sección Servicios_Grid.
8. WHEN el visitante hace clic en "AGENDAR CITA", THE Hero SHALL abrir el enlace WhatsApp_API en una nueva pestaña del navegador.
9. WHILE el ancho de la ventana es igual o inferior al Breakpoint_Movil, THE Hero SHALL reducir el tamaño del encabezado a un mínimo de `1.8rem` y apilar los botones verticalmente.

---

### Requirement 4: Sección Servicios con Tabs

**User Story:** Como visitante, quiero filtrar los servicios por categoría, para que pueda encontrar rápidamente lo que me interesa.

#### Acceptance Criteria

1. THE Servicios_Grid SHALL mostrar cinco Tabs con las etiquetas: TODOS, MAQUILLAJE, MANOS Y PIES, CABELLO, FACIALES.
2. WHEN la Landing_Page carga por primera vez, THE Servicios_Grid SHALL mostrar el Tab "TODOS" activo y todas las Tarjeta_Servicio visibles.
3. WHEN el visitante hace clic en un Tab, THE Servicios_Grid SHALL mostrar únicamente las Tarjeta_Servicio que pertenecen a esa categoría y marcar el Tab seleccionado como activo con fondo negro y texto blanco.
4. WHEN el visitante hace clic en un Tab, THE Servicios_Grid SHALL aplicar una transición de opacidad suave (fade-in) de al menos `0.3s` a las Tarjeta_Servicio que aparecen, evitando cambios bruscos que rompan la estética editorial.
4. THE Servicios_Grid SHALL organizar las Tarjeta_Servicio en una cuadrícula de tres columnas en escritorio.
5. WHILE el ancho de la ventana es igual o inferior al Breakpoint_Movil, THE Servicios_Grid SHALL reorganizar la cuadrícula a una sola columna.
6. THE Tarjeta_Servicio SHALL mostrar la imagen del servicio en la parte superior, el nombre del servicio en mayúsculas y el precio debajo del nombre.
7. THE Servicios_Grid SHALL incluir al menos una Tarjeta_Servicio por cada categoría usando las imágenes disponibles: `cejas.jpeg`, `maquillaje.jpeg`, `peinado.jpeg`, `pestañas.jpeg`, `tinte.jpeg`, `tratamiento-de-pedicura.png`.
8. WHEN el visitante hace clic en una Tarjeta_Servicio, THE Servicios_Grid SHALL abrir el enlace WhatsApp_API en una nueva pestaña del navegador.

---

### Requirement 5: Sección Premium 50/50

**User Story:** Como visitante, quiero ver los servicios premium con sus precios en un diseño elegante, para que pueda evaluar las opciones de mayor valor.

#### Acceptance Criteria

1. THE Seccion_Premium SHALL dividir el espacio horizontal en dos columnas iguales (50% cada una) en escritorio.
2. THE Seccion_Premium SHALL mostrar una fotografía vertical en la columna izquierda usando `peinado.jpeg` con `object-fit: cover` y altura mínima de `500px`.
3. THE Seccion_Premium SHALL mostrar en la columna derecha un título de sección, una lista de al menos cinco servicios premium, cada uno con nombre y precio alineados en extremos opuestos de la fila.
4. THE Seccion_Premium SHALL mostrar un botón "AGENDAR CITA" al final de la lista de servicios premium.
5. WHEN el visitante hace clic en el botón "AGENDAR CITA" de la Seccion_Premium, THE Seccion_Premium SHALL abrir el enlace WhatsApp_API en una nueva pestaña del navegador.
6. WHILE el ancho de la ventana es igual o inferior al Breakpoint_Movil, THE Seccion_Premium SHALL apilar las dos columnas verticalmente, mostrando primero la fotografía y luego la lista de servicios.

---

### Requirement 6: Franja CTA

**User Story:** Como visitante, quiero ver una llamada a la acción destacada, para que me resulte fácil solicitar una cita de valoración gratuita.

#### Acceptance Criteria

1. THE CTA_Franja SHALL tener fondo negro `#000000` y texto blanco `#FFFFFF`.
2. THE CTA_Franja SHALL mostrar el texto "CITA DE VALORACIÓN GRATUITA" como encabezado principal de la franja.
3. THE CTA_Franja SHALL mostrar un texto secundario breve que describa el beneficio de la cita de valoración.
4. THE CTA_Franja SHALL mostrar un botón con borde blanco y fondo transparente con la etiqueta "AGENDAR AHORA".
5. WHEN el visitante hace clic en "AGENDAR AHORA", THE CTA_Franja SHALL abrir el enlace WhatsApp_API en una nueva pestaña del navegador.
6. WHILE el ancho de la ventana es igual o inferior al Breakpoint_Movil, THE CTA_Franja SHALL centrar todos los elementos y ajustar el tamaño del encabezado para que no desborde el ancho de la pantalla.

---

### Requirement 7: Feed de Instagram

**User Story:** Como visitante, quiero ver una muestra del feed de Instagram del estudio, para que pueda evaluar el trabajo real antes de agendar.

#### Acceptance Criteria

1. THE Feed_Instagram SHALL mostrar cuatro imágenes cuadradas en una cuadrícula de cuatro columnas en escritorio.
2. THE Feed_Instagram SHALL usar las imágenes disponibles en el workspace para poblar la cuadrícula.
3. WHILE el ancho de la ventana es igual o inferior al Breakpoint_Movil, THE Feed_Instagram SHALL reorganizar la cuadrícula a dos columnas.
4. WHEN el visitante pasa el cursor sobre una imagen del Feed_Instagram, THE Feed_Instagram SHALL mostrar un Overlay oscuro con un ícono de Instagram centrado.
5. THE Feed_Instagram SHALL mostrar un botón o enlace "SEGUIR EN INSTAGRAM" debajo de la cuadrícula que abra el perfil de Instagram del estudio en una nueva pestaña.

---

### Requirement 8: Footer

**User Story:** Como visitante, quiero encontrar la información de contacto y ubicación del estudio en el pie de página, para que pueda comunicarme o visitarlos fácilmente.

#### Acceptance Criteria

1. THE Footer SHALL dividir el espacio horizontal en dos columnas iguales (50% cada una) en escritorio.
2. THE Footer SHALL mostrar en la columna izquierda: el logotipo del estudio, dirección, número de teléfono, correo electrónico y enlaces a redes sociales.
3. THE Footer SHALL mostrar en la columna derecha un mapa embebido de Google Maps con filtro CSS `grayscale(100%)` para mantener la estética monocromática. El contenedor del mapa SHALL tener `pointer-events: none` para evitar que el mapa capture el scroll en dispositivos táctiles.
4. THE Footer SHALL mostrar un botón "CÓMO LLEGAR" debajo del mapa que abra la dirección del estudio directamente en Google Maps en una nueva pestaña, permitiendo al visitante iniciar la navegación desde su app nativa.
5. THE Footer SHALL mostrar una franja inferior de cierre con el texto de copyright "© 2025 lg.glam_ — Todos los derechos reservados" centrado.
6. WHILE el ancho de la ventana es igual o inferior al Breakpoint_Movil, THE Footer SHALL apilar las dos columnas verticalmente, mostrando primero la información de contacto y luego el mapa.
7. THE Footer SHALL tener fondo negro `#000000` y texto blanco `#FFFFFF`.

---

### Requirement 9: Responsividad global

**User Story:** Como visitante desde un dispositivo móvil, quiero que el sitio se adapte correctamente a mi pantalla, para que pueda navegar sin necesidad de hacer zoom ni desplazamiento horizontal.

#### Acceptance Criteria

1. THE Landing_Page SHALL incluir la etiqueta meta viewport `<meta name="viewport" content="width=device-width, initial-scale=1.0">` en el `<head>`.
2. THE Landing_Page SHALL usar unidades relativas (`rem`, `%`, `vw`, `vh`) o CSS Grid / Flexbox para todos los layouts, evitando anchos fijos en píxeles para contenedores principales.
3. IF el contenido de cualquier sección desborda horizontalmente en el Breakpoint_Movil, THEN THE Landing_Page SHALL aplicar `overflow-x: hidden` en el elemento `<body>` para evitar scroll horizontal.
4. THE Landing_Page SHALL mantener un tamaño mínimo de fuente de `14px` en todos los textos en el Breakpoint_Movil para garantizar legibilidad.

---

### Requirement 10: Integración con WhatsApp

**User Story:** Como visitante interesado, quiero que todos los botones de agendar me lleven directamente a WhatsApp con un mensaje relevante al servicio que vi, para que pueda contactar al estudio de forma inmediata sin tener que explicar qué quiero.

#### Acceptance Criteria

1. THE Landing_Page SHALL definir el número de WhatsApp del estudio en una única variable JavaScript al inicio del script, de modo que cambiar ese valor actualice todos los enlaces de la página.
2. WHEN el visitante hace clic en cualquier botón de agendar cita, THE Landing_Page SHALL construir la URL `https://wa.me/<número>?text=<mensaje>` y abrirla en una nueva pestaña.
3. THE Landing_Page SHALL leer el atributo `data-message` del botón presionado para construir el mensaje contextual de WhatsApp. Cada botón o Tarjeta_Servicio SHALL tener un `data-message` específico al servicio o sección correspondiente (ej. `data-message="Hola, me interesa el servicio de Tintes de Cabello"`).
4. WHEN el botón presionado no tenga atributo `data-message`, THE Landing_Page SHALL usar un mensaje genérico de reserva: `"Hola, me gustaría agendar una cita en lg.glam_"`.
