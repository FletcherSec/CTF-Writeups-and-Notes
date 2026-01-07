- Debugging in Production the normal way:
	- Test locally
	- Add log statements everywhere
	- Re-deploy in production
- Log formats differ across applications and log analysis is hard
- Debugging: one big monolith "easy", but distributed services are "hard"
- No common views of your entire architecture
- AWS X-Ray aims to solve this issue

Provides a visual analysis of applications

##### X-Ray advantages
- Troubleshooting performance (bottlenecks)
- Understand dependencies in a microservice architecture
- Pinpoint service issues
- Review request behavior
- Find errors and exceptions
- Are we meeting time SLA?
- Where is throttling occurring?
- Identify users that are impacted