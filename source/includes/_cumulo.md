# Cúmulo

Método para la consulta de cúmulo para clientes titulares / codeudores hacia SFDC

Los cúmulos de los saldos insolutos por asegurado, deben ser enviados al Core de seguros en la moneda del crédito que está siendo solicitado y al tipo de cambio que maneje el banco. 

#### OPERACIONES NORMALES 
El cúmulo es el resultado de la suma de saldos de todas las operaciones vigentes con seguro por producto (licitado y no licitado), más los límites de las líneas de crédito y montos disponibles de tarjetas de crédito vigentes que tengan seguro. 

#### NUEVAS LÍNEAS DE CRÉDITO 
El cúmulo es el resultado de la suma de saldos de todas las operaciones vigentes que tengan seguro fuera de la línea de crédito por producto (licitado y no licitado), más los límites de las líneas de crédito y montos disponibles de tarjetas de crédito vigentes que tengan seguro.

#### OPERACIONES BAJO LÍNEA DE CRÉDITO YA INSTRUMENTADA 
No genera cúmulo y por tanto el Core de seguros no solicita integración. 

#### REPROGRAMACIONES 
El cúmulo es el resultado de la suma de los saldos de las operaciones vigentes que tengan por producto (licitado y no licitado), considerando la particularidad de las líneas de crédito y montos disponibles de tarjetas de crédito y se resta el monto de la operación seleccionada a dar de baja por la reprogramación. 

#### REFINANCIAMIENTO 
El cúmulo es el resultado de la suma de los saldos de las operaciones vigentes que tengan seguro por producto (licitado y no licitado), considerando la particularidad de las líneas de crédito y montos disponibles de tarjetas de crédito y se resta el monto de la operación seleccionada a dar de baja por el refinanciamiento. 


## Cúmulo de clientes

El método consulta al banco o entidad externa el valor de cúmulo del cliente

### HTTP Request
`GET por/definir`

### Content-type
`application/json`

### Objeto de consulta

> Ejemplo de objeto de consulta

```json
{
    "tipoIdentificacion": "CI",
    "numeroDeIdentificacion": "123456",
    "complementoIdentificacion": "1A",
    "extensionIdentificacion": "SC",
    "tipoProducto": "",
    "tipoDeOperacion": "",
    "jts": 00000,
    "numeroDeLineaDeCredito": ""
}
```

Atributo | Tipo | Descripción
-------- | ---- | -----------
tipoIdentificacion | string | Codificación del documento de identificación de deudor
numeroDeIdentificacion | number | Número de identificación
complementoIdentificacion | string | Complemento al número de identificación
extensionIdentificacion | string | Sufijo con el código del estado de emisión del carnet
tipoProducto | string | [Tipo de Operación](#tipo-de-operacion)
tipoDeOperacion | string | 
jts | number | 
numeroDeLineaDeCredito | string |

### Objeto de respuesta
> Ejemplo de objeto de respuesta

```json
{
    "saldoAdeudado": 987654
}
```

Atributo | Tipo | Descripción
-------- | ---- | -----------
saldoAdeudado | number | Valor adeudado a la fecha de consulta por el cliente titular/codeudor