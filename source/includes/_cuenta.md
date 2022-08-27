# Cuenta

Consulta a la entidad financiera o agente externo de la información del cliente.

## Crear Nueva Cuenta

El método permite crear nueva cuenta para un Cliente, el cliente ya debe estar registrado previamente

### HTTP Request
POST = localhost:9090/api/v1/cuenta

### Content-type
`application/json`

### Objeto - Request

> Ejemplo de objeto de envio

```json
{
    "clienteId":"1",
    "nombreCuenta":"SUELDO",
    "descripcion":"DESCRIPCIÓN"
}
```

Atributo | Tipo | Requerido | Descripción
-------- | ---- | --------- | -----------
clienteId | string | true | Identificador de Cliente
nombreCuenta | string | false | Nombre de la Cuenta
descripcion | string | false | Descripción de la Cuenta

### Objeto de respuesta

> Ejemplo de objeto de respuesta

```json
{
    "codigo": "COD1000",
    "mensaje": "Proceso Completado",
    "elementoGenerico": "0.00"
}
```

Atributo | tipo | Requerido | Descripción
-------- | ---- | --------- | -----------
codigo | string | true | Código de Respuesta
mensaje | string | true | Mensaje de Respuesta
elementoGenerico | string | false | Información Adicional de Respuesta


## Crear Deposito y Retiro (Transacción)

El método permite crear nueva transacción de tipo Deposito o Retiro 

### HTTP Request
POST = localhost:9090/api/v1/transaccion

### Content-type
`application/json`

### Objeto - Request

> Ejemplo de objeto de envio

```json
{
    "cuentaId":"1",
    "detalle":"DETALLE DE LA TRANSACCIÓN",
    "ingreso":"100",
    "egreso":"",
    "saldo":"100",
    "tipoTransaccionId":1003
}
```

Atributo | Tipo | Requerido | Descripción
-------- | ---- | --------- | -----------
cuentaId | string | true | Identificador de Cuenta 
detalle | string | true |Dealle de Transacción
ingreso | string | false | Monto en caso de ser un DEPOSITO
egreso | string | false | Monto en caso de ser un RETIRO
saldo | string | false | Monto Saldo Actual
tipoTransaccionId | Integer | true | tipo de transacción 1003 (DEPOSITO) y 1004 (RETIRO)


### Objeto de respuesta

> Ejemplo de objeto de respuesta

```json
{
    "codigo": "COD1000",
    "mensaje": "Proceso Completado",
    "elementoGenerico": null
}
```

Atributo | tipo | Requerido | Descripción
-------- | ---- | --------- | -----------
codigo | string | true | Código de Respuesta (Mayor Información ver ANEXO)
mensaje | string | true | Mensaje de Respuesta
elementoGenerico | string | false | Información Adicional de Respuesta


## Consultar Saldo Cuenta

El método que permite obtener Saldo de una Cuenta

### HTTP Request
GET = localhost:9090/api/v1/saldo-por-nrocuenta/{nroCuenta}

### URL Parameters
Atributo | Tipo | Requerido | Descripción
-------- | ---- | --------- | -----------
nroCuenta | string | true | Número de Cuenta por el cual va buscar las transacciones

### Objeto de respuesta

> Ejemplo de objeto de respuesta

```json
{
    "codigo": "COD1000",
    "mensaje": "Proceso Completado",
    "saldo": 0.0
}
```

Atributo | tipo | Requerido | Descripción
-------- | ---- | --------- | -----------
codigo | string | true | Código de Respuesta (Mayor Información ver ANEXO)
mensaje | string | true | Mensaje de Respuesta
saldo | Double | false | Saldo actual de la Cuenta

## Consultar Historico Cuenta

El método que permite obtener todas las transacciones de una determinada Cuenta

### HTTP Request
GET = localhost:9090/api/v1/transaccion/verhistorico-por-cuenta/{nroCuenta}
### URL Parameters
Atributo | Tipo | Requerido | Descripción
-------- | ---- | --------- | -----------
nroCuenta | string | true | Número de Cuenta por el cual va buscar las transacciones

### Objeto de respuesta

> Ejemplo de objeto de respuesta

```json
{
    "codigo": "COD1000",
    "mensaje": "Proceso Completado",
    "elementoGenerico": [
        {
            "nombreCliente": "EDWIN",
            "apPaterno": "QUISPE",
            "apMaterno": "SEGALES",
            "nroCuenta": "1203000421513366",
            "deposito": 100.0,
            "retiro": null,
            "monto": 100.0,
            "tipoTransaccion": "DEPOSITO"
        },
        {
            "nombreCliente": "EDWIN",
            "apPaterno": "QUISPE",
            "apMaterno": "SEGALES",
            "nroCuenta": "1203000421513366",
            "deposito": 100.0,
            "retiro": null,
            "monto": 100.0,
            "tipoTransaccion": "DEPOSITO"
        }
    ]
}
```

Atributo | tipo | Descripción
-------- | ----  | -----------
codigo | string  | Código de Respuesta (Mayor Información ver ANEXO)
mensaje | string  | Mensaje de Respuesta
elementoGenerico.nombreCliente | String | Nombre Cliente
elementoGenerico.apPaterno | String  | Apellido Materno
elementoGenerico.apMaterno | String  | Apellido Paterno
elementoGenerico.nroCuenta | String  | número de Cuenta
elementoGenerico.deposito | Decimal  | deposito
elementoGenerico.retiro | Decimal  | Nombre Cliente
elementoGenerico.monto | Decimal  | Monto o Saldo Actual
elementoGenerico.tipoTransaccion | Integer  | Nombre del Tipo de la Transacción

## Obtener todas las Cuentas

El método que permite obtener todas las cuentas registradas

### HTTP Request
GET = localhost:9090/api/v1/cuentas-todos



### Objeto de respuesta

> Ejemplo de objeto de respuesta

```json
{
    "codigo": "COD1000",
    "listadoCuentas": [
        {
            "cuentaId": 1,
            "numeroCuenta": "1203000421513366",
            "clienteId": 1,
            "nombreCuenta": "SUELDO",
            "descripcion": "DESCRIPCIÓN",
            "moneda": 1000,
            "saldo": 0.0
        },
        {
            "cuentaId": 2,
            "numeroCuenta": "1313740854428702",
            "clienteId": 1,
            "nombreCuenta": "SUELDO",
            "descripcion": "DESCRIPCIÓN",
            "moneda": 1000,
            "saldo": 0.0
        }
    ],
    "mensaje": "Proceso Completado"
}
```

Atributo | tipo  | Descripción
-------- | ----  | -----------
codigo | string  | Código de Respuesta (Mayor Información ver ANEXO)
mensaje | string  | Mensaje de Respuesta
listadoCuentas.cuentaId | Integer  | Identificador de la Cuenta
listadoCuentas.numeroCuenta | String| Número de la Cuenta
listadoCuentas.clienteId | Integer  | Identificador de Cliente
listadoCuentas.nombreCuenta | String  | Nombre de la Cuenta
listadoCuentas.descripcion | String | Descripción de la Cuenta
listadoCuentas.moneda | Integer  | 1005 (es Bs, este valor deve estar registrado en tabla Dominios, pero por falta de tiempo se esta enviando 1000)
listadoCuentas.saldo | Decimal  | Saldo de Cuenta