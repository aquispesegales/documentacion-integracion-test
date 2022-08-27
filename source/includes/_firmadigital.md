# Firma Digital 

Métodos para firma Digital

## A) Generación de Token de Conexión

El servicio permite obtener un token el cual permite autenticarse en el momento de realizar las firmas consumiendo los servicios correspondientes

### HTTP Request
`POST https://springboot-oauth-heroku.herokuapp.com/oauth/token`

### Content-type
`application/json`

### Authorization

Los siguientes parametros  se envian en: <b>Authorization</b> de tipo  <b>Basic Auth</b>

 Nombre Atributo   |Tipo         | Descripción                 | Obligatorio 
-------------------|-------------|-----------------------------|-------------
 Username          | string      | Usuario                     |SI           
 Password          | string      | Contraseña                  |SI           


### Body
Los siguientes parametros son de tipo  <b>x-www-form-urlencoded</b>  <br>

| Nombre Atributo   |Tipo         | Descripción                 | Obligatorio |
|-------------------|-------------|-----------------------------|-------------|
| username          | string      | Usuario                     |SI           |
| password          | string      | Contraseña                  |SI           |
| grant_type        | string      | Tipo de Autenticación       |SI           |


### Objeto de respuesta

> Ejemplo de objeto de respuesta

```json
{
  "access_token": "eyJhbGciOiJSUzI1NiIsIn......",
  "token_type": "bearer",
  "refresh_token": "eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9....",
  "expires_in": 600,
  "scope": "read write",
  "inf_adicional": "...",
  "jti": "1f55abd1-22ea-4a4c-8b6a-cbffb6278dd1"
}
```

| Nombre Atributo| Tipo        | Descripción                  | 
|----------------|-------------|----------------------------------------------------|
| access_token   | string      | Token generado para el cliente de la API           |
| token_type     | string      | Es el tipo del token y siempre es Bearer           |
| refresh_token  | string      | Actualmente no se usa  |                                                        
| expires_in     | integer     | El tiempo de vida del token es de 10 minutos| 
| scope          | string      | Alcance del generador del token Actualmente es para lectura y escritura                       | 
| inf_adicional  | string      | Información adicional que puede venir en el token, actualmente no trae nada   | 
| jti            | string      | Identificador de el token        | 



