docker volume create rabbitmq
docker run -d --hostname my-rabbit --mount source=rabbitmq,target=/var/lib/rabbitmq --name some-rabbit rabbitmq:3.9.3-management
mkdir go-rabbitmq && cd go-rabbitmq
go mod init github.com/germondc/go-rabbitmq
mkdir send && cd send
wget https://raw.githubusercontent.com/rabbitmq/rabbitmq-tutorials/master/go/send.go
cd .. && mkdir receive && cd receive
wget https://raw.githubusercontent.com/rabbitmq/rabbitmq-tutorials/master/go/receive.go
cd ..

Get IP fot container:
```
docker exec -it some-rabbit hostname -i
```

Change localhost in send.go and receive.go to the container IP

Run receive.go
```
go run ./receive
```
Run send.go
```
go run ./send
```