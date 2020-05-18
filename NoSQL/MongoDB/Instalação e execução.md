## MongoDB - Arch Linux
 
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
 
## MongoDB Compass - Arch Linux
 
É o programa oficial de visualização de dados do MongoDB
1. Fazer download do MongoDB Compas no AUR:
```
yay mongodb-compass
```
2. Para conexão local Para executar o servidor, por padrão fica salvo em /data/db, mas é possível trocar o diretório com --dbpath:
```
sudo mongod
sudo mongod --dbpath <diretório>
```
3. Abrir MongoDB Compass e ir na opção "connect"
![]()
 
4. O painel do MongoDB Compass
![]()
 
