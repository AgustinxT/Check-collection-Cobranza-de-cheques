# Check_collection-Cobranza_de_cheques

## Table of Contents - Tabla de Contenidos

- [Project Overview](#project-overview)
- [Introduction](#introduction)
- [Introduccion](#introduccion)
- [Data source-Fuente de datos](#data-source-fuente-de-datos)
- [Tool-Excel](#tool-excel)
- [Funcionamiento del archivo](#funcionamiento-del-archivo)
- [File Operation](#file-operation)
- [Conclusiones](#conclusiones)
- [Insights](#insights)




## Project Overview

Demostration of how to register and automate the check collection process in a very simple way // Demostración de como registrar y automatizar el proceso de cobranzas de cheques de manera muy sencilla.

Aclaración: para asegurar la confidencialidad de los datos de la empresa se tomaron las siguientes determinaciones 

* Se asignó un ID a cada proveedor.
* No se revela informacion de los extractos bancarios.
* Se mantiene anónimo el nombre de la empresa.

Clarification: To ensure the confidentiality of the company's data, the following measures have been taken:

* ID Assignment: Each supplier has been assigned a unique ID.
* Bank Statement Protection: Information from bank statements is not disclosed.
* Company Anonymity: The company's name is kept anonymous.


## Introduction
A small construction company, with 45 employees and experiencing growth, uses physical and electronic checks (e-checks) for most of its payments to suppliers. The company faces irregular cash flows, as revenues depend on the biweekly progress of construction projects. However, approximately 50% of its expenses are regular, such as salaries, basic services, and corporate credit card payments, which have fixed due dates. This highlights the critical need for strict liquidity and working capital control. Proper management of these resources is essential to ensure the company's financial stability, meet financial obligations in a timely manner, and maximize the returns on idle funds whenever possible.

In the past, the company used to pay $2,000 annually for check recording software. This software allowed the entry of due dates, suppliers, amounts, and check IDs, and then it automatically generates a report of due dates on selected dates.

As a more practical and cost-effective alternative, a simple but effective Excel spreadsheet was developed that maintains and extends the functions of the previous application at no cost. In it, only four pieces of data associated with each check are entered: Payment or due date, supplier ID, amount, and check ID. In the "Not Cleared" tab, the amounts to be debited from the bank account are generated. Additionally, this spreadsheet allows for expanded analysis with other useful business metrics, including the average collection time for checks based on their amounts and a segmentation of each supplier. This provides a more complete and detailed view of the company's financial performance in relation to its suppliers.

### Daily Operation
In the daily routine, first thing in the morning, the company owner logs into the bank account to verify transactions, particularly which checks have been debited. For these checks, the owner copies the check ID, opens the relevant sheet in the "1. Checks" tab, and uses Ctrl+F to search for the check number. The check is then marked as "Cobrado" in the "Estado" column.

For expense forecasting, in the "2. No Cobrado" sheet, all checks that meet the following criteria are summed:

* They are "on term," meaning no more than 33 days have passed since their due date.
* They have not been cleared.
* Their due date does not exceed the current date.
* They fall within the date range of interest.

In the case of new checks being issued, simply enter their data in the spreadsheet, copy and paste the formulas already written in the cells above, and the rest of the process is automatic.

## Introduccion

Una pequeña empresa constructora, con 45 empleados y en pleno crecimiento, utiliza cheques físicos y electrónicos (e-cheques) para la mayoría de sus pagos a proveedores. Se enfrenta a flujos de ingresos irregulares, ya que los ingresos dependen del avance quincenal de las obras en construcción. Sin embargo, aproximadamente el 50% de sus gastos son regulares, como los salarios, servicios básicos y pagos de tarjetas de crédito corporativas, que tienen fechas de vencimiento fijas. Esto resalta la necesidad crítica de un estricto control de la liquidez y del capital de trabajo. La gestión adecuada de estos recursos es fundamental para garantizar la estabilidad financiera de la empresa, cumplir con las obligaciones financieras de manera oportuna y maximizar los rendimientos de los fondos ociosos cuando sea posible.

Anteriormente, la empresa pagaba $2,000 al año por un software de registro de cheques. Este software permitía ingresar la fecha de vencimiento, el proveedor, el monto y el ID del cheque, generando automáticamente un informe de vencimientos en las fechas seleccionadas.

Como una alternativa más práctica y económica, se desarrolló una simple pero eficaz hoja de cálculo en Excel que mantiene y amplía las funciones de la aplicación anterior a un costo nulo. En la misma, se introducen solo cuatro datos asociados a cada cheque: Fecha de pago o vencimiento, ID del proveedor, Importe e ID del cheque. En la pestaña "No Cobrados", se generan los montos que deben ser debitados de la cuenta bancaria. Además, esta hoja de cálculo permite ampliar los análisis con otras métricas útiles para el negocio, que incluyen el tiempo promedio de cobro de los cheques según su monto y una segmentación de cada proveedor. Esto proporciona una visión más completa y detallada del desempeño financiero de la empresa en relación con sus proveedores.

### Funcionamiento diario 
En la rutina diaria, a primera hora de la mañana, el dueño de la compañía ingresa a la cuenta bancaria para verificar los movimientos, especialmente los cheques debitados. Para estos últimos, copia el ID del cheque, abre la hoja correspondiente en la pestaña "1. Cheques" y, utilizando Ctrl+F, busca el número de cheque. Luego, marca el cheque en la columna de "Estado" como "Cobrado".

Para la previsión de gastos, en la hoja "2. No Cobrados", se suman todos los cheques que cumplan con los siguientes requisitos:

* Estar "en término", es decir, que no hayan transcurrido más de 33 días desde su vencimiento.
* No haber sido cobrados.
* Que su fecha de vencimiento no sea posterior a la fecha actual.
* Estar comprendidos en el rango de fechas de interés.

En el caso de que se hayan emitido cheques nuevos, basta con cargar sus datos en la planilla, copiar y pegar las fórmulas ya escritas en las celdas de arriba y el resto del proceso es automático.

## Data source-Fuente de datos

For this project, primary data is used, obtained directly from the check duplicates, which are created with each issuance and then loaded into the file. Subsequently, from the bank statements of each month of the year 2023 in PDF format, the information on the date the checks were debited from the account is extracted. This was done using Power Query and the data was combined using the append function.

Para este proyecto, se emplean datos de tipo primario, obtenidos directamente de los duplicados de cheques, los cuales se generan con cada emisión para luego cargarlos en el archivo. 
Posteriormente, a partir de los resúmenes bancarios de cada mes del año 2023, en formato PDF, se extrae la información de la fecha en que los cheques fueron debitados de la cuenta. Esto se realizó con Power Query y se combinaron los datos utilizando la función de anexar (append).

## Tool-Excel

Funciones utilizadas: 
* nested if statements  / condicionales SI anidados
* pivot tables  / tablas dinámicas
* sum.if  / sumar si
* date dif / sifecha 
* data validation  / validación de datos
* vlookup-index&match   / buscarv or indice&coincidir

## Funcionamiento del archivo

La planilla consta de 3 paginas. 

### 1. Cheques
La primera, consta de una tabla dividida en data entry y formulas, ya que la data primaria que será procesada y analizada se carga en esos 4 campos. Para luego pasar a las fórmulas, las cuales ya estan construidas, quien cargue los cheques, solo tiene que agregar una fila extra, y darle copiar y pegar a la sección formulas en la(s) filas de interés. 

Los campos de formulas se construyen de la siguiente manera:  
* Cobrado el día: se utilizó un index-match para cruzar el ID cheque con la fecha en la que fue cobrado
* Clasificador: al hacer un histograma del monto de los cheques (ver en la hoja "3.Pivot table"), se observó que la mayoría de los cheques estan debajo del promedio (288 aproximadamente), por lo que se clasificó a cada cheque en 3 rangos: menor a 288, mayor a 288 & menor a 500, mayor a 500.

![image](https://github.com/AgustinxT/Check-collection-Cobranza-de-cheques/assets/130587628/47e4cb8a-a3e3-4300-80b1-ad918c8db07d)

* Término 33 días: si el cheque figura como No cobrado por mas de 33 dias, se lo considera fuera de termino, y queda excluido.
* Tipo de banco: en caso de que la empresa tenga cuenta en mas de una institucion bancaria.
* Estado: Validacion de datos para marcar si el cheque fue cobrado o no (esto forma parte del control diario de los saldos).
* Day-dif: al igual que clasificador, es una formula para el posterior análisis, indica cuanto tiempo transcurrió entre el pago y el vencimiento del cheque.

### 2. No Cobrados

Se actualiza automáticamente teniendo en cuenta la fecha actual. Para realizar este análisis, se decidió utilizar la fecha del 24 de mayo, pero si en el recuadro naranja se escribe la fórmula =HOY(), toda la planilla se sincronizará a partir de la fecha actual.

La lógica es mostrar los vencimientos acumulados para el día actual y a futuro (hasta 90 días). En la columna "monto a pagar" se indica lo que teóricamente se debitaría de la cuenta bancaria de la empresa en concepto de cheques; y a la derecha, para más detalle, se ven los vencimientos intradiarios o a una fecha particular.

Con este sistema, la empresa controla los saldos a primera hora de la mañana, determina si hay suficiente dinero (o si sobra), y toma decisiones a partir de esa información.

### 3. Pivot table

Finalmente, aquí se presenta un análisis a partir de tablas dinámicas, obteniendo dos indicadores muy relevantes:

1. Suma total por proveedor: Determina la importancia de cada proveedor, lo cual puede ser útil para saber cuánto se compra a cada uno y a cuáles se podría comprar más, por ejemplo.
2. Periodo medio de cobro de los cheques por clasificador y proveedor: Muestra cuánto tiempo, en promedio, tardan en cobrarse los cheques después de su vencimiento, segmentados según clasificador y proveedor. Esta información es muy útil porque, en épocas en las que se busca mantener el saldo justo y necesario en la cuenta bancaria, se puede recurrir a la probabilidad para calcular un saldo estimado, de manera que no se pierda la oportunidad de invertir saldos ociosos.

## File Operation
The spreadsheet consists of 3 pages.

### "1. Checks"
The first page consists of a table divided into data entry and formulas, as the primary data to be processed and analyzed is entered in these 4 fields. Then, moving on to the formulas, which are already built, whoever enters the checks only needs to add an extra row and copy and paste the formula section into the relevant ones.

The formula fields are constructed as follows:

* Cleared on the day: An index-match was used to cross-reference the check ID with the date it was cleared.
* Classifier: When creating a histogram of check amounts (see in the "3. Pivot table" sheet), it was observed that most checks are below the average (approximately 288), so each check was classified into 3 ranges: less than 288, greater than 288 & less than 500, greater than 500.
* 33-Day Term: If the check is listed as not cleared for more than 33 days, it is considered overdue and is excluded.
* Bank Type: In case the client has more than one bank account.
* Status: Data validation to mark whether the check was cleared or not (this is part of the daily balance control).
* Day-dif: Similar to the classifier, it is a formula for subsequent analysis, indicating how much time elapsed between the payment and the due date of the check.

### "2. Not Cleared"
It updates automatically considering the current date. To perform this analysis, it was decided to use the date of May 24th, but if the formula =TODAY() is written in the orange box, the entire spreadsheet will synchronize from the current date.

The logic is to display accumulated due dates for the current day and future (up to 90 days). The "amount to be paid" column indicates what would theoretically be debited from the company's bank account for checks; and to the right, for more detail, intraday due dates or a specific date are shown.

With this system, the company checks balances first thing in the morning, determines if there is enough money (or if there is excess), and makes decisions based on that information.

### 3. Pivot table
Finally, here is an analysis using pivot tables, obtaining two very relevant indicators:

Total sum by client: Determines the importance of each supplier, which can be useful for understanding how much is purchased from each and identifying suppliers from whom more could be purchased, for example.
Average collection period of checks by classifier and client: Shows how long, on average, it takes for checks to be cleared after their due date, segmented by classifier and supplier. This information is very useful because, in periods when maintaining the exact necessary balance in the bank account is crucial, probability can be used to estimate a balance, ensuring that the opportunity to invest idle funds is not missed.


## Conclusiones

Si bien el análisis se puede seguir extendiendo segun las necesidades de la empresa, se utilizó la información histórica para realizar un análisis de todo el 2023. 
Encontrando que los top 10 abarcan un 80% de la suma total de las compras realizadas. Y segun los rangos, el periodo medio de cobro de cheques es de 6 dias, aunque conforme aumente el monto del cheque, menor es su tardanza. En promedio, los mayores a 500, tardan 3 dias, mientras que los demas, tardan aproximadamente 5 y 7 dias luego del vencimiento. 

Este ultimo hallazgo es muy útil a nivel estratégico, debido a que montos grandes pueden distribuirse en pequeñas porciones para influir en la tardanza del cobro y tener un mejor manejo de los saldos en la cuenta bancaria.

## Insights

While the analysis could be further extended according to the company's needs, historical information was used to conduct an analysis of the entire year of 2023. It was found that the top 10 suppliers account for 80% of the total purchases made. Additionally, according to the ranges of amounts, it was found that the average collection period of checks is 6 days, although this period tends to decrease as the check amount increases. On average, checks over 500 dollars are cashed in only 3 days, while smaller checks take approximately 5 to 7 days after their due date to be cashed.

This latter finding is very useful at a strategic level. Large amounts can be subdivided into smaller payments to influence the speed of collection and to make better decisions when it comes to idle funds


