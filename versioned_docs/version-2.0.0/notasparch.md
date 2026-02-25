---
sidebar_position: 1
---
# 📝 Notas del Parche 2.0.0
## 🚀 Versión 2.0.0 – Refactorización y carga dinámica de datos

En esta versión se realiza una **refactorización estructural del proyecto**, modificando la forma en que se consultan y presentan los datos en la aplicación.

### 🔹 Cambios principales
#### ✔ 1. Nuevo `MantenedorController`

- Se crea el controlador `MantenedorController`.

- Se traslada la lógica de consulta de datos desde `HomeController`.

- Se implementa el método `Listar()` que devuelve los datos en formato **JSON**.

- La información ahora es consumida mediante AJAX.

#### ✔ 2. Simplificación del `HomeController`

Se elimina la lógica de acceso a base de datos.

El controlador queda únicamente para navegación (`Index` y `Privacy`).

Se mejora la separación de responsabilidades.

#### ✔ 3. Actualización de la Vista `Index`

- Se elimina el renderizado con `foreach`.

- Se implementa **DataTables** con carga dinámica vía AJAX.

- Se mejora la experiencia de usuario con:

  - Paginación

  - Búsqueda

  - Ordenamiento automático

  - Internacionalización en español

#### ✔ 4. Corrección del `_Layout.cshtml`

- Se elimina el uso de `asp-page`.

- Se estandariza la navegación usando `asp-controller` y `asp-action`.

- Se corrige el comportamiento de redirección.

### 🎯 Impacto del cambio

Este parche introduce un cambio significativo en la arquitectura del proyecto:

- Mejora la organización del código.

- Prepara el sistema para futuras operaciones CRUD.

- Permite escalabilidad.

- Mejora rendimiento y mantenimiento.

### 🔢 Motivo del cambio de versión

Se incrementa la versión a **2.0.0** porque:

- Se modifica la arquitectura de consumo de datos.

- Se cambia la forma en que la vista obtiene la información.

- Se introduce un nuevo controlador estructural.

Siguiendo versionado semántico (SemVer):

- Cambio mayor → Refactorización estructural.