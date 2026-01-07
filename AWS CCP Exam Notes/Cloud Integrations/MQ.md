- [[SQS]], [[SNS]] are "cloud-native" services: proprietary protocols from AWS
- Traditional applications running from on-premises may use open protocols such as: MQTT, AMQP, STOMP, Openwire, WSS
- When migrating tot he cloud, instead of re-engineering the application to use [[SQS]] and [[SNS]], we can use Amazon MQ
- MQ is a managed message broker service for:
	- RabbitMQ
	- ActiveMQ
- Amazon MQ doesn't "scale" as much as [[SQS]] / [[SNS]]
- Amazon MQ runs on servers, can run in Multi-AZ with failover
- Comes with both queue feature ([[SQS]]) and topic features ([[SNS]])

#### Used if a company is migrating to the cloud and needs to use an open protocol