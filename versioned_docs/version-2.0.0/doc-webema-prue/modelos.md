---
sidebar_position: 3
---

# Modelos

Después de configurar la cadena de conexión, se procede a crear un nuevo modelo dentro de la carpeta `Models`

En este caso, el modelo fue llamado `EmaUsuariosModel`, y en él se define la estructura de los datos que serán obtenidos desde la base de datos.

```csharp title="EmaUsuariosModel.cs" 
namespace MostrarEma.Models
{
    public class EmaUsuariosModel
    {
        public string? UsuTipIde { get; set; }
        public string? UsuIde { get; set; }
        public string? UsuClave { get; set; }
        public string? UsuTempClave { get; set; }
        public string? UsuTerminos { get; set; }
        public string? UsuAuten { get; set; }
        public string? UsuFecAut { get; set; }
        public string? UsuAsegurador { get; set; }
        public string? UsuRegimen { get; set; }
        public string? UsuPoblacion { get; set; }
    }
}
```

Aunque actualmente el programa está diseñado únicamente para la obtención de datos, se incluyen propiedades con `get` y `set` para permitir futuras actualizaciones o inserciones de información.