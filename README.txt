TOSHIBATECH — SERVICIO TÉCNICO DYNABOOK / TOSHIBA (MADRID)

REVISIÓN ADICIONAL (checklist unificado de la familia, a petición del cliente — repo 10/48):
- BUG REAL — no existía ninguna sección de Cal.com en todo el sitio.
  Añadida en index.html, entre la sección "proof" (Google
  Business/YouTube) y "Ubicación": "Reserva una cita de 30 minutos"
  con el iframe compartido de la familia
  (https://cal.com/kelatos/30min?embed=true&theme=light&attendeePhoneNumber=%2B34&overlayCalendar=true),
  720px de alto en escritorio y 760px en móvil. Añadido enlace "Pedir
  cita" al menú en las 47 páginas que comparten la cabecera completa
  (todas menos aviso-legal.html y politica-privacidad.html, que solo
  tienen un enlace de vuelta).
- Verificado: el correo soporte@kelatos.com solo aparece en el
  schema.org (dato estructurado no visible), no en el HTML visible de
  ninguna página.
- BUG REAL — el mensaje prellenado de WhatsApp decía "¡Hola Kelatos!"
  en las 47 páginas con cabecera completa (141 apariciones en total:
  botón "WhatsApp" del header + CTA del hero + flotante). Corregido a
  "¡Hola ToshibaTech!" en las 47 páginas mediante un script.
- BUG REAL — el menú móvil (#mainMenu) no tenía ningún listener que lo
  cerrara al pulsar un enlace del propio menú, en ninguna de las 47
  páginas. Añadido un script que quita la clase "open" de .nav al
  hacer clic en cualquier enlace.
- Verificado: los iconos del sitio son de fuente (Bootstrap Icons,
  <i class="bi ...">), no SVG/imagen con width/height fijos, así que
  no hay riesgo de deformación por proporciones incorrectas.
- BUG REAL — el H1 del hero en móvil (styles.css, compartido por las
  49 páginas) estaba en 40px. Corregido a 48px. (No se ha tocado
  ".seo-hero h1", que es un encabezado distinto y más pequeño usado
  solo en las páginas de /servicios/ y /modelos/, no en la home.)
- BUG REAL — botones del hero (.action) con border-radius de 12px y
  sin ningún estado hover. Aumentado a border-radius:999px; añadido
  filter:brightness(.88) en los tres (wa, pickup, call — los tres ya
  tenían fondo sólido de color, sin necesitar un caso especial).

Sitio multipágina grande: home + aviso-legal + política de privacidad +
20 páginas de servicio (/servicios/) + 26 páginas de modelo (/modelos/)
= 49 páginas en total. NO se ha convertido a one-page (a diferencia de
otros repos de la familia), así que no se ha añadido ningún middleware
de redirección — todas las páginas siguen existiendo y funcionando.

Dominio:
https://123pcsolutions.com.es/

⚠️ AVISO IMPORTANTE — DOMINIO DUPLICADO:
Este dominio (123pcsolutions.com.es) es EXACTAMENTE el mismo que usa el
repositorio MedionTech (otra marca distinta, revisado en esta misma
sesión). Dos negocios no pueden compartir la misma home de dominio. No
se ha modificado nada en ninguno de los dos repos — solo se deja
documentado aquí para que se confirme cuál de las dos marcas debe tener
este dominio real, o si ToshibaTech necesita uno propio.

REVISIÓN (fixes aplicados):
- Ya tenía menú móvil funcional (.menu-toggle + .nav.open) y schema.org
  completo (LocalBusiness/ProfessionalService + Service, con dirección,
  teléfono, horario y sameAs); no se ha tocado ninguno de los dos.
- Chat: no existía colisión de selector [class*="chat-window"] (este
  sitio usa nombres de clase exactos, no selectores "contiene"), pero
  faltaba el borde blanco estándar del botón del chat. Añadido
  border:1px solid #fff!important a .chat-window-toggle.
- No se ha añadido una sección SEO adicional: el sitio ya tiene 20
  páginas de servicio y 26 páginas de modelo con contenido propio, más
  completo que la plantilla one-page.
- Banner de cookies: no existía en ninguna página. Añadido (Aceptar /
  Rechazar / Política de privacidad → https://kelatos.com/privacy-policy/)
  en las 49 páginas del sitio, con diseño apilado a ancho completo en
  móvil.
- Google Analytics: no existía. Añadido G-6N4REJWY21 en las 49 páginas.

CAMBIO IMPORTANTE — formulario de contacto:
api/contacto.js usaba la API de Gmail vía OAuth2 (paquete "googleapis",
variables GOOGLE_CLIENT_ID/GOOGLE_CLIENT_SECRET/GOOGLE_REFRESH_TOKEN/
GOOGLE_EMAIL), distinto al resto de la familia. Sustituido por el mismo
patrón SMTP + nodemailer que usan todas las demás webs (sintaxis ESM,
ya que el proyecto usa "type":"module"), mismo endpoint /api/contacto y
mismos campos. Actualizado también el texto de la web que mencionaba
explícitamente "Gmail API" ("El formulario se envía mediante Gmail API
y Vercel." → "...mediante el servidor configurado en Vercel.").

Variables SMTP a configurar en Vercel (sustituyen a las de Google):
SMTP_HOST=cp7124.webempresa.eu
SMTP_PORT=465
SMTP_SECURE=true
SMTP_USER=soporte@kelatos.com
SMTP_PASS=[configurada únicamente en Vercel]
CONTACT_EMAIL=soporte@kelatos.com

Las variables antiguas (GOOGLE_CLIENT_ID, GOOGLE_CLIENT_SECRET,
GOOGLE_REFRESH_TOKEN, GOOGLE_EMAIL) ya no se usan y pueden eliminarse de
Vercel. package.json actualizado: quitada la dependencia "googleapis",
añadida "nodemailer".

REVISIÓN ADICIONAL (esta pasada):
- H1 de portada no seguía la regla final de la familia: era solo el
  nombre de la marca + tagline ("ToshibaTech | Reparación de
  ordenadores Dynabook , portátiles"), sin ser una frase afirmativa
  sobre el problema/servicio. Reescrito: "Tu Toshiba no enciende.
  Diagnóstico gratuito en Madrid." (8 palabras, distinto del H1 de
  ToshibaWEB2 — "Tu Dynabook no funciona..." — para no repetir
  redacción entre repos de la misma familia de marca). Solo se ha
  tocado el H1 de la home; las 20 páginas de /servicios/ y 26 de
  /modelos/ mantienen sus propios H1 específicos de cada página, que
  no siguen esta regla (son páginas de contenido, no la portada).
- Verificado: schema.org ya usaba correctamente el teléfono de la caja
  de información (+34 910 05 37 53), no el número compartido de los
  botones (+34 914 46 85 03); no se ha tocado.
- Confirmado: GA y banner de cookies siguen presentes en las 49
  páginas (verificado por conteo), sin regresiones.

RESUELTO — el aviso de dominio duplicado con MedionTech ya se
solucionó en otra pasada: MedionTech pasó a
informaticoschamberi.com.es, y ToshibaTech se queda con
123pcsolutions.com.es en exclusiva. No requiere ninguna acción aquí.

REVISIÓN ADICIONAL (checklist unificado de la familia, a petición del cliente):
- Añadida la franja de aviso de servicio técnico independiente
  ("Somos un servicio técnico independiente. No vemos equipos en
  garantía.") justo debajo de la cabecera, en las 47 páginas que
  comparten el header estándar (todas menos aviso-legal.html y
  politica-privacidad.html, que no tienen cabecera). Ya existía el
  aviso en el footer de cada página; esta franja lo hace visible de
  inmediato, igual que en el resto de la familia.
- Enlace de política de privacidad del formulario (solo en index.html,
  es la única página con formulario): apuntaba a la página legal
  interna /politica-privacidad.html; cambiado al enlace estándar de
  toda la familia, https://kelatos.com/privacy-policy/, y resaltado en
  azul (antes solo llevaba subrayado, sin color).
- Horario: "Sábados y domingos: cerrado" → "Sábados, domingos y días
  festivos: cerrado" (solo en index.html, único sitio donde aparece).
- Verificado: sin elemento .hero-chip/.hero-tag; sin textos
  decorativos gigantes tipo "HARDWARE" (este diseño no usa ese
  patrón); iconos ya presentes en los botones de acción (Bootstrap
  Icons); schema.org ya usaba correctamente el teléfono de la caja de
  información. Sin cambios en ninguno de estos.
- Validado: balance de etiquetas <div> y <a> correcto en las 49
  páginas tras los cambios.

REVISIÓN ADICIONAL (nueva regla de menú móvil, a petición del cliente):
- Verificado en las 49 páginas: la franja de aviso de independencia
  ya estaba fuera de <header>, como hermana justo después de él (no
  dentro), así que no se solapa con el menú móvil desplegable.
- Verificado: el header (.header{position:sticky;top:0}) ya se
  mantenía fijo/pegado arriba al hacer scroll.
- Sin cambios de código en este repo: ya cumplía la nueva regla.
