# Pago mensual de EPS (salud) con beneficiarios adicionales
 
Una oficina de talento humano necesita calcular lo que se paga cada mes a la EPS. Si la persona es empleada (dependiente), el aporte del 12.5 % se reparte entre el trabajador (4 %) y el empleador (8.5 %). Si es independiente, paga el 12.5 % completo. Además, si cotiza por padres a cargo, cada uno genera una Unidad de Pago por Capitación (UPC) adicional que paga siempre el afiliado.
 
## Algoritmo
 
### Entradas
 
**Constantes:**

- SMMLV (Salario Mínimo Mensual Legal Vigente): COP $1.750.000 (Pesos colombianos)
- Tope máximo del IBC: 25 SMMLV (COP $43.750.000)
- Dependiente: trabajador 4 %; empleador 8.5 %
- Independiente: 12.5 % a cargo del afiliado
- UPC adicional por cada padre a cargo: 150.000 mensuales (máximo 2 padres)

**Variables de entrada:**

- `salario`: salario o ingreso base mensual (mayor que 0)
- `tipo`: 1 = dependiente (empleado), 2 = independiente
- `padres`: cantidad de padres a cargo (0, 1 o 2).
 
### Proceso de cálculo
 
1. Validar que el salario sea mayor que 0, que el tipo sea 1 o 2 y que los padres sean 0, 1 o 2. Si no, informar el error y terminar.
2. El IBC es el salario. Si es menor que 1 SMMLV, el IBC es 1 SMMLV. Si es mayor que 25 SMMLV, el IBC es 25 SMMLV.
3. Según el tipo de usuario:
  - 1 (Dependiente):
    - Aporte del trabajador = 4 % del IBC
    - Aporte del empleador = 8.5 % del IBC.
  - 2 (Independiente):
    - Aporte del afiliado = 12.5 % del IBC
    - Aporte del empleador = 0.
4. UPC adicional: padres × 150,000.
5. Total a cargo del afiliado: su aporte más la UPC adicional.
6. Total que recibe la EPS: total a cargo del afiliado más aporte del empleador.

### Salidas
 
Mostrar con `alert()`: IBC, aporte del afiliado, UPC adicional, aporte del empleador, total a cargo del afiliado y total que recibe la EPS. Si hay un dato inválido, mostrar un mensaje de error.
 
## Casos de prueba
 
| Caso | Entradas (salario, tipo, padres) | Salidas |
|---|---|---|
| 1 | 1.200.000, 1, 0 | IBC 1.750.000 <br> Aporte afiliado 70.000 <br> UPC 0 <br> Empleador 148.750 <br> Afiliado total 70.000 <br> EPS 218.750 |
| 2 | 1.200.000, 1, 1 | IBC 1.750.000 <br> Aporte afiliado 70.000 <br> UPC 150.000 <br> Empleador 148.750 <br> Afiliado total 220.000 <br> EPS 368.750 |
| 3 | 1.200.000, 1, 2 | IBC 1.750.000 <br> Aporte afiliado 70.000 <br> UPC 300.000 <br> Empleador 148.750 <br> Afiliado total 370.000 <br> EPS 518.750 |
| 4 | 1.200.000, 2, 0 | IBC 1.750.000 <br> Aporte afiliado 218.750 <br> UPC 0 <br> Empleador 0 <br> Afiliado total 218.750 <br> EPS 218.750 |
| 5 | 1.200.000, 2, 1 | IBC 1.750.000 <br> Aporte afiliado 218.750 <br> UPC 150.000 <br> Empleador 0 <br> Afiliado total 368.750 <br> EPS 368.750 |
| 6 | 1.200.000, 2, 2 | IBC 1.750.000 <br> Aporte afiliado 218.750 <br> UPC 300.000 <br> Empleador 0 <br> Afiliado total 518.750 <br> EPS 518.750 |
| 7 | 4.000.000, 1, 0 | IBC 4.000.000 <br> Aporte afiliado 160.000 <br> UPC 0 <br> Empleador 340.000 <br> Afiliado total 160.000 <br> EPS 500.000 |
| 8 | 4.000.000, 1, 1 | IBC 4.000.000 <br> Aporte afiliado 160.000 <br> UPC 150.000 <br> Empleador 340.000 <br> Afiliado total 310.000 <br> EPS 650.000 |
| 9 | 4.000.000, 1, 2 | IBC 4.000.000 <br> Aporte afiliado 160.000 <br> UPC 300.000 <br> Empleador 340.000 <br> Afiliado total 460.000 <br> EPS 800.000 |
| 10 | 4.000.000, 2, 0 | IBC 4.000.000 <br> Aporte afiliado 500.000 <br> UPC 0 <br> Empleador 0 <br> Afiliado total 500.000 <br> EPS 500.000 |
| 11 | 4.000.000, 2, 1 | IBC 4.000.000 <br> Aporte afiliado 500.000 <br> UPC 150.000 <br> Empleador 0 <br> Afiliado total 650.000 <br> EPS 650.000 |
| 12 | 4.000.000, 2, 2 | IBC 4.000.000 <br> Aporte afiliado 500.000 <br> UPC 300.000 <br> Empleador 0 <br> Afiliado total 800.000 <br> EPS 800.000 |
| 13 | 50.000.000, 1, 0 | IBC 43.750.000 <br> Aporte afiliado 1.750.000 <br> UPC 0 <br> Empleador 3.718.750 <br> Afiliado total 1.750.000 <br> EPS 5.468.750 |
| 14 | 50.000.000, 2, 0 | IBC 43.750.000 <br> Aporte afiliado 5.468.750 <br> UPC 0 <br> Empleador 0 <br> Afiliado total 5.468.750 <br> EPS 5.468.750 |
| 15 | 4.000.000, 3, 0 | "Tipo de afiliado no válido" |
| 16 | 4.000.000, 1, 3 | "Cantidad de padres no válida" |
| 17 | 0, 1, 0 | "Salario no válido" |
