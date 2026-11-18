# Revisión de calidad · Menorca Singular

*Clase 8 · Revisión, entrega y presentación. 18 de noviembre de 2026.*

Revisión de las cinco páginas de `web/` antes de la publicación: portada, ficha de excursión, área del viajero, guía de estilo y página de ejemplo. Este informe recoge los fallos encontrados **sin corregir**, ordenados por prioridad, para resolverlos en una segunda fase y medir el antes y el después.

## 1. Cómo se ha revisado

**Revisión automática**

| Herramienta | Qué mide | Versión |
| :---- | :---- | :---- |
| Lighthouse | Rendimiento, accesibilidad, buenas prácticas y SEO, en móvil y escritorio | 13.6 |
| axe-core | Errores de accesibilidad WCAG 2.2 AA, con movimiento reducido activado | 4.14 |
| html-validate | Errores de marcado HTML | 11.21 |

**Revisión manual asistida** (navegador automatizado, Chrome 153)

* Recorrido completo con el teclado: orden de tabulación, foco visible y elementos tapados.
* Jerarquía de encabezados, textos alternativos, idioma y metadatos de cada página.
* Adaptación a 320 px de ancho (equivale a ampliar el texto al 400 %) en busca de desbordamientos.
* Tamaño de las zonas táctiles.
* Coherencia de contenidos entre páginas: precios, fechas y tono.

**Condiciones de la prueba.** Las páginas se sirvieron desde un servidor local sin compresión ni caché. Las cifras de rendimiento de Lighthouse en móvil simulan una conexión 4G lenta y un móvil de gama media; en el servidor de publicación, con compresión, serán algo mejores.

## 2. Resultados de Lighthouse

| Página | Rendimiento | Accesibilidad | Buenas prácticas | SEO | LCP | CLS | Peso |
| :---- | ----: | ----: | ----: | ----: | ----: | ----: | ----: |
| Portada · móvil | 96 | 100 | 100 | 100 | 2,8 s | 0 | 380 KB |
| Portada · escritorio | 100 | 96 | 100 | 100 | 0,6 s | 0 | 399 KB |
| Ficha · móvil | 96 | 96 | 100 | 100 | 2,7 s | 0 | 274 KB |
| Ficha · escritorio | 100 | 96 | 100 | 100 | 0,6 s | 0 | 274 KB |
| Área del viajero | 100 | 100 | 100 | 63 \* | 1,2 s | 0 | 156 KB |
| Guía de estilo | 100 | 96 | 100 | 63 \* | 1,4 s | 0 | 195 KB |
| Página de ejemplo | 100 | 100 | 100 | 63 \* | 1,2 s | 0 | 136 KB |

\* SEO 63 en las páginas marcadas como `noindex` a propósito: no deben aparecer en buscadores.

*LCP: tiempo hasta que se ve el elemento principal de la pantalla (bueno: menos de 2,5 s). CLS: cuánto se mueve el contenido mientras carga (bueno: menos de 0,1).*

### Después de corregir los hallazgos críticos e importantes

| Página | Rendimiento | Accesibilidad | Buenas prácticas | SEO | LCP | Peso |
| :---- | ----: | ----: | ----: | ----: | ----: | ----: |
| Portada · móvil | 96 → **97** | 100 | 100 | 100 | 2,8 → **2,5 s** | 380 → **270 KB** |
| Portada · escritorio | 100 | 96 \*\* | 100 | 100 | 0,6 → **0,5 s** | 399 → **272 KB** |
| Ficha · móvil | 96 → **98** | 96 → **100** | 100 | 100 | 2,7 → **2,4 s** | 274 → **214 KB** |
| Ficha · escritorio | 100 | 96 → **100** | 100 | 100 | 0,6 → **0,5 s** | 274 → **214 KB** |
| Área del viajero | 100 | 100 | 100 | 63 \* | 1,2–1,4 s | 156 → **138 KB** |
| Guía de estilo | 100 | 96 \*\* | 100 | 63 \* | 1,4 s | 195 → **175 KB** |
| Página de ejemplo | 100 | 100 | 100 | 63 \* | 1,2 s | 136 → **116 KB** |

