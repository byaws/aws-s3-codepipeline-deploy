<img src='https://github.com/byaws/aws-s3-codepipeline-deploy/raw/master/screenshots/architecture.png' border='0' alt='architecture' />

Implementation of automated distribution through [aws](https://aws.amazon.com/ko/) product [s3](https://aws.amazon.com/ko/s3/) and [codepipeline](https://aws.amazon.com/ko/codepipeline/)

> Create smart AWS diagrams [Cloudcraft](https://cloudcraft.co/)

<br />

## What is AWS ?

Whether you're looking for compute power, database storage, content delivery, or other features with services operated by Amazon, 

AWS has services to help you build sophisticated applications with increased flexibility, scalability, and reliability.

## What is S3 ?

Amazon Simple Storage Service (Amazon S3) is an object storage service that offers industry-leading scalability, data availability, security, and performance.

This means customers of all sizes and industries can use it to store and protect any amount of data for a range of use cases, such as websites, mobile applications, backup and restore, archive, enterprise applications, IoT devices, and big data analytics.

▾ Amazon S3 works

<img src='https://github.com/byaws/aws-s3-codepipeline-deploy/raw/master/screenshots/s3-works.png' border='0' alt='ecs-works' />

## What is CodePipeline ?

AWS CodePipeline is a fully managed continuous delivery service that helps you automate your release pipelines for fast and reliable application and infrastructure updates.

CodePipeline automates the build, test, and deploy phases of your release process every time there is a code change, based on the release model you define.

▾ Amazon CodePipeline works

<img src='https://github.com/byaws/aws-s3-codepipeline-deploy/raw/master/screenshots/codepipeline-works.png' border='0' alt='codepipeline-works' />

## Continuous Deployment with CodePipeline

### Add a Build Specification File to Your Source Repository

CodeBuild to build your Docker image and push the image to Amazon ECR.

Add a `buildspec.yml` file to your source code repository to tell CodeBuild how to do that.

▾ buildspec.yml

```bash
version: 0.2

phases:
  install:
    runtime-versions:
      nodejs: 12
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
      - aws s3 sync ./build s3://{ S3_BUCKET }
```
