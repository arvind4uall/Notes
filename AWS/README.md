# AWS Cloud Practitioner

## Difference between EFS(Elastic file system) & EBS (Elastic block store)

EFS (Elastic File System) and EBS (Elastic Block Store) are both storage solutions provided by AWS (Amazon Web Services), but they differ in their functionality and use. The short difference between EFS and EBS are:

- EFS is a fully managed, scalable file storage service that is designed for use with AWS cloud services and on-premises resources, whereas EBS is a block-level storage service that is used to store data within the EC2 instance.

- EFS can be accessed by multiple EC2 instances simultaneously, making it suitable for shared workloads such as web servers or content management systems, whereas EBS can only be attached to one EC2 instance at a time, making it suitable for individual workloads such as databases or application servers.

- EFS is designed for data sharing and collaboration, while EBS is designed for high-performance, low-latency storage.

- EFS uses a pay-as-you-go pricing model, where customers pay only for the storage they use, while EBS uses a provisioned IOPS pricing model, where customers pay for the amount of provisioned IOPS (input/output operations per second) they require.

## Some AWS Service and their uses

### AWS Trusted Advisor

You are a AWS user and you want to take most of benefits from your investment in that case AWS Trusted Advisor will help you.

AWS Trusted Advisor scans whole your infrastructure and compare it with AWS best practice in five categories, and provide recommended actions.

These five categories are (CPSFS)

1. Cost Optimization
2. Performance
3. Security
4. Fault Tolerance
5. Service limits

## Six pillars of AWS Well Architected framework (OpSeRePeCoSu)

1. Operational Excellence
2. Security
3. Reliability
4. Performance Efficiency
5. Cost Optimization
6. Sustainability

### Some important things to know

You may see use-cases asking you to select one of CloudWatch vs CloudTrail vs Config. Just remember this thumb rule -

- Think resource performance monitoring, events, and alerts; think CloudWatch.

- Think account-specific activity and audit; think CloudTrail.

- Think resource-specific change history, audit, and compliance; think Config.
