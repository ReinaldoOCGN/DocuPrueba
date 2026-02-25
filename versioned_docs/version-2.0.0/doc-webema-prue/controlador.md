---
sidebar_position: 5
---

# Controlador

En la carpeta `Controllers` se encuentra el controlador principal, encargado de gestionar las solicitudes del usuario.

## HomeController

:::info Actualización de controlador
El `HomeController` ahora solo se encarga de la navegación del layout.
Se añadieron los métodos `Index` y `Privacy`.
:::

En esta nueva versión:

- `Index()` → Muestra la página principal

- `Privacy()` → Muestra la página de privacidad

```csharp title="HomeControllers.cs"
using Microsoft.AspNetCore.Mvc;
using System.Data;
using MostrarEma.Clases;
using MostrarEma.Models;

namespace MostrarEma.Controllers
{
    public class HomeController : Controller
    {
        private readonly ILogger<HomeController> _logger;

        public HomeController(ILogger<HomeController> logger)
        {
            _logger = logger;
        }
        public IActionResult Index()
        {
            return View();
        }
        public IActionResult Privacy()
        {
            return View();
        }

    }
}
```
:::tip Nuevo controlador agregado
Se agregó el `MantenedorController` para gestionar la obtención de usuarios
desde la base de datos mediante una consulta directa con ADO.NET.
:::
## MantenedorController

Este controlador expone el método:

- `Listar()` → Devuelve un `JsonResult` con la lista de usuarios.

```csharp title="MantenedorControllers.cs"
using Microsoft.AspNetCore.Mvc;
using MostrarEma.Datos;
using MostrarEma.Models;
using MostrarEma.Clases;
using MostrarEma.Models;
using System.Data;
using System.Data.SqlClient;

namespace MostrarEma.Controllers
{
    public class MantenedorController : Controller
    {
        [HttpGet]
        public JsonResult Listar()
        {
            List<EmaUsuariosModel> oLista = new List<EmaUsuariosModel>();
            var cn = new Conexion();

            using (var conexion = new SqlConnection(cn.getCadenaSQL()))
            {
                conexion.Open();

                SqlCommand cmd = new SqlCommand("SELECT  UsuTipIde,UsuIde,UsuClave,UsuTempClave,UsuTerminos,UsuAuten,UsuFecAut,UsuAsegurador,UsuRegimen,UsuPoblacion FROM EmaUsuario", conexion);
                cmd.CommandType = CommandType.Text;

                using (var dr = cmd.ExecuteReader())
                {
                    while (dr.Read())
                    {
                        oLista.Add(new EmaUsuariosModel()
                        {
                            UsuTipIde = dr["UsuTipIde"].ToString(),
                            UsuIde = dr["UsuIde"].ToString(),
                            UsuClave = dr["UsuClave"].ToString(),
                            UsuTempClave = dr["UsuTempClave"].ToString(),
                            UsuTerminos = dr["UsuTerminos"].ToString(),
                            UsuAuten = dr["UsuAuten"].ToString(),
                            UsuFecAut = dr["UsuFecAut"].ToString(),
                            UsuAsegurador = dr["UsuAsegurador"].ToString(),
                            UsuRegimen = dr["UsuRegimen"].ToString(),
                            UsuPoblacion = dr["UsuPoblacion"].ToString()
                        });
                    }
                }
            }

            return Json(new { data = oLista });
        }
    }
}
```

