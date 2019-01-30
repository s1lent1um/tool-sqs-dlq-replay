# SQS Dead Letter Replayer

Binaries for handling SQS Dead Letter Queues:

* sqs-dead-letter-requeue: Requeue all messages from dead letter queue to related active queue. Can set max number of messages to be replayed (won't be exactly respected)

## Usage

```
usage: dlq-replay [<flags>] <destination-queue-name>

Requeues messages from a SQS dead-letter queue to the active one.

Flags:
  --help   Show help.
  --source-queue-name=SOURCE-QUEUE-NAME  
           Name of the source SQS queue (e.g. prod-service-crm-v2-webhooks-ringover-dlq).
  --account-id=ACCOUNT-ID  
           AWS account ID. (e.g. 123456789)
  --max=0  Max number of messages to requeue. 0 means all messages. This will not be exactly respected due to AWS batch size

Args:
  <destination-queue-name>  
    Name of the destination SQS queue (e.g. prod-service-crm-v2-webhooks-ringover).
```

## Dev

* Golang

### Building it

```sh
go build -o bin/dlq-replay sqs-dead-letter-requeue/main.go
```

### Running it

Make sure you have the environment variables for AWS set

```sh
export AWS_ACCESS_KEY_ID=<my-access-key>
export AWS_SECRET_ACCESS_KEY=<my-secret-key>
```

Then

```sh
bin/dlq-replay my-queue-name
```
