# Check-collection-Cobranza-de-cheques
Demostration of how to register and automate the check collection process in a very simple way // Demostración de como registrar y automatizar el proceso de cobranzas de cheques de manera muy sencilla

## Introduction 

A small-sized construction company with 45 employees is experiencing rapid growth and relies on both physical and electronic checks (e-checks) for the majority of its supplier payments. The company faces irregular income flows, as revenue is dependent on the biweekly progress of ongoing construction projects. However, approximately 50% of its expenses are regular, including payroll, utility bills, corporate credit card payments, etc., all with fixed due dates. This underscores the critical need for rigorous liquidity and working capital management. Proper management of these resources is essential to ensure the company's financial stability, meet financial obligations promptly, and maximize returns on idle funds when available

In the past, the company used to spend $2000 per year on check registration software. This software allowed entering data such as the due date, supplier, amount, and check ID, automatically generating a report of due dates on selected dates.

As a more practical and cost-effective alternative, a simple yet powerful Excel spreadsheet was developed. In this spreadsheet, the same data is entered into a table, and on the "Due Dates" tab, the amounts to be debited from each bank account are generated. Additionally, this spreadsheet allows for expanded analysis, considering additional criteria such as "out of term" checks (which expire after 32 days past their due date). Other useful metrics for the business could include the average time taken to collect checks based on their amount and the behavior of each supplier. This provides a more comprehensive and detailed insight into the company's financial performance.

## Introducción

Una empresa constructora de tamaño pequeño, con 45 empleados y en pleno crecimiento, utiliza cheques físicos y electrónicos (e-cheques) para la mayoría de sus pagos a proveedores. Se enfrenta a flujos de ingresos irregulares, ya que los ingresos dependen del avance quincenal de las obras en construcción. Sin embargo, aproximadamente el 50% de sus gastos son regulares, como los salarios, servicios básicos y pagos de tarjetas de crédito corporativas, que tienen fechas de vencimiento fijas. Esto resalta la necesidad crítica de un estricto control de la liquidez y del capital de trabajo. La gestión adecuada de estos recursos es fundamental para garantizar la estabilidad financiera de la empresa, cumplir con las obligaciones financieras de manera oportuna y maximizar los rendimientos de los fondos ociosos cuando sea posible.

Anteriormente, la empresa pagaba $2000 al año por un software de registro de cheques. Este software permitía ingresar datos como la fecha de vencimiento, el proveedor, el monto y el ID del cheque, generando automáticamente un informe de vencimientos en las fechas seleccionadas.

Como una alternativa más práctica y económica, se desarrolló una simple pero eficaz hoja de cálculo en Excel. En esta hoja, se introducen los mismos datos en una tabla y, en la pestaña "Vencimientos", se generan los montos que deben ser debitados de cada cuenta bancaria. Además, esta hoja de cálculo permite ampliar los análisis, considerando criterios adicionales, como los cheques "fuera de término" (que caducan después de 32 días de su vencimiento). Otras métricas útiles para el negocio podrían incluir el tiempo promedio de cobro de los cheques según su monto y el comportamiento de cada proveedor. Esto proporciona una visión más completa y detallada del desempeño financiero de la empresa.

## Data source

Para este proyecto, se emplean datos de tipo primario obtenidos directamente de los cheques duplicados, que se realizan con cada emisión para luego cargar en el archivo. 

## Tool : Excel

Funciones utilizadas: 
* nested if statements 
* pivot tables 
* sum.if
* date dif
* data validation
* vlookup-index&match

## Funcionamiento del archivo

La planilla consta de 3 paginas. 

### 1. Cheques
La primera, consta de una tabla dividida en data entry y formulas, ya que la data primaria que será procesada y analizada se carga en esos 4 campos. Para luego pasar a las fórmulas, las cuales ya estan construidas, quien cargue los cheques, solo tiene que agregar una fila extra, y darle copiar y pegar a la sección formulas en la(s) filas de interés. 

Los campos de formulas se construyen de la siguiente manera:  
* Cobrado el día: se utilizó un index-match para cruzar el ID cheque con la fecha en la que fue cobrado
* Clasificador: al hacer un diagrama de dispersión del monto de los cheques (ver en la hoja "3.Pivot table"), se observó que la mayoría de los cheques estan debajo del promedio (271k aproximadamente), por lo que se clasificó a cada cheque en 3 rangos: menor a 271k, mayor a 271k & menor a 500k, mayor a 500k.
* Término 33 días: si el cheque figura como No cobrado por mas de 33 dias, se lo considera fuera de termino, y queda excluido.
* Tipo de banco: por si el cliente tiene mas de una cuenta bancaria
* Estado: Validacion de datos para marcar si el cheque fue cobrado o no (esto forma parte del control diario de los saldos).
* Day-dif: al igual que clasificador, es una formula para el posterior análisis, indica cuanto tiempo transcurrió entre la cobranza y el vencimiento del cheque.

### 2. No Cobrados

Se actualiza automáticamente teniendo en cuenta la fecha del día actual. A fines de poder hacer este análisis se decidió cortar en mayo/24, pero si en el recuadro naranja se escribe la formula =HOy(), toda la planilla se sincronizará a partir de la misma.
La lógica es mostrar los vencimientos acumulados para el dia actual y a futuro (hasta 90 días). En la columna "monto a pagar" es lo que teóricamente se debitaría de la cuenta bancaria de la empresa en concepto de cheques; y a la derecha, para mas detalle, se ven los vencimiento intradiarios o a una fecha particular.

Con este sistema, la empresa controla a primera hora de la mañana los saldos, determina si hay suficiente dinero (o si sobra), y toma decisiones a partir de la misma.

### 3. Pivot table

Finalmente, aquí se ve un análisis a partir de tablas dinámicas, obteniendo dos indicadores muy relevantes.
1. Suma total por cliente, determinando la importancia de cada uno, esto puede ser util para mejorar vinculos-relaciones y acceder a mejores condiciones de compra.
2. Periodo medio de cobro de los cheques por clasificador y cliente, aquí se puede apreciar cuanto en promedio tardan en cobrarse cheques luego de su vencimiento. Esto es muy útil en épocas donde se necesita un estricto seguimiento de los saldos.

## Summarize - Conclusiones

Si bien el análisis se puede seguir extendiendo segun las necesidades de la empresa, con esta información se decidió categorizar los clientes, encontrando que los primeros 3 abarcan un 40% de la suma total de las compras realizadas. Y segun los rangos, el periodo medio de cobro de cheques es de x dias, aunque los mayores a 500mil, prácticamente no tienen atraso, los demas, tardan aproximadamente 3 dias luego del vencimiento. 
Este ultimo hallazgo es muy útil a nivel estratégico, debido a que montos grandes pueden distribuirse en pequeñas porciones para i) influir en la urgencia del cobro y ii) para el receptor, tiene la ventaja debido a que los cheques pueden endosarse, utilizandolos como medio de pago y evitando el impuesto a los debitos y creditos bancarios, ventaja que puede utilizarse para negociación de monto y plazo de compra.

## Disclaimer

Para asegurar la confidencialidad e integridad de los datos, no se revela el nombre de la empresa ni los nombres de sus clientes.

## pendientes

buscarv con fechas para el 2023
pasar al ingles 
verificar que no hayan faltado formulas
subir archivo final

