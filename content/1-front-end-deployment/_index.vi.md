---
title : "Triển Khai Front-end"
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 1. </b> "
---
Bước đầu trong bài này, chúng ta sẽ host ứng dụng web (front-end) với S3 Static website hosting:

1. Mở bảng điều khiển [Amazon S3](https://s3.console.aws.amazon.com/s3/get-started?region=ap-southeast-1)

![S3Console](/images/1-front-end-deployment/1-front-end-deployment-1.png?featherlight=false&width=90pc)

2. Ấn **Create bucket**

![CreateBucket](/images/1-front-end-deployment/1-front-end-deployment-2.png?featherlight=false&width=90pc)

3. Nhập tên cho bucket, ví dụ: `fcjdmswebstore`
- Chọn vùng gần bạn nhất

![CreateBucket](/images/1-front-end-deployment/1-front-end-deployment-3.png?featherlight=false&width=90pc)

4. Bỏ chọn chặn cho phép truy cập public
- Tích vào mục **I acknowledge that the current settings might result in this bucket and the objects within becoming public**

![CreateBucket](/images/1-front-end-deployment/1-front-end-deployment-4.png?featherlight=false&width=90pc)

5. Ấn nút **Create bucket**

![CreateBucket](/images/1-front-end-deployment/1-front-end-deployment-5.png?featherlight=false&width=90pc)

6. Ấn vào bucket vừa tạo

![CreateBucket](/images/1-front-end-deployment/1-front-end-deployment-6.png?featherlight=false&width=90pc)

7. Ấn sang tab **Properties**

![SettingBucket](/images/1-front-end-deployment/1-front-end-deployment-7.png?featherlight=false&width=90pc)

8. Kéo xuống cuối trang, ấn **Edit** của mục **Static web hosting**

![SettingBucket](/images/1-front-end-deployment/1-front-end-deployment-8.png?featherlight=false&width=90pc)

9. Chọn **Enable** để kích hoạt host web tĩnh trên S3
- Nhập `index.html` cho mục **Index document**

![SettingBucket](/images/1-front-end-deployment/1-front-end-deployment-9.png?featherlight=false&width=90pc)

10. Ấn nút **Save changes**

![SettingBucket](/images/1-front-end-deployment/1-front-end-deployment-10.png?featherlight=false&width=90pc)

- Sau khi kích hoạt thành công, bạn hãy ghi lại đường dẫn của web

![SettingBucket](/images/1-front-end-deployment/1-front-end-deployment-11.png?featherlight=false&width=90pc)

11. Sau đó, chúng ta cần thêm policy cho S3 bucket để có thể truy cập được:
- Chọn sang tab **Permissions**
- Ấn nút **Edit** tại mục **Bucket policy**

![SettingBucket](/images/1-front-end-deployment/1-front-end-deployment-12.png?featherlight=false&width=90pc)

12. Sao chép đoạn dưới đây vào mục **Policy**
```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::BUCKET_NAME/*"
        }
    ]
}
```
- Thay thế `BUCKET_NAME` bằng tên bucket mà bạn đặt, sau đó ấn nút **Save changes**

![SettingBucket](/images/1-front-end-deployment/1-front-end-deployment-13.png?featherlight=false&width=90pc)

13. Mở tệp **src/component/Home/Upload.js** trong thư mục source code của ứng dụng và bỏ comment đoạn code gọi API ghi dữ liệu vào DynamoDB.

![SettingBucket](/images/1-front-end-deployment/1-front-end-deployment-16.png?featherlight=false&width=90pc)

14. Tiếp theo chạy câu lệnh sau tại thư mục gốc của project bạn đã tải về từ workshop 2.
```
yarn build
aws s3 cp build s3://BUCKET_NAME --recursive
```

- Thay thế `BUCKET_NAME` bằng tên bucket mà bạn đặt

{{% notice note %}}
Nếu bạn tải lên thất bại, hãy cấu hình access key ID, secret access key, aws region và output format với câu lệnh `aws configure`
{{% /notice %}}

Kết quả sau khi tải xong:

![SettingBucket](/images/1-front-end-deployment/1-front-end-deployment-14.png?featherlight=false&width=90pc)

15. Dán đường dẫn web mà bạn vừa ghi lại vào trình duyệt web của bạn

![SettingBucket](/images/1-front-end-deployment/1-front-end-deployment-15.png?featherlight=false&width=90pc)

Bạn đã hoàn thành việc host website của mình trên S3. Sang phần tiếp theo chúng ta cập nhật lại các lambda function của bài workshop số 2.