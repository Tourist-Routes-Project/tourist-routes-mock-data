# Mock del Microservicio de Audioguía

Este documento detalla cómo se estructura y simula el microservicio de audioguía. A continuación, se describen las peticiones que deben realizarse para las distintas operaciones de la API.

## **Endpoints y Estructura del Microservicio**

### **GET /audioguides**

Obtiene todas las audioguías almacenadas.

#### **Respuesta**:

```json
[
  {
    "_id": "6782b08660a6b72111a85f6f",
    "title": "Santa Iglesia Catedral de Sevilla",
    "url_audioguia": "https://res.cloudinary.com/dp7cqbl3w/video/upload/v1736615309/catedral_nyqvv3.mp3",
    "id_checkpoint": 1,
    "__v": 0
  },
  {
    "_id": "6782bcf23ab89aba6cf75f41",
    "title": "Metropol Parasol Setas de Sevilla",
    "url_audioguia": "https://res.cloudinary.com/dp7cqbl3w/video/upload/v1736621112/setas_v7gny5.mp3",
    "id_checkpoint": 1,
    "__v": 0
  }
]
```

### **POST /audioguide**

Crea una nueva audioguia.

#### **Cuerpo de la petición**:

```json
{
  "title": "Metropol Parasol Setas",
  "url_audioguia": "https://res.cloudinary.com/dp7cqbl3w/video/upload/v1736621112/setas_v7gny5.mp3",
  "id_checkpoint": 1
}
```

#### **Respuesta**:

```json
{
  "_id": "6782bcf23ab89aba6cf75f41",
  "title": "Metropol Parasol Setas de Sevilla",
  "url_audioguia": "https://res.cloudinary.com/dp7cqbl3w/video/upload/v1736621112/setas_v7gny5.mp3",
  "id_checkpoint": 1,
  "__v": 0
}
```

### **PUT /audioguide/{id}**

Actualiza una audioguia existente.

#### **URL**:

`http://localhost:8080/api/v1/audioguide/1`

#### **Cuerpo de la petición**:

```json
{
  "title": "Metropol Parasol Setas de Sevilla",
  "url_audioguia": "https://res.cloudinary.com/dp7cqbl3w/video/upload/v1736621112/setas_v7gny5.mp3",
  "id_checkpoint": 1
}
```

#### **Respuesta**:

```json
{
  "_id": "6782bcf23ab89aba6cf75f41",
  "title": "Metropol Parasol Setas de Sevilla",
  "url_audioguia": "https://res.cloudinary.com/dp7cqbl3w/video/upload/v1736621112/setas_v7gny5.mp3",
  "id_checkpoint": 1,
  "__v": 0
}
```

---

### **DELETE /audioguide/{id}**

Elimina una audioguia existente.

#### **URL**:

`http://localhost:8080/api/v1/audioguide/1`

#### **Método HTTP**:

`DELETE`

---

## **Notas Importantes**

1. **Datos generados automáticamente**:

   - `id_comment`: Se genera en el backend al crear un nuevo audioguía.
   - `__v`: Es el campo de versión en MongoDB
   - `id_checkpoint`: Se asigna al checkpoint asociado a la audioguía.

2. **Estructura Base de Audioguia**:
   Cada audioguia tiene la siguiente estructura:

   ```json
   {
   "_id": <string>,
   "title": <string>,
   "url_audioguia": <string>,
   "id_checkpoint": <number>,
   "__v": <number>
   }

   ```
