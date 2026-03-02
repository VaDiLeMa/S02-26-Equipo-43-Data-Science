</>Markdown
# DATAMARK Frontend

Aplicación cliente de DATAMARK, construida bajo arquitectura SPA moderna, diseñada para análisis interactivo de datasets, visualización estadística avanzada y consumo eficiente de Apis RESTful.

## Propósito del Frontend

El Frontend es responsable de:

- Orquestación de flujo de datos hacia el Backend
- Gestión del estado global de la aplicación
- Renderizado de dashboards dinámicos
- Visualización estadística interactiva
- Gestión de autenticación
- Control de permisos de usuario
- Manejo de errores distribuido
- Optimización de performance y caching

ARQUITECTURA DEL SISTEMA

 Estilo Arquitectónico:

- SPA (Single Page Application)
- Arquitectura basada en componentes
- Separación por capas
- Patrón Container / Presentational
- Principios SOLID aplicados a componentes

 Estructura de Carpetas

frontend/
│
├── src/
│ ├── core/ # Configuración global
│ │ ├── api/
│ │ ├── constants/
│ │ ├── routes/
│ │ └── config/
│ │
│ ├── modules/ # Módulos desacoplados por dominio
│ │ ├── auth/
│ │ ├── dashboard/
│ │ ├── datasets/
│ │ └── statistics/
│ │
│ ├── components/ # Componentes reutilizables
│ ├── hooks/ # Custom Hooks
│ ├── context/ # Context Providers
│ ├── store/ # Gestión de estado global
│ ├── services/ # Servicios HTTP
│ ├── utils/ # Funciones puras
│ ├── layouts/
│ └── assets/
│
├── public/
├── tests/
├── .env
├── vite.config.ts / next.config.js
└── README.md

</>Código
Stack Tecnológico

Framework Principal
React 18+ / Next.js 14+

Manejo de Estado
Redux Toolkit / Zustand / Context API

Networking
-Axios (interceptores)
-Fetch API (opcional)

Visualización de Datos
 Recharts / Chart.js / D3.js

 Estilos
-TailwindCSS
-CSS Modules / Styled Components

 Tipado
 TypeScript (estrict mode activado)

## Autenticación y Seguridad

Implementación basada en:

- JWT (Access + Refresh Token)
- Interceptores de Axios
- Almacenamiento seguro (HttpOnly cookies recomendado)
- Protección de rutas privadas
- Role-based access control (RBAC)

Ejemplo de protección de ruta:

```ts
<Route
  path="/dashboard"
  element={
    <PrivateRoute roles={["admin", "analyst"]}>
      <Dashboard />
    </PrivateRoute>
  }
/>

</>


## Gestión de API
Configuración Base
</>Codigo
VITE_API_URL=http://localhost:8000/api

</>

## Servicio HTTP Centralizado
</>Codigo
src/core/api/axiosInstance.ts
</>

Configuración incluye:
•Base URL
•Interceptores de request
•Interceptores de response
•Refresh token automático
•Manejo global de errores
•Retry automático (opcional)

**Motor de Visualización** 

El frontend renderiza métricas provenientes del backend:
•Media
•Mediana
•Moda
•Distribuciones categóricas
•Series temporales
•KPIs comparativos
•Segmentaciones dinámicas

Estrategia:
•Lazy loading de módulos
•Memoización con useMemo
•Virtualización de tablas
•Renderizado condicional optimizado

Flujo de Datos Interno
1.Usuario carga dataset
2.Se envía request a backend
3.Backend procesa estadísticas
4.Store actualiza estado global
5.Dashboard se re-renderiza
6.Usuario aplica filtros
7.Se recalculan métricas dinámicamente

Modularización por Dominio
Cada módulo contiene:
</>Codigo
dashboard/
│── components/
│── hooks/
│── services/
│── types.ts
│── index.ts
</>

Esto permite:
•Escalabilidad horizontal
•Bajo acoplamiento
•Alta cohesión
•Fácil testing


Testing
•Jest
•React Testing Library
•Testing de hooks personalizados
•Testing de servicios HTTP
•Mocking de APIs

Optimización y Performance

Implementaciones incluidas:
•Code splitting                 
•Lazy loading
•Suspense
•Tree shaking
•Optimización de bundle
•Compresión Gzip/Brotli (servidor)

Scripts Disponibles

</>Bash

npm run dev          # Desarrollo
npm run build        # Build producción
npm run preview      # Vista previa producción
npm run lint         # Linter
npm run format       # Prettier
npm run test         # Testing

</>

Estrategia de Escalabilidad

El frontend está preparado para:
•Microfrontends
•SSR (si usa Next.js)
•Edge rendering
•Integración con CDN
•Deploy automatizado (CI/CD)
•Feature toggles

 Principios de Ingeniería Aplicados
•Clean Code
•SOLID
•Separation of Concerns
•DRY
•Atomic Design (componentes)
•Arquitectura orientada a dominio

Estrategia de Despliegue
Recomendado:
•Vercel (Next.js)
•AWS S3 + CloudFront
•Nginx como reverse proxy
•Dockerización

Roadmap Técnico
• Dark Mode
• Filtros avanzados
• Exportación PDF/Excel
• Control de sesiones
• Persistencia offline
• WebSocket para tiempo real

Equipo
Desarrollado como parte del proyecto DATAMARK


