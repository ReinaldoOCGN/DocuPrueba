---
sidebar_position: 7

---

# Vistas

Para acceder a la vista, desde el controlador se debe seleccionar el método `Index`, hacer clic derecho y elegir:

* Ir a la vista (si ya existe), o

- Agregar vista (si aún no ha sido creada).

La vista `Index.cshtml` es la encargada de mostrar los datos en una tabla HTML.

:::info Vista actualizada
La vista `Index.cshtml` fue refactorizada.  
Ahora los datos no se reciben directamente desde el modelo enviado por el controlador,
sino que se cargan dinámicamente mediante una petición AJAX al `MantenedorController`
usando DataTables.
:::

```html tittle="Index.cshtml"
@{
    ViewData["Title"] = "Index";
    Layout = "~/Pages/Shared/_Layout.cshtml";
}
@section Estilos {
    <link href="https://cdn.datatables.net/2.3.7/css/dataTables.dataTables.css" rel="stylesheet" />
}
<div class="card">
    <div class="card-header">
        Mostrar Datos
    </div>
    <div class="card-body">
        <hr />
        <table id="ema" class="display">
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

            </tbody>
        </table>
    </div>
</div>
@section Scripts {
    <script src="https://cdn.datatables.net/2.3.7/js/dataTables.js"></script>
    <script>
                new DataTable('#ema'  , {
            language: {
                url: '//cdn.datatables.net/plug-ins/2.3.7/i18n/es-ES.json',
            },
            ajax:{
                url: '@Url.Action("Listar", "Mantenedor")',
                type: 'GET',
                dataType: 'json',
                dataSrc: 'data'
            },
            columns:[
                {data:'usuTipIde'},
                {data:'usuIde'},
                {data:'usuClave'},
                {data:'usuTempClave'},
                {data:'usuTerminos'},
                {data:'usuAuten'},
                {data:'usuFecAut'},
                {data:'usuRegimen'},
                {data:'usuAsegurador'},
                {data:'usuPoblacion'},

            ]

        });


    </script>
}
```
### 🔄 Cambios realizados

- Se eliminó el foreach que recorría el Model.

- Se integró DataTables mediante CDN.

- Los datos ahora se obtienen mediante @Url.Action("Listar", "Mantenedor").

- La tabla se llena dinámicamente usando AJAX.

- Se agregó configuración de idioma en español.