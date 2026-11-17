# Informe de trabajo: Integrante 2

**Proyecto:** Proyecto de Aplicaciones Web — VetCare  
**Responsabilidad:** Mascotas y citas  
**Casos de uso:** CU-03, CU-04, CU-05 y CU-11  
**Fecha:** 17 de noviembre de 2026  
**Rama de integración:** `develop`

## 1. Resumen

Se completaron las doce pantallas asignadas al Integrante 2 usando la plantilla común y los estilos compartidos del proyecto. Los cambios se trabajaron en dos ramas, se publicaron en GitHub y se integraron a `develop` mediante los Pull Requests #2 y #3.

Después de integrar los Pull Requests, la copia local quedó en `develop`, sincronizada con `origin/develop` y sin cambios pendientes. Este informe se creó después de esa sincronización.

## 2. Trabajo realizado

### CU-03: Mascotas

Se completaron las cinco pantallas siguientes:

- `pages/mascotas-listado.html`: tabla con M-001 a M-004, propietarios, acciones por fila, buscador, acceso a **Nueva mascota** y enlace **Retomar nueva cita**.
- `pages/mascotas-nueva.html`: formulario con nombre, especie, raza, sexo, fecha de nacimiento, peso, propietario, esterilización y observaciones. Incluye el enlace **Registrar propietario**.
- `pages/mascotas-detalle.html`: ficha de Toby (M-001), con los datos de su propietario P-001.
- `pages/mascotas-editar.html`: formulario de Toby precargado, con especie, sexo, propietario y esterilización seleccionados.
- `pages/mascotas-eliminar.html`: confirmación para Kiwi (M-004), con las acciones **Confirmar** y **Cancelar**.

Los listados y formularios usan los datos de ejemplo definidos en el plan: Toby, Michi, Luna y Kiwi, con sus propietarios correspondientes.

### CU-04, CU-05 y CU-11: Citas

Se completaron las siete pantallas siguientes:

- `pages/citas-listado.html`: tabla con C-001 a C-005, estados **Programada**, **Atendida** y **Cancelada**, buscador, enlace **Nueva cita** y acciones según el estado de cada cita.
- `pages/citas-nueva.html`: selección obligatoria de mascota, servicio, veterinario y fecha; enlaza a **Identificar mascota** y permite consultar disponibilidad.
- `pages/citas-disponibilidad.html`: resumen de la consulta de ejemplo, tabla con veinte bloques de treinta minutos entre 08:00 y 17:30, selección de hora y enlaces para volver al formulario de nueva cita o de edición.
- `pages/citas-detalle.html`: ficha de la cita C-001 y enlaces para volver, reprogramar, cancelar o eliminar.
- `pages/citas-editar.html`: datos de C-001 y formulario para consultar otra fecha, manteniendo el veterinario asignado.
- `pages/citas-cancelar.html`: resumen de C-001 y campo obligatorio para el motivo de cancelación, con máximo de 200 caracteres.
- `pages/citas-eliminar.html`: confirmación para la cita C-005, incluido su motivo de cancelación.

En la disponibilidad de ejemplo, los bloques de 09:00 y 10:30 aparecen ocupados por C-001 y C-002; los otros bloques se muestran libres. También se incluyó el escenario de demostración **Sin bloques libres**.

## 3. Validaciones y navegación

Los formularios usan validación nativa de HTML:

- Mascotas: nombre obligatorio de 2 a 40 caracteres; especie, sexo y propietario obligatorios; fecha de nacimiento con límite máximo 18/11/2026; peso entre 0,1 y 120 kg, en pasos de 0,1; observaciones de hasta 300 caracteres.
- Nueva cita: mascota, servicio, veterinario y fecha obligatorios; la fecha mínima es 18/11/2026.
- Disponibilidad: hora obligatoria entre 08:00 y 17:30, en pasos de 30 minutos.
- Cancelación: motivo obligatorio de hasta 200 caracteres.

Se enlazaron las pantallas internas de mascotas y citas, incluido el paso de mascotas al registro de citas y el acceso al registro de propietarios.

## 4. Revisión manual

Se abrieron las pantallas en el navegador mediante Live Server y se revisaron visualmente los formularios, tablas y fichas. Las capturas compartidas muestran la validación del navegador al intentar avanzar con campos obligatorios vacíos en los formularios de nueva mascota y nueva cita, y muestran la llegada a la pantalla de disponibilidad.

No se ejecutaron pruebas automatizadas ni validadores externos. Como revisión manual adicional, conviene probar el envío vacío del motivo de cancelación y los límites de fecha y hora, además de recorrer los enlaces entre todas las pantallas.

## 5. Alcance estático

Estas pantallas son una maqueta HTML5/CSS3. Los formularios sirven para mostrar campos, validaciones y navegación entre páginas, pero no guardan datos ni actualizan los registros. Los buscadores tampoco filtran la tabla. Por eso, al guardar una mascota o cita, el listado vuelve a mostrar los registros fijos de ejemplo. La persistencia requeriría una función de almacenamiento, JavaScript o un backend, fuera del alcance HTML/CSS definido en el plan.

## 6. Ramas, commits e integración

El trabajo se separó por módulo, como indica el plan:

| Rama | Commit | Pull Request | Resultado |
|---|---|---|---|
| `feature/mascotas` | `38cbceb` — `CU-03: implementa pantallas de mascotas` | #2 | Fusionado en `develop` |
| `feature/citas` | `2d8a5c3` — `CU-04, CU-05 y CU-11: implementa pantallas de citas` | #3 | Fusionado en `develop` |

Los commits de integración visibles en `develop` son `6311bb2` (PR #2) y `6b34a84` (PR #3). Después de la fusión, se actualizó la copia local con `git pull origin develop`; el estado quedó sincronizado con `origin/develop`.

Antes de actualizar el repositorio, los cambios locales previos sin commit se guardaron en `stash@{0}` con el mensaje `mis cambios locales antes de actualizar`. Esos cambios no forman parte de los Pull Requests de Integrante 2 y permanecen respaldados en el stash. Este informe es documentación adicional y no está incluido en los PR #2 ni #3.

## 7. Archivos del módulo

Los doce archivos HTML modificados son:

```text
pages/mascotas-listado.html
pages/mascotas-nueva.html
pages/mascotas-detalle.html
pages/mascotas-editar.html
pages/mascotas-eliminar.html
pages/citas-listado.html
pages/citas-nueva.html
pages/citas-disponibilidad.html
pages/citas-detalle.html
pages/citas-editar.html
pages/citas-cancelar.html
pages/citas-eliminar.html
```

No se modificó `css/estilos.css`, que en el plan corresponde al Integrante 1; las pantallas reutilizan las clases y estilos compartidos existentes.
