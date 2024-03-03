# How to use SQL Database Docker

## Containerの起動
```
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=55Itolab!!" -p 1433:1433 --name mssql --hostname mssql -d mcr.microsoft.com/mssql/server:2022-latest
```
Containerが既に存在している場合
```
docker start mssql
```

## データベースの作成
1. Containerにアタッチ
```
docker exec -it sql1 "bash"
```
2. データベースの作成
```
/opt/mssql-tools/bin/sqlcmd -S localhost -U SA

CREATE DATABASE test_db
go

USE test_db
go

CREATE TABLE item (id INT, name NVARCHAR(50))
go
```

## Mybatis Generatorの起動
```
./mvnw mybatis-generator:generate
```

## Containerの停止
```
docker stop mssql
```