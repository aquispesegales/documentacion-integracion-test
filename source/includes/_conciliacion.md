# Conciliación 

Métodos para la conciliación de pagos hacia SF

## Conciliación de pago de pólizas

El método consulta al banco o entidad externa las pólizas que se han pagado en un rango de fechas

### HTTP Request
`GET por/definir`

### Content-type
`application/json`

### Objeto de consulta

> Ejemplo de objeto de consulta

```json
{
    "fechaInicial" : "2022-05-21 00:00:00",
    "fechaFinal" : "2022-05-21 24:59:59",
    "tipoProducto" : ""
}
```

Atributo | Tipo | Descripción
-------- | ---- | -----------
fechaInicial | Date | Fecha inicial de la consulta de pólizas pagadas
fechaFinal | Date | Fecha final de la consulta de pólizas pagadas
tipoProducto | string | `*por codificar`

### Objeto de respuesta
> Ejemplo de objeto de respuesta

```json
{
    "operaciones": [
        {
            "numeroDeCertificado": "SC-DL22-000001",
            "numeroDeOperacion": "123456",
            "fechaDeDesembolso": "2022-05-21 00:00:00",
            "fechaDeVencimientoOperacion" : "2025-05-21 00:00:00",
            "montoDesembolsado": 100000,
            "saldoInsoluto": 90000,
            "interesesReportados": 0,
            "periodoPago": 30,
            "primaTotal": 1000,
            "numeroCuentaCMS": "",
            "diferimiento": false
        },
        {
            "numeroDeCertificado": "SC-DL22-000002",
            "numeroDeOperacion": "123456",
            "fechaDeDesembolso": "2022-05-21 00:00:00",
            "fechaDeVencimientoOperacion" : "2025-05-21 00:00:00",
            "montoDesembolsado": 100000,
            "saldoInsoluto": 90000,
            "interesesReportados": 0,
            "periodoPago": 30,
            "primaTotal": 1000,
            "numeroCuentaCMS": "",
            "diferimiento": false
        },
        {
            "numeroDeCertificado": "SC-DL22-000003",
            "numeroDeOperacion": "123456",
            "fechaDeDesembolso": "2022-05-21 00:00:00",
            "fechaDeVencimientoOperacion" : "2025-05-21 00:00:00",
            "montoDesembolsado": 100000,
            "saldoInsoluto": 90000,
            "interesesReportados": 0,
            "periodoPago": 30,
            "primaTotal": 1000,
            "numeroCuentaCMS": "",
            "diferimiento": false
        }
    ]
}
```

Atributo | Tipo | Descripción
-------- | ---- | -----------
operaciones | Arreglo de [Items de conciliación](#items-de-conciliacion) | Las pólizas a conciliar el pago

### Items de conciliación

Atributo | Tipo | Descripción
-------- | ---- | -----------
numeroDeCertificado | string | Número de certificado del producto asegurado
numeroDeOperacion | string | Número de operación o referencia del producto asegurado
fechaDeDesembolso | Date | Fecha en la cual se desembolsó el crédito asegurado. Formato: `yyyy-MM-dd HH:mm:ss`
fechaDeVencimientoOperacion | Date | Fecha en la cual se vence el crédito asegurado. Formato: `yyyy-MM-dd HH:mm:ss`
montoDesembolsado | number | Valor del crédito que se desembolsó
saldoInsoluto | number | Valor del saldo insoluto del crédito desembolsado
interesesReportados | number | `*por definir`
periodoPago | number | Cantidad de días que se pagan en la cuota
primaTotal | number | Valor total de prima cobrado para el seguro
numeroCuentaCMS | string | Número identificador para tarjetas de crédito
diferimiento | boolean | 