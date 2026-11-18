# Simulador de crédito hipotecario (con y sin subsidio VIS)
 
Una constructora ofrece apartamentos a la venta y quiere un simulador de crédito hipotecario. Si la vivienda es de interés social (VIS), el comprador puede recibir un subsidio de vivienda según sus ingresos y paga una tasa menor. Si no es VIS, no hay subsidio y la tasa es mayor. El banco aprueba el crédito solo si la cuota inicial cumple el mínimo y si la cuota mensual no supera el 30 % de los ingresos. Para simplificar, la cuota se calcula con la **fórmula didáctica** indicada abajo.
 
## Algoritmo
 
### Entradas
 
**Constantes:**
- SMMLV (Salario Mínimo Mensual Legal Vigente): COP $1.750.000 (Pesos colombianos)
- Tope de vivienda VIS: 150 SMMLV (COP $262.500.000)
- Subsidio:
  - Hasta 2 SMMLV (3.500.000) = 30 SMMLV (52,500.000)
  - Mayores a 2 SMMLV y hasta 4 SMMLV (7,000.000) = 20 SMMLV (35,000.000)
  - Mayores a 4 SMMLV = sin subsidio
- Cuota inicial mínima:
  - VIS = 10 % del valor
  - No VIS = 30 % del valor
- Tasa mensual didáctica:
  - VIS = 0.6 %
  - No VIS = 0.9 %
- Límite de endeudamiento: la cuota no puede superar el 30 % de los ingresos
  
**Variables de entrada:**

- `valorVivienda`: precio de la vivienda (mayor que 0)
- `ingresos`: ingresos mensuales del comprador (mayor que 0)
- `cuotaInicial`: dinero que el comprador aporta de entrada
- `plazoAnios`: 10, 15 o 20

### Proceso de cálculo
 
1. Validar que valor de la vivienda e ingresos sean mayores que 0 y que el plazo sea 10, 15 o 20. Si no, informar el error y terminar.
2. Determinar si la vivienda es VIS: lo es si su valor es menor o igual a $262.500.000.
3. Calcular la cuota inicial mínima según el tipo (10 % o 30 % del valor). Si la cuota inicial es menor a ese mínimo, rechazar la solicitud por cuota inicial insuficiente y terminar.
4. Si es VIS, calcular el subsidio según los ingresos; si no es VIS, el subsidio es 0.
5. Monto a financiar: valor de la vivienda menos cuota inicial menos subsidio.
6. Número de meses: plazo en años × 12.
7. Cuota mensual: (monto a financiar ÷ meses) + (monto a financiar × tasa mensual).
8. Cuota máxima permitida: 30 % de los ingresos.
9. Si la cuota mensual es menor o igual a la cuota máxima, el crédito es aprobado; de lo contrario, rechazado por capacidad de pago.
### Salidas
 
Mostrar con `alert()`: tipo de vivienda (VIS o No VIS), subsidio, monto a financiar, cuota mensual, cuota máxima permitida y el estado de la solicitud (aprobada o rechazada con el motivo).
 
## Casos de prueba
 
| Caso | Entradas (valor, ingresos, cuota inicial, años) | Salidas |
|---|---|---|
| 1 | 120.000.000, 3,000.000, 12,000.000, 20 | VIS <br> Subsidio 52.500.000 <br> Financiar 55.500.000 <br> Cuota 564.250 <br> Máx. 900.000 <br> **Aprobado** |
| 2 | 120.000.000, 5,000.000, 12,000.000, 20 | VIS <br> Subsidio 35.000.000 <br> Financiar 73.000.000 <br> Cuota 742.166.67 <br> Máx. 1.500.000 <br> **Aprobado** |
| 3 | 120.000.000, 8,000.000, 12,000.000, 20 | VIS <br> Subsidio 0 <br> Financiar 108.000.000 <br> Cuota 1.098.000 <br> Máx. 2.400.000 <br> **Aprobado** |
| 4 | 120.000.000, 3,000.000, 6,000.000, 20 | VIS <br> **Rechazado**: cuota inicial insuficiente (mínimo 12.000.000) |
| 5 | 200.000.000, 3,000.000, 20.000.000, 10 | VIS <br> Subsidio 52,500.000 <br> Financiar 127,500.000 <br> Cuota 1,827,500 <br> Máx. 900.000 <br> **Rechazado** por capacidad de pago |
| 6 | 400.000.000, 15,000.000, 120.000.000, 20 | No VIS <br> Subsidio 0 <br> Financiar 280.000.000 <br> Cuota 3,686,666.67 <br> Máx. 4,500.000 <br> **Aprobado** |
| 7 | 400.000.000, 15,000.000, 80.000.000, 20 | No VIS <br> **Rechazado**: cuota inicial insuficiente (mínimo 120.000.000) |
| 8 | 400.000.000, 8,000.000, 120.000.000, 20 | No VIS <br> Subsidio 0 <br> Financiar 280.000.000 <br> Cuota 3,686,666.67 <br> Máx. 2,400.000 <br> **Rechazado** por capacidad de pago |
| 9 | 262,500.000, 3,000.000, 26,250.000, 20 (límite VIS) | VIS <br> Subsidio 52,500.000 <br> Financiar 183,750.000 <br> Cuota 1,868,125 <br> Máx. 900.000 <br> **Rechazado** por capacidad de pago |
| 10 | 120.000.000, 7,000.000, 12,000.000, 20 (límite de ingresos 4 SMMLV) | VIS <br> Subsidio 35.000.000 <br> Financiar 73.000.000 <br> Cuota 742.166.67 <br> Máx. 2.100.000 <br> **Aprobado** |
| 11 | 120.000.000, 3,500.000, 12,000.000, 20 (límite de ingresos 2 SMMLV) | VIS <br> Subsidio 52.500.000 <br> Financiar 55.500.000 <br> Cuota 564.250 <br> Máx. 1.050.000 <br> **Aprobado** |
| 12 | 120.000.000, 3,000.000, 12,000.000, 12 | "Plazo no válido" |
| 13 | 0, 3,000.000, 12,000.000, 20 | "Valor de vivienda no válido" |
