# Comandos Básicos
- A maioria dos comandos você informa db.<coleção>.função(<parâmetro em JSON>);
 
- Se o comando for executado com sucesso terá como resposta um JSON com "ok": 1 se não "ok": 0 e algumas mensagens de erro;
 
- O parâmetro JSON segue o padrão de objeto JavaScript nele é opcional o uso de "" nas chaves, exemplo "nome" : "Lucas" \ nome : "Lucas", mas é uma boa prática o uso das aspas.

## Criar Coleções
Uma coleção e como se fosse uma tabela de um banco SQL, mas os campos só são informados durante a inserção no banco.

```
db.creatCollections("nome da Coleção")

Ex:
db.creatCollections("pessoas")
```

## Inserir no Banco
Para inserir na coleção mongoDb, primeiro informa qual a coleção, escolhe a função e nesse caso será insert e passa como parâmetro um JSON, um id é Criado de forma automática:

```
db.<coleção>.insert(<parâmetro>)

Ex:
db.pessoas.insert({
    "nome" : "Lucas",
    "sobrenome" : "Araujo",
    "habilidades": [
        {"nome" : "MongoDB",
        "nível" : "Iniciante"}
        ]
    })
```
## Procurar no Banco
Para pegar uma coleção no mongoDb, primeiro informa qual a coleção, escolhe a função que nesse caso será find, senão informa o parâmetro irá retornar todos os itens da coleção:

```
db.<coleção>.find(<dados>)

Ex:
    db.pessoas.find()
    Vai retorna todos os usuários. 
    
    db.pessoas.find({"_id" : ObjectId("5eb36e2a6df8e42ee7b2db9c")})
    { "_id" : ObjectId("5eb36e2a6df8e42ee7b2db9c"),
        "nome" : "Lucas",
        "sobrenome" : "Araujo",
        "habilidades" : [ 
            { "nome" : "MongoDB", "nível" : "Iniciante" } 
        ]
    }
        
```
## Remover no Banco
Informa qual a coleção, escolhe a função que nesse caso será remove e informa um parâmetro para encontrar usuários para exclusão:

```
db.<coleção>.remove(<parâmetro>)

Ex:
    db.pessoas.remove({"_id" : ObjectId("5eb36e2a6df8e42ee7b2db9c")})        
```

## Editar no Banco