# Design de API

O estilo arquitetural REST tem como princípio definir recursos que podem ser manipulados usando um pequeno conjunto de métodos. Os recursos são conhecidos como substantivos (nouns) e os métodos como verbos (verbs) das APIs. Utilizando o protocolo HTTP, os nomes de recursos são mapeados para URLs e os métodos são associados aos métodos HTTP POST, GET, PUT, PATCH e DELETE.

## Use RESTful service URLs

- URL identifica um recurso
- URLs devem incluir substantivos (no plural) e não verbos
- Métodos HTTP são usados para operar nos recursos
- Os códigos de status de resposta HTTP devem ser usados para representar o resultado das operações nos recursos

## Use HTTP methods and status codes

Examplos:
- GET /magazines  
  List all magazines contained within the /magazines resource  
  - _Status Codes_:  
  200 OK – no error  
  404 Not Found – the “magazines” resource does not exist

- POST /magazines  
  Create new magazine within the /magazines resource  
  - _Status Codes_:  
    201 Created – magazine created  
    405 Method Not Allowed – unable to create “magazine” resource

- PUT /magazines  
  Replace all magazines in the /magazines resource with those in the request  
  - _Status Codes_:  
    200 OK – magazines replaced

- PUT /magazines/1234  
  Replace the /magazines/1234 resource with the representation in the request  
  - _Status Codes_:  
    200 OK – magazine 1234 replaced

-  DELETE /magazines  
  Delete all magazines from the /magazines resource
    - _Status Codes_:  
    200 OK – all magazines deleted

 - DELETE /magazines/1234  
  Delete the magazine resource /magazines/1234  
   - _Status Codes_:  
    200 OK – magazine 1234 deleted

## Use versions

Never release an API without a version number.

Versions should be integers, not decimal numbers, prefixed with ‘v’. For example: v1, v2, v3.

---

- [API Guide: Guidelines para design de API](https://apiguide.readthedocs.io)
- [Swagger](https://swagger.io/) 
- [OpenAPI-Specification, versão 3.0.0](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/3.0.0.md).
