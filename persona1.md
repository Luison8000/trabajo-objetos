#  Persona 1 — Backend Catálogo

##  Objetivo
Construir la jerarquía de productos, calcular precios finales y validar reglas de negocio.

---

##  Tareas

1. Crear clase abstracta `Producto`
2. Crear `ProductoFisico`
3. Crear `ProductoDigital`
4. Implementar cálculo de precios
5. Validar que productos digitales NO tengan peso
6. Exponer endpoint `GET /productos/{id}`

---

##  Reglas de Negocio

### Producto Físico
precioFinal = precioBase + (pesoKg * 1.2) + costoAlmacen

### Producto Digital
precioFinal = precioBase + (tamanoMB * 0.05)

###  Regla Crítica
Si `ProductoDigital.pesoKg > 0` ➜ lanzar excepción

---

##  Endpoint

### GET /productos/{id}

---

##  Response — Producto Físico

```json
{
  "id": 123,
  "nombre": "Raqueta Profesional",
  "tipo": "FISICO",
  "precioBase": 150.00,
  "pesoKg": 1.3,
  "costoAlmacen": 10.00,
  "precioFinal": 161.56
}
