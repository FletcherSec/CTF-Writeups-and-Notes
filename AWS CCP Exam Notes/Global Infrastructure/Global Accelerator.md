- Improve global application availability and performance using the AWS global network
- Leverage the AWS internal network to optimize the route to your application (60% improvement)
- Traffic goes to local AWS edge location which uses the AWS network to send to the applications public [[ALB]]
- 2 [[Anycast]] IP are created for your application and traffic is sent through Edge Locations
- The Edge locations send the traffic to your application

