# Brief de Menorca Singular

## *Curso de Diseño con IA*

## **Documento de Briefing: Menorca Singular**

*Versión 2 · 18 de noviembre de 2026. Incorpora las decisiones de identidad aprobadas tras la primera ronda de diseño (apartado 5) y el registro de cambios respecto a la versión inicial (apartado 9).*

### **1\. Propuesta de valor y objetivos de negocio**

* **Marca y dominio objetivo:** *Menorca Singular* (menorcasingular.com).

* **Servicio principal:** Excursiones y rutas culturales por la isla de Menorca guiadas por historiadores, arquitectos y expertos locales.

* **Diferenciador:** Alternativa al turismo convencional de sol y playa. Grupos muy reducidos (máximo 8 personas), acceso a espacios patrimoniales poco conocidos (cultura talayótica, arquitectura señorial en Ciutadella y Maó, talleres de artesanía) y ritmo pausado. Los guías no son animadores: son especialistas que investigan aquello que enseñan.

* **Objetivo de conversión:** Captar reservas directas de experiencias mediante un flujo claro desde la exploración del catálogo hasta la confirmación en el área del viajero.

* **Indicadores para medir el éxito** *(a fijar con el cliente tras el primer mes de datos)*:
  * Porcentaje de visitas a una ficha de ruta que terminan en reserva.
  * Porcentaje de reservas hechas desde el móvil.
  * Número de consultas previas a la reserva (si bajan, la información práctica está funcionando).

### **2\. Público objetivo y contexto de uso**

* **Perfil ideal:** Viajeros culturales (parejas y pequeños grupos de 30 a 65 años, tanto nacionales como internacionales) y residentes que buscan redescubrir la isla con profundidad. Valoran el rigor, la estética cuidada y la exclusividad sin ostentación.

* **Contexto de navegación:** Uso intensivo desde dispositivos móviles, ya que muchos viajeros planifican y reservan estas actividades culturales una vez instalados en la isla.

* **Frenos de compra y cómo los resuelve la web:**

| Freno | Respuesta en el diseño |
| :---- | :---- |
| Miedo a un tour masificado | «Máx. 8 personas» aparece en el hero, en cada ficha de ruta y en la rejilla de datos de la reserva. |
| Dudas sobre la dificultad física | Cada ficha detalla distancia, terreno y calzado («unos 2 km por senderos de tierra y roca calcárea irregular»). |
| Falta de transparencia en precio, duración y punto de encuentro | Precio, duración, nivel y punto de inicio en una rejilla de datos visible antes de reservar; en el área del viajero, croquis del punto de encuentro con coordenadas, dirección y horario hora a hora. |
| Inseguridad ante cambios de planes | Cancelación gratuita hasta 24 h antes, visible junto a cada botón de reserva y gestionable desde el área del viajero. |

### **3\. Alcance, estructura y funcionalidades (Fase 1\)**

* **Pantallas incluidas en esta entrega:**

  1. **Portada** (`web/index.html`): propuesta de valor, compromisos de la marca, rutas destacadas, presentación de los guías e información práctica.
  2. **Ficha de excursión** (`web/ruta-talayotica.html`): *«Ruta talayótica al atardecer»*, con narrativa, itinerario, guía, información práctica, preguntas frecuentes, módulo de reserva y rutas relacionadas.
  3. **Área del viajero** (`web/panel-usuario.html`): vista funcional con datos de demostración donde el cliente consulta y gestiona su reserva, como paso previo a la integración con pasarela de pago.

* **Entregables complementarios:**
  * **Guía de estilo viva** (`web/guia-estilo.html`): logotipo, color, tipografía, componentes, imagen, tono de voz y accesibilidad, construida con el mismo código que la web.
  * **Logotipo y favicon** en SVG, con versión en negativo.
  * **Textos de las tres pantallas** en `copys/`, sincronizados con las páginas.

* **Fuera del alcance de esta fase:** catálogo completo, fichas de otras rutas, flujo de reserva y pago, contacto y textos legales. Los enlaces a estas páginas llevan a `web/pagina-de-ejemplo.html`, que lo explica.

