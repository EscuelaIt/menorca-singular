# Instrucciones para el agente

## Proyecto

Este sitio web es para **Menorca Singular**, una empresa que organiza paseos turísticos en Menorca.

## Organización del proyecto

- Construye los archivos del sitio web dentro de la carpeta `web/`.
- La carpeta `copys/` contiene los textos del sitio; consúltala y reutiliza su contenido al crear páginas.
- Organiza el contenido de `web/` de forma clara, creando carpetas específicas para cada tipo de asset cuando se incorporen. Por ejemplo, separa imágenes, fuentes y otros recursos en carpetas propias, en lugar de mezclarlos con los documentos HTML y CSS.
- El proyecto es un ejemplo de curso con tres páginas de referencia (`index.html`, `ruta-talayotica.html` y `panel-usuario.html`) y la guía de estilo (`guia-estilo.html`). Los enlaces a páginas que quedan fuera de ese alcance (catálogo, otras rutas, reservas, contacto, textos legales…) apuntan a `pagina-de-ejemplo.html`, que lo explica. Si se construye una de esas páginas, cambia sus enlaces para que apunten a ella.

## Tecnologías y alcance

- Trabaja únicamente con tecnologías frontend vanilla: **HTML y CSS**.
- El contenido del sitio debe ser estático.
- No introduzcas JavaScript por ahora. Añádelo únicamente si una necesidad concreta lo requiere.
- No uses frameworks, librerías ni dependencias externas por defecto.
- Si una funcionalidad parece requerir una dependencia especial, explica la necesidad y sugiérela para evaluación antes de incorporarla.
- Evita herramientas de compilación o configuración innecesarias para este sitio estático.

## Criterios de implementación

- Usa HTML semántico y estructura clara.
- Diseña siempre con enfoque **mobile-first**: comienza por móvil y amplía progresivamente para tabletas y escritorio mediante media queries.
- Mantén los estilos en CSS y procura que la experiencia funcione en móvil y escritorio.
- Cuida la accesibilidad básica: jerarquía de encabezados, textos alternativos para imágenes informativas y controles comprensibles.
- Mantén el código sencillo y fácil de mantener, sin añadir complejidad que no requiera el contenido estático.

## Imágenes

- Las fotografías del proyecto (hero, rutas y guías) son marcadores provisionales generados con IA: sirven como referencia realista de encuadre, luz y tono. El cliente aportará las fotografías reales definitivas.
- No las señales como problema en las revisiones, aunque no sean fieles a los lugares o monumentos que representan.
- Mantén los textos alternativos y los pies de figura descriptivos y prudentes: describe lo que se ve, sin afirmar que la imagen muestra un lugar concreto.

## Lenguaje visual: «cuaderno de campo»

La identidad se apoya en el trabajo de campo de los guías (arqueólogos e historiadores). Sus componentes son compartidos y viven en `web/css/main.css`; reutilízalos en cualquier página nueva en lugar de crear variantes:

- `.registro`: etiqueta de registro en mono, numerada por sección (`01 · La ruta`, `Ruta nº 01 · Arqueología`).
- `.taula`: la taula como marca gráfica (icono en máscara CSS que toma el color del texto). Es una taula real: un único soporte vertical bajo el capitel, nunca dos pilares.
- `.section-head`: cabecera de sección con filete oliva, registro y H2.
- `.fig` y `.pie`: imágenes tratadas como láminas, con marcas de registro en las esquinas y pie de figura con lugar y coordenadas (`.pie__coord`).
- `.datos`: datos en rejilla, como una ficha de catalogación (etiqueta en mono y valor en serif; `.datos--texto` para valores largos, `.datos--4` para cuatro columnas en escritorio).
- `.ficha`: tarjeta de ruta.
- `.itinerary`: etapas de una ruta como un trazado en un plano (línea discontinua y marcas; `.itinerary__step--taula` para la etapa principal).
- `.banda-cuadricula`: fondo de papel milimetrado, para bloques de catálogo.

La guía de estilo viva está en `web/guia-estilo.html` (estilos propios en `web/css/guia.css`). Se construye con los mismos componentes y tokens que la web: si añades o cambias un componente, un color o una regla de tono, actualiza también la guía para que siga siendo la referencia visual del cliente.

Criterios de texto: titulares sin punto final, datos concretos en lugar de promesas genéricas y sin fórmulas típicas de texto generado («No somos X, somos Y», «Sin X, Y ni Z», urgencias sin datos que las respalden).

## Guía tipográfica

Dirección elegida: **«Editorial con oficio»**. Sustituye a la pareja Playfair Display + Inter, descartada por ser la combinación «elegante» que las herramientas de IA proponen por defecto y restar personalidad a la marca.

- Las familias se declaran como tokens en `web/css/tokens.css`. Usa siempre las variables, nunca el nombre de la fuente directamente:
  - `--font-titulares`: **Brygada 1918**, revival de una tipografía de imprenta clásica. Para titulares, nombres de rutas y guías, y cifras destacadas. Transmite rigor académico y poso histórico.
  - `--font-interfaz`: **IBM Plex Sans**. Para el cuerpo de texto y la interfaz.
  - `--font-registro`: **IBM Plex Mono**. Solo para el lenguaje de «cuaderno de campo»: etiquetas de registro (`01 · Cómo trabajamos`, `Ruta nº 01`), coordenadas, pies de figura y etiquetas de datos. No la uses en párrafos ni en botones.
- Se cargan desde Google Fonts con un único enlace, igual en todas las páginas: Brygada 1918 (400–700, redonda y cursiva), IBM Plex Sans (400, 500 y 600) e IBM Plex Mono (400 y 500). Si añades una página, copia ese enlace.
- Titulares en **Brygada 1918 SemiBold (600)**.
- Los títulos de sección **H2** deben medir **28 px en móvil** y **32 px en escritorio**, con interlineado de **120 %**.
- Cuerpo de texto en **IBM Plex Sans Regular (400)** y elementos de interfaz en **IBM Plex Sans Medium (500)**.
- Los botones deben medir **13 px**, usar peso **500**, ir en mayúsculas y tener un espaciado entre letras de **1.5 px**.
- Las etiquetas de registro, en `--font-registro`, miden **13 px** (12 px las etiquetas de datos), con peso **500**, en mayúsculas y con un espaciado de **0.5 px**: la mono ya es espaciada de por sí.
- Excepción: los enlaces de navegación del header en escritorio van en minúscula, a **14 px**, con **IBM Plex Sans Medium (500)** y en color grafito. La regla de mayúsculas aplica a botones y etiquetas.
- No añadas otras familias ni otro proveedor de fuentes sin proponerlo antes para evaluación.
