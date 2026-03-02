# Descripción General

El Backend de DATAMARK es una API RESTful encargada de:
-Procesamiento estadístico.
-Consolidación de múltiples fuentes de datos.
-Limpieza y transformación de datasets.
-Cálculo de métricas descriptivas.
-Exposición de endpoints para el Frontend.
-Gestión de autenticación y autorización.
-Orquestación mediante Docker.

## ARQUITECTURA

Arquitectura basada en principios:

- Clean Architecture
- Separación por capas (Controller → Service → Repository)
- Modularización por dominios
- Configuración desacoplada por variables de entorno
│── src/
│ ├── controllers/
│ ├── services/
│ ├── repositories/
│ ├── models/
│ ├── routes/
│ ├── middlewares/
│ └── config/
│
│── docker-compose.yml
│── .env
│── requirements.txt / package.json
│── README.md

</>Codigo

---

## Tecnologías

- Python / Node.js (según tu implementación)
- FastAPI / Express
- Pandas / Numpy
- PostgreSQL / MySQL
- Docker
- JWT (Authentication)
- SQLAlchemy / Sequelize

---

## VARIABLES DE ENTORNO

Definir archivo `.env` basado en `.env.example`:

```env
APP_PORT=8000
DB_HOST=localhost
DB_PORT=5432
DB_USER=datamark
DB_PASSWORD=******
DB_NAME=datamark_db
JWT_SECRET=supersecretkey

## INSTALACION LOCAL

1.Clonar repositorio
---
</> Bash
git clone https: //github.com/tuusuario/datamark.get
Cd backkend
</>
---

2.Crear entorno virtual (si es Python)

---
</>Bash
python -m venv venv
source venv/bin/activate
---
3. Instalar dependencias
---
</>Bash
pip install -r requirements.txt
---
O si es Node
---
</>Bash
npm install
---

*Ejecutar con Docker 
---
</>Bash
docker-compose up –build

---

## ENDPOINTS PRINCIPALES:
*Salud del servicio
---
</>Código
GET /api/health
---
*Cargar Dataset
---
</>Codigo
POST /api/datasets/upload

---
*Unificar Bases de Datos
---
</>Codigo
POST /api/datasets/merge
---
*Generar Estadísticas
----
</>Codigo
GET /api/statistics/descriptive
---
*Autenticación
---
</>Codigo
POST /api/auth/login
---
## Procesamiento Estadístico
El sistema calcula automáticamente:
•Media
•Mediana
•Moda
•Desviación estándar
•Varianza
•Distribución por categorías
•Segmentación avanzada

Utiliza Pandas para manipulación y SQL optimizado para consultas agregadas.

Testing
---
</> Bash
Pytest 
---
O también se puede ese modo
</> Bash
 npm test
---
## Escalabilidad

- Containerización con Docker
- Preparado para despliegue en AWS / GCP / Azure
- Escalable horizontalmente
- Preparado para integración con microservicios

## Seguridad

- Autenticación JWT
- Hash de contraseñas con bcrypt
- Validación de entrada
- Protección CORS
- Control de roles

## Licencia
MIT License © DATAMARK
