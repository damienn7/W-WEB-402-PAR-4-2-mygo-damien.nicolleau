## Golang tips

### Golang installation
- Follow this resource for more informations : https://go.dev/doc/install

### Project initialization
- Try this command inside your back-end (server) folder : go mod init <folder_name>
- Then install the postgres image on docker by trying this command : docker pull postgres:15-alpine
- Run the postgres service by using the following command : docker run --name postgres15 -p 5433:5432 -e POSTGRES_USER=root -e POSTGRES_PASSWORD=password -d postgres:15-alpine
- Run this command to create the database : docker exec -it postgres15 createdb --username=root --owner=root go-chat
- So run this command to go in the postgres container : docker exec -it postgres15 psql

### Postgres command-line
- "\l" will list databases
- "\c go-chat" will connect to go-chat database
- "\d users" will describe the table
- "exit" or "\q" will quit the postgres service

### Golang command-line
- go mod tidy install the dependencies for you

### Migrate command-line
- migrate create -ext sql -dir db/migrations add_users_table
- migrate -path db/migrations -database "postgresql://root:password@localhost:5433/go-chat?sslmode=disable" -verbose up
- migrate -path db/migrations -database "postgresql://root:password@localhost:5433/go-chat?sslmode=disable" -verbose force 20241027155056