TOSHIBATECH — SERVICIO TÉCNICO DYNABOOK / TOSHIBA (MADRID)

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
