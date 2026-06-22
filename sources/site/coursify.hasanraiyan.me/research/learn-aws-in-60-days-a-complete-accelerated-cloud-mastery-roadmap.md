# Source: https://coursify.hasanraiyan.me/research/learn-aws-in-60-days-a-complete-accelerated-cloud-mastery-roadmap

Learn AWS in 60 Days: A Complete Accelerated Cloud Mastery Roadmap

# 

Learn AWS in 60 Days: A Complete Accelerated Cloud Mastery Roadmap

Verified Sources

Jun 15, 2026

## AI Summary

Amazon Web Services (AWS) dominates the global cloud infrastructure market with a ~31% share, making it the most demanded cloud platform for professionals worldwide . Whether you're transitioning into cloud computing or upgrading your existing IT skills, a focused 60-day plan can take you from cloud novice to confidently building and deploying on AWS.

This course section provides a structured, accelerated learning path covering **cloud fundamentals**, **core services**, **architecture patterns**, **hands-on projects**, and **certification readiness**. The approach emphasizes **learning by building**—not memorizing—because employers overwhelmingly value practical ability over credentials alone .

At the heart of this roadmap is the AWS Well-Architected Framework, which guides every architectural decision you'll make on AWS.

The diagram above illustrates the five phases of your 60-day journey. Each phase builds on the prior one, ensuring a solid foundation before progressing to more complex topics.

## Footnotes

