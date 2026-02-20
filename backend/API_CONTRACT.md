# Contrato de API (MVP)

**Base URL (local):** `http://localhost:3000`  
**Formato:** JSON  
**Notas:** Store fijo en MVP: `demo-store-id` (hardcode en backend)

---

## Health

### GET `/health`
Verifica que el servicio está arriba.

**200 OK**
```json
{
  "status": "ok",
  "service": "datamark-backend",
  "timestamp": "2026-02-19T15:17:27.219Z"
}
```

---

## Productos

### GET `/products`
Lista productos activos.

**200 OK**
```json
[
  {
    "id": "uuid",
    "storeId": "demo-store-id",
    "name": "Playera blanca básica",
    "sku": null,
    "barcode": null,
    "category": "Ropa",
    "cost": "100",
    "price": "199",
    "stock": 17,
    "isActive": true,
    "createdAt": "ISO",
    "updatedAt": "ISO"
  }
]
```

---

### POST `/products`
Crea un producto.

**Body**
```json
{
  "storeId": "demo-store-id",
  "name": "Playera blanca básica",
  "category": "Ropa",
  "cost": 100,
  "price": 199,
  "stock": 20
}
```

**201 Created**  
Devuelve el producto creado.

---

### PUT `/products/:id`
Actualiza un producto.

**Ejemplo Body**
```json
{
  "name": "Playera blanca básica",
  "category": "Ropa",
  "cost": 110,
  "price": 209,
  "stock": 25
}
```

---

### DELETE `/products/:id`
Desactiva un producto (soft delete).

**200/204**

El producto deja de aparecer en `GET /products` (o queda con `isActive=false` según implementación).

---

## Ventas

### POST `/sales`
Registra una venta y descuenta inventario (transacción atómica).

**IMPORTANTE:** El campo correcto es `quantity` (NO `qty`).

**Body**
```json
{
  "items": [
    {
      "productId": "uuid",
      "quantity": 3
    }
  ]
}
```

**201 Created**

- Crea la venta  
- Crea items de venta  
- Descuenta stock por producto  

### Errores

- **400:** items vacío o quantity inválido  
- **404:** producto no encontrado  
- **409:** stock insuficiente  

---

## Dashboard

### GET `/dashboard/summary`
Retorna KPIs agregados para el dashboard.

**200 OK**
```json
{
  "totalSalesAmount": 1037,
  "totalSalesCount": 2,
  "todaySalesAmount": 597,
  "todaySalesCount": 1,
  "avgTicketToday": 597,
  "activeProducts": 4,
  "lowStockProducts": 1,
  "topProductsToday": [
    {
      "productId": "uuid",
      "name": "Playera blanca básica",
      "category": "Ropa",
      "qtySold": 3
    }
  ],
  "grossProfitToday": 297,
  "grossProfitTotal": 497
}
```
