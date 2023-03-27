---
title : "Serverless - Hướng dẫn viết Front-end gọi API Gateway"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
---
# Serverless - Hướng dẫn viết Front-end gọi API Gateway

### Tổng quan

Trong bài lần trước, chúng ta đã biết cách tạo và sử dụng Lambda function tương tác với DynamoDB và sử dụng Amplify cho việc xác thực người dùng và lưu trữ. Tiếp theo trong series này, chúng ta dựng một ứng dụng web (front-end) để tương tác với cơ sở dữ liệu thông qua Lambda và API Gateway.

{{% notice warning %}}
Bạn hãy thực hiện workshop số 1 và số 2 trong series này trước khi thực hiện bài này.
{{% /notice %}}

Kiến trúc của ứng dụng chúng ta sẽ xây dựng:

![WebArchitect](/images/serverless-architect-diagram.png?featherlight=false&width=45pc)

### Nội dung

1. [Triển khai Front-end](1-front-end-deployment/)
2. [Cấu hình API Gateway](2-config-api-gw/)
3. [Kiểm tra API với Postman](3-test-api-by-postman/)
4. [Kiểm tra API với Front-end](4-test-front-end/)
5. [Dọn dẹp tài nguyên](5-cleanup)