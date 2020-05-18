# Index

Um atalho para o dados do banco, mas o falho e que todo update, insert ou delete precisa refazer o index forçando o banco,mas é melhor para buscar, por isso se utiliza em algo que buscamos muito.

#### Criar Index
No primeiro Parâmetro irá separar por ordem, o segundo falando que não pode repetidos.
```
db.<nome da coleção>.createIndex({ <campo da coleção>: 1 }, { unique:true });

db.pessoas.createIndex({ cidade: 1 });
```

#### Ver Index
Função para ver todos os Index do banco
```
db.<nome da coleção>.getIndexes();

db.artigos.getIndexes();
```

