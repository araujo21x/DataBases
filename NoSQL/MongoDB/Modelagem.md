# Modelagem 

Verificar as coleções que mais irá utilizar e com isso tomar certas medidas para otimizar as consultas ao banco evitando coisas como Inner Join, update e delete em outra coleção Ex:

- Para evitar inner join, colocando como exemplo blog, ao pegar as postagens no banco banco Sql vc iria pegar as postagens e fazer um inner join pra pegar os dados do autor que fez a postagem, no mongo para evitar esse inner join, você poderia criar a cópia dos dados do autor utilizado pela postagem em um array com o id do autor e esses dados.

- Quando for muitos para muitos, os dados de ligação fica no que tem mais entrada no banco, exemplo “produto” e “lojas”, a quantidade de produtos cadastrado e maior que de “lojas”, então é melhor “id” e alguns dados prévio da “loja” no “produto” assim quando for fazer cadastro, exclusão ou edição só vai precisar trabalhar com uma coleção, isso porque a coleção de “produto” vai ser modificada e cadastrada várias vezes, se tivesse alguma informação na “loja” sobre “produtos” em cada uma dessas mudanças seria necessário modificar os dados desse “produto” na coleção de “lojas” também, assim fazendo queries desnecessárias.
 
“No update alterar somente os campos que de fato foram atualizados pela sua aplicação. Ou seja, se somente o nome do cliente foi editado, envie apenas essa alteração ao banco de dados, diminuindo com isso o tempo de update e o uso de rede.”