\*\* El 96 restante corresponde a avisos que no son fallos (apartado 4): la animación de aparición de la portada y las muestras «prohibidas» de la guía.

## 3. Lo que ya está bien

* **Estructura:** un único H1 por página, sin saltos en la jerarquía de encabezados, idioma declarado y HTML semántico.
* **Imágenes:** todas tienen texto alternativo, ancho y alto declarados (por eso el CLS es 0) y carga diferida fuera de la primera pantalla.
* **Teclado:** todos los elementos interactivos se alcanzan con el tabulador y muestran un contorno de foco visible, también sobre el pie oliva.
* **Adaptación:** ninguna página se desborda a 320 px.
* **Formularios:** todos los campos tienen su etiqueta.
* **Movimiento:** las animaciones desaparecen si el usuario pide reducir el movimiento.
* **Privacidad:** ninguna petición a servidores de terceros; las fuentes ya se sirven desde el propio proyecto.
* **Ligereza:** sin JavaScript y con menos de 400 KB por página.
* **Enlaces:** ninguno roto.

## 4. Hallazgos

### Críticos: impiden publicar

**C1 · El formulario de datos del área del viajero no informa sobre protección de datos**
* **Dónde:** `panel-usuario.html`, sección «Tus datos de contacto».
* **Por qué importa:** recoge nombre, correo y teléfono. El RGPD obliga a informar, en el propio formulario, de quién es el responsable, para qué se usan los datos y dónde ejercer los derechos, con enlace a la política de privacidad.
* **Cómo se corrige:** añadir bajo el formulario la «información básica sobre protección de datos» y el enlace a la política de privacidad. Las páginas legales (aviso legal, privacidad y condiciones) siguen pendientes, como recoge el brief.
* **Estado: corregido.** Recuadro de información básica (responsable, finalidad, legitimación, destinatarios, derechos y enlace a la política de privacidad) entre los campos y el botón, asociado al botón con `aria-describedby`. Sin errores en axe. Pendiente del cliente: razón social y NIF del responsable, y la página de política de privacidad.

### Importantes

**I1 · Contraste insuficiente en la etiqueta del módulo de reserva**
* **Dónde:** `ruta-talayotica.html`, «Reserva · Ruta nº 01».
* **Por qué importa:** oliva sobre piedra de marés da 4,28:1 y el texto de 13 px necesita 4,5:1 (WCAG 1.4.3). Lo detectan Lighthouse y axe. Es justo la combinación que la guía de estilo limita a texto grande.
* **Cómo se corrige:** dentro del módulo de reserva, la etiqueta en grafito, como ya se hace en el panel.
* **Estado: corregido.** En el módulo de reserva las etiquetas de registro van en grafito (9,2:1). Además, `AGENTS.md` recoge ahora la regla para que no se repita.

**I2 · La barra fija del móvil tapa el elemento que tiene el foco**
* **Dónde:** `ruta-talayotica.html`, en móvil.
* **Por qué importa:** al avanzar con el tabulador, el selector de fecha y algunos enlaces del pie quedan detrás de la barra «55 € / persona». Quien navega con teclado no ve dónde está (WCAG 2.4.11, nuevo en la versión 2.2).
* **Cómo se corrige:** reservar el alto de la barra con `scroll-padding-bottom` en el documento, solo en móvil.
* **Estado: corregido.** `scroll-padding-bottom: 6rem` en el documento mientras la barra está visible (por debajo de 1024 px). Recorrido completo con el tabulador en móvil: ningún elemento queda tapado.

**I3 · No hay enlace para saltar al contenido**
* **Dónde:** todas las páginas.
* **Por qué importa:** quien usa teclado o lector de pantalla tiene que atravesar la cabecera completa en cada página (WCAG 2.4.1). Las regiones de la página lo mitigan, pero el enlace es la solución esperada.
* **Cómo se corrige:** un enlace «Saltar al contenido» como primer elemento, visible solo al recibir el foco, que lleve al `main`.
* **Estado: corregido.** Enlace «Saltar al contenido» en las cinco páginas, primer elemento al tabular, visible solo con el foco. El siguiente tabulador ya cae dentro del contenido principal.