* **Requisitos técnicos:**
  * Diseño *responsive* pensado primero para móvil, con puntos de corte en 768 px (tableta) y 1024 px (escritorio).
  * HTML y CSS estáticos, sin frameworks ni dependencias. JavaScript solo si una funcionalidad concreta lo requiere; en esta fase, menús, desplegables y animaciones se resuelven sin él.
  * Accesibilidad: contraste mínimo WCAG 2.1 AA, foco visible, HTML semántico y respeto a la preferencia de movimiento reducido.
  * Privacidad: sin recursos de terceros que reciban datos de los visitantes; las fuentes se alojan en el propio servidor.

### **4\. Referencias y personalidad**

**Benchmarking (referencias visuales y funcionales):**

* *Para estructura y rigor (competencia global):* **Context Travel** (`contexttravel.com`). Su forma de presentar rutas culturales guiadas por expertos: diseño muy limpio, sin presión comercial, centrado en el prestigio del guía y el valor académico de la experiencia.
* *Para atmósfera y arraigo local (inspiración estética):* **Hauser & Wirth Menorca** (`menorca.hauserwirth.com`). El uso de los espacios en blanco, la estética minimalista y la tipografía editorial del sitio de esta galería en la Illa del Rei.

**Personalidad:** Editorial, rigurosa, mediterránea y serena.

**Lo que se evita:** los clichés de agencia de viajes masiva (colores flúor, botones gigantes, insignias de oferta), las urgencias sin datos que las respalden y la estética «elegante por defecto» que proponen las herramientas de IA.

### **5\. Identidad aprobada**

**Concepto: el cuaderno de campo.** Los guías son arqueólogos e historiadores, así que la identidad toma prestados los recursos de su trabajo: registros numerados, láminas con pie de figura y coordenadas, fichas de catalogación y papel milimetrado. El resultado tiene que parecer hecho por quien investiga la isla, no por una agencia de viajes.

**Logotipo:** una taula, el monumento talayótico propio de Menorca (un capitel horizontal sobre un único soporte vertical), dibujada con un trazo grueso y redondeado, como hecho a mano, junto al nombre en Brygada 1918. Sustituye al primer símbolo, que representaba un dolmen. El favicon usa una versión maciza en blanco cal sobre oliva.

**Paleta:** cinco colores sacados del paisaje y del patrimonio menorquín.

| Color | Código | Función |
| :---- | :---- | :---- |
| Blanco cal | `#F7F4EF` | Fondo principal. |
| Piedra de marés | `#D8C7B0` | Fondos secundarios: reserva y bloques destacados. |
| Verde oliva | `#4E5D42` | Jerarquía: titulares, filetes, enlaces, etiquetas y pie de página. |
| Terracota | `#C2785C` | Acción: botones principales, numeraciones y la taula como marca. |
| Grafito | `#262624` | Texto de lectura (y `#1A1A18` para el texto de los botones). |

La terracota no alcanza el contraste mínimo para texto pequeño, así que nunca se usa en texto de lectura: solo en botones (con texto grafito), cifras grandes y marcas.

**Tipografía:** dirección «Editorial con oficio».

* **Brygada 1918** para titulares: revival de una tipografía de imprenta clásica que transmite rigor académico y poso histórico.
* **IBM Plex Sans** para el texto y la interfaz: muy legible en pantalla y en tamaños pequeños.
* **IBM Plex Mono** solo para el lenguaje de cuaderno: etiquetas de registro, coordenadas y etiquetas de datos.

Sustituye a la pareja inicial Playfair Display + Inter, descartada por ser la combinación que las herramientas de IA proponen por defecto. Amplía lo previsto en la versión anterior del brief («una serif clásica y una sans geométrica») con una tercera familia monoespaciada, que es la que más personalidad aporta al concepto.

**Componentes del lenguaje visual:** etiqueta de registro, la taula como marca gráfica, cabecera de sección, lámina con pie de figura, rejilla de datos, ficha de ruta, itinerario como trazado de ruta y papel milimetrado. Están documentados, con ejemplos, en la guía de estilo.

