[[Docker]]: container technology to run applications
[[ECS]]: run [[Docker]] containers on [[EC2]] instances
[[Fargate]]:
- Run [[Docker]] containers without provisioning the infrastructure
- Serverless offering (No [[EC2]] instances)
[[ECR]]: Private [[Docker]] Images Repository
[[Batch]]: run batch jobs on AWS across managed [[EC2]] instances
[[Lightsail]]: predictable and low pricing for simple application and DB stacks
##### Lambda
[[Lambda]]: is [[Serverless]], [[FaaS]], seamless scaling, reactive
Lambda Billing:
- By the time run * by the RAM provisioned
- By the number of times the function has been invoked
Lambda Language Support: many languages except (arbitrary) Docker (use [[ECS]] instead)
Lambda Invocation time: up to 15 minutes
Lambda Use Cases:
- Create thumbnails for images uploaded to [[S3]]
- Run a serverless CRON job
[[API Gateway]]: expose Lambda functions as HTTP API