# go-graphql-example
 
 ### Installation steps:

1. Run Mysql image from docker and use it:

```shell
docker run -p 3306:3306 --name mysql -e MYSQL_ROOT_PASSWORD=dbpass -e MYSQL_DATABASE=hackernews -d mysql:latest
```

2. Install go mysql driver and golang-migrate packages then run migrations:

```shell
go get -u github.com/go-sql-driver/mysql
go install -tags 'mysql' github.com/golang-migrate/migrate/v4/cmd/migrate@latest
migrate -database mysql://root:dbpass@/hackernews -path internal/pkg/db/migrations/mysql up
```

3. Run app

```shell
go run server.go
```