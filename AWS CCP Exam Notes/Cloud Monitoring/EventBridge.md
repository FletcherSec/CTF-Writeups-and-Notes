- Formerly [[CloudWatch Events]]
- Schedule: Cron jobs (scheduled scripts)
- Event Pattern: Event rules to react to a service doing something
- Can trigger [[Lambda]] functions, [[SQS]]/[[SNS]] notifications

##### Event Bus
- Can use [[Default Event Bus]] (AWS Services)
- [[Partner Event Bus]] (AWS SaaS Partners)
- or [[Custom Event Bus]] (Custom apps)

- Has Schema Registry to model event schema
- Can archive events (all/filter) sent to an event bus (indefinitely or set period)
- Ability to replay archived events