---
sidebar_position: 4
---

# Clases

En esta sección se describe la carpeta `Clases` y las clases creadas junto con su funcionalidad.

## Conexión

En la clase `Conexion` se implementa el método encargado de obtener la cadena de conexión definida en `appsettings.json`.

```csharp tittle="Conexion.cs"
using System.Data.SqlClient;
namespace MostrarEma.Clases
{

    public class Conexion
    {
        public string cadenaSQL = string.Empty;

        public Conexion()
        {
            var builder = new ConfigurationBuilder().SetBasePath(Directory.GetCurrentDirectory())
                        .AddJsonFile("appsettings.json").Build();

            cadenaSQL = builder.GetSection("ConnectionStrings:CadenaSQL").Value;
        }
        public string getCadenaSQL()
        {
            return cadenaSQL;
        }
    }
}
```
Esta clase permite centralizar la obtención de la cadena de conexión, evitando repetir código cada vez que se necesite acceder a la base de datos.



## Consultas

:::caution Clase obsoleta
Evita usar esta clase. Está en proceso de deprecación.
:::

La clase `Consultas` es la encargada de ejecutar las consultas a la base de datos y mapear los resultados al modelo correspondiente.

```csharp title="Consultas.cs"
using MostrarEma.Datos;
using System.Data;
using System.Data.SqlClient;

using MostrarEma.Models;

namespace MostrarEma.Clases;

public class Consultas
{

    public List<EmaUsuariosModel> Listar()
    {
        var oLista = new List<EmaUsuariosModel>();
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

        return oLista;
    }

}
```

Esta clase ejecuta una consulta SQL directa sobre la tabla `EmaUsuario` y devuelve una lista de objetos `EmaUsuariosModel`.