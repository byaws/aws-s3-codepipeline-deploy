<img src='https://github.com/byaws/aws-s3-codepipeline-deploy/raw/images/architecture.png' border='0' alt='architecture' />

Implementation of automated distribution through [AWS](https://aws.amazon.com/ko/) product [S3](https://aws.amazon.com/ko/s3/) and [CodePipeline](https://aws.amazon.com/ko/codepipeline/)

Notifications over Slack using through [AWS](https://aws.amazon.com/ko/) product [SNS](https://aws.amazon.com/ko/sns) and [Chatbot](https://aws.amazon.com/ko/chatbot/)

> Create smart AWS diagrams [Cloudcraft](https://cloudcraft.co/)

<br />

## What is AWS ?

Whether you're looking for compute power, database storage, content delivery, or other features with services operated by Amazon, 

AWS has services to help you build sophisticated applications with increased flexibility, scalability, and reliability.

## What is S3 ?

Amazon Simple Storage Service (Amazon S3) is an object storage service that offers industry-leading scalability, data availability, security, and performance.

This means customers of all sizes and industries can use it to store and protect any amount of data for a range of use cases, such as websites, mobile applications, backup and restore, archive, enterprise applications, IoT devices, and big data analytics.

▾ Amazon S3 works

<img src='https://github.com/byaws/aws-s3-codepipeline-deploy/raw/images/s3-works.png' border='0' alt='s3-works' />

## What is CodePipeline ?

AWS CodePipeline is a fully managed continuous delivery service that helps you automate your release pipelines for fast and reliable application and infrastructure updates.

CodePipeline automates the build, test, and deploy phases of your release process every time there is a code change, based on the release model you define.

▾ Amazon CodePipeline works

<img src='https://github.com/byaws/aws-s3-codepipeline-deploy/raw/images/codepipeline-works.png' border='0' alt='codepipeline-works' />

### Add a Build Specification File to Your Source Repository

Add a `buildspec.yml` file to your source code repository to tell CodeBuild how to do that.

▾ buildspec.yml

```bash
version: 0.2

phases:
  install:
    runtime-versions:
      nodejs: lts
    commands:
      - npm install -g npm@latest
  pre_build:
    commands:
      - npm install
  build:
    commands:
      - npm run build
  post_build:
    commands:
      - aws s3 sync ./[dist folder] s3://[s3 bucket]
```

## What is SNS ?

Amazon Simple Notification Service (SNS) is a highly available, durable, secure, fully managed pub/sub messaging service that enables you to decouple microservices, distributed systems, and serverless applications.

Amazon SNS provides topics for high-throughput, push-based, many-to-many messaging.

▾ Amazon SNS works

<img src='https://github.com/byaws/aws-s3-codepipeline-deploy/raw/images/sns-works.png' border='0' alt='sns-works' />

## What is Chatbot ?

AWS Chatbot is an interactive agent that makes it easy to monitor and interact with your AWS resources in your Slack channels and Amazon Chime chat rooms.

AWS Chatbot is currently in beta.

▾ Amazon Chatbot Notifications

<img src='https://github.com/byaws/aws-s3-codepipeline-deploy/raw/images/chatbot-notifications.png' border='0' alt='chatbot-notifications' />

▾ Amazon Chatbot Commands

<img src='https://github.com/byaws/aws-s3-codepipeline-deploy/raw/images/chatbot-commands.png' border='0' alt='chatbot-commands' />
