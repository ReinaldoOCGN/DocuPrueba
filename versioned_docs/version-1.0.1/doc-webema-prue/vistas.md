---
sidebar_position: 6
---

# Vistas

Para acceder a la vista, desde el controlador se debe seleccionar el método `Index`, hacer clic derecho y elegir:

* Ir a la vista (si ya existe), o

- Agregar vista (si aún no ha sido creada).

La vista `Index.cshtml` es la encargada de mostrar los datos en una tabla HTML.

```html tittle="Index.cshtml"
@{
    ViewData["Title"] = "Index";
    Layout = "~/Pages/Shared/_Layout.cshtml";
}


<div class="card">
    <div class="card-header">
        Mostrar Datos
    </div>
</div>
<div class="card-body">
    <div class="card">
        <div class="card-header">
            Mostrar Datos
        </div>
    </div>
    <div class="card-body">
        <a asp-action="index" asp-asp-controller="Home" class="btn btn-success">Refrezcar </a>
        <hr />
        <table class="table table-bordered" id="EmaUsuarios">
            <thead>
                <tr>
                    <th>UsuTipIde</th>
                    <th>UsuIde</th>
                    <th>UsuClave</th>
                    <th>UsuTempClave</th>
                    <th>UsuTerminos</th>
                    <th>UsuAuten</th>
                    <th>UsuFecAut</th>
                    <th>UsuAsegurador</th>
                    <th>UsuRegimen</th>
                    <th>UsuPoblacion</th>
                </tr>
            </thead>
            <tbody>
                @foreach (var item in Model)
                {
                    <tr>
                        <td>@item.UsuTipIde</td>
                        <td>@item.UsuIde</td>
                        <td>@item.UsuClave</td>
                        <td>@item.UsuTempClave</td>
                        <td>@item.UsuTerminos</td>
                        <td>@item.UsuAuten</td>
                        <td>@item.UsuFecAut</td>
                        <td>@item.UsuAsegurador</td>
                        <td>@item.UsuRegimen</td>
                        <td>@item.UsuPoblacion</td>
                    </tr>
                }
            </tbody>
        </table>
    </div>
```
Esta vista recorre el modelo recibido desde el controlador y muestra los datos en una tabla estructurada para que el usuario pueda visualizarlos correctamente.