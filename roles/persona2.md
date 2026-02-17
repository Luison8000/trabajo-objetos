
#  Persona 2 — Backend Logística (El Matemático)

##  Objetivo
Calcular costos de envío usando patrón Strategy + Factory.

---

##  Tareas

1. Crear interfaz `CalculadorEnvio`
2. Implementar:
   - `EnvioDron`
   - `EnvioCamion`
   - `EnvioDigital`
3. Crear `EnvioFactory`
4. Evitar if-else gigantes
5. Exponer endpoint POST `/envios/cotizar`

---

##  Reglas de Negocio

###  Dron
- Solo si peso < 2kg
- costo = 5.00

###  Camión
- costo = pesoKg * 2.00

###  Digital
- costo = 0.00 SIEMPRE

---

##  Endpoint

### POST /envios/cotizar

---

##  Request

```json
{
  "tipoProducto": "FISICO",
  "pesoKg": 1.5,
  "direccionDestino": "León, Guanajuato, México"
}
```

### Response Dron
```json
{
  "metodo": "DRON",
  "costoEnvio": 5.00,
  "moneda": "USD"
}
```
### Response Camión
```json
{
  "metodo": "CAMION",
  "costoEnvio": 6.00,
  "moneda": "USD"
}
```
### Response Digital
```json
{
  "metodo": "DIGITAL",
  "costoEnvio": 0.00,
  "moneda": "USD"
}
```
### Error
```json
{
  "error": "EnvioDronNoDisponible",
  "mensaje": "El peso excede el límite permitido para envío por dron"
}
```

