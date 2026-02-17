
#  Persona 3 — Backend Órdenes (El Orquestador)

##  Objetivo
Construir órdenes, calcular totales y coordinar Catálogo + Logística.

---

##  Tareas

1. Crear clase `Orden`
2. Crear clase `ItemOrden`
3. Configurar relación:
   - Orden tiene lista de items (Cascade Delete ON)
4. Agregar `clienteId` (sin cascade delete)
5. Calcular total
6. Conectarse con:
   - Catálogo (precio y tipo)
   - Logística (costo envío)

---

##  Fórmula de Total

totalOrden = SUM(subtotales) + costoEnvio

---

##  Endpoint

### POST /ordenes

---

##  Request

```json
{
  "clienteId": 9001,
  "items": [
    { "productoId": 123, "cantidad": 1 },
    { "productoId": 456, "cantidad": 2 }
  ],
  "direccionEnvio": "León, Guanajuato, México"
}
```
### Response
```json
json
Copiar código
{
  "ordenId": 8001,
  "clienteId": 9001,
  "items": [
    {
      "productoId": 123,
      "tipo": "FISICO",
      "cantidad": 1,
      "precioUnitario": 161.56,
      "subtotal": 161.56
    },
    {
      "productoId": 456,
      "tipo": "DIGITAL",
      "cantidad": 2,
      "precioUnitario": 110.00,
      "subtotal": 220.00
    }
  ],
  "costoEnvio": 5.00,
  "totalOrden": 386.56,
  "moneda": "USD"
}