**I4 · Precio «desde» incorrecto**
* **Dónde:** `index.html`, hero: «Desde 45 €».
* **Por qué importa:** la ruta de Maó cuesta 40 €. Un dato falso en la primera pantalla resta credibilidad, y la marca se apoya en dar datos exactos.
* **Cómo se corrige:** «Desde 40 €», o un precio distinto para Maó. Actualizar también el borrador de textos.
* **Estado: corregido.** «Desde 40 €» en la portada, en el borrador de textos y en el ejemplo de la guía de estilo.

**I5 · La imagen principal tarda en aparecer en móvil**
* **Dónde:** portada y ficha, en móvil (LCP de 2,7 a 2,8 s; lo bueno es menos de 2,5 s).
* **Por qué importa:** es lo primero que ve el visitante, y en la isla la cobertura no siempre es buena.
* **Causas y cómo se corrige:**
  * Las fotos de las fichas de ruta son JPG sin versión WebP ni tamaños alternativos (68 y 77 KB). En WebP pesarían unos 25 KB cada una.
  * Las imágenes WebP admiten más compresión (Lighthouse estima 40 KB menos en la de la ficha).
  * En pantallas retina de escritorio se descarga la imagen de 1.920 px (350 KB); conviene una versión intermedia de 1.200 px.
  * Cuatro o cinco hojas de estilo, según la página, bloquean el primer pintado. Se pueden unir `fuentes.css` y `tokens.css` en `main.css`.
  * Las dos fuentes precargadas compiten con la imagen principal. Hay que medir si conviene precargar solo la de titulares.
* **Estado: corregido.** LCP en móvil de 2,8 a 2,5 s en la portada y de 2,7 a 2,4 s en la ficha. Cambios:
  * Fotos de las fichas en WebP con JPG de respaldo (`<picture>`): de 68–77 KB a unos 30 KB.
  * WebP recomprimidos y versiones nuevas de 640 px (móvil) y 1.200 px (escritorio); `sizes` ajustado al ancho real, así el escritorio grande ya no descarga la imagen de 1.920 px.
  * La imagen principal de la portada se precarga desde la cabecera del documento.
  * Fuentes recortadas a los pesos que se usan: Brygada solo en 600 (de 23 a 12 KB) y Plex Sans limitada a 400–600 (de 46 a 35 KB). Fue el cambio con más efecto en las pruebas.
  * Se probó también unir las hojas de estilo: mejora la primera pintura (1,4 → 1,1 s), pero apenas el LCP, así que se mantiene la organización actual de archivos.
  * Las imágenes pasan por el sistema de archivos con metadatos de procedencia (C2PA) que añaden unos 6 KB a cada WebP.

**I6 · Las tablas con desplazamiento de la guía no se pueden mover con el teclado**
* **Dónde:** `guia-estilo.html`, tablas de color y de tono de voz, en móvil.
* **Por qué importa:** en pantallas estrechas se desplazan en horizontal, pero sin ratón ni dedo no hay forma de verlas enteras (WCAG 2.1.1).
* **Cómo se corrige:** el contenedor con `tabindex="0"`, `role="region"` y un nombre accesible.
* **Estado: corregido.** Las dos tablas se pueden enfocar y desplazar con las flechas; tienen nombre accesible («Tabla de combinaciones de color», «Tabla de textos antes y después») y contorno de foco.

### Menores

**M1 · Dos navegaciones con el mismo nombre.** La de escritorio y la del menú móvil se llaman las dos «Navegación principal». Conviene distinguir la segunda, por ejemplo «Menú móvil».

**M2 · La barra fija queda fuera de las regiones de la página.** En la ficha, el lector de pantalla la encuentra fuera de `main` y del pie (axe, «region»). Puede ser un `aside` con nombre propio.

**M3 · Sin metadatos para compartir en redes.** Ni la portada ni la ficha tienen etiquetas Open Graph. Al compartir un enlace por WhatsApp o redes no sale imagen, título ni descripción cuidados.

**M4 · La descripción de la portada para buscadores no sigue el tono.** Empieza por «Descubre Menorca…», una fórmula que la guía de estilo evita, y no menciona a la arqueóloga ni al historiador.

**M5 · Mayúsculas innecesarias en el pie.** «Preguntas Frecuentes», «Aviso Legal», «Política de Privacidad», «Términos y Condiciones». En español solo va en mayúscula la primera palabra.

