---
sidebar_position: 6
---
:::tip Nuevo
Se realizaron modificaciones en el archivo `_Layout.cshtml` para mejorar la navegación
y agregar acceso directo a la documentación del proyecto.
:::
 # Layout
 :::info Cambios en navegación
- Se reemplazaron enlaces tipo `asp-page` por `asp-controller` y `asp-action`.
- Se agregó un nuevo botón **Documentación** en el menú principal.
- Se mantiene la estructura base con Bootstrap.
:::

## Actualización del Layout
Antes se utilizaban rutas tipo Razor Pages:

```HTML
<a class="navbar-brand" asp-area="" asp-page="/Index">MostrarEma</a>
```
Ahora se utilizan rutas basadas en controladores:
```HTML
<a class="nav-link text-dark" asp-controller="Home" asp-action="Index">Home</a>
<a class="nav-link text-dark" asp-controller="Home" asp-action="Privacy">Privacy</a>
```
Esto adapta la navegación al patrón MVC basado en controladores.

## Nuevo botón de documentación

Se agregó un enlace externo hacia la documentación del proyecto:
```HTML
<a class="nav-link text-dark"
   href="https://reinaldoocgn.github.io/DocuPrueba/"
   target="_blank"
   rel="noopener noreferrer">
   Documentación
</a>
```
- Este botón permite acceder directamente a la documentación técnica
- Se abre en una nueva pestaña por seguridad y mejor experiencia de usuario

