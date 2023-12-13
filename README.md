# rabbitmq-go
Go code for RabbitMQ

Experimenting with RabbitMQ on your workstation? Try the following Docker image:
# latest RabbitMQ 3.12

    docker run -it --rm --name rabbitmq -p 5672:5672 -p 15672:15672 rabbitmq:3.12-management

## Requirements

These examples use the [`rabbitmq/amqp091-go`](https://github.com/rabbitmq/amqp091-go) client library.
Get it first with

    go get github.com/rabbitmq/amqp091-go

## Code

Code examples are executed via `go run`:

"Hello World!":

    go run send.go
    go run receive.go
![image](https://github.com/skartikey/rabbitmq-go/assets/1942366/c5f21911-f2a1-4994-8690-4c03c06362eb)


Work Queues:

    go run new_task.go hello world
    go run worker.go
![image](https://github.com/skartikey/rabbitmq-go/assets/1942366/3cab244a-d418-4e7e-8829-d22da0403409)


Publish/Subscribe

    go run receive_logs.go
    go run emit_log.go hello world
![image](https://github.com/skartikey/rabbitmq-go/assets/1942366/e0bc52a1-9965-4cb2-a567-77793a707ab9)


Routing

    go run receive_logs_direct.go info warn
    go run emit_log_direct.go warn "a warning"
![image](https://github.com/skartikey/rabbitmq-go/assets/1942366/033ce9d0-9046-44e8-81c3-99304db16bd1)


Topics

    go run receive_logs_topic.go "kern.*" "*.critical"
    go run emit_log_topic.go kern.critical "A critical kernel error"
![image](https://github.com/skartikey/rabbitmq-go/assets/1942366/69948aa3-bbe4-4541-9bd8-4da44ffc5a5d)


RPC

    go run rpc_server.go
    go run rpc_client.go 10
![image](https://github.com/skartikey/rabbitmq-go/assets/1942366/f390bee4-a65e-4a4c-8269-88d1d94eee09)