**M6 · Los teléfonos se pueden partir en dos líneas.** «+34 971 00 00 00» usa espacios normales; con espacios de no separación se mantiene en una línea.

**M7 · Enlaces pequeños para el dedo.** Los enlaces del pie, de la cabecera y de texto miden 18–20 px de alto. Cumplen el mínimo de WCAG 2.5.8 por la separación entre ellos, pero en móvil son incómodos: lo recomendable son 44 px de zona táctil.

**M8 · El módulo de reserva llega tarde con el teclado.** En escritorio se ve arriba a la derecha, pero en el orden de tabulación aparece después de las preguntas frecuentes. No es un error, pero un enlace «Ir a la reserva» al principio de la ficha ayudaría.

### Avisos que no son fallos

* **Contraste en la guía de estilo:** las muestras de combinaciones prohibidas fallan a propósito, porque ilustran lo que no se debe hacer.
* **SEO en el panel, la guía y la página de ejemplo:** el `noindex` es intencionado.
* **Contraste en la portada de escritorio (Lighthouse):** se midió a mitad de la animación de aparición. Con movimiento reducido, axe no lo detecta y los colores finales cumplen.
* **Caché, compresión y CSS sin minificar:** dependen del servidor de publicación, no del código. Se configuran en el alojamiento (compresión Brotli o Gzip y caché larga para fuentes e imágenes).
* **`<!doctype html>` en minúscula:** es válido en HTML5; la herramienta solo lo marca por estilo.

## 5. Pendiente de comprobar en dispositivos reales

Estas pruebas no se pueden automatizar y conviene hacerlas antes de publicar:

* [ ] Safari en iPhone y Chrome en Android: menú desplegable, barra fija de reserva, desplegable del calendario y formulario.
* [ ] VoiceOver (iOS o macOS) y TalkBack (Android): recorrer la ficha y reservar sin mirar la pantalla.
* [ ] Firefox y Safari de escritorio.
* [ ] Ampliación al 200 % en el navegador y tamaño de texto grande del sistema.
* [ ] Lectura al aire libre con el brillo alto: contraste de las etiquetas pequeñas.
* [ ] Una persona ajena al proyecto que intente reservar una ruta y encontrar el punto de encuentro.

## 6. Lista de comprobación reutilizable

Para aplicar a cualquier proyecto del curso:

**Accesibilidad**
* [ ] Lighthouse y axe sin errores (o con los falsos positivos justificados).
* [ ] Contraste de 4,5:1 en texto normal y 3:1 en texto grande.
* [ ] Todo funciona con el teclado, el foco siempre se ve y nunca queda tapado.
* [ ] Enlace para saltar al contenido.
* [ ] Un H1 por página y encabezados sin saltos.
* [ ] Texto alternativo en las imágenes con contenido; vacío en las decorativas.
* [ ] Formularios con etiquetas y mensajes de error claros.
* [ ] Animaciones que respetan el movimiento reducido.

**Adaptación**
* [ ] Sin desbordamiento horizontal a 320 px.
* [ ] Zonas táctiles de 44 px en móvil.
* [ ] Probado en un móvil real.

**Rendimiento**
* [ ] LCP por debajo de 2,5 s en móvil.
* [ ] Imágenes en WebP o AVIF, con varios tamaños y compresión ajustada.
* [ ] Ancho y alto declarados en las imágenes (CLS cercano a 0).
* [ ] Pocas hojas de estilo bloqueantes; fuentes alojadas y precargadas con criterio.

**Contenido y SEO**
* [ ] Título y descripción propios en cada página, en el tono de la marca.
* [ ] Metadatos para compartir en redes.
* [ ] Datos coherentes entre páginas: precios, horarios y fechas.
* [ ] Ortografía y mayúsculas revisadas.

**Legal y privacidad**
* [ ] Aviso legal, política de privacidad y condiciones.
* [ ] Información de protección de datos en cada formulario que recoja datos personales.
* [ ] Sin recursos de terceros que reciban datos de los visitantes, o con consentimiento previo.
* [ ] Política de cookies y aviso solo si se usan cookies no técnicas.
