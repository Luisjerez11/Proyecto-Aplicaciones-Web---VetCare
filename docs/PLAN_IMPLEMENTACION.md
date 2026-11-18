# VetCare · Plan de implementación del entregable 3.6

Guía de trabajo para los 3 integrantes del grupo. Explica **qué** construye cada uno, **cómo** hacerlo para que todas las pantallas se vean iguales y **cómo** trabajar en GitHub sin pisarse.

> **Fecha límite:** miércoles 18/11/2026, 23:59 (sitio publicado en GitHub Pages).
>
> **Fuentes de verdad, en este orden:**
> 1. `docs/VetCare_Entregable_3_5_Mapa_Navegacional (1).pdf`: las 34 pantallas, los nombres de archivo y las 122 transiciones (Anexo A).
> 2. `docs/VetCare_3_2_Especificacion_Casos_de_Uso_CORREGIDO.docx`: los campos y atributos exactos de cada formulario.
> 3. `docs/Proyecto_Bimestre1_VetCare.pdf`: los requisitos técnicos y la rúbrica.
>
> Si este plan contradice alguno de esos documentos, manda el documento.

---

## 1. Reglas no negociables (del enunciado y la rúbrica)

| Tema | Regla |
|---|---|
| Tecnología | Solo **HTML5 y CSS3**. Nada de JavaScript, Bootstrap, Tailwind ni estilos en línea (`style="…"`). |
| Documento | `<!DOCTYPE html>`, `lang="es"`, `meta charset="UTF-8"`, `meta viewport`. |
| Semántica | `header`, `nav`, `main`, `section`, `article`, `aside`, `footer` con la **misma estructura** en todas las pantallas. Evitar el abuso de `div`. |
| Tablas | `caption`, `thead`, `tbody` y `th scope="col"`/`scope="row"`. |
| Formularios | Cada control con `label for`/`id` (y `name`). Los grupos de campos van en `fieldset` + `legend`. **Nunca** `novalidate`. Todo `pattern` lleva un `title` que explica el formato. |
| Navegación | El texto de cada enlace o botón es **idéntico al evento del Anexo A** («Ver detalle», «Guardar», «Confirmar», «Volver», «Menú», «Cerrar sesión»…). Ningún enlace roto. |
| CRUD estático | Create = formulario vacío cuyo `action` apunta a la pantalla siguiente del mapa. Read = tabla + `type="search"`. Update = el mismo formulario precargado (`value`, `selected`, `checked`). Delete = pantalla de confirmación con «Confirmar» y «Cancelar». |
| Pantallas | Exactamente las **34 del mapa**. **No** se crean páginas de resultado (`citas-cancelada.html`, `citas-eliminada.html`, `citas-reprogramada.html` y `atencion-confirmada.html` se eliminan): al guardar, se vuelve al listado indicado en el mapa. |
| Calidad | Pasa el [validador HTML](https://validator.w3.org/) y el [validador CSS](https://jigsaw.w3.org/css-validator/) sin errores. Se ve y valida igual en Chrome y Firefox. |
| Datos | Ficticios y **coherentes en todo el sitio** (ver sección 6). |

---

## 2. Estructura del repositorio (la del enunciado)

```
/
├── index.html            ← Inicio de sesión (CU-01)
├── pages/                ← las otras 33 pantallas, con el nombre exacto del mapa
├── css/
│   └── estilos.css       ← ÚNICA hoja de estilos (dueño: Integrante 1)
├── img/                  ← imágenes (p. ej. de https://picsum.photos/)
├── docs/                 ← PDF de los entregables 3.1–3.5 y este plan
└── README.md             ← proyecto, integrantes, enlace a GitHub Pages y reparto
```

Las rutas son relativas. Desde `pages/*.html` se usa `../css/estilos.css`, `../index.html` y `../img/...`. Entre pantallas de `pages/` se enlaza solo con el nombre del archivo (`mascotas-listado.html`).

---

## 3. Reparto del trabajo (cada pantalla tiene un solo dueño)

| | Integrante 1 · Oscar (base) | Integrante 2 · Recepción | Integrante 3 · Veterinario y Administración |
|---|---|---|---|
| **Casos de uso** | Base + CU-01 + CU-02 | CU-03, CU-04, CU-05, CU-11 | CU-06, CU-07, CU-08, CU-09, CU-10 |
| **Archivos** | `css/estilos.css`, `README.md`, `img/`, `index.html`, `menu-recepcion.html`, `menu-veterinario.html`, `menu-administrador.html`, `propietarios-listado.html`, `propietarios-nuevo.html`, `propietarios-detalle.html`, `propietarios-editar.html`, `propietarios-eliminar.html` | `mascotas-listado.html`, `mascotas-nueva.html`, `mascotas-detalle.html`, `mascotas-editar.html`, `mascotas-eliminar.html`, `citas-listado.html`, `citas-nueva.html`, `citas-disponibilidad.html`, `citas-detalle.html`, `citas-editar.html`, `citas-cancelar.html`, `citas-eliminar.html` | `agenda-dia.html`, `atencion-registrar.html`, `historial-clinico.html`, `veterinarios-listado.html`, `veterinarios-nuevo.html`, `veterinarios-detalle.html`, `veterinarios-editar.html`, `veterinarios-eliminar.html`, `servicios-listado.html`, `servicios-nuevo.html`, `servicios-detalle.html`, `servicios-editar.html`, `servicios-eliminar.html` |
| **N.º de pantallas** | 9 + sistema de estilos + esqueleto de las 34 + QA y publicación | 12 | 13 |
| **Transiciones del Anexo A que salen de sus pantallas** | 32 | 46 | 43 |

**Por qué este reparto:**
- El flujo «agendar con registro previo» (mascota ↔ cita) queda en una sola persona (Integrante 2).
- Todo lo del rol Veterinario y del rol Administrador queda en otra (Integrante 3).
- El Integrante 1 asume el trabajo transversal: estilos, plantilla, esqueleto, README, QA final y GitHub Pages.

**Reutilización:** en el historial de git ya existen versiones de algunas pantallas que sirven de punto de partida. Hay que ajustarlas al mapa (textos de botones y destinos):
- Integrante 2: `citas-listado`, `citas-detalle`, `citas-editar`, `citas-cancelar` y `citas-eliminar`.
- Integrante 3: `agenda-dia` y `atencion-registrar`.

Para verlas:

```bash
git show 9563c73:pages/citas-cancelar.html
```

**Coherencia con los documentos:** el reparto cambia la columna «Responsable» del MoSCoW (3.4): CU-01 pasa al Integrante 1, CU-03 al Integrante 2 y CU-07 al Integrante 3. El Integrante 1 actualiza ese documento, porque la rúbrica pide que la priorización sea «coherente con lo implementado».

---

## 4. Fase 0 · Estandarización (Integrante 1, antes que nadie)

Esta fase **desbloquea a los demás**. Hasta que el Integrante 1 fusione `feature/base-estilos` en `develop`, los otros dos solo preparan contenido (sección 9).

### 4.1 Tokens de diseño (`:root` de `css/estilos.css`)

Todos los integrantes usan **solo estas variables**. Prohibido escribir colores, tamaños o márgenes «a mano» en el HTML. Los contrastes de color están verificados con la fórmula WCAG y todos superan el nivel AA (≥ 4.5:1).

```css
/* Fuentes web: se cargan con <link> de Google Fonts en cada página (ver 4.2) */
:root {
    /* Tipografía */
    --ff-titulos: "Poppins", system-ui, sans-serif;      /* 600 y 700 */
    --ff-texto: "Nunito Sans", system-ui, sans-serif;    /* 400, 600 y 700 */

    /* Escala tipográfica: base 16px, razón 1.25 */
    --fs-sm: 0.875rem;    /* ayudas, pie de página, captions */
    --fs-base: 1rem;      /* texto, inputs, botones */
    --fs-md: 1.125rem;    /* legend, h4 */
    --fs-lg: 1.25rem;     /* h3 */
    --fs-xl: 1.563rem;    /* h2 */
    --fs-2xl: 1.953rem;   /* h1: uno solo por página */
    --lh-texto: 1.5;
    --lh-titulos: 1.2;

    /* Espaciado: múltiplos de 4px */
    --sp-1: 0.25rem;  /*  4px */
    --sp-2: 0.5rem;   /*  8px */
    --sp-3: 0.75rem;  /* 12px */
    --sp-4: 1rem;     /* 16px: separación estándar entre campos */
    --sp-5: 1.5rem;   /* 24px: separación entre secciones */
    --sp-6: 2rem;     /* 32px */
    --sp-7: 3rem;     /* 48px: márgenes grandes del layout */

    /* Colores (contraste AA verificado) */
    --c-primario: #0f766e;        /* teal: botones y enlaces (5.47:1 sobre blanco) */
    --c-primario-osc: #134e4a;    /* hover/active (9.48:1) */
    --c-texto: #1f2937;           /* texto principal (14:1 sobre el fondo) */
    --c-texto-suave: #4b5563;     /* ayudas y captions (7.2:1) */
    --c-fondo: #f8fafc;           /* fondo de página */
    --c-superficie: #ffffff;      /* tarjetas, tablas, formularios */
    --c-fila-alterna: #f1f5f9;    /* zebra de tablas */
    --c-borde: #d1d5db;
    --c-error: #b91c1c;           /* :user-invalid y botón peligro (6.47:1) */
    --c-exito: #15803d;           /* :valid (5.02:1) */
    --c-aviso-fondo: #fef3c7;
    --c-aviso-texto: #92400e;     /* 6.37:1 */
    --c-info-fondo: #dbeafe;
    --c-info-texto: #1e40af;      /* 7.15:1 */

    /* Color por rol (igual que los recuadros del mapa navegacional) */
    --c-rol: var(--c-primario);

    /* Otros */
    --radio: 0.5rem;
    --sombra: 0 1px 3px rgb(0 0 0 / 0.12);
    --ancho-max: 72rem;
    --transicion: 200ms ease;
}

.rol-recepcion     { --c-rol: #166534; }  /* verde (7.13:1) */
.rol-veterinario   { --c-rol: #92400e; }  /* ámbar (7.09:1) */
.rol-administrador { --c-rol: #5b21b6; }  /* morado (8.98:1) */
```

**Breakpoints (mobile-first).** Se escriben con valores fijos, porque `var()` no funciona dentro de `@media`:

| Nombre | Media query | Qué cambia |
|---|---|---|
| Móvil (base) | sin media query | una columna; la tabla hace scroll horizontal dentro de `.tabla-contenedor` |
| Tablet | `@media (min-width: 40rem)` | formularios en 2 columnas; menús en una cuadrícula de 2 |
| Escritorio | `@media (min-width: 64rem)` | contenido centrado a `--ancho-max`; menús en una cuadrícula de 3 o 4 |

**Reglas base que define el Integrante 1:**
- `box-sizing: border-box` global.
- `body` con `--ff-texto`, `--fs-base`, `--lh-texto`, `--c-texto` y `--c-fondo`.
- `h1`–`h3` con `--ff-titulos` y `--lh-titulos`.
- Márgenes verticales solo hacia abajo (`margin-block: 0 var(--sp-4)`).
- `main.contenido` con `max-width: var(--ancho-max)`, `margin-inline: auto` y `padding: var(--sp-5) var(--sp-4)`.

### 4.2 Plantilla HTML obligatoria (todas las pantallas internas)

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Listado de mascotas | VetCare</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Nunito+Sans:wght@400;600;700&family=Poppins:wght@600;700&display=swap">
    <link rel="stylesheet" href="../css/estilos.css">
</head>
<body class="rol-recepcion">
    <header class="encabezado">
        <p class="marca">VetCare <span>Clínica veterinaria Huellitas</span></p>
        <p class="rol-actual">Recepción</p>
        <nav class="nav-principal" aria-label="Navegación común">
            <ul>
                <li><a href="menu-recepcion.html">Menú</a></li>
                <li><a href="../index.html">Cerrar sesión</a></li>
            </ul>
        </nav>
    </header>

    <main class="contenido">
        <h1>Listado de mascotas</h1>
        <!-- CU-03, paso 2: … -->
        …
    </main>

    <footer class="pie-pagina">
        <p>VetCare · Proyecto de Aplicaciones Web · Grupo …</p>
    </footer>
</body>
</html>
```

**Convenciones de código:**
- Sangría de 4 espacios. Etiquetas y atributos en minúscula, con comillas dobles.
- En cada página van `<body class="rol-…">` (el rol de la pantalla) y un `<title>` con el formato «Nombre de pantalla | VetCare».
- La navegación común del `header` tiene «Menú» (→ menú del rol) y «Cerrar sesión» (→ `../index.html`). En los tres menús solo aparece «Cerrar sesión».
- Antes de cada bloque funcional va un comentario que lo enlaza a la especificación: `<!-- CU-05, flujo 5b: … -->`.
- Los `id` van en español y con guiones (`fecha-nacimiento`). Cada control lleva `id` **y** `name`; el `name` es imprescindible para que los `radio` funcionen como grupo. Única excepción: la contraseña de `index.html` no lleva `name`, para que no aparezca en la URL del envío GET.
- Ningún `style="…"` y ninguna clase fuera del catálogo 4.3.

### 4.3 Catálogo de componentes (las únicas clases permitidas)

| Clase / selector | Uso | Requisito CSS3 que cubre |
|---|---|---|
| `.encabezado`, `.marca`, `.rol-actual`, `.nav-principal` | Cabecera común, con borde o fondo en `--c-rol` | Flexbox |
| `main.contenido` | Contenedor central | — |
| `.pie-pagina` | Pie de página | — |
| `.menu-tarjetas` (en un `nav`) | Opciones de cada menú de rol como tarjetas | Grid + `:hover` + `transition` |
| `.barra-herramientas` | Fila con el buscador y el botón «Nuevo …» de cada listado | Flexbox |
| `form.buscador` (`role="search"`) | Buscador `type="search"` + botón «Buscar» | — |
| `.tabla-contenedor` › `table.tabla` | Listados | `tbody tr:nth-child(even)` (zebra), scroll horizontal en móvil |
| `.estado[data-estado="Programada"]`, `[data-estado="Atendida"]`, `[data-estado="Cancelada"]` | Etiqueta de estado de la cita | **Selector de atributo** |
| `.acciones-fila` | Lista de enlaces por fila (Ver detalle / Editar / Eliminar) | Flexbox |
| `.introduccion` | Párrafo breve bajo el `h1` | — |
| `.formulario` | Todo formulario de alta o edición (separa los `fieldset`) | Flexbox |
| `.campos` | Contenedor de los `.campo` dentro de cada `fieldset` | Grid (2 columnas ≥ 40rem) |
| `.campo`, `.campo--ancho` | `label` + control + `.ayuda`; `--ancho` ocupa las 2 columnas (p. ej. `textarea`) | — |
| `.campo-grupo` › `.opciones` | `fieldset` anidado con un grupo de `radio`/`checkbox`; cada opción es `<label><input> Texto</label>` | Flexbox |
| `.ayuda` | Texto bajo el control (con `aria-describedby`) | — |
| `.acciones` | Fila de botones al final de un formulario | Flexbox |
| `.boton`, `.boton--secundario`, `.boton--peligro` | Botones y enlaces con aspecto de botón | `:hover`, `:active`, `:focus-visible`, `transition` |
| `.ficha` (un `dl`) | Datos de un registro en detalle, eliminar y cancelar | Grid |
| `.aviso`, `.aviso--error`, `.aviso--exito`, `.aviso--info` | Escenarios estáticos («Sin bloques libres», «sin coincidencias»…) | — |
| `aside.nota-demo` | Instrucciones para quien prueba («ingresa 12,5 kg…») | `aside` semántico |
| `.solo-lector` | Texto oculto visualmente para lectores de pantalla | Accesibilidad |
| `.acceso`, `.opciones-acceso` | Solo `index.html` (tarjeta de inicio de sesión) | Grid |
| `article:target` | Detalle resaltado al llegar por un ancla (historial clínico) | `:target` |
| `.acceso-portada` | Solo `index.html`: foto de la clínica + tarjeta `.acceso` | Grid (2 columnas ≥ 64rem) |
| `img.portada-modulo` | Foto decorativa (`alt=""`) bajo el `h1` de cada pantalla de entrada de módulo | `aspect-ratio` + `object-fit` |

**Imágenes e iconos** (rama `feature/mejora-interfaz`; análisis en `docs/ANALISIS_UX.md`):
- Las fotos están en `img/fotos/`. En los menús, cada tarjeta empieza con un `<img alt="">`, sin clase: el estilo lo da `.menu-tarjetas img`.
- Los iconos (Lucide, en `img/iconos/`) **no se escriben en el HTML**. `estilos.css` los agrega con `::before` según la función del elemento, por ejemplo `.buscador .boton`, `.boton--peligro`, `.acciones-fila a[href*="-editar"]`, `.aviso--info` o `.nav-principal a[href$="index.html"]`. Por eso el texto de enlaces y botones sigue igual al del Anexo A.

**Página de referencia:** `pages/propietarios-listado.html` está totalmente maquetada con este catálogo; úsala como modelo para los demás listados.

**Estados de los formularios (los define el Integrante 1 una sola vez):**
- `input:required`, `select:required` y `textarea:required` muestran un indicador en su `label`.
- `:user-invalid` usa borde `--c-error` y muestra el mensaje `.ayuda` en rojo. Funciona en Chrome 119+ y Firefox 88+. No se usa `:invalid` solo, porque pintaría de rojo los campos vacíos nada más cargar la página.
- `:valid` usa borde `--c-exito` mientras el campo tiene el foco.
- `:focus-visible` usa un contorno de 3px en `--c-primario` con `outline-offset: 2px`.
- `a` y `.boton` cambian con `:hover` y `:active`, con `transition: background-color var(--transicion), color var(--transicion)`.

Si alguien necesita un estilo que no está en el catálogo, **no edita `estilos.css`**: abre un Issue «Solicitud CSS: …» y el Integrante 1 lo agrega (sección 8).

### 4.4 Patrones por tipo de pantalla (copiar y adaptar)

**Listado (Read).** `…-listado.html`

```html
<!-- CU-0X, paso 2: listado con buscador -->
<section class="barra-herramientas" aria-label="Herramientas del listado">
    <form class="buscador" role="search" action="mascotas-listado.html#resultados" method="get">
        <label for="busqueda">Buscar</label>
        <input type="search" id="busqueda" name="busqueda" placeholder="Buscar mascota">
        <button type="submit" class="boton">Buscar</button>
    </form>
    <a class="boton" href="mascotas-nueva.html">Nueva mascota</a>
</section>

<section id="resultados" aria-labelledby="titulo-resultados">
    <h2 id="titulo-resultados">Mascotas registradas</h2>
    <div class="tabla-contenedor">
        <table class="tabla">
            <caption>Mascotas de ejemplo de la clínica Huellitas</caption>
            <thead>
                <tr><th scope="col">Código</th><th scope="col">Nombre</th>…<th scope="col">Acciones</th></tr>
            </thead>
            <tbody>
                <tr>
                    <th scope="row">M-001</th>
                    <td>Toby</td>
                    …
                    <td>
                        <ul class="acciones-fila">
                            <li><a href="mascotas-detalle.html">Ver detalle<span class="solo-lector"> de Toby</span></a></li>
                            <li><a href="mascotas-editar.html">Editar<span class="solo-lector"> a Toby</span></a></li>
                            <li><a href="mascotas-eliminar.html">Eliminar<span class="solo-lector"> a Toby</span></a></li>
                        </ul>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</section>

<!-- CU-0X, flujo 3a.2a: escenario estático sin coincidencias -->
<section class="aviso aviso--info" aria-label="Ejemplo de búsqueda sin resultados">
    <p>Ejemplo: al buscar «Rex» no se encontraron coincidencias. Intenta con otro criterio.</p>
</section>
```

**Nuevo (Create).** `…-nuevo.html` / `…-nueva.html`. «Cancelar» es un **enlace**, no un botón de envío, para que no exija datos válidos.

```html
<form class="formulario" action="mascotas-listado.html" method="get">
    <fieldset>
        <legend>Datos de la mascota</legend>
        <div class="campos">
            <div class="campo">
                <label for="nombre">Nombre</label>
                <input type="text" id="nombre" name="nombre" required minlength="2" maxlength="40" placeholder="Toby">
            </div>

            <fieldset class="campo-grupo campo--ancho">
                <legend>Sexo</legend>
                <div class="opciones">
                    <label><input type="radio" name="sexo" value="Macho" required> Macho</label>
                    <label><input type="radio" name="sexo" value="Hembra"> Hembra</label>
                </div>
            </fieldset>

            <div class="campo campo--ancho">
                <label for="observaciones">Observaciones</label>
                <textarea id="observaciones" name="observaciones" maxlength="300"></textarea>
            </div>
        </div>
    </fieldset>
    <div class="acciones">
        <button type="submit" class="boton">Guardar</button>
        <a class="boton boton--secundario" href="mascotas-listado.html">Cancelar</a>
    </div>
</form>
```

**Editar (Update).** Usa el mismo formulario que «Nuevo», precargado con los datos canónicos (`value="Toby"`, `<option selected>`, `checked`) y con los mismos `action` y botones.

**Detalle.** `…-detalle.html`

```html
<article aria-labelledby="titulo-ficha">
    <h2 id="titulo-ficha">Toby</h2>
    <dl class="ficha">
        <dt>Especie</dt><dd>Perro</dd>
        …
    </dl>
    <div class="acciones">
        <a class="boton" href="mascotas-editar.html">Editar</a>
        <a class="boton boton--secundario" href="mascotas-listado.html">Volver</a>
    </div>
</article>
```

**Eliminar (Delete).** `…-eliminar.html`

```html
<article aria-labelledby="titulo-ficha">
    <h2 id="titulo-ficha">¿Eliminar a Toby?</h2>
    <dl class="ficha">…</dl>
    <form action="mascotas-listado.html" method="get">
        <div class="acciones">
            <button type="submit" class="boton boton--peligro">Confirmar</button>
            <a class="boton boton--secundario" href="mascotas-listado.html">Cancelar</a>
        </div>
    </form>
</article>
```

**Las transiciones rojas del mapa** («Guardar [datos inválidos] / mostrar error») **no necesitan código extra**: las resuelve el navegador con `required`, `pattern`, `min`, `max` y `step`. El formulario no se envía y la pantalla no cambia.

**Las reglas que dependen de datos** (bloque ocupado, nombre de servicio repetido, día sin citas, búsqueda sin resultados, mascota sin historial) se muestran como una `section.aviso` con datos de ejemplo, junto al contenido normal.

### 4.5 Esqueleto de las 34 pantallas

En la misma rama `feature/base-estilos`, el Integrante 1 crea **los 34 archivos**, cada uno con:
- la plantilla 4.2 completa (rol correcto en `body`, «Menú» apuntando al menú de ese rol y «Cerrar sesión»);
- el `h1` con el nombre de la pantalla;
- un comentario `<!-- Pendiente: Integrante N · CU-XX -->` dentro de `main`.

En los tres menús deja ya los enlaces definitivos a los listados.

Con esto:
1. Ningún enlace está roto aunque un módulo no esté terminado.
2. Nadie crea archivos ajenos ni toca el `header` o el `footer` de otros.
3. Cada integrante solo rellena el `<main>` de sus pantallas.

Además, borra las 4 páginas de resultado que ya no existen en el mapa.

**Entregable de la Fase 0:** un PR `feature/base-estilos → develop` con `css/estilos.css` completo (tokens, base, layout, componentes, estados y 2 breakpoints) y las 34 pantallas del esqueleto, más una página interna de ejemplo totalmente maquetada (`propietarios-listado.html`) que sirva de referencia visual.

---

## 5. Cobertura obligatoria de controles HTML5

El enunciado exige que, en el conjunto del sitio, aparezcan todos estos tipos de control. Con este reparto quedan cubiertos así:

| Control | Dónde aparece (dueño) |
|---|---|
| `email` | `index` y `propietarios-nuevo`/`-editar` (I1); `veterinarios-nuevo`/`-editar` (I3) |
| `password` | `index` (I1) |
| `tel` | `propietarios-*` (I1); `veterinarios-*` (I3) |
| `date` | `mascotas-*` fecha de nacimiento, `citas-nueva` y `citas-editar` (I2); `agenda-dia` (I3) |
| `time` | `citas-disponibilidad` (I2) |
| `number` | `mascotas-*` peso (I2); `atencion-registrar` peso y `servicios-*` precio (I3) |
| `search` | todos los listados (I1, I2, I3) y `historial-clinico` (I3) |
| `radio` | `mascotas-*` sexo (I2) |
| `checkbox` | `mascotas-*` esterilizado (I2); `veterinarios-*` días de atención (I3) |
| `select` | `mascotas-*` especie y propietario, `citas-nueva` mascota, servicio y veterinario (I2) |
| `textarea` | `mascotas-*` observaciones y `citas-cancelar` motivo (I2); `atencion-registrar` (I3) |
| `datalist` | `mascotas-*` raza (I2) |

Atributos que deben verse en el conjunto: `required`, `pattern` + `title`, `min`, `max`, `step`, `minlength`, `maxlength`, `placeholder` y `autocomplete` (todos aparecen en las especificaciones de la sección 7).

---

## 6. Datos de ejemplo canónicos (usar exactamente estos)

La fecha de referencia es **miércoles 18/11/2026**. Si una pantalla muestra a Toby, siempre es de Carlos Andrade, pesa lo mismo, etc.

**Usuarios de demostración (login):** el placeholder es `nombre@correo.com`. Para probar sirve cualquier correo válido, por ejemplo `recepcion@correo.com`, `veterinario@correo.com` o `admin@correo.com`.

**Propietarios**

| Código | Nombres | Apellidos | Cédula | Celular | Correo | Mascotas |
|---|---|---|---|---|---|---|
| P-001 | Carlos Andrés | Andrade Ruiz | 1712345678 | 0991234567 | carlos.andrade@correo.com | Toby |
| P-002 | María Fernanda | López Vera | 1723456789 | 0987654321 | maria.lopez@correo.com | Michi, Luna |
| P-003 | Jorge Luis | Paredes Mena | 1734567890 | 0976543210 | jorge.paredes@correo.com | Kiwi |

**Mascotas**

| Código | Nombre | Especie | Raza | Sexo | Nacimiento | Peso | Esterilizado | Propietario |
|---|---|---|---|---|---|---|---|---|
| M-001 | Toby | Perro | Mestizo | Macho | 15/03/2021 | 12,5 kg | Sí | Carlos Andrade |
| M-002 | Michi | Gato | Siamés | Hembra | 02/07/2022 | 4,2 kg | Sí | María López |
| M-003 | Luna | Perro | Labrador | Hembra | 20/01/2020 | 28,0 kg | No | María López |
| M-004 | Kiwi | Ave | Loro amazona | Macho | 10/05/2024 | 0,4 kg | No | Jorge Paredes |

**Veterinarios**

| Código | Nombres | Apellidos | Celular | Correo | Días de atención |
|---|---|---|---|---|---|
| V-001 | Ana Lucía | Pérez Cevallos | 0991112233 | ana.perez@correo.com | Lunes a viernes |
| V-002 | Luis Alberto | Mora Salazar | 0992223344 | luis.mora@correo.com | Lunes, miércoles, viernes y sábado |
| V-003 | Sofía Elena | Vega Ríos | 0993334455 | sofia.vega@correo.com | Martes, jueves y sábado |

En listados se muestran como «Dra. Ana Pérez», «Dr. Luis Mora» y «Dra. Sofía Vega».

**Servicios**

| Código | Nombre | Precio |
|---|---|---|
| S-001 | Consulta general | $25,00 |
| S-002 | Vacunación | $18,00 |
| S-003 | Desparasitación | $12,00 |
| S-004 | Control postoperatorio | $20,00 |
| S-005 | Baño medicado | $15,00 |

**Citas**

| Código | Mascota | Servicio | Veterinario | Fecha | Hora | Estado |
|---|---|---|---|---|---|---|
| C-001 | Toby | Consulta general | Dra. Ana Pérez | 18/11/2026 | 09:00 | Programada |
| C-002 | Michi | Vacunación | Dra. Ana Pérez | 18/11/2026 | 10:30 | Programada |
| C-003 | Luna | Desparasitación | Dr. Luis Mora | 18/11/2026 | 11:00 | Programada |
| C-004 | Toby | Vacunación | Dra. Ana Pérez | 12/11/2026 | 09:30 | Atendida |
| C-005 | Kiwi | Consulta general | Dra. Sofía Vega | 19/11/2026 | 15:00 | Cancelada (motivo: «El propietario solicitó cancelar») |

**Escenarios fijos**
- **Agenda (CU-06):** el veterinario de referencia es la Dra. Ana Pérez. El 18/11/2026 tiene C-001 (09:00) y C-002 (10:30). El sábado 21/11/2026 sirve como ejemplo de «No hay citas programadas para esta fecha».
- **Disponibilidad (CU-11):** Dra. Ana Pérez el 18/11/2026, con bloques de 30 min de 08:00 a 17:30 (20 bloques). Están ocupados 09:00 y 10:30; los demás están libres. Ejemplo «Sin bloques libres»: Dr. Luis Mora, sábado 21/11/2026.
- **Historial de Toby (CU-08):**
  - A-001, 20/05/2026: «Otitis externa leve», «Gotas óticas cada 12 h por 7 días», 11,8 kg.
  - A-002, 12/11/2026: «Paciente sano, apto para vacunación», «Vacuna antirrábica; refuerzo en un año», 12,3 kg.
  - A-003, 18/11/2026: «Control de rutina», «Control en seis meses», 12,5 kg. Es la atención que se acaba de registrar desde `atencion-registrar`.
  - Michi no tiene atenciones previas y sirve como ejemplo del flujo 4a.

---

## 7. Tareas por integrante

Para cada pantalla se indican:
- las **filas del Anexo A** (mapa 3.5) que deben existir como enlace o botón en ella. El texto del enlace es el evento y el destino es la columna «Destino»;
- los **campos** con los atributos de la especificación 3.2;
- el **escenario estático** que hay que mostrar.

Además, todas las pantallas internas llevan «Menú» y «Cerrar sesión» en el `header`; eso ya viene del esqueleto.

### 7.1 Integrante 1 · Oscar: base, acceso, menús y propietarios

**Fase 0 completa (sección 4)**, más:

| Pantalla | Filas del Anexo A | Contenido y validaciones |
|---|---|---|
| `index.html` | 2, 3, 4, 5 | Sin «Menú» ni «Cerrar sesión». Lleva `fieldset` «Datos de acceso» con correo (`type="email" required placeholder="nombre@correo.com" autocomplete="email"`) y contraseña (`type="password" required autocomplete="current-password"`), y `fieldset` «Ingresar según tu rol» con 3 `button type="submit"`, cada uno con su `formaction`: «Ingresar como recepcionista», «Ingresar como veterinario» e «Ingresar como administrador». Puede llevar una imagen de `img/`. |
| `menu-recepcion.html` | 6, 9, 10, 11, 12 | `nav.menu-tarjetas` con «Propietarios», «Mascotas», «Citas» y «Agendar cita» (→ `citas-nueva.html`). En el header solo «Cerrar sesión». |
| `menu-veterinario.html` | 7, 76, 77 | Tarjetas «Agenda» e «Historial clínico». |
| `menu-administrador.html` | 8, 89, 90 | Tarjetas «Veterinarios» y «Servicios». |
| `propietarios-listado.html` | 13, 16, 17, 21, 23, 28, 31 | Buscador con `placeholder="Buscar propietario"`, tabla con P-001 a P-003 y «Nuevo propietario». Enlace **«Retomar nueva mascota»** (→ `mascotas-nueva.html`) en un `aside` o un `.aviso--info` que explique que sirve para continuar el registro de una mascota. Aviso «sin coincidencias» (3a.2a). |
| `propietarios-nuevo.html` | 18, 19, 20 | Cédula: `type="text" required minlength="10" maxlength="10" pattern="[0-9]{10}" placeholder="1712345678" autocomplete="off"` + `title`. Nombres y apellidos: `required minlength="2" maxlength="50" pattern="[A-Za-zÁÉÍÓÚáéíóúÑñÜü ]{2,50}"` + `title`, con `autocomplete="given-name"` / `"family-name"`. Celular: `type="tel" required pattern="09[0-9]{8}" minlength="10" maxlength="10" placeholder="0991234567" autocomplete="tel"` + `title`. Correo: `type="email" required placeholder="nombre@correo.com" autocomplete="email"`. «Guardar» → listado; «Cancelar» → listado. |
| `propietarios-detalle.html` | 22, 24 | `article` + `.ficha` de P-001 con sus mascotas. «Volver» y «Editar». |
| `propietarios-editar.html` | 25, 26, 27 | El mismo formulario precargado con P-001. |
| `propietarios-eliminar.html` | 29, 30 | Ficha de P-003 con «Confirmar» y «Cancelar». |

**Cierre (Fase 3):** `README.md` (proyecto, integrantes, enlace a Pages, tabla de reparto), GitHub Pages, actualización del doc 3.4 y QA final.

### 7.2 Integrante 2: mascotas y citas (CU-03, CU-04, CU-05, CU-11)

| Pantalla | Filas del Anexo A | Contenido y validaciones |
|---|---|---|
| `mascotas-listado.html` | 14, 32, 33, 38, 40, 45, 48, 49 | Buscador con `placeholder="Buscar mascota"` y tabla con M-001 a M-004 (incluye la columna Propietario). En cada fila: «Ver detalle», «Editar», «Eliminar» y **«Seleccionar mascota»** (→ `citas-nueva.html`). En la barra: «Nueva mascota» y **«Retomar nueva cita»** (→ `citas-nueva.html`). Aviso «sin coincidencias». |
| `mascotas-nueva.html` | 34, 35, 36, 37 | Nombre: `required minlength="2" maxlength="40" placeholder="Toby"`. Especie: `select required` con Perro, Gato, Ave, Roedor y Otro (más una primera opción vacía «Selecciona…» con `value=""`). Raza: `text` + `list` → `datalist` de razas. Sexo: `fieldset` con `radio` Macho/Hembra, mismo `name` y `required`. Fecha de nacimiento: `type="date" max="2026-11-18"`. Peso: `type="number" min="0.1" max="120" step="0.1"`. Propietario: `select required`. Esterilizado: `checkbox`. Observaciones: `textarea maxlength="300"`. Enlace **«Registrar propietario»** (→ `propietarios-nuevo.html`) junto al select de propietario. «Guardar» → listado; «Cancelar» → listado. |
| `mascotas-detalle.html` | 39, 41 | Ficha de Toby con los datos de su propietario. «Volver» y «Editar». |
| `mascotas-editar.html` | 42, 43, 44 | El mismo formulario precargado con Toby (`selected` y `checked`). |
| `mascotas-eliminar.html` | 46, 47 | Ficha de Kiwi con «Confirmar» y «Cancelar». |
| `citas-listado.html` | 15, 50, 51, 60, 62, 67, 72 | Buscador con `placeholder="Buscar cita"`, tabla con C-001 a C-005 y `.estado[data-estado]`. «Reprogramar cita» y «Cancelar cita» **solo en las filas Programadas** (flujo 5d). «Ver detalle» y «Eliminar» en todas. «Nueva cita» en la barra. Aviso «sin coincidencias». |
| `citas-nueva.html` | 52, 53, 54, 55 | Mascota, servicio y veterinario: `select required`. Fecha: `type="date" required min="2026-11-18"`. **«Identificar mascota»** (→ `mascotas-listado.html`). Botón submit **«Consultar disponibilidad»** con `action="citas-disponibilidad.html"`. «Cancelar» → `citas-listado.html`. **No tiene «Guardar».** |
| `citas-disponibilidad.html` | 56, 57, 58, 59 | Resumen de la consulta (Dra. Ana Pérez, 18/11/2026). Tabla de 20 bloques de 08:00 a 17:30 con estado Libre u Ocupado (informativa, sin selector). `section.aviso` con el ejemplo **«Sin bloques libres»**. Formulario con Hora: `type="time" required min="08:00" max="17:30" step="1800"` y «Guardar» → `citas-listado.html`. Siempre muestra **«Volver a nueva cita»** y **«Volver a edición»**, con un `aside.nota-demo` que explica por qué hay dos enlaces. |
| `citas-detalle.html` | 61, 63, 68, 73 | Ficha de C-001. «Volver», «Reprogramar cita», «Cancelar cita» y «Eliminar». |
| `citas-editar.html` | 64, 65, 66 | Ficha de C-001. El veterinario se muestra pero no se edita (se conserva). Fecha: `type="date" required min="2026-11-18" value="2026-11-18"`. Botón **«Consultar disponibilidad»** → `citas-disponibilidad.html`. «Cancelar» → listado. **No guarda aquí.** |
| `citas-cancelar.html` | 69, 70, 71 | Ficha de C-001. Motivo: `textarea required maxlength="200"` con `.ayuda`. Botón **«Confirmar»** → listado; enlace **«Volver»** → listado. Hay que corregir la versión anterior, que decía «Guardar» y «Volver al listado». |
| `citas-eliminar.html` | 74, 75 | Ficha de C-005 con «Confirmar» y «Cancelar». |

### 7.3 Integrante 3: veterinario y administración (CU-06 a CU-10)

| Pantalla | Filas del Anexo A | Contenido y validaciones |
|---|---|---|
| `agenda-dia.html` | 78, 79, 80, 81, 82 | Formulario con Fecha (`type="date" required`, **sin `min`**) y «Consultar» (`action="agenda-dia.html#resultado"`). `section#resultado` con la tabla de citas Programadas de la Dra. Ana Pérez ordenadas por hora. En cada fila, **«Registrar atención»** (→ `atencion-registrar.html`) y **«Ver historial»** (→ `historial-clinico.html`). `.aviso` con «No hay citas programadas para esta fecha» (ejemplo del 21/11/2026). |
| `atencion-registrar.html` | 83, 84, 85 | Ficha de C-001. Diagnóstico y tratamiento: `textarea required`. Peso: `type="number" required min="0.1" max="120" step="0.1"`. `aside.nota-demo` con los valores de ejemplo. «Guardar» → **`historial-clinico.html`** (no a una página de confirmación); «Cancelar» → `agenda-dia.html`. |
| `historial-clinico.html` | 86, 87, 88 | Todo ocurre en una sola página. Buscador con `placeholder="Buscar mascota"` y `action="historial-clinico.html#mascotas"`. Lista de mascotas. Atenciones de Toby (A-001 a A-003) con **«Ver detalle»** → `#atencion-1`, `#atencion-2`, `#atencion-3`; cada detalle es un `article id="atencion-N"` resaltado con `:target`, o bien `<details>/<summary>`. Avisos: Michi «aún no tiene historial» (4a) y «sin coincidencias» (3a). Botón **«Volver»** → `menu-veterinario.html`. |
| `veterinarios-listado.html` | 91, 93, 94, 98, 100, 105 | Buscador con `placeholder="Buscar veterinario"` y tabla con V-001 a V-003 y sus días. «Nuevo veterinario». Aviso «sin coincidencias». |
| `veterinarios-nuevo.html` | 95, 96, 97 | Nombres y apellidos: `required minlength="2" maxlength="50" pattern="[A-Za-zÁÉÍÓÚáéíóúÑñÜü ]{2,50}"` + `title`. Celular: `type="tel" required pattern="09[0-9]{8}" minlength="10" maxlength="10" placeholder="0991234567"` + `title`. Correo: `type="email" required placeholder="nombre@correo.com"`. `fieldset` «Días habituales de atención» con 6 `checkbox` (lunes a sábado). |
| `veterinarios-detalle.html` | 99, 101 | Ficha de V-001. «Volver» y «Editar». |
| `veterinarios-editar.html` | 102, 103, 104 | El mismo formulario precargado con V-001 (`checked` en sus días). |
| `veterinarios-eliminar.html` | 106, 107 | Ficha de V-003 con «Confirmar» y «Cancelar». |
| `servicios-listado.html` | 92, 108, 109, 113, 115, 120 | Buscador con `placeholder="Buscar servicio"` y tabla con S-001 a S-005 y sus precios. «Nuevo servicio». Aviso «sin coincidencias». |
| `servicios-nuevo.html` | 110, 111, 112 | Nombre: `type="text" required placeholder="Consulta general"`. Precio: `type="number" required min="1" max="500" step="0.01"`. `.aviso--error` de ejemplo: «Ya existe un servicio llamado “Vacunación”» (RN-09, flujo 7b). |
| `servicios-detalle.html` | 114, 116 | Ficha de S-001. «Volver» y «Editar». |
| `servicios-editar.html` | 117, 118, 119 | El mismo formulario precargado con S-001. |
| `servicios-eliminar.html` | 121, 122 | Ficha de S-005 con «Confirmar» y «Cancelar». |

---

## 8. GitHub: ramas y reglas para evitar conflictos

### 8.1 Ramas

```
main ─────────────────────────────────────────●  (entrega, GitHub Pages)
  └─ develop ──●──────●──────●──────●──────●──┘  (integración)
               ↑      ↑      ↑      ↑      ↑
   feature/base-estilos (I1)  │      │      │
           feature/acceso-menus (I1) │      │
           feature/propietarios (I1) │      │
                  feature/mascotas (I2)     │
                  feature/citas (I2)        │
                       feature/veterinario (I3)
                       feature/veterinarios (I3)
                       feature/servicios (I3)
```

| Rama | Propósito | Quién |
|---|---|---|
| `main` | Versión entregable. GitHub Pages publica desde `main` / raíz. Protegida: solo recibe el merge final de `develop`. | Integrante 1 (merge final) |
| `develop` | Integración. Solo recibe Pull Requests revisados. | Todos, vía PR |
| `feature/base-estilos` | CSS, plantilla, esqueleto de las 34 y borrado de las páginas de resultado | I1 |
| `feature/acceso-menus` | `index` y los 3 menús | I1 |
| `feature/propietarios` | CU-02 | I1 |
| `feature/mascotas` | CU-03 | I2 |
| `feature/citas` | CU-04, CU-05 y CU-11 | I2 |
| `feature/veterinario` | CU-06, CU-07 y CU-08 | I3 |
| `feature/veterinarios` | CU-09 | I3 |
| `feature/servicios` | CU-10 | I3 |
| `fix/<descripcion>` | Corrección puntual durante el QA | El dueño del archivo |

**Configuración (Integrante 1):** crear `develop` desde `main`. En *Settings → Branches* proteger `main` y `develop` (exigir PR y 1 aprobación). Agregar a los otros dos como colaboradores.

### 8.2 Reglas anti-conflicto

1. **Un archivo = un dueño** (tabla de la sección 3). Nadie edita archivos ajenos. Si ves un error en una pantalla de otro, abre un Issue y asígnaselo.
2. `css/estilos.css`, `README.md`, `index.html` y los menús **solo los toca el Integrante 1**. Para un componente nuevo, abre un Issue «Solicitud CSS: …»; el Integrante 1 lo agrega en una rama `feature/base-ajustes` y avisa cuando esté en `develop`.
3. Nadie toca el `header`, el `footer` ni el `<head>` del esqueleto: solo se trabaja dentro de `<main>`.
4. Antes de abrir un PR, actualiza tu rama con `develop` (ver comandos). Si hubo conflicto, solo puede estar en tus archivos.
5. PR pequeños, uno por módulo, con al menos 1 revisión de otro integrante. Quien revisa comprueba los enlaces contra el Anexo A y el validador W3C.
6. Commits en español, con el CU como prefijo y **desde tu propia cuenta** (la rúbrica revisa el aporte de cada uno):
   - `CU-03: agrega formulario mascotas-nueva con validaciones`
   - `CU-05: corrige texto Confirmar en citas-cancelar`
   - `BASE: agrega componente .aviso--info`

### 8.3 Comandos (para cada integrante)

```bash
# Una sola vez
git clone https://github.com/<usuario>/Proyecto-Aplicaciones-Web---VetCare.git
cd Proyecto-Aplicaciones-Web---VetCare
git config user.name "Tu Nombre"
git config user.email "tu-correo-de-github"

# Empezar un módulo (siempre desde develop actualizado)
git switch develop
git pull origin develop
git switch -c feature/mascotas

# Trabajar y guardar avances
git add pages/mascotas-listado.html
git commit -m "CU-03: agrega listado de mascotas con buscador"
git push -u origin feature/mascotas

# Antes de abrir el PR: traer lo último de develop
git fetch origin
git merge origin/develop          # resolver conflictos (solo deberían estar en tus archivos)
git push

# Abrir PR en GitHub: base = develop, compare = feature/mascotas
# Después de que lo fusionen:
git switch develop
git pull origin develop
git switch -c feature/citas       # siguiente módulo
```

---

## 9. Cronograma

| Fase | Cuándo | Integrante 1 | Integrante 2 | Integrante 3 |
|---|---|---|---|---|
| **0 · Base** | 17/11, primeras horas | Tokens, CSS, plantilla, esqueleto de las 34, borrar las páginas de resultado y PR a `develop` | Leer CU-03, 04, 05 y 11 y redactar en borrador (fuera del repo) el contenido de tablas y formularios con los datos de la sección 6 | Leer CU-06 a CU-10 y hacer lo mismo |
| **1 · Módulos** | 17/11 tarde → 18/11 mediodía | `feature/acceso-menus` y `feature/propietarios`; atender las «Solicitudes CSS» | `feature/mascotas` y `feature/citas` | `feature/veterinario`, `feature/veterinarios` y `feature/servicios` |
| **2 · Integración y QA** | 18/11 tarde | Coordina: recorrer el Anexo A fila por fila (1–122) | QA de las pantallas de I3 | QA de las pantallas de I1 |
| **3 · Entrega** | 18/11, antes de las 21:00 | Merge `develop → main`, GitHub Pages, README con el enlace, doc 3.4 actualizado y PDF en `docs/` | Revisar el sitio publicado | Revisar el sitio publicado |

Se deja margen de unas 3 horas antes de las 23:59 por si Pages tarda o aparece algún error del validador.

---

## 10. Checklist final (según la rúbrica, criterios 5 a 9)

**Mapa ↔ sitio (criterio 5)**
- [ ] Existen exactamente las 34 pantallas del mapa, con el mismo nombre de archivo; ninguna página extra.
- [ ] Las 122 transiciones del Anexo A existen con el texto exacto del evento y el destino correcto.

**HTML5 y navegación (criterio 6)**
- [ ] Todas las pantallas usan la plantilla común (`header` / `nav` / `main` / `footer`), con `section`, `article` y `aside` donde corresponde.
- [ ] Todas las tablas tienen `caption`, `thead`, `tbody` y `th scope`.
- [ ] No hay enlaces rotos (revisar también `../index.html` y `../css/`).

**Formularios (criterio 7)**
- [ ] Están los 12 tipos de control de la sección 5.
- [ ] Cada control tiene `label for` y los grupos usan `fieldset` + `legend`.
- [ ] Cada `pattern` tiene `title`; no hay `novalidate`.
- [ ] Las validaciones coinciden con RN-01 a RN-09 y con los atributos de la 3.2.

**CSS (criterio 8)**
- [ ] Una hoja externa en `css/`; ningún `style=""`.
- [ ] Variables en `:root`, Flexbox y Grid, y 2 breakpoints (`40rem`, `64rem`).
- [ ] Pseudoclases `:valid`, `:invalid`/`:user-invalid`, `:focus-visible`, `:required`, `:hover` y `:active`.
- [ ] Selector de atributo (`[data-estado]`), `:nth-child()` en tablas, `transition` y fuente web.
- [ ] Contraste AA.

**Publicación (criterio 9)**
- [ ] Validador HTML W3C sin errores en las 34 pantallas.
- [ ] Validador CSS sin errores.
- [ ] Probado en Chrome y Firefox: se ve y valida igual.
- [ ] Probado en móvil (DevTools a 375 px) y escritorio.
- [ ] GitHub Pages publicado; el enlace funciona.
- [ ] `README.md` completo y commits de los 3 integrantes en el historial.
- [ ] Doc 3.4 actualizado con los nuevos responsables y PDF de los entregables 3.1–3.5 en `docs/`.
