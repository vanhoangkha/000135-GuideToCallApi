---
title : "Dọn Dẹp Tài Nguyên"
date :  "`r Sys.Date()`" 
weight : 5
chapter : false
pre : " <b> 5. </b> "
---
1. Xoá bảng trong DynamoDB
- Mở bảng điều khiển của [DynamoDB](https://ap-southeast-1.console.aws.amazon.com/dynamodbv2/home?region=ap-southeast-1#dashboard)
- Chọn **Tables** ở menu phía bên trái
- Chọn bảng **Documents**
- Ấn **Delete**
- Nhập **delete** và ấn **Delete table**
2. Xoá S3 bucket
- Mở bảng điều khiển của [S3](https://s3.console.aws.amazon.com/s3/buckets?region=ap-southeast-1)
- Chọn bucket **fcjdmswebstore**
- Ấn nút **Empty**
- Nhập **permanently delete** và ấn **Empty**
- Chọn bucket **fcjdmsstore...-dev**
- Ấn nút **Empty**
- Nhập **permanently delete** và ấn **Empty**
3. Xoá REST API
- Mở bảng điều khiển của [API Gateway](https://ap-southeast-1.console.aws.amazon.com/apigateway/main/apis?region=ap-southeast-1#)
- Chọn **fcj-dms-api**
- Ấn **Actions** và chọn **Delete**
- Ấn **Delete**
4. Xoá Lambda function
- Mở bảng điều khiển của [AWS Lambda](https://ap-southeast-1.console.aws.amazon.com/lambda/home?region=ap-southeast-1#/functions)
- Chọn **list_documents** function
- Ấn **Actions**
- Chọn **Delete**
- Nhập **delete** và ấn **Delete**
- Tương tự với các function **upload_document**, **delete_document**.
5. Chạy câu lệnh sau ở thư mục gốc của project:
```
amplify remove auth
amplify remove storage
amplify push
amplify delete
```