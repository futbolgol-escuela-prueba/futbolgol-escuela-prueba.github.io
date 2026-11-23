# Fútbol Gol — cómo funciona y cómo mudarla

## Partes

| Parte | Dónde vive | Qué tiene |
|---|---|---|
| Página (app e inscripción) | Este repositorio, publicado con GitHub Pages | Solo pantallas. No tiene datos ni claves. |
| Servidor | Proyecto de Apps Script "Fútbol Gol - Web App" (Drive → carpeta Fútbol Gol → 02 - App) | Login, permisos por rol, lectura y escritura de datos. |
| Datos | Planilla "Futbol Gol - Gestion" y carpetas de fotos, aptos y comprobantes en Drive | Todo lo cargado. Privado. |

`config.js` tiene la dirección del servidor (la URL que termina en `/exec`).

## Links

- App: https://futbolgol-escuela-prueba.github.io/
- Inscripción para familias: https://futbolgol-escuela-prueba.github.io/?inscripcion=1

## Mudar todo a la cuenta de Google de la escuela

1. **Transferir la propiedad.** Desde la cuenta actual, en Drive, compartí la carpeta **Fútbol Gol** con el Gmail de la escuela como editor. Después transferí la propiedad de la planilla, del proyecto de Apps Script y de las carpetas de imágenes (clic derecho → Compartir → elegir a la escuela → "Transferir propiedad"). La escuela acepta la transferencia desde su Drive.
   - Así se conservan los mismos archivos: los usuarios, las sesiones y las apps de códigos siguen funcionando.
2. **Publicar el servidor desde la cuenta de la escuela.** Con el Gmail de la escuela, abrí el proyecto de Apps Script → **Implementar → Nueva implementación** → tipo "Aplicación web":
   - Ejecutar como: **Yo** (la escuela)
   - Quién tiene acceso: **Cualquier usuario**
   - Aceptá los permisos y copiá la **URL de la aplicación web** (termina en `/exec`).
3. **Avisarle a la página.** En este repositorio, editá `config.js` (lápiz → pegar la URL nueva → *Commit changes*). En 1 o 2 minutos la página usa el servidor nuevo.
4. **Probar.** Entrá a la app, pedí un código y verificá que el mail llegue **desde el Gmail de la escuela**.

### Si además se muda la página (otra cuenta de GitHub o Cloudflare)

- Subí los archivos de este repositorio al nuevo lugar.
- En Apps Script corré `configurarUrlApp` (o cambiá `APP_URL_DEFECTO` en Código.gs) con la nueva dirección, así el link de inscripción que comparte la app y el aviso del link viejo apuntan bien.

## Seguridad (resumen)

- Entran solo los mails dados de alta en **Usuarios**. El código por mail vence en 10 minutos y tiene como máximo 5 intentos.
- **Admin y Encargado** además usan Google o Microsoft Authenticator. Tienen sesión de 7 días y reciben un aviso por mail cuando alguien entra desde un dispositivo nuevo.
- **Lectura** y **Profe** no reciben datos de plata.
- La hoja **Accesos** de la planilla registra cada ingreso.
- Si alguien pierde el celular: Más → Configuración → Usuarios → el usuario → **Resetear app de códigos**.
- La cuenta de Google dueña de la planilla tiene que tener **verificación en 2 pasos** activada.
