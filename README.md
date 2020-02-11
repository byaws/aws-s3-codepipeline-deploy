<img src='https://github.com/byaws/images/raw/master/s3-codepipeline/architecture.png' border='0' alt='architecture' />

Implementation of automated distribution through [aws](https://aws.amazon.com/ko/) product [s3](https://aws.amazon.com/ko/s3/), [codepipeline](https://aws.amazon.com/ko/codepipeline/), [sns](https://aws.amazon.com/ko/sns), [chatbot](https://aws.amazon.com/ko/chatbot/)

> Create smart AWS diagrams [Cloudcraft](https://cloudcraft.co/)

<br />

## What is AWS ?

Whether you're looking for compute power, database storage, content delivery, or other features with services operated by Amazon, 

AWS has services to help you build sophisticated applications with increased flexibility, scalability, and reliability.

## What is S3 ?

Amazon Simple Storage Service (Amazon S3) is an object storage service that offers industry-leading scalability, data availability, security, and performance.

This means customers of all sizes and industries can use it to store and protect any amount of data for a range of use cases, such as websites, mobile applications, backup and restore, archive, enterprise applications, IoT devices, and big data analytics.

▾ Amazon S3 works

<img src='https://github.com/byaws/images/raw/master/s3-codepipeline/s3-works.png' border='0' alt='s3-works' />

## What is CodePipeline ?

AWS CodePipeline is a fully managed continuous delivery service that helps you automate your release pipelines for fast and reliable application and infrastructure updates.

CodePipeline automates the build, test, and deploy phases of your release process every time there is a code change, based on the release model you define.

▾ Amazon CodePipeline works

<img src='https://github.com/byaws/images/raw/master/s3-codepipeline/codepipeline-works.png' border='0' alt='codepipeline-works' />

## Continuous Deployment with CodePipeline

### Add a Build Specification File to Your Source Repository

Add a `buildspec.yml` file to your source code repository to tell CodeBuild how to do that.

▾ buildspec.yml

```bash
version: 0.2

phases:
  install:
    runtime-versions:
      nodejs: 12                               # Runtime node.js 12
    commands:
      - npm install -g npm@latest              # Install npm latest
  pre_build:
    commands:
      - npm install                            # Install dependencies
  build:
    commands:
      - npm run build                          # Build 
  post_build:
    commands:
      - aws s3 sync ./build s3://{ S3_BUCKET } # Upload S3
```

## What is SNS ?

Amazon Simple Notification Service (SNS) is a highly available, durable, secure, fully managed pub/sub messaging service that enables you to decouple microservices, distributed systems, and serverless applications.

Amazon SNS provides topics for high-throughput, push-based, many-to-many messaging.

▾ Amazon SNS works

<img src='https://github.com/byaws/images/raw/master/s3-codepipeline/sns-works.png' border='0' alt='sns-works' />

## What is Chatbot ?

AWS Chatbot is an interactive agent that makes it easy to monitor and interact with your AWS resources in your Slack channels and Amazon Chime chat rooms.

AWS Chatbot is currently in beta.

▾ Amazon Chatbot works Notifications

<img src='https://github.com/byaws/images/raw/master/s3-codepipeline/chatbot-notifications.png' border='0' alt='chatbot-notifications' />

▾ Amazon Chatbot works Commands

<img src='https://github.com/byaws/images/raw/master/s3-codepipeline/chatbot-commands.png' border='0' alt='chatbot-commands' />
