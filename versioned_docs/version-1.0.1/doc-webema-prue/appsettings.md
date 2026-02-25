---
sidebar_position: 2
---

# AppSetting.json

Esta sección mostrará la cadena de conexión configurada en el appsettings

```json title="AppSentting.json"
{
  "ConnectionStrings": {
    //Pruebas
    "CadenaSQL": "Data Source=172.27.29.231,1433; Initial Catalog=basges; User Id=ocgn_desa; Password=desa2019;Pooling=true;Connection Timeout=60; Connection Lifetime=60; Max Pool Size=30000; Min Pool Size=5  "
  },
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning"
    }
  },
  "AllowedHosts": "*"
}
```
Esta cadena de conexión permite conectarse a la base de datos de pruebas **Basges**.
