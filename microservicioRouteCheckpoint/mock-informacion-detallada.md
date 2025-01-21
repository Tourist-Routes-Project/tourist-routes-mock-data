# Mock del Microservicio de Ruta y Checkpoint

Este documento detalla cómo se estructura y simula el microservicio de rutas y checkpoints. A continuación, se describen las peticiones que deben realizarse para las distintas operaciones de la API.

## **Endpoints y Estructura del Microservicio**

### **POST /route**

Añade una nueva ruta con sus checkpoints.

#### **URL**:

`http://localhost:8080/api/v1/route`

#### **Cuerpo de la Petición**:

```json
{
  "nameRoute": "Sevilla Walking Tour 4",
  "descriptionRoute": "A walking route through the landmarks of Sevilla.",
  "cityName": "Seville",
  "checkpoints": [
    {
      "nameCheckpoint": "Iglesia de San Juan de la Palma",
      "coordinates": {
        "startLatitude": 37.386,
        "startLongitude": -5.985,
        "endLatitude": 37.3862,
        "endLongitude": -5.9845
      }
    },
    {
      "nameCheckpoint": "Iglesia de la Basílica de la Macarena",
      "coordinates": {
        "startLatitude": 37.3865,
        "startLongitude": -5.9867,
        "endLatitude": 37.387,
        "endLongitude": -5.986
      }
    }
  ]
}
```

## **Notas Importantes**

1. **Estructura Base de la ruta**:

```json
{
  "nameRoute": <string>,
  "descriptionRoute": <string>,
  "cityName": <string>,
  "checkpoints": [
    {
      "nameCheckpoint": <string>,
      "coordinates": {
        "startLatitude": <float>,
        "startLongitude": <float>,
        "endLatitude": <float>,
        "endLongitude": <float>
      }
    }
  ]
}
```
