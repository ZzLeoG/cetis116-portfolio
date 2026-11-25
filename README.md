# Portal escolar CETis 116

Portal web para el **CETis 116**, un bachillerato tecnológico. Reúne la información pública de la escuela, los servicios para alumnos y docentes, y un panel de administración para que el personal actualice todo el contenido sin tocar código.

> **Nota:** el código fuente es privado porque pertenece a la institución. Este repositorio documenta el proyecto: qué hace, cómo está construido y las decisiones técnicas que tomé.

---

## Capturas

| Inicio | Oferta educativa |
|---|---|
| ![Inicio](capturas/inicio.png) | ![Oferta educativa](capturas/oferta-educativa.png) |

| Consulta de calificaciones | Panel de administración |
|---|---|
| ![Calificaciones](capturas/calificaciones.png) | ![Admin](capturas/admin.png) |

| Editor de horarios | Vista en celular |
|---|---|
| ![Editor de horarios](capturas/editor-horarios.png) | ![Celular](capturas/movil.png) |

---

## Funcionalidades

### Sitio público
- Inicio con slider, eventos y avisos.
- **Oferta educativa** con las carreras técnicas en tarjetas, búsqueda y filtro, y una ventana de detalle por carrera con pestañas, galería y video.
- Secciones del Sistema DUAL, empresas aliadas, talleres extracurriculares, logros y galería del plantel.
- Enlaces de interés y buzón de quejas.

### Servicios para alumnos
- **Consulta de calificaciones** por número de control, con bloqueo temporal tras varios intentos fallidos.
- **Constancia de estudios generada al momento:** se llena una plantilla de Word con los datos del alumno y se convierte a PDF.
- Horarios por grupo.
- Información de inscripciones, servicio social, prácticas profesionales, titulación, becas y calendario escolar.

### Servicios para docentes
- **Portal docente** con su horario semanal, eventos y avisos, y cambio de contraseña.
- Inicio de sesión con bloqueo por intentos fallidos.
- Información de tutorías, laboratorios, exámenes extraordinarios, recursamientos y exámenes semestrales.

### Panel de administración
- Dashboard con tarjetas de estadísticas, gráficas, mini calendario, búsqueda global, notificaciones y modo oscuro.
- Administración de carreras, slider, eventos, galería (imágenes y video), talleres, empresas aliadas, logros, enlaces de interés y buzón de quejas, con carga de archivos arrastrando y soltando.
- **Importación de calificaciones** desde los archivos oficiales.
- Restablecimiento de contraseñas de docentes y configuración general.
- **Editor visual de horarios:** se arma el horario de cada grupo seleccionando con el mouse, por sesiones y con el receso marcado.
- Gestión de exámenes extraordinarios y recursamientos.

---

## Retos y decisiones técnicas

- **Archivos oficiales que no son lo que parecen.** Las calificaciones llegan en archivos `.xls` que en realidad son HTML. El importador los lee como HTML con `DOMDocument`, extrae las tablas y las carga a la base de datos.
- **Nombres que no coinciden entre fuentes.** Los nombres de los docentes venían escritos distinto en sus archivos individuales, en los de grupo y en la base de datos. Tomé como fuente oficial el archivo de cada docente y generé actualizaciones para unificarlos, para que las búsquedas por nombre funcionen.
- **Constancias en PDF sin edición manual.** La constancia se genera con PhpWord sobre la plantilla de la escuela y se convierte a PDF con LibreOffice desde el servidor.
- **Proteger datos de alumnos.** La consulta de calificaciones limita los intentos para evitar que alguien recorra números de control al azar.

---

## Seguridad

- Contraseñas con `password_hash` y bloqueo por intentos fallidos en el portal docente.
- Límite de intentos en la consulta de calificaciones.
- Consultas con sentencias preparadas.
- Sesiones protegidas para el panel de administración.
- Archivos de conexión y de configuración bloqueados desde la web.
- Carpeta de archivos subidos sin ejecución de PHP.

---

## Tecnologías

| Área | Tecnología |
|---|---|
| Backend | PHP |
| Base de datos | MySQL |
| Frontend | HTML, CSS y JavaScript sin frameworks |
| Gráficas | Chart.js |
| Documentos | PhpWord y LibreOffice (conversión a PDF) |
| Dependencias | Composer |
| Hosting | Hostinger |

---

## Mi rol

Desarrollador **backend** del portal:

- Diseño de la base de datos: alumnos, calificaciones, carreras, horarios, docentes, eventos y contenido del sitio.
- Importador de calificaciones desde los archivos oficiales y limpieza de los datos de docentes.
- Consulta de calificaciones con límite de intentos.
- Generador de constancias en PDF.
- Lógica del panel de administración, del portal docente y de los horarios.
- Inicio de sesión, sesiones y seguridad.
- Puesta en producción en Hostinger.

El diseño visual y el frontend estuvieron a cargo de otro integrante del equipo.

---

## Contacto

- GitHub: [@ZzLeoG](https://github.com/ZzLeoG)
- Correo: [LeonardoGXD@gmail.com](mailto:LeonardoGXD@gmail.com)
