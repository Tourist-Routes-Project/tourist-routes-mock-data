# Mock del Microservicio de Comentarios

Este documento detalla cómo se estructura y simula el microservicio de comentarios. A continuación, se describen las peticiones que deben realizarse para las distintas operaciones de la API.

## **Endpoints y Estructura del Microservicio**

### **GET /comments**

Obtiene todos los comentarios almacenados.

#### **Respuesta**:

```json
{
  "comments": [
    {
      "id_comment": 1,
      "description": "Me ha encantado la ruta, la recomiendo 100%, los lugares eran preciosos y las audioguías eran claras y se ajustaban perfectamente al tiempo de ruta",
      "userId": 1,
      "routeId": 4,
      "createdDate": "2025-01-20"
    },
    {
      "id_comment": 2,
      "description": "La experiencia fue maravillosa.",
      "userId": 2,
      "routeId": 4,
      "createdDate": "2025-01-18"
    }
  ]
}
```

---

### **POST /comments**

Crea un nuevo comentario.

#### **Cuerpo de la petición**:

```json
{
  "description": "Me ha encantado la ruta, la recomiendo 100%, los lugares eran preciosos y las audioguías eran claras y se ajustaban perfectamente al tiempo de ruta"
}
```

#### **Notas**:

- Los valores de `id_comment`, `userId`, `routeId` y `createdDate` se generan automáticamente en el backend.

#### **Estructura**:

```json
{
  "id_comment": 3,
  "description": "Me ha encantado la ruta, la recomiendo 100%, los lugares eran preciosos y las audioguías eran claras y se ajustaban perfectamente al tiempo de ruta",
  "userId": 2,
  "routeId": 4,
  "createdDate": "2025-01-21"
}
```

---

### **PUT /comments/{id}**

Actualiza un comentario existente.

#### **URL**:

`http://localhost:8080/api/v1/comments/1`

#### **Cuerpo de la petición**:

```json
{
  "description": "He editado mi comentario para corregir algunos errores."
}
```

#### **Estructura**:

```json
{
  "id_comment": 1,
  "description": "He editado mi comentario para corregir algunos errores.",
  "userId": 1,
  "routeId": 4,
  "createdDate": "2025-01-20"
}
```

---

### **DELETE /comments/{id}**

Elimina un comentario existente.

#### **URL**:

`http://localhost:8080/api/v1/comments/1`

#### **Método HTTP**:

`DELETE`

#### **Respuesta**:

```json
{
  "message": "Comentario eliminado correctamente."
}
```

---

## **Notas Importantes**

1. **Datos generados automáticamente**:

   - `id_comment`: Se genera en el backend al crear un nuevo comentario.
   - `userId`: Se asocia automáticamente con el usuario que está logeado.
   - `routeId`: Se toma de la ruta actual en la que se encuentra el usuario.
   - `createdDate`: Se asigna la fecha actual al momento de la creación.

2. **Estructura Base del Comentario**:
   Cada comentario tiene la siguiente estructura:
   ```json
   {
     "id_comment": <number>,
     "description": <string>,
     "userId": <number>,
     "routeId": <number>,
     "createdDate": <string>
   }
   ```
