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

Work Queues:

    go run new_task.go hello world
    go run worker.go

Publish/Subscribe

    go run receive_logs.go
    go run emit_log.go hello world

Routing

    go run receive_logs_direct.go info warn
    go run emit_log_direct.go warn "a warning"

Topics

    go run receive_logs_topic.go "kern.*" "*.critical"
    go run emit_log_topic.go kern.critical "A critical kernel error"

RPC

    go run rpc_server.go
    go run rpc_client.go 10
