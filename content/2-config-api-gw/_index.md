---
title : "Config API Gateway"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 2. </b> "
---

#### Config API Gateway

1. Open [Amazon API Gateway console](https://ap-southeast-1.console.aws.amazon.com/apigateway/main/apis?region=ap-southeast-1)

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-2.png?featherlight=false&width=90pc)

2. Click **Create API**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-3.png?featherlight=false&width=90pc)

3. Scroll down to **REST API** section, click **Build**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-4.png?featherlight=false&width=90pc)

4. Leave the default **New API**.
- Enter API name: `fcj-dms-api`
- Select Endpoint type as **Regional**
- Click **Create API**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-5.png?featherlight=false&width=90pc)

5. After creating the API, click **Action | Create Resource** to create resource for API.

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-6.png?featherlight=false&width=90pc)

6. Enter resource name: `docs`, then click **Create resource**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-7.png?featherlight=false&width=90pc)

7. Select **docs** resource, then click **Action | Create Method**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-8.png?featherlight=false&width=90pc)

8. Click **POST** method.
- Check **Lambda Proxy integration**
- Select the region of the Lambda function you created
- Select **upload_document** function
- Finally press **Create method**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-9.png?featherlight=false&width=90pc)

9. Select **docs** resource and click **Create resource**.

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-10.png?featherlight=false&width=90pc)

10. Enter resource name: `{id}`, then click **Create resource**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-11.png?featherlight=false&width=90pc)

11. Select **/{id}** resource and click **Create method**.

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-12.png?featherlight=false&width=90pc)

12. Select **GET** method.
- Check **Lambda Proxy integration**
- Select the region of the Lambda function you created
- Select **list_documents** function
- Finally press **Create method**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-13.png?featherlight=false&width=90pc)

13. Select **/{id}** resource, then click **Create method**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-14.png?featherlight=false&width=90pc)

14. Select **GET** method.
- Check **Lambda Proxy integration**
- Select the region of the Lambda function you created
- Select **list_documents** function
- Finally click **Create method**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-15.png?featherlight=false&width=90pc)

15. Choose **DELETE** method, then select **Method request** and click **Edit**.

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-16.png?featherlight=false&width=90pc)

16. Expand **URL Query String Parameters** section.
- Click **Add query string** to add a new parameter
- Enter parameter name: `file`. This parameter is value of the name of the file you want to delete.
- Ấn **Save**.

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-17.png?featherlight=false&width=90pc)

17. Select **docs** resource, then click **Enable CORS**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-18.png?featherlight=false&width=90pc)

18. Select **POST** method and click **Save**.

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-19.png?featherlight=false&width=90pc)

19. Do the same to enable CORS for **/{id}** resource
- Select **/{id}** resource, then click **Enable CORS**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-20.png?featherlight=false&width=90pc)

20. Select **GET** and **DELETE** methods and click **Save**.

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-21.png?featherlight=false&width=90pc)

21. After completing the setup, we deploy the API. Select **/**, then click **Deploy API**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-22.png?featherlight=false&width=90pc)

22. Select **[New Stage]**
- Enter stage name: `dev`
- Click **Deploy**

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-23.png?featherlight=false&width=90pc)

23. Note down the URL of the API used for the next section.

![ConfigAPI](/images/2-config-api-gw/2-config-api-gw-24.png?featherlight=false&width=90pc)


#### Update Lambda function

1. Open [AWS Lambda console](https://ap-southeast-1.console.aws.amazon.com/lambda/home?region=ap-southeast-1#/functions).
2. Select **upload_document** function.
3. Comment on line 13 and uncomment line 12.
4. Click **Deploy**

![UpdateFunction](/images/2-config-api-gw/2-config-api-gw-1.png?featherlight=false&width=90pc)

You have finished setting up the API. Next, we will test the API working and integrate it into our application.

