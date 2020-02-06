# Capacitación básica API WS

Especificación del API

Objetivo final poder obtener el tipo de cambio(compra y venta) actual en Dólares del Banco Central de Costa Rica.

**Referencia del API del Banco Central:**

* []() https://gee.bccr.fi.cr/Indicadores/Suscripciones/WS/wsindicadoreseconomicos.asmx?op=ObtenerIndicadoresEconomicos

**Recomendación revisar si la información es correcta al consumir los servicios.**

* []() https://gee.bccr.fi.cr/indicadoreseconomicos/Cuadros/frmVerCatCuadro.aspx?idioma=1&CodCuadro=%20400

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
*   Editar el archivo de configuración request_soap1_2-venta.xml, con la siguiente estructura:

```
<?xml version="1.0" encoding="utf-8"?>
<soap12:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap12="http://www.w3.org/2003/05/soap-envelope">
  <soap12:Body>
    <ObtenerIndicadoresEconomicos xmlns="http://ws.sdde.bccr.fi.cr">
      <tcIndicador>318</tcIndicador>
      <tcFechaInicio>15/11/2019</tcFechaInicio>
      <tcFechaFinal>15/11/2019</tcFechaFinal>
      <tcNombre>S</tcNombre>
      <tnSubNiveles>S</tnSubNiveles>
    </ObtenerIndicadoresEconomicos>
  </soap12:Body>
</soap12:Envelope>

```

## Tema 2 : Consumir el Servicio de Compra SOAP 1.1

Objetivo

Para ello se debe consumir el servicio usando el  Protocolo de HTTP, utilizando la configuración el archivo request_soap1_1-compra.xml.

*   Se debe hacer uso de la especificación SOAP 1.1, para realizar el request.
*   Editar el archivo y cambiar el valor de los campos tcFechaInicio y tcFechaFinal por 05/11/2019(Puede realizar una copia del archivo en caso de realizar una incorrecta edición).
*   Usar las siguiente cabeceras:
    *   Content-Type: text/xml; charset=utf-8
    *   SOAPAction: http://ws.sdde.bccr.fi.cr/ObtenerIndicadoresEconomicos
*   La url para consumir el servicio
    *   http://indicadoreseconomicos.bccr.fi.cr/indicadoreseconomicos/WebServices/wsIndicadoresEconomicos.asmx
*   Almacenar la respuesta con el nombre del archivo: respuesta_compra_soap1_1.xml
    *   En el directorio /home/$USER$/WebServices/compra/respuesta

## Tema 3 : Consumir el Servicio de Venta

Objetivo

Para ello se debe consumir el servicio usando el  Protocolo de HTTP bajo el método POST.

Para consumir el API se puede utilizar clientes por línea de comando como son las herramientas de curl, wget(Recomendados).

*   Se debe hacer uso de HTTP POST, para realizar el request.
*   Las variables de envio(POST DATA), con sus respectivos valores:
    *   tcIndicador=318
    *   tcFechaInicio=05/11/2019
    *   tcFechaFinal=05/11/2019
    *   tcNombre=S
    *   tnSubNiveles=S
*   La url para consumir el servicio
    *   http://indicadoreseconomicos.bccr.fi.cr/indicadoreseconomicos/WebServices/wsIndicadoresEconomicos.asmx/ObtenerIndicadoresEconomicos
*   Almacenar la respuesta con el nombre del archivo: respuesta_venta_post.xml
    *   En el directorio /home/$USER$/WebServices/venta/respuesta