**Tono de voz:** concreto antes que evocador, datos en lugar de promesas, cercano y riguroso, frases cortas y titulares sin punto final. Se evitan las fórmulas típicas de texto generado («No somos X, somos Y», «Sin X, Y ni Z», «Descubre…»). La guía de estilo recoge ejemplos de antes y después.

### **6\. Contenidos y recursos gráficos**

* **Copywriting:** El cliente aporta los textos de base. Nosotros los revisamos con apoyo de modelos de lenguaje y los ajustamos al tono de voz de la marca; cada cambio se valida con el cliente. Los textos vigentes están en `copys/`.

* **Fotografía:** Las imágenes actuales son marcadores provisionales generados con IA, que sirven como referencia de encuadre, luz y tono. **El cliente aportará la fotografía real definitiva**: lugares reconocibles, los guías de verdad y la luz de la isla. Una marca que vende rigor no puede mostrar monumentos mal representados; por ejemplo, la imagen provisional de la ruta talayótica muestra un dolmen en lugar de una taula.

* **Dirección de arte fotográfica:** luz natural de primera o última hora, texturas de piedra, cal y vegetación mediterránea, grupos pequeños y gestos de conversación. Sin imágenes de banco genéricas ni filtros que falseen el color de la piedra.

* **Logotipo e iconografía:** diseñados para el proyecto y entregados en SVG.

### **7\. Metodología de trabajo y producción asistida por IA**

Este proyecto se desarrolla con **dirección de diseño asistida por inteligencia artificial**:

* **La IA como copiloto de ejecución:** Usamos modelos de lenguaje y agentes (como GPT, Gemini y Claude) para definir la arquitectura de contenidos, explorar propuestas visuales y generar el código de las interfaces. Esto permite revisar pantallas reales en el navegador en lugar de maquetas estáticas.

* **Instrucciones permanentes para la IA:** Las decisiones de identidad se recogen en `AGENTS.md`, el archivo de instrucciones que leen los agentes de IA en cada sesión. Así cualquier pantalla nueva parte de las mismas reglas.

* **Dirección de arte y control de calidad humano:** La IA acelera, pero no decide. Cada pantalla se audita y se refina manualmente para evitar acabados genéricos, asegurar la personalidad de marca, validar la jerarquía visual, garantizar un contraste accesible y comprobar la adaptación a móvil y escritorio. La primera versión generada, correcta pero intercambiable con cualquier otra marca, es el ejemplo de por qué este paso es imprescindible.

* **Hitos de revisión y publicación:**
  1. Aprobación del brief y de la estructura de contenidos. *Completado.*
  2. Elección de la dirección estética y la identidad visual. *Completado: concepto de cuaderno de campo, logotipo de la taula y tipografía «Editorial con oficio».*
  3. Revisión interactiva de las tres pantallas construidas. *En curso.*
  4. Publicación final en el servidor y dominio acordados.

### **8\. Pendiente antes de la publicación**

* **Fotografía real** del cliente para sustituir todos los marcadores provisionales.
* **Textos legales:** aviso legal, política de privacidad, condiciones de reserva y, si se añade analítica, política de cookies.
* **Revisión de calidad final:** auditoría de accesibilidad, rendimiento y SEO, y prueba en dispositivos reales.

### **9\. Registro de cambios**

| Fecha | Cambio |
| :---- | :---- |
| 11 nov 2026 | Logotipo: el dolmen se sustituye por una taula. Nuevo favicon. |
| 11 nov 2026 | Tipografía: Playfair Display + Inter se sustituyen por Brygada 1918, IBM Plex Sans e IBM Plex Mono. |
| 13 nov 2026 | Fotografía: los recursos generados con IA pasan a ser marcadores provisionales; el cliente aporta la fotografía real. |
| 18 nov 2026 | Fuentes alojadas en el propio servidor en lugar de Google Fonts, para no transmitir la IP de los visitantes a terceros (RGPD). |
