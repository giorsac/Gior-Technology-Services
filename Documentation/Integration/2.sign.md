

# **Autenticación 🚀🔥:**

Para consumir los servicios del PSE, en las cabeceras **(Headers)** se debe enviar la palabra **“Bearer”** concatenando con un espacio y luego el token de seguridad que generará en el siguiente punto.

## Generación Token:

Para generar el token se le brindará sus respectivas credenciales de acceso (Usuario y Contraseña), luego debe acceder al siguiente EndPoint:

|               EndPoint               | Método |   Entorno  | 
|:------------------------------------:|:------:|:----------:|
|    http://core.gior/api/auth/login   |  POST  | Producción |
| http://beta-core.gior/api/auth/login |  POST  |    Beta    |

### **Esquema:**

|     Parámetro   |  Condición  | Tipo De Dato |           Descripción          |
|:---------------:|:-----------:|:------------:|:------------------------------:|
|    usernameℹ️   | Obligatorio |    String    |   Usuario que se le brindará.  |
|    passwordℹ️   | Obligatorio |    String    | Contraseña que se le brindará. |

#### **Ejemplo de Solicitud:**

```json
{
    username: 12345678901,
    password: 5eND0NwXx&A5
}
```

####  **Respuesta:**
```json
{
    username: 12345678901,
    password: 5eND0NwXx&A5
}
```

## **Solicitud Generar ✉️:**
Firma el archivo enviado en formato **XML** o **JSON**, al realizar el envio se genera un estado del documento en el servicio.

|               EndPoint               | Método |   Entorno  | 
|:------------------------------------:|:------:|:----------:|
|     http://core.gior/api/cpe/sign    |  POST  | Producción |
|  http://beta-core.gior/api/cpe/sign  |  POST  |    Beta    |

### **Esquema:**

|     Parámetro   |  Condición  | Tipo De Dato |                                   Descripción                            |
|:---------------:|:-----------:|:------------:|:------------------------------------------------------------------------:|
|   file_nameℹ️   | Obligatorio |    String    | Nombre del archivo según el formato establecido por SUNAT sin extensión. |
| file_contentℹ️  | Obligatorio |    String    |                  Contenido del archivo XML/JSON en base64.               |

####  **Respuesta:**
```json
{
    username: 12345678901,
    password: 5eND0NwXx&A5
}
```