1. [AWS Certification - Validate AWS Cloud Skills](https://aws.amazon.com/certification) - AWS official certification overview with industry statistics on certified professionals and employer preferences. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1)
 
2. [r/AWSCertifications - Study plan for AWS Solutions Architect Associate](https://www.reddit.com/r/AWSCertifications/comments/1c9j635/study_plan_for_aws_solutions_architect_associate) - Community discussion emphasizing hands-on practice over video-only learning. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-2)
 

#### How I'd Learn AWS Cloud in 2026 (After 5 Years in Cloud)

### 

60-Day AWS Learning Roadmap

#### Cloud Foundations & Account Setup

Days 1-10

Understand cloud computing concepts, the AWS Global Infrastructure (Regions, Availability Zones, Edge Locations), the AWS Management Console, and IAM fundamentals. Create your AWS Free Tier account and explore the console."

#### Compute & Networking Essentials

Days 11-18

Master Amazon EC2 (instances, AMIs, security groups, key pairs, Elastic IPs), Auto Scaling, and Elastic Load Balancing. Build your first VPC with public/private subnets, route tables, Internet Gateways, and NAT Gateways."

#### Storage & Databases

Days 19-25

Deep dive into Amazon S3 (buckets, policies, versioning, lifecycle rules, static website hosting), EBS, EFS, Glacier. Then cover databases: RDS (MySQL, PostgreSQL), DynamoDB (key concepts, read/write capacity modes), and ElastiCache."

#### Security, Monitoring & Architecture

Days 26-34

Study IAM deep-dive (policies, roles, STS, MFA), KMS encryption, CloudWatch, CloudTrail, AWS Config, VPC security (NACLs, Security Groups, VPC Flow Logs). Learn the 5 pillars of the Well-Architected Framework and practice designing resilient architectures."

#### Serverless, Messaging & Integration

Days 35-42

Master AWS Lambda, API Gateway, Step Functions, SNS, SQS, EventBridge, and SQS-Lambda patterns. Build serverless applications and understand event-driven architecture."

#### Advanced Services & Portfolio Projects

Days 43-50

Explore CloudFormation/Terraform (IaC), ECS/EKS (containers), CodePipeline/CodeBuild (CI/CD), Route 53, CloudFront CDN, and AWS AI services. Complete 2-3 portfolio-grade projects."

#### Certification Prep & Exam Strategy

Days 51-60

Take practice exams, review weak areas, master exam question techniques, and sit for the AWS Certified Solutions Architect – Associate (SAA-C03) exam."

### Phase 1: Cloud Foundations (Days 1–10)

Before touching any AWS service, you need a conceptual framework. Cloud computing fundamentally changes how IT resources are provisioned—shifting from CapEx to OpEx, and from months-long procurement to on-demand provisioning in seconds .

**Key concepts to master in Phase 1:**

| Concept | Description |
| --- | --- |
| **Regions & AZs** | AWS operates in 30+ Regions, each containing multiple Availability Zones |
| **Shared Responsibility Model** | AWS secures the cloud infrastructure; you secure what you deploy in it |
| **IAM** | Identity and Access Management — the gatekeeper for all AWS resources |
| **Billing & Cost Explorer** | Understand how pricing works and set up billing alarms immediately |
| **Free Tier** | Up to $200 in credits for new accounts; Always Free, 12-Month Free, and Trial tiers |

The foundational certification, **AWS Cloud Practitioner (CLF-C02)**, validates this knowledge and is the recommended starting point for all beginners .

## Footnotes

1. [Start Your Learning Journey with the Right Roadmap from AWS Training and Certification](https://aws.amazon.com/blogs/apn/start-your-learning-journey-with-the-right-roadmap-from-aws-training-and-certification) - AWS official blog on learning paths, free resources, and the Gallup research on digital skills. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-3)
 
2. [AWS Free Tier](https://aws.amazon.com/free) - Official AWS Free Tier page detailing the $200 credits for new accounts, Free plan, Paid plan, and Always Free services. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
3. [AWS re:Post - Learning Path/Training Material](https://repost.aws/questions/QUHgg8pUjJT9uWcsAE4MQMiQ/learning-path-training-material) - Community-recommended learning path starting with Cloud Practitioner Essentials. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5)
 

### Setting Up Your AWS Free Tier Account

1. 1
 
 Step 1
 
 Create Your AWS Account
 
 Visit aws.amazon.com and sign up. You'll need an email address, phone number, and credit card (for identity verification—charges won't apply within the Free Tier). Select the **Free plan** to get up to $200 in credits over 6 months with no surprise bills .
 
 ## Footnotes
 
 1. [AWS Free Tier](https://aws.amazon.com/free) - Official AWS Free Tier page detailing the $200 credits for new accounts, Free plan, Paid plan, and Always Free services. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
 
2. 2
 
 Step 2
 
 Set Up IAM Root Account Protection
 
 Enable MFA (Multi-Factor Authentication) on your root account immediately. Never use the root account for daily tasks—create an IAM admin user instead.
 
3. 3
 
 Step 3
 
 Configure Billing Alerts
 
 Go to AWS Billing Console → Budgets → Create a zero-spend budget alert. This prevents surprise charges. Also enable Cost Explorer for spending visibility.
 
4. 4
 
 Step 4
 
 Choose Your Home Region
 
 Select a Region geographically close to you (e.g., us-east-1 for US East, eu-west-1 for Europe). This minimizes latency and often has the most service availability.
 
5. 5
 
 Step 5
 
 Explore the AWS Console
 
 Navigate through key service categories: Compute, Storage, Database, Networking. Use the search bar and bookmark frequently used services. Complete the 'AWS Cloud Practitioner Essentials' free course on AWS Skill Builder .
 
 ## Footnotes
 
 1. [Start Your Learning Journey with the Right Roadmap from AWS Training and Certification](https://aws.amazon.com/blogs/apn/start-your-learning-journey-with-the-right-roadmap-from-aws-training-and-certification) - AWS official blog on learning paths, free resources, and the Gallup research on digital skills. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-3)
 
 

### Phase 2: Core Services Deep Dive (Days 11–25)

This is where the real learning accelerates. AWS offers 200+ services, but a focused subset accounts for 80%+ of what you'll use professionally and what appears on the Solutions Architect Associate exam.

#### Compute: Amazon EC2 & Lambda

Amazon EC2 is the foundational compute service. You must understand instance types (t3.micro, m5.large, etc.), AMIs, Security Groups, key pairs (SSH), and the bootstrapping process via User Data scripts.

AWS Lambda represents the paradigm shift to serverless computing, where servers are abstracted entirely. Lambda supports Python, Node.js, Java, Go, .NET, and Ruby—executing functions within milliseconds of a trigger event .

#### Storage: S3, EBS & EFS

Amazon S3 is arguably the most-used AWS service. Key exam and real-world concepts include:

- **S3 Storage Classes**: Standard, Intelligent-Tiering, Standard-IA, One Zone-IA, Glacier Flexible Retrieval, Glacier Deep Archive, S3 Express One Zone
- **S3 Security**: Bucket policies, ACLs, IAM policies, pre-signed URLs, Object Lock
- **S3 Performance**: Multipart uploads, S3 Transfer Acceleration, S3 Select

S3 Pricing\=Storage Cost+Request Cost+Data Transfer Cost\\text{S3 Pricing} = \\text{Storage Cost} + \\text{Request Cost} + \\text{Data Transfer Cost}S3 Pricing\=Storage Cost+Request Cost+Data Transfer Cost

#### Networking: VPC Architecture

The Amazon VPC is the backbone of every AWS deployment. Understanding VPC design is non-negotiable:

#### Databases: RDS, DynamoDB & More

| Service | Type | Best For |
| --- | --- | --- |
| **RDS** | Managed Relational | Transactional workloads (OLTP) |
| **Aurora** | MySQL/PostgreSQL-compatible | High-performance, auto-scaling relational |
| **DynamoDB** | NoSQL Key-Value/Document | Low-latency, high-throughput workloads |
| **ElastiCache** | In-Memory (Redis/Memcached) | Caching, session stores |
| **Redshift** | Data Warehouse | OLAP, analytics on petabytes |

[2]()

## Footnotes

1. [Leveraging AWS Free Tier for Hands-On Certification Training](https://www.cybrary.it/blog/leveraging-aws-free-tier-hands-certification-training) - Detailed Free Tier service list and hands-on lab recommendations for EC2, S3, Lambda, IAM, KMS. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-6) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-6-2)
 
2. [AWS Free Tier Explained: How to Maximize Benefits and Optimize Costs](https://www.cloudoptimo.com/blog/aws-free-tier-explained-how-to-maximize-benefits-and-optimize-costs) - Comprehensive breakdown of Free Tier offers by service category including compute, storage, databases, and CI/CD tools. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-7)
 

### 

AWS Services by Learning Priority

Relative importance for the Solutions Architect Associate exam and real-world usage

#### Pro Tip: Hands-On Over memorization

Certifications alone won't get you hired. According to community consensus on r/AWSCertifications, employers value practical skills far more than exam scores. For every hour of video lectures, spend at least 30 minutes actually building in the AWS Console. Use the Free Tier aggressively—launch EC2 instances, create S3 buckets, configure VPCs, write Lambda functions, and set up RDS databases .

## Footnotes

1. [r/AWSCertifications - Study plan for AWS Solutions Architect Associate](https://www.reddit.com/r/AWSCertifications/comments/1c9j635/study_plan_for_aws_solutions_architect_associate) - Community discussion emphasizing hands-on practice over video-only learning. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-2)
 

more...

Serverless Architecture

Traditional Web AppData Pipeline

`1API Gateway → Lambda → DynamoDB 2        ↓ 3  S3 (Static Assets) 4        ↓ 5  CloudFront (CDN) 6 7Key Services: Lambda, API Gateway, DynamoDB, 8S3, CloudFront, Cognito, SQS, SNS`

### Building a Serverless Web Application (Days 35-42 Project)

1. 1
 
 Step 1
 
 Design the Architecture
 
 Sketch the architecture: S3 hosts the React/Vue frontend → CloudFront serves it globally → API Gateway receives requests → Lambda processes business logic → DynamoDB stores data → Cognito handles authentication. This is the canonical serverless pattern.
 
2. 2
 
 Step 2
 
 Set Up S3 Static Hosting
 
 Create an S3 bucket with static website hosting enabled. Upload your frontend build artifacts (HTML, CSS, JS). Configure the bucket policy to allow public reads. Set up CloudFront as the CDN with the S3 bucket as the origin.
 
3. 3
 
 Step 3
 
 Create DynamoDB Tables
 
 Design your schema. DynamoDB uses partition keys and optional sort keys. Create a table with appropriate read/write capacity mode (on-demand recommended for development). Enable point-in-time recovery for safety.
 
4. 4
 
 Step 4
 
 Write Lambda Functions
 
 Create Lambda functions for CRUD operations (Create, Read, Update, Delete). Each function should: parse the API Gateway event, validate input, interact with DynamoDB via the AWS SDK, and return a properly formatted response (status code, headers, body).
 
5. 5
 
 Step 5
 
 Configure API Gateway
 
 Create a REST API with resources and methods (GET, POST, PUT, DELETE). Link each method to the corresponding Lambda function. Enable CORS for the frontend domain. Deploy to a stage (e.g., 'dev' or 'prod').
 
6. 6
 
 Step 6
 
 Add Authentication with Cognito
 
 Create a Cognito User Pool for user registration/sign-in. Configure a Cognito Identity Pool for temporary AWS credentials. Protect your API Gateway endpoints by adding a Cognito authorizer.
 
7. 7
 
 Step 7
 
 Test and Monitor
 
 Test all endpoints via Postman or curl. Set up CloudWatch alarms for Lambda errors and API Gateway 5xx rates. Enable X-Ray tracing for request visualization. Review CloudTrail logs for API call auditing.
 

### Phase 4: Advanced Services & Infrastructure as Code (Days 43–50)

Modern AWS deployments rely on IaC to ensure repeatability, version control, and auditability. Two dominant tools are AWS CloudFormation (native) and HashiCorp Terraform (multi-cloud).

CloudFormation templates declare your entire infrastructure, and CloudFormation handles the ordering and dependencies of resource creation. Terraform offers similar capabilities with its HCL syntax and broader provider ecosystem.

#### CI/CD on AWS

The CI/CD pipeline on AWS typically involves:

- **CodeCommit**: Source code repository (Git-compatible)
- **CodeBuild**: Managed build service (compiles code, runs tests)
- **CodeDeploy**: Automated deployment to EC2, Lambda, or ECS
- **CodePipeline**: Orchestrates the entire pipeline end-to-end

AWS offers free tiers for each: 1 active pipeline/month on CodePipeline, 100 build minutes/month on CodeBuild, and 1,000 deployments/month on CodeDeploy .

## Footnotes

1. [AWS Free Tier Explained: How to Maximize Benefits and Optimize Costs](https://www.cloudoptimo.com/blog/aws-free-tier-explained-how-to-maximize-benefits-and-optimize-costs) - Comprehensive breakdown of Free Tier offers by service category including compute, storage, databases, and CI/CD tools. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-7)
 

#### Warning: Free Tier Cost Management

AWS Free Tier does **not** automatically stop services when limits are exceeded. An unattended EC2 instance or a misconfigured data transfer can result in unexpected charges. Always: (1) Set up AWS Budgets with a zero-spend alert, (2) Use the AWS Pricing Calculator before deploying, (3) Clean up resources after each lab/project, (4) Tag all resources for cost tracking, and (5) Check your billing dashboard weekly .

## Footnotes

1. [AWS Free Tier](https://aws.amazon.com/free) - Official AWS Free Tier page detailing the $200 credits for new accounts, Free plan, Paid plan, and Always Free services. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 

more...

### Certification Preparation Strategy (Days 51-60)

1. 1
 
 Step 1
 
 Review the Exam Guide
 
 Download the official SAA-C03 exam guide from AWS Certification. The exam has 65 questions (50 scored, 15 unscored) across 4 domains: Secure Architectures (30%), Resilient Architectures (26%), High-Performing Architectures (24%), Cost-Optimized Architectures (20%). You have 130 minutes and need a scaled score of 720/1000 to pass .
 
 ## Footnotes
 
 1. [AWS Certified Solutions Architect – Associate](https://aws.amazon.com/certification/certified-solutions-architect-associate) - Official exam page with format, scoring, preparation resources, and domain breakdowns. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-8)
 
 
2. 2
 
 Step 2
 
 Take a Diagnostic Practice Exam
 
 Complete the free AWS Official Practice Question Set on Skill Builder. This identifies your weak domains. Don't worry about the score—use it to build a targeted study plan for the remaining 9 days.
 
3. 3
 
 Step 3
 
 Targeted Domain Review
 
 For each weak domain, review your notes, re-do hands-on labs, and study AWS documentation for key services. Focus on service limits, default configurations, and architectural patterns. Use comparison tables to distinguish similar services (e.g., S3 vs EFS vs EBS, or SQS vs SNS vs Kinesis).
 
4. 4
 
 Step 4
 
 Practice Exam Sprint
 
 Take at least 2 full-length practice exams under timed conditions (130 minutes, no breaks). AWS recommends doing 10-20 questions at a time in 30-60 minute study chunks, building up to full-length exams . Aim for 80%+ on practice exams before booking the real one.
 
 ## Footnotes
 
 1. [5 Tips for AWS Certification Exams from AWS Solutions Architects](https://aws.amazon.com/blogs/training-and-certification/5-tips-for-aws-certification-exams-from-aws-solutions-architects) - AWS official blog with exam strategies including breaking study into chunks and using process of elimination. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-9)
 
 
5. 5
 
 Step 5
 
 Exam Day Preparation
 
 Book the exam at a Pearson VUE testing center if possible (more stable than online proctoring). If testing online, ensure a quiet, empty room. Non-native English speakers can request ESL +30 minutes accommodation. Use process of elimination on difficult questions—eliminate clearly wrong answers first, then compare the remaining 2 options .
 
 ## Footnotes
 
 1. [5 Tips for AWS Certification Exams from AWS Solutions Architects](https://aws.amazon.com/blogs/training-and-certification/5-tips-for-aws-certification-exams-from-aws-solutions-architects) - AWS official blog with exam strategies including breaking study into chunks and using process of elimination. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-9)
 
 

### 

SAA-C03 Exam Domain Weights

Distribution of questions across the four exam domains

### Common Questions & Edge Cases

What if I have zero IT experience?

Should I learn Terraform or CloudFormation first?

How do I avoid AWS Free Tier charges?

Is the Solutions Architect Associate enough to get a job?

What about AI/ML on AWS?

### Study Time Commitment

To complete this 60-day roadmap, you need a consistent daily study commitment. Here's the math:

Total Study Hours\=60 days×2.5 hrs/day\=150 hrs\\text{Total Study Hours} = 60 \\text{ days} \\times 2.5 \\text{ hrs/day} = 150 \\text{ hrs}Total Study Hours\=60 days×2.5 hrs/day\=150 hrs

For those working full-time, this translates to approximately 2 hours on weekdays and 4-5 hours on weekends. The breakdown by phase:

| Phase | Days | Focus | Estimated Hours |
| --- | --- | --- | --- |
| Foundations | 1–10 | Cloud concepts, IAM, console | 25 |
| Core Services | 11–25 | EC2, VPC, S3, RDS, DynamoDB | 38 |
| Architecture & Security | 26–34 | Well-Architected, encryption, monitoring | 23 |
| Serverless & Integration | 35–42 | Lambda, API Gateway, SQS/SNS, Step Functions | 20 |
| Advanced & Projects | 43–50 | IaC, CI/CD, containers, portfolio projects | 20 |
| Certification Prep | 51–60 | Practice exams, weak area review | 24 |

Research from Gallup and AWS shows that nearly **72% of professionals** who acquire advanced digital skills express high job satisfaction and greater confidence in job security—making the investment well worthwhile .

## Footnotes

1. [Start Your Learning Journey with the Right Roadmap from AWS Training and Certification](https://aws.amazon.com/blogs/apn/start-your-learning-journey-with-the-right-roadmap-from-aws-training-and-certification) - AWS official blog on learning paths, free resources, and the Gallup research on digital skills. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-3)
 

### Knowledge Check

Question 1 of 5

Q1Single choice

Which AWS service provides serverless compute that runs code in response to events without provisioning servers?

Amazon EC2

AWS Lambda

Amazon ECS

AWS Batch

BackNext

## Explore Related Topics

[1\\ \\ DevOps Roadmap: From Foundations to Cloud-Native Mastery\\ \\ The DevOps roadmap is one of the most sought-after career guides in modern technology. With the global DevOps market projected to grow from 10.4billionin2023to10.4 billion in 2023 to 10.4billionin2023to25.5 billion by 2028 at a CAGR of 19.7%, and 80% of organizations now practicing DevOps, the demand for skilled professionals has neve](https://coursify.hasanraiyan.me/research/devops-roadmap-from-foundations-to-cloud-native-mastery) [2\\ \\ Learn Python in 30 Days\\ \\ Python is one of the most versatile and in-demand programming languages in the world. Created by Guido van Rossum and first released on February 20, 1991, Python has grown from a hobby project to the 1 programming language on the TIOBE Index as of 2024 . With over 18.2 million active developers worl](https://coursify.hasanraiyan.me/research/learn-python-in-30-days)

[![Coursify logo](https://coursify.hasanraiyan.me/_next/image?url=%2Fimages%2Fapps%2Fcoursify.png&w=48&q=75)Browse all research articles](https://coursify.hasanraiyan.me/research)