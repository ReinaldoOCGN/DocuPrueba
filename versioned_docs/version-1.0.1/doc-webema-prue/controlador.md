---
sidebar_position: 5
---

# Controlador

En la carpeta `Controllers` se encuentra el controlador principal, encargado de gestionar las solicitudes del usuario.

## HomeController

En este controlador se utiliza el método `Index` para obtener los datos desde la clase `Consultas` y enviarlos a la vista.

```cs title="HomeControllers.cs"
using Microsoft.AspNetCore.Mvc;
using System.Data;
using MostrarEma.Clases;
using MostrarEma.Models;

namespace MostrarEma.Controllers
{
    public class HomeController : Controller
    {
        private readonly Consultas _consultas;
        public HomeController()
        {
            _consultas = new Consultas();
        }
        public IActionResult Index()
        {
                var oLista = _consultas.Listar();
                return View(oLista);
            }
        }
    }
```
El método `Index` obtiene la lista de usuarios y la envía a la vista para su visualización.