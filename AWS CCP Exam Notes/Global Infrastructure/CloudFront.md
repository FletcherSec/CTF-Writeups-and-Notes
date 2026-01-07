- Cloudfront is a [[CDN]]
- Improves read performance, content is cached at the edge
- Improves users experience
- Hundreds of Points of Presence globally (edge locations, caches)
- DDoS protection (because worldwide), integration with [[Shield]], AWS [[Web Application Firewall]]
- Content is served at the edge

##### Origins
- [[S3]] bucket
	- for distributing files and caching them at the edge
	- for uploading files to [[S3]] through CloudFront
	- Secured using Origin Access Control ([[OAC]])
- [[VPC]] Origin
	- For applications hosted in [[VPC]] private subnets
	- [[ALB]] / [[NLB]] / [[EC2]] instances
- Custom Origin ([[HTTP]])
	- [[S3]] website (must first enable the bucket as a [[S3 Static Website Hosting]])
	- Any public HTTP backend

##### CloudFront vs S3 Cross Region Replication
- CloudFront
	- Using Global Edge network
	- Files are cached for a TTL (maybe a day)
	- Great for static content that must be available everywhere
- S3 Cross Region Replication
	- Must be setup for each region you want replication to happen
	- Files are updated in near real-time
	- Read only
	- Great for dynamic content that needs to be available at low-latency in few regions