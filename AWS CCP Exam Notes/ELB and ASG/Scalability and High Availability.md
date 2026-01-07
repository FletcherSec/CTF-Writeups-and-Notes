- Scalability means that an application / system can handle greater loads by adapting
- There are two kinds of scalability:
	- Vertical Scalability
	- Horizontal Scalability (= elasticity)
- Scalability is linked but different to High Availability

##### Vertical Scalability
- Vertical Scalability means increasing the size of the instance
- Example: your application runs on a t2.micro
- Scaling vertically means running it on a t2.large
- Vertical Scalability is very common for non distributed systems, such as a database
- Usually a limit to how much you can vertically scale (hardware limit)

##### Horizontal Scalability
- Horizontal Scalability means increasing the number of instances / systems for your application
- Example: Scaling from 1 operator to 6 operators
- Horizontal scaling implies distributed systems
- Very common for web applications / modern applications
- Very easy to scale horizontally due to [[EC2]]

##### High Availability
- High availability usually goes hand in hand with horizontal scaling
- High availability means running your application / system in at least 2 Availability Zones
- Goal of high availability is to survive the loss of a datacenter

