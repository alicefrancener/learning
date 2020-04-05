# MongoDB

- [MongoDB](#mongodb)
  - [Criar coleção, inserir e remover](#criar-cole%c3%a7%c3%a3o-inserir-e-remover)
  - [Consultar](#consultar)
  - [Consultar com OR e IN](#consultar-com-or-e-in)
  - [Update](#update)
  - [Update array](#update-array)
  - [Ordenar](#ordenar)

## Criar coleção, inserir e remover

- Operadores: https://docs.mongodb.com/manual/reference/operator/query/

```bash
# criar coleção
db.createCollection("alunos")

# inserir registro
db.alunos.insert({
       "nome" : "Felipe",
       "data_nascimento" : new Date (1994,02,26),
       "habilidades": [
        {
            "nome" : "inglês",
            "nível" : "avançado"
        },
        {
            "nome" : "taekwondo",
            "nível" : "básico"
        }
    ]
   })

# remover registro
db.alunos.remove({
  "_id" : ObjectId ("56cb0002b6d75ec12f75d3b5")
  })

```

## Consultar

```bash
# listar registros (pretty - formatado)
db.alunos.find()
db.alunos.find().pretty()
db.alunos.find({nome: "Felipe"}).pretty()
db.alunos.find({"habilidades.nome": "inglês" }).pretty()
```

```bash
# encontrar maiores que ($gt: greater than)
db.alunos.find({
  "notas": { $gt : 5}
})
```
```bash
# encontrar só um
db.alunos.findOne({
  "notas": 5
})

# limitar os resultados
db.alunos.find().limit(3)

```

- Referência para comandos `find`
  https://docs.mongodb.com/manual/reference/method/db.collection.find/

## Consultar com OR e IN

```bash
# listar alunos de um determinado curso OU outro
db.alunos.find({
    $or : [
        {"curso.nome" : "Sistemas de informação"},
        {"curso.nome" : "Engenharia Química"}
    ]
})

# listar aluna com nome Daniela E de algum dos cursos
 db.alunos.find({
     $or : [
        {"curso.nome" : "Sistemas de informação"},
        {"curso.nome" : "Engenharia Química"},
        {"curso.nome" : "Moda"}
    ],
    "nome" : "Daniela"
 })

# listar alunos de uma lista de determinados cursos
 db.alunos.find({
    "curso.nome" : {
        $in : ["Sistemas de informação", "Engenharia Química"]
        }
})
```

## Update

- Se não usar `$set`, documento inteiro é modificado

```bash
# update primeiro documento que têm determinado curso e update somente o campo curso
db.alunos.update(
  {"curso.nome" : "Sistemas de informação"},
  { $set: {
    "curso.nome": "Sistemas de informação"
  }}
  )

# update múltiplos documentos
db.alunos.update(
  {"curso.nome" : "Sistemas de informação"},
  { $set: {
    "curso.nome": "SISTEMAS DE INFORMAÇÃO"
  },
  {
    multi: true
  }}
  )
```

- Referência para update
  https://docs.mongodb.com/manual/reference/operator/update/

## Update array

- `$push`: inserir elemento no array
  ```bash
  db.alunos.update(
    {"_id" : ObjectId("56cb0002b6d75ec12f75d3b5")},
    {
        $push : {
            notas : 8.5
        }
    }
  )
  ```
  
- `$each`: adicionar notas para array
  ```bash
  db.alunos.update(
    {"_id" : ObejctId("56cb0139b6d75ec12f75d3b6")},
    {
        $push : {
            "notas" : {$each : [8.5, 3] }
        }
    }
  )
  ```

## Ordenar

  ```bash
  # ordenar um campo ordem crescente
  db.alunos.find().sort({"nome": 1})
  
  # ordenar em ordem decrescente
  db.alunos.find().sort({"nome": -1})
  ```


- Referência para operadores update de array
https://docs.mongodb.com/manual/reference/operator/update-array/
