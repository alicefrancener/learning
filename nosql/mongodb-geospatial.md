# Buscar por distância

- Incluir informações geoespaciais
  -  localização geográfica no MongoDB necessita de dois valores que são obrigatórios, o `coordinates`, que é latitude e longitude e o `type`
  -  outras informações, como país e endereço, são opcionais
  
  ```bash
  db.alunos.update(
  { "_id" : ObjectId("56cb0139b6d75ec12f75d3b6") },
  {
      $set : {
      localizacao : {
          endereco : "Rua Vergueiro, 3185",
          cidade : "São Paulo",
          coordinates : [-23.588213, -46.632356],
          type : "Point"
          }
      }
  }
  )
  ```

- Criar índice de busca
  - `createIndex()`: nele passaremos o campo que criamos que possui as informações `coordinates` e `type`. No exemplo, `localizacao`
  - no caso de um `type: "Point"` na terra, queremos a distância de uma esfera 2D
  
  ```bash
  db.alunos.createIndex({
      localizacao : "2dsphere"
  })
  ```

- Agregar o conjunto de dados
  - `$geoNear`: indica que queremos uma busca por proximidade
  - `near`: indica que queremos aquilo que esteja próximo a uma coordenada específica
  - `spherical : true`: para calcular a distância considerar esfera
  - `distanceField: distancia_calculada`: isso mostra onde guardar a informação da distância calculada nos documentos
  - `num`: refere-se aos resultados a serem exibidos
  
  ```bash
  db.alunos.aggregate([
  {
      $geoNear : {
          near : {
              coordinates: [-23.5640265, -46.6527128],
              type : "Point"
          },
          distanceField : "distancia.calculada",
          spherical : true,
          num : 4
      }
  }
  ])
  ```

---

- https://docs.mongodb.com/manual/reference/operator/query-geospatial/
- https://www.alura.com.br/curso-online-mongodb
