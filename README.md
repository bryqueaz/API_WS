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

## Tema 1 : Preparar ambiente Web Service

### Paso #1

**Crear estructura de ambiente de trabajo**

*   Se debe crear los directorios en el home del usuario de la prueba, ejemplo
    *   /home/$USER$/WebServices/compra
    *   /home/$USER$/WebServices/compra/respuesta
    *   /home/$USER$/WebServices/venta
    *   /home/$USER$/WebServices/venta/respuesta

*   Dentro del directorio /home/$USER$/WebServices/compra, se debe crear un archivo llamado:
    *   request_soap1_1-compra.xml
*   Dentro del directorio /home/$USER$/WebServices/venta, se debe crear un archivo llamado:
    *   request_soap1_2-venta.xml

**Crear archivos de configuración**

*   Editar el archivo de configuración request_soap1_1-compra.xml, con la siguiente estructura:

```
<?xml version="1.0" encoding="utf-8"?>
<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
  <soap:Body>
    <ObtenerIndicadoresEconomicos xmlns="http://ws.sdde.bccr.fi.cr">
      <tcIndicador>317</tcIndicador>
      <tcFechaInicio>15/11/2019</tcFechaInicio>
      <tcFechaFinal>15/11/2019</tcFechaFinal>
      <tcNombre>S</tcNombre>
      <tnSubNiveles>S</tnSubNiveles>
    </ObtenerIndicadoresEconomicos>
  </soap:Body>
</soap:Envelope>


```








