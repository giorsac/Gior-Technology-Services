## **❌ Manejo de Errores (Error Handling) :**

Cuando se realiza una solicitud errada a la API, el sistema devolverá una **estructura estándar de error** que permite al cliente comprender y manejar adecuadamente lo ocurrido.

A continuación se describe el **formato general** y el significado de cada campo retornado.

---

#### **🧬 Estructura de Error General**

```json
{
  "status": 400,
  "is_rejected": false,
  "title": "Título del Error",
  "errors": [
    "Descripción detallada del primer error.",
    "Descripción detallada del segundo error."
  ]
}
```

#### **Descripción Campos :**

|**Parámetro**|**Tipo**|                                                     **Descripción**                                           |
|:-----------:|:------:|:-------------------------------------------------------------------------------------------------------------:|
|    status   |  int   |                Código HTTP que indica el tipo de error (por ejemplo: 400, 401, 404, 500, etc.).               |
| is_rejected |  bool  | Indica si el comprobante fue rechazado. Este campo solo aparece cuando se trata de comprobantes electrónicos. |
|    title    | string |                                    Título descriptivo y resumido del error.                                   |
|    errors   | array  |                           Lista de errores detallados que explican qué falló en la solicitud.                 |

### **🎯 Consideraciones Importantes**
- El campo is_rejected no aplica para todas las operaciones. Por ejemplo, al generar un token de autenticación, este campo no se incluye ya que no se está tratando con un comprobante.

- Cuando un cliente está configurado para enviar comprobantes a través de OSE, este campo suele permanecer en false, ya que la OSE no realiza un rechazo definitivo. En cambio, SUNAT sí puede rechazar un comprobante de forma definitiva, invalidando el número de serie usado.

### **📌 Ejemplos de Respuestas**

**🛑 Error en solicitud de comprobante con rechazo (SUNAT)**

```json
{
  "status": 400,
  "is_rejected": true,
  "title": "Comprobante rechazado por SUNAT.",
  "errors": [
    "El monto del IGV no corresponde con el subtotal.",
    "Fecha del documento fuera de rango permitido."
  ]
}
```

**🔐 Error en autenticación**

```json
{
  "status": 401,
  "title": "Acceso no autorizado.",
  "errors": [
    "Usuario o contraseña inválidos."
  ]
}
```

### **🧠 Recomendaciones para Integradores**

- Siempre validar el campo status para identificar el tipo de error HTTP retornado.

- Verificar si is_rejected está presente y en true para iniciar un proceso de corrección o reemisión de comprobante.

- Mostrar el contenido del array errors al usuario o al desarrollador para facilitar el diagnóstico.

> ☕ **¡Pro tip!** Centraliza el manejo de errores en tu integración para mostrar mensajes claros al usuario final, y loguear información detallada para soporte técnico.