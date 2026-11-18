# Pago de un comparendo de tránsito con descuento por curso
 
Un ciudadano recibe un comparendo de tránsito y quiere saber cuánto debe pagar. El valor depende del tipo de infracción (expresado en salarios mínimos diarios). Si realiza el curso de pedagogía y paga oportunamente, obtiene un descuento: mayor si paga en los primeros días hábiles y menor si paga más tarde.
 
## Algoritmo
 
### Entradas
 
**Constantes:**
- SMMLV (Salario Mínimo Diario Legal Vigente): COP $60.000
- Tipo de Infracción:
  - A = 15 SMDLV (COP $900.000)
  - B = 30 SMDLV (COP $1,800.000)
  - C = 45 SMDLV (COP $2,700.000)
- Descuento:
  - 50 %: Realizó el curso y pagó dentro de los primeros 5 días hábiles.
  - 25 %: Realizó el curso y pagó entre el día hábil 6 y el 20
  - Sin descuento: No realizó el curso, o pagó después del día hábil 20

**Variables de entrada:**

- `tipo`: letra de la infracción (A, B o C)
- `curso`:
  - S : Si realizó el curso
  - N : No realizó el curso,
- `dias`: días hábiles transcurridos desde la notificación (mayor o igual a 1)

### Proceso de cálculo
 
1. Validar que el tipo sea A, B o C, que el curso sea S o N y que los días sean mayores o iguales a 1. Si no, informar el error y terminar. (Se recomienda convertir las letras a mayúsculas antes de comparar.)
2. Asignar el valor del comparendo según el tipo (multiplicando los SMDLV por 60.000).
3. Determinar el porcentaje de descuento:
  - 50 % si hizo el curso y días ≤ 5
  - 25 % si hizo el curso y días entre 6 y 20
  - 0 % en los demás casos.
4. Valor del descuento: valor del comparendo × porcentaje.
5. Total a pagar: valor del comparendo menos descuento.

### Salidas
 
Mostrar con `alert()`: valor del comparendo, porcentaje de descuento, valor del descuento y total a pagar. Si hay un dato inválido, mostrar un mensaje de error.
 
## Casos de prueba
 
| Caso | Entradas (tipo, curso, días) | Salidas |
|---|---|---|
| 1 | A, S, 5 | Valor 900.000 <br> 50 % <br> Descuento 450.000 <br> Total 450.000 |
| 2 | A, S, 6 | Valor 900.000 <br> 25 % <br> Descuento 225,000 <br> Total 675,000 |
| 3 | A, S, 20 | Valor 900.000 <br> 25 % <br> Descuento 225,000 <br> Total 675,000 |
| 4 | A, S, 21 | Valor 900.000 <br> 0 % <br> Descuento 0 <br> Total 900.000 |
| 5 | A, N, 3 | Valor 900.000 <br> 0 % <br> Descuento 0 <br> Total 900.000 |
| 6 | B, S, 5 | Valor 1.800.000 <br> 50 % <br> Descuento 900.000 <br> Total 900.000 |
| 7 | B, S, 20 | Valor 1.800.000 <br> 25 % <br> Descuento 450.000 <br> Total 1.350.000 |
| 8 | B, S, 21 | Valor 1.800.000 <br> 0 % <br> Descuento 0 <br> Total 1.800.000 |
| 9 | B, N, 3 | Valor 1.800.000 <br> 0 % <br> Descuento 0 <br> Total 1.800.000 |
| 10 | C, S, 5 | Valor 2.700.000 <br> 50 % <br> Descuento 1.350.000 <br> Total 1,350.000 |
| 11 | C, S, 20 | Valor 2.700.000 <br> 25 % <br> Descuento 675.000 <br> Total 2.025.000 |
| 12 | C, S, 21 | Valor 2.700.000 <br> 0 % <br> Descuento 0 <br> Total 2.700.000 |
| 13 | C, N, 3 | Valor 2.700.000 <br> 0 % <br> Descuento 0 <br> Total 2.700.000 |
| 14 | D, S, 3 | "Tipo de infracción no válido" |
| 15 | A, X, 3 | "Respuesta de curso no válida" |
| 16 | A, S, 0 | "Días hábiles no válidos" |
