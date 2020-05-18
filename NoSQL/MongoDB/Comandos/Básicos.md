# Comandos Básicos
- A maioria dos comandos você informa db.<coleção>.função(<parâmetro em JSON>);
 
- Se o comando for executado com sucesso terá como resposta um JSON com "ok": 1 se não "ok": 0 e algumas mensagens de erro;
 
- O parâmetro JSON segue o padrão de objeto JavaScript nele é opcional o uso de "" nas chaves, exemplo "nome" : "Lucas" \ nome : "Lucas", mas é uma boa prática o uso das aspas.

## Coleções

Uma coleção e como se fosse uma tabela de um banco SQL, mas os campos só são informados durante a inserção no banco.

#### Criar 
```
db.creatCollections("nome da Coleção")

Ex:
db.creatCollections("pessoas")
```

#### Usar
```
use <nome da coleção>;

use pessoas;
```
#### Deletar 
```
db.<nome da coleção>.drop()

Ex:
db.pessoas.drop()
```

#### Listar 
```
db.getCollectionsNames()
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
        "nivel" : "Iniciante"}
        ]
    })
```
## Procurar no Banco
Para pegar uma coleção no mongoDb, primeiro informa qual a coleção, escolhe a função que nesse caso será find,informa os parametros em forma de JSON, caso não informe o parâmetro irá retornar todos os itens da coleção:
* Caso não desejo todos os todos os dados, só precisa passar um segundo parametro com o campo e 1(true);

```
db.<coleção>.find(<dados>)

Ex:
    db.pessoas.find()
    Vai retorna todos os usuários. 
    
    db.pessoas.find({"_id" : ObjectId("5eb36e2a6df8e42ee7b2db9c")})

    db.pessoas.find({"_id" : ObjectId("5eb36e2a6df8e42ee7b2db9c")},{"nome": 1, "sobrenome": 1})

        
```

## Remover no Banco
Informa qual a coleção, escolhe a função que nesse caso será remove e informa um parâmetro para encontrar usuários para exclusão:

```
db.<coleção>.remove(<parâmetro>)

Ex:
    db.pessoas.remove({"_id" : ObjectId("5eb36e2a6df8e42ee7b2db9c")})        
```

## Editar no Banco
Informa qual a coleção, escolhe a função que nesse caso será update e informa um parâmetro para encontrar usuários e outro para modificar:

* Para modificar apenas um campo utiliza "$set:" exemplo, {$set: {"nome": "Novo nome"}}, caso não utilizar "$set" será modificada toda a coleção, nessa por exemplo iria ficar "nome": "Novo nome" e os outros campos seriam apagados.

* Por padrão o update no MongoDb só vai modificar o primeiro usuário encontrado, mas ao utiliza o comando "$set", caso deseje mudar varios usuário é nescessário informar um outro parâmetro;

* Update atualiza somente o primeiro item encontrado, já UpdateMany vai percorrer todo o banco e atualizar todos que se encaixam no " parâmetro de pesquisa".

```
db.<coleção>.update(<parâmetro de pesquisa>, <parâmetro com a mudança>, <parametro vários usuários>)

EX:


db.pessoas.update({"nome":"Lucas"}, {$set: {"nome":"Novo nome"} }, {multi: true})

```

## Procurar e atualizar
No mongo é possivel pegar e atualizar um argumento com o FindOneAndUpdate.


```
db.<coleção>.FindOneAndUpdate(<parâmetro de pesquisa>, <parâmetro com a mudança>)

EX:


db.pessoas.FindOneAndUpdate({"nome":"Lucas"}, {$set: {"nome":"Novo nome"} })

```

### projection pesquisar 

### dato historico
### OR e IN

Quando quiser usar mais de um parâmetro do mesmo tipo como parâmetro pode utilizar o "or":
```
db.pessoas.find({ $or:[{"sobrenome":"Araujo"},{"sobrenome":"Paulo"}]}).pretty()

```
Quando quiser que procure por um usuário contento dois dados utiliza-se o "in"
```

```

### array

* Array tem alguns comandos como $push, $each entre outras;

* Para modificar um array de objetos
```
db.pessoas.update(
    {"habilid ades.nivel" : "Iniciante"}, 
    {$set: { "habilidades.$.nivel": "básica" }},
    {multi: true}
    )
```