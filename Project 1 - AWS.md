# 🛒 Project 1: Migrating an E-commerce Website with Variable Traffic

## The Case:
A client wants to migrate their e-commerce website to the cloud. The site experiences unpredictable traffic, with high peaks during promotional events and quieter periods for the rest of the year. The client wants to minimize costs while ensuring the site remains available during high-demand periods. Currently, they are using a MySQL relational database.

![AWS Architecture Diagram](https://raw.githubusercontent.com/Kzax01/AWS-Architecture-Projects/main/Diagram%20AWS/Project%201%20AWS%20-%20animated.svg)


## 💡 AWS Solution:
Here are the core AWS services that provide a robust, scalable, and cost-effective architecture:

- **Amazon EC2 with Auto Scaling**: Dynamically scales server capacity based on demand, perfect for handling fluctuating traffic.
- **Amazon RDS for MySQL**: A fully managed MySQL database with automated backups, vertical scaling, and high availability through Multi-AZ.
- **Amazon CloudFront**: Distributes the site's static content globally via a Content Delivery Network (CDN), reducing latency and improving user experience.
- **Amazon S3**: Stores static files (images, videos, etc.) with high availability and low latency.
- **Amazon VPC (Virtual Private Cloud)**: Isolates EC2 instances and RDS in secure private subnets for better security and network control.
- **Internet Gateway & NAT Gateway**: Provides public-facing resources like CloudFront with internet access, while NAT Gateway enables instances in private subnets to securely access the internet.
- **Application Load Balancer (ALB)**: Distributes incoming traffic across multiple EC2 instances to ensure availability and redundancy.
- **Amazon CloudWatch**: Monitors EC2, RDS, and Auto Scaling, triggering scaling events and sending alerts for potential bottlenecks.
- **Amazon Route 53**: Manages DNS routing for your application, enabling users to access your resources via friendly domain names.
- **AWS WAF (Web Application Firewall)**: Protects your application from common web exploits, ensuring enhanced security.

## 🤔 **Why These Services?**

- **Amazon EC2 with Auto Scaling**:
    - Automatically adjusts server capacity to match demand, reducing costs during off-peak times.
    - Ensures performance during peaks.
- **Amazon RDS for MySQL**:
    - A reliable managed database that minimizes the need for manual intervention.
    - Offers automated backups and high availability with Multi-AZ replication.
- **Amazon CloudFront**:
    - Optimizes global content delivery by caching static content close to users.
    - Reduces server load and improves performance.
- **Amazon S3**:
    - High availability, low-cost storage for static assets like product images and videos.
    - Seamlessly integrated with CloudFront.
- **Amazon VPC**:
    - Keeps critical resources, like EC2 and RDS, securely isolated in private subnets.
    - Protects them from external threats.
- **Internet Gateway/NAT Gateway**:
    - Ensures that public-facing resources can access the internet while keeping your private infrastructure secure.
- **Application Load Balancer**:
    - Distributes incoming traffic to maintain performance.
    - Ensures failover for uninterrupted service during peak loads.
- **Amazon CloudWatch**:
    - Provides real-time monitoring and triggers Auto Scaling.
    - Maintains optimal performance and resource efficiency.
- **Amazon Route 53**:
    - Directs user traffic to the correct AWS resources based on domain name resolution.
- **AWS WAF**:
    - Helps protect your web applications from common security threats and vulnerabilities.

## 🔗 **How Does it All Work Together?**

Here’s a simplified breakdown of how the components integrate:

1. Users (Clients) access the website through their browsers.
2. Amazon CloudFront handles requests for static and dynamic content:
    - Cached content is immediately served by CloudFront for faster response times and reduced server load.
    - For non-cached content, CloudFront pulls static files directly from Amazon S3, storing them locally for future requests.
3. Application Load Balancer (ALB) balances incoming traffic across multiple EC2 instances in an Auto Scaling group:
    - Auto Scaling automatically adjusts the number of EC2 instances based on traffic levels to ensure the site remains responsive and cost-efficient.
4. Amazon RDS for MySQL stores all transactional data (like customer orders, inventory):
    - Isolated in a private subnet within Amazon VPC for enhanced security.
5. Internet Gateway and NAT Gateway ensure EC2 instances and RDS can access necessary external resources (e.g., updates, APIs) while staying secure in the VPC.
6. Amazon CloudWatch monitors the overall health of your services (EC2, RDS, Auto Scaling):
    - Triggers alerts and scaling actions when needed to keep performance optimal.
7. Amazon Route 53 resolves domain names to the appropriate AWS resources, guiding user traffic effectively.
8. AWS WAF filters incoming web traffic to protect the application from threats.

## 🛠️ **How These Services Solve Scale, Cost, and Performance Challenges:**

⚖️ **Scaling Issues**:
- **Amazon EC2 with Auto Scaling**:
    - Dynamically adjusts the number of instances.
    - Ensures you’re not over-provisioned during low traffic.
    - Always available during high peaks.
- **Application Load Balancer (ALB)**:
    - Distributes traffic evenly across EC2 instances.
    - Reduces bottlenecks and enhances redundancy.
- **Amazon CloudFront**:
    - Caches static content across global Points of Presence (PoPs).
    - Offloads traffic from your origin servers.

💰 **Cost Concerns**:
- **Amazon EC2 with Auto Scaling**:
    - Automatically reduces the number of instances when traffic is low.
    - Minimizes costs without sacrificing performance.
- **Amazon S3**:
    - Offers low-cost storage for static content.
    - Provides long-term storage solutions, helping to optimize your budget.
- **Amazon CloudWatch**:
    - Identifies inefficient configurations.
    - Tracks resource usage to help you fine-tune for cost savings.

🚀 **Performance Problems**:
- **Amazon RDS for MySQL**:
    - Uses SSD storage and Multi-AZ replication.
    - Ensures high performance and availability, even in the event of hardware failure.
- **Amazon CloudFront**:
    - Reduces latency for global users by serving cached content from the nearest location.
- **Amazon CloudWatch**:
    - Constantly monitors your resources.
    - Allows you to quickly resolve performance bottlenecks and scale dynamically as needed.

## 💡 **Final Thoughts**:
With these AWS services, your e-commerce platform will not only scale efficiently but also operate at lower costs and provide an enhanced user experience globally. Each component plays a crucial role in balancing the demands of scale, cost-efficiency, and performance, ensuring a robust and elastic system that adapts to your business needs. 🔐 Secure, 💰 Cost-effective, and 🏎️ High-performance—everything your e-commerce platform needs to thrive in the cloud!

## 🎯 **Other Options to Consider**:
- ⚡ **Amazon ElastiCache**:
    - If your e-commerce site handles a large volume of transactions or user sessions, consider integrating Amazon ElastiCache (Redis/Memcached).
    - This can significantly boost back-end performance by caching temporary data, reducing the load on your database.
- 📬 **Amazon SQS / SNS**:
    - To improve your architecture and decouple the components of your application, you can leverage Amazon SQS (Simple Queue Service) or Amazon SNS (Simple Notification Service).
    - These services help manage asynchronous communications between different services, ensuring better scalability and reliability in your system.
- 💸 **AWS Cost Explorer**:
For better budget management, AWS Cost Explorer lets you track and forecast expenses, allowing you to optimize resources and avoid unnecessary costs.


# 📚 Resources
Here are the links to the AWS documentation for the services used in this scenario:
- **Amazon EC2 with Auto Scaling**: [AWS EC2 Documentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EC2_GetStarted.html)  
- **Amazon RDS for MySQL**: [AWS RDS Documentation](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_MySQL.html)  
- **Amazon CloudFront**: [AWS CloudFront Documentation](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Welcome.html)  
- **Amazon S3**: [AWS S3 Documentation](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html)  
- **Amazon VPC (Virtual Private Cloud)**: [AWS VPC Documentation](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html)  
- **Internet Gateway**: [AWS Internet Gateway Documentation](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Internet_Gateway.html)  
- **NAT Gateway**: [AWS NAT Gateway Documentation](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-nat-gateway.html)  
- **Application Load Balancer (ALB)**: [AWS ALB Documentation](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/introduction.html)  
- **Amazon CloudWatch**: [AWS CloudWatch Documentation](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/WhatIsCloudWatch.html)  
- **Amazon Route 53**: [AWS Route 53 Documentation](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/Welcome.html)  
- **AWS WAF (Web Application Firewall)**: [AWS WAF Documentation](https://docs.aws.amazon.com/waf/latest/developerguide/waf-chapter.html)  
- **Tool Used for Designing the Architecture**: [Draw.io](https://www.draw.io/)  




### 💬 Let's Connect!
Thank you for taking the time to read through my project! If you'd like to connect, feel free to reach out on LinkedIn: [Kenza S. - Cyber & Cloud](https://www.linkedin.com/in/kenza-s-cyber-cloud)

### ☁️ I look forward to connecting with you!
