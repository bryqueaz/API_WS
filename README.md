# Capacitación básica API WS

Especificación del API

Objetivo final poder obtener el tipo de cambio(compra y venta) actual en Dólares del Banco Central de Costa Rica.

**Referencia del API del Banco Central:**

* []() http://indicadoreseconomicos.bccr.fi.cr/indicadoreseconomicos/WebServices/wsIndicadoresEconomicos.asmx?op=ObtenerIndicadoresEconomicos

**Recomendación revisar si la información es correcta al consumir los servicios.**

* []()http://indicadoreseconomicos.bccr.fi.cr/indicadoreseconomicos/cuadros/frmvercatcuadro.aspx?CodCuadro=400

**Detalle de de especificación**

Los siguiente campos describen cada variable utilizada por el API de tipo de cambio:

*   tcIndicador
    *   317: Codigo de Compra
    *   318: Codigo Venta
*   tcFechaInicio
    *   Fecha Inicio de la consulta en formato: dd/mm/yyyy (día/mes/año)
*   tcFechaFinal
    *   Fecha fin de la consulta en formato: dd/mm/yyyy (día/mes/año)
*   tcNombre
    *   Por defecto: S
*   tnSubNiveles 
    *   Por defecto: S
