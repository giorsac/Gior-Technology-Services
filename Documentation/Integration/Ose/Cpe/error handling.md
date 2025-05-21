# ❌ Manejo de Errores (Error Handling)

Cuando se realiza una solicitud incorrecta o ocurre un fallo interno en el servicio, la API responde con una **estructura de error estandarizada**, diseñada para facilitar el diagnóstico y la implementación de una gestión de errores eficiente.

---

## 🧬 Estructura General de Error

```json
{
  "status": 400,
  "title": "Título del Error",
  "errors": [
    "Descripción detallada del primer error.",
    "Descripción detallada del segundo error."
  ]
}

```

#### **Descripción Campos :**

|**Parámetro**|**Tipo**|                                                             **Descripción**                                                       |
|:-----------:|:------:|:---------------------------------------------------------------------------------------------------------------------------------:|
|    status   |  int   |                        Código HTTP que indica el tipo de error (por ejemplo: 400, 401, 404, 500, etc.).                           |
|    title    | string |                                              Título descriptivo y resumido del error.                                             |
|    errors   | array  |                               Lista de errores detallados que explican qué falló en la solicitud.                                 |

### 📌 **Algunos Ejemplos de Respuestas**

🔐 **Error 401 (Unauthorized)**

```json
{
  "status": 401,
  "title": "Acceso no autorizado.",
  "errors": [
    "Usuario o contraseña inválidos."
  ]
}
```

🛑 **Error 404 (Not Found)**

```json
{
  "status": 404,
  "title": "No se pudo encontrar el recurso solicitado.",
  "errors": [
        "No se pudo encontrar ningún archivo con el nombre proporcionado."
    ]
}
```

### 🧠 **Recomendaciones para Integradores**

- 🔍 Mostrá los errores contenidos en el arreglo errors al desarrollador o usuario técnico para facilitar la solución.
- ✅ Validá siempre el campo status antes de procesar la respuesta.
- 📣 Mostrá mensajes amigables al usuario final y reservá los detalles técnicos para entornos de desarrollo o soporte.