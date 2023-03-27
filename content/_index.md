---
title : "Serverless - A Guide to Writing Front-End Code for Calling API Gateway"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
---
# Serverless - A Guide to Writing Front-End Code for Calling API Gateway

#### Overview

In the last workshop, we learned how to create and use a Lambda function that interacts with DynamoDB and uses Amplify for user authentication and storage. Next in this series, we build a web application (front-end) to interact with the database through Lambda and API Gateway.

{{% notice warning %}}
Please do workshops 1 and 2 in this series before doing this one.
{{% /notice %}}

The architecture of the application we will build:

![WebArchitect](/images/serverless-architect-diagram.png?featherlight=false&width=45pc)

#### Content

1. [Front-end Deployment](1-front-end-deployment/)
2. [Config API Gateway](2-config-api-gw/)
3. [Test APIs By Postman](3-test-api-by-postman/)
4. [Test APIs With Front-end](4-test-front-end/)
5. [Cleanup](5-cleanup)