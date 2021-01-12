# Questions

- When programming using the AWS SDK locally on your personal computer, which method should you use for supplying AWS credentials?
  - Configure the AWS Credentials file to contain an access key id and secret access associated with an IAM User
- What are the three common ways you can interact with the APIs of AWS?
  - AWS Management Console (GUI: graphical user interface), CLI (commmand line interface) and SDK (software development kit)
  ![how to interact with aws](assets/aws-interaction.png)
- In Cloud9, how often are the AWS managed temporary credentials automatically rotated?
  - Every 5 minutes
- Which file contains your credentials that the CLI uses to make calls AWS on Cloud9 or from your laptop?
  - `.aws/credentials`
- What command can you use to have more information about the S3 list bucket CLI command?
  - `aws s3 ls help`
- AWS Cloud9 operates as what kind of cloud-based environment?
  - Integrated Development Environment (IDE)
  - It includes a code editor, debugger and terminal
- What is considered a best practice for providing AWS credentials to your code using the AWS SDK running?
  - Using IAM Roles