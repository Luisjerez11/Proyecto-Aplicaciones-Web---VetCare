# Informe de trabajo: Integrante 3

**Proyecto:** Proyecto de Aplicaciones Web — VetCare  
**Responsabilidad:** Veterinario y Administración  
**Casos de uso:** CU-06, CU-07, CU-08, CU-09 y CU-10  
**Fecha:** 17 de noviembre de 2026  
**Rama de trabajo:** `develop` (cambios locales pendientes de commit)

## 1. Resumen

Se completaron las trece pantallas asignadas al Integrante 3, siguiendo la plantilla común, el catálogo CSS existente, el plan de implementación y los datos de ejemplo definidos para VetCare. Las páginas cubren la agenda, el registro de atención, el historial clínico y las operaciones CRUD de veterinarios y servicios.

Los cambios permanecen en la copia local del repositorio. Todavía no se han creado un commit ni un Pull Request, ni se han subido a GitHub.

## 2. Trabajo realizado

### CU-06, CU-07 y CU-08: Veterinario

- `pages/agenda-dia.html`: formulario de consulta por fecha, agenda de ejemplo de la Dra. Ana Pérez para el 18/11/2026, enlaces para registrar atención y consultar historial, y aviso de día sin citas para el 21/11/2026.
- `pages/atencion-registrar.html`: ficha de la cita C-001 de Toby, campos obligatorios para diagnóstico y tratamiento, peso con límites de 0,1 a 120 kg y paso de 0,1; guardar conduce al historial y cancelar vuelve a la agenda.
- `pages/historial-clinico.html`: buscador de mascotas, listado de las cuatro mascotas canónicas, historial de Toby con A-001 a A-003, detalle de cada atención mediante anclas y aviso de que Michi aún no tiene historial.

### CU-09: Veterinarios

- `pages/veterinarios-listado.html`: buscador, tabla accesible con V-001 a V-003, días habituales de atención y accesos a detalle, edición y eliminación.
- `pages/veterinarios-nuevo.html`: formulario de alta con validaciones de nombres, apellidos, celular y correo, además de las seis casillas de días de atención.
- `pages/veterinarios-detalle.html`: ficha de V-001, con volver y editar.
- `pages/veterinarios-editar.html`: formulario precargado con los datos de V-001 y sus días habituales seleccionados.
- `pages/veterinarios-eliminar.html`: confirmación de eliminación de V-003 con las acciones Confirmar y Cancelar.

### CU-10: Servicios

- `pages/servicios-listado.html`: buscador, tabla accesible con S-001 a S-005 y sus precios, y accesos a detalle, edición y eliminación.
- `pages/servicios-nuevo.html`: formulario con nombre obligatorio y precio entre $1,00 y $500,00, con paso de $0,01; incluye el ejemplo estático de nombre duplicado.
- `pages/servicios-detalle.html`: ficha de S-001 con volver y editar.
- `pages/servicios-editar.html`: formulario precargado con Consulta general y $25,00.
- `pages/servicios-eliminar.html`: confirmación de eliminación de S-005 con las acciones Confirmar y Cancelar.

## 3. Revisión de estructura, formularios y navegación

Se realizó una revisión estructural local de las trece páginas. El recorrido automático comprobó:

- La estructura común con `header`, `nav`, `main` y `footer`, y un solo `h1` por página.
- `id`, `name` y etiqueta asociada para cada control; `title` en cada campo que usa `pattern`.
- Tablas con `caption`, `thead`, `tbody` y atributos `scope` válidos.
- Destinos locales existentes, incluidas las anclas del historial clínico.
- Ausencia de atributos `style`, scripts y `novalidate`.

**Resultado:** 13 páginas revisadas y 0 hallazgos en esas comprobaciones. Este recorrido no sustituye el validador W3C de HTML ni una prueba visual en Chrome y Firefox; esas revisiones todavía están pendientes.

## 4. Alcance estático

Las pantallas son un prototipo HTML5/CSS3 sin JavaScript ni backend. Los formularios validan los datos que permiten validar los controles nativos y navegan a los destinos del mapa, pero no guardan registros ni actualizan las tablas. El historial muestra A-003 como dato de ejemplo; guardar una atención no la crea ni cambia C-001 a Atendida. De igual forma, el nombre duplicado de un servicio se presenta como escenario de demostración y no se comprueba dinámicamente.

## 5. Revisión del estado del proyecto

Los archivos asignados a Integrante 3 ya no conservan los avisos de «Pantalla en construcción». En la revisión general del repositorio quedaron identificadas cuatro páginas de propietarios con esos avisos: `propietarios-nuevo.html`, `propietarios-detalle.html`, `propietarios-editar.html` y `propietarios-eliminar.html`. Pertenecen al Integrante 1 y no forman parte de este módulo.

## 6. Archivos del módulo

```text
pages/agenda-dia.html
pages/atencion-registrar.html
pages/historial-clinico.html
pages/veterinarios-listado.html
pages/veterinarios-nuevo.html
pages/veterinarios-detalle.html
pages/veterinarios-editar.html
pages/veterinarios-eliminar.html
pages/servicios-listado.html
pages/servicios-nuevo.html
pages/servicios-detalle.html
pages/servicios-editar.html
pages/servicios-eliminar.html
```
