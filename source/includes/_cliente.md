# Cliente

Consulta a la entidad financiera o agente externo de la información del cliente.

## Crear Nuevo Cliente

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


## Obtener Todos los Clientes

El método permite obtener todos los clientes

### HTTP Request
POST = localhost:9090/api/v1/cliente-todos


### Objeto de respuesta

> Ejemplo de objeto de respuesta

```json
{
    "listadoClientes": [
        {
            "clienteId": 1,
            "codigoCliente": "COD_9133041",
            "nombres": "EDWIN",
            "apPaterno": "QUISPE",
            "apMaterno": "SEGALES",
            "ci": "9133041",
            "direccion": "VILLA ADELA",
            "fechaRegistro": "2022-08-26T19:53:29.299+00:00",
            "estadoId": 1000
        }
    ],
    "codigo": "COD1000",
    "mensaje": "Proceso Completado"
}
```

Atributo | tipo  | Descripción
-------- | ----  | -----------
codigo | string | Código de Respuesta
mensaje | string| Mensaje de Respuesta
listadoClientes.clienteId | Integer  | Identificador Cliente
listadoClientes.codigoCliente | string  | Código de Cliente
listadoClientes.nombres | string  | Nombres
listadoClientes.apPaterno | string  | Apellido Paterno
listadoClientes.apMaterno | string  | Apellido Materno
listadoClientes.ci | string  | CI (Numero de Carnet)
listadoClientes.direccion | string  | Dirección
listadoClientes.fechaRegistro | datetime  | Fecha de Registro
listadoClientes.estadoId | Integer  | Estado