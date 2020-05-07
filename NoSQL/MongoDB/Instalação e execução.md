# Instalação

## Arch Linux

1. Fazer download do mongodb-bin no AUR:
```
yay mongodb-bin
```

2. Para executar o servidor, por padrão fica salvo em /data/db:
```
 sudo mongod
```

3. Para executar o servidor em um diretório diferente do padrão:
```
 sudo mongod --dbpath <diretório>
```

4. Após servidor executando e online criar nova aba para no terminal para conectar com o cliente:
```
 mongo
```