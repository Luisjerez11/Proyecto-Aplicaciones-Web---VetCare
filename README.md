# VetCare

**Sistema web de gestión de citas y pacientes para la clínica veterinaria «Huellitas»**

Proyecto Bimestre 1 de **Desarrollo de Aplicaciones Web**, Escuela Politécnica Nacional, semestre 2026B.
Grupo 3 · Docente: Carlos Iñiguez · Entrega: 18 de noviembre de 2026.

| | Enlace |
|---|---|
| Sitio publicado (GitHub Pages) | **https://luisjerez11.github.io/Proyecto-Aplicaciones-Web---VetCare/** |
| Repositorio | https://github.com/Luisjerez11/Proyecto-Aplicaciones-Web---VetCare |

## Integrantes

| N.º | Integrante | Usuario de GitHub | Módulo |
|---|---|---|---|
| 1 | Oscar Aldahir Gualotuña Asimbaya | [@OscarGualo](https://github.com/OscarGualo) | Base, acceso y propietarios |
| 2 | Luis Jerez | [@Luisjerez11](https://github.com/Luisjerez11) | Recepción: mascotas y citas |
| 3 | Abraham | [@AbrahamMIbd1](https://github.com/AbrahamMIbd1) | Veterinario y administración |

## Reparto del trabajo

Cada pantalla tiene un solo dueño, y el historial de commits muestra el aporte de cada integrante.

| Integrante | Casos de uso | Pantallas | Otras tareas |
|---|---|---|---|
| **1 · Oscar Gualotuña** | CU-01 Iniciar sesión<br>CU-02 Gestionar propietarios | `index.html`, `menu-recepcion`, `menu-veterinario`, `menu-administrador`, `propietarios-listado`, `-nuevo`, `-detalle`, `-editar`, `-eliminar` (9) | Hoja de estilos común (`css/estilos.css`), plantilla y esqueleto de las 34 pantallas, imágenes, README, QA final y publicación en GitHub Pages |
| **2 · Luis Jerez** | CU-03 Gestionar mascotas<br>CU-04 Agendar cita<br>CU-05 Gestionar citas<br>CU-11 Consultar disponibilidad horaria | `mascotas-listado`, `-nueva`, `-detalle`, `-editar`, `-eliminar`, `citas-listado`, `-nueva`, `-disponibilidad`, `-detalle`, `-editar`, `-cancelar`, `-eliminar` (12) | QA de las pantallas del Integrante 3 |
| **3 · Abraham** | CU-06 Consultar agenda del día<br>CU-07 Registrar atención<br>CU-08 Consultar historial clínico<br>CU-09 Gestionar veterinarios<br>CU-10 Gestionar servicios | `agenda-dia`, `atencion-registrar`, `historial-clinico`, `veterinarios-listado`, `-nuevo`, `-detalle`, `-editar`, `-eliminar`, `servicios-listado`, `-nuevo`, `-detalle`, `-editar`, `-eliminar` (13) | QA de las pantallas del Integrante 1 |

## Descripción

VetCare es un **prototipo navegable** del sistema de gestión de la clínica. Tiene 34 pantallas, organizadas por rol según el mapa navegacional (entregable 3.5):

- **Recepción:** propietarios, mascotas, agendamiento, gestión de citas y disponibilidad horaria.
- **Veterinario:** agenda del día, registro de la atención médica e historial clínico.
- **Administrador:** veterinarios y catálogo de servicios con sus precios.

Es un sitio estático: el CRUD es simulado. Los formularios validan los datos con HTML5 y, si son válidos, navegan a la pantalla que indica el mapa. Los listados muestran datos de ejemplo, que son coherentes en todo el sistema (por ejemplo, la mascota Toby siempre pertenece a Carlos Andrade).

## Tecnologías y requisitos cumplidos

- **Solo HTML5 y CSS3**: sin JavaScript, sin frameworks y sin paso de compilación.
- **HTML5 semántico**: `header`, `nav`, `main`, `section`, `article`, `aside` y `footer`. Las tablas son accesibles (`caption`, `thead`, `tbody` y `th scope`).
- **Validación nativa**:
  - Tipos de control: `email`, `tel`, `password`, `date`, `time`, `number`, `search`, `radio`, `checkbox`, `select`, `textarea` y `datalist`.
  - Atributos: `required`, `pattern` + `title`, `min`, `max`, `step`, `minlength`, `maxlength`, `placeholder` y `autocomplete`.
  - Cada control tiene su `label for`, y los grupos usan `fieldset` y `legend`. No se usa `novalidate`.
- **CSS3**:
  - Una sola hoja externa, con variables en `:root`.
  - Maquetación con Flexbox y Grid; dos puntos de quiebre (40rem y 64rem).
  - Pseudoclases de validación (`:valid`, `:user-invalid`, `:required`, `:focus-visible`) y de estado (`:hover`, `:active`).
  - Selectores de atributo, `:nth-child()`, transiciones y fuentes web (Poppins y Nunito Sans).
- **Calidad**:
  - Contraste AA de WCAG.
  - Pasa los validadores W3C de HTML y CSS sin errores.
  - Se prueba en Google Chrome y Mozilla Firefox (`:has()` necesita Firefox 121 o superior).

## Estructura del repositorio

```
index.html        Inicio de sesión (CU-01)
pages/            Las otras 33 pantallas, con los nombres del mapa navegacional
css/estilos.css   Hoja de estilos común
img/fotos/        Fotos de la interfaz (WebP)
img/iconos/       Iconos SVG (Lucide)
docs/             Entregables 3.1 a 3.5 y enunciado del proyecto
README.md         Este archivo
```

## Cómo ejecutarlo

No requiere instalación. Puedes hacer cualquiera de estas tres cosas:

- Abrir el [sitio publicado](https://luisjerez11.github.io/Proyecto-Aplicaciones-Web---VetCare/).
- Abrir `index.html` directamente en el navegador.
- Servir la carpeta en local, por ejemplo con `python -m http.server`, y entrar a `http://localhost:8000/`.

**Datos de prueba:** cualquier correo con formato válido (por ejemplo `recepcion@correo.com`) y cualquier contraseña. Luego elige el rol con el que quieres ingresar.

## Documentación (`docs/`)

| Documento | Contenido |
|---|---|
| `VetCare_Vision_y_Alcance_Corregido.docx` | Visión y alcance |
| `VetCare_3_2_Especificacion_Casos_de_Uso_CORREGIDO.docx` | 3.2 Especificación de casos de uso (CU-01 a CU-11) |
| `VetCare_3_3_Diagramas_de_Casos_de_Uso_por_Actor.pdf` | 3.3 Diagramas de casos de uso por actor |
| `VetCare_Entregable_3_4_MoSCoW_3_Integrantes_Valor_Negocio.docx` | 3.4 Priorización MoSCoW y responsables |
| `VetCare_Entregable_3_5_Mapa_Navegacional (1).pdf` | 3.5 Mapa navegacional (34 pantallas, Anexo A con las transiciones) |
| `Proyecto_Bimestre1_VetCare.pdf` | Enunciado del proyecto y rúbrica |

## Flujo de trabajo en Git

- `main`: versión entregada, que es la que publica GitHub Pages.
- `develop`: rama de integración.
- `feature/*`: una rama por módulo, que entra a `develop` mediante un Pull Request revisado por otro integrante.

Los commits van en español y con el caso de uso como prefijo, por ejemplo `CU-03: agrega listado de mascotas`.

## Créditos de imágenes

- **Fotos** (`img/fotos/`): [Pexels](https://www.pexels.com/), con la [licencia de Pexels](https://www.pexels.com/license/) (uso libre, sin atribución obligatoria). Fotos originales:

  | Archivo | Foto original |
  |---|---|
  | `acceso-veterinaria.webp` | https://www.pexels.com/photo/6234618/ |
  | `propietarios.webp` | https://www.pexels.com/photo/1975989/ |
  | `mascotas.webp` | https://www.pexels.com/photo/16395150/ |
  | `citas.webp` | https://www.pexels.com/photo/6234612/ |
  | `agendar-cita.webp` | https://www.pexels.com/photo/6408282/ |
  | `agenda.webp` | https://www.pexels.com/photo/6235231/ |
  | `historial.webp` | https://www.pexels.com/photo/7470634/ |
  | `veterinarios.webp` | https://www.pexels.com/photo/6235653/ |
  | `servicios.webp` | https://www.pexels.com/photo/6816869/ |

- **Iconos:** [Lucide](https://lucide.dev/) v0.460.0, con licencia ISC (ver [`img/iconos/LICENSE-lucide.txt`](img/iconos/LICENSE-lucide.txt)).
