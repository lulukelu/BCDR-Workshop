﻿---
title: "准备工作"
chapter: false
weight: 31
---

## 配置Storage Gateway之前的准备工作

接下来我们会进行准备工作：
1.创建一个IAM用户
登录 AWS 管理控制台，并通过网址https://console.amazonaws.cn/iam/home#/users$new?step=details打开 “IAM”控制台，并开始创建一个新的用户。
创建一个新的IAM用户，“访问类型”选择”Programmatic access”，用户名为”storagegateway-coldbackup”。
![](/images/SetupStorageGW/addIAMUser.png)
下一步选择AWS管理的策略：AmazonS3FullAccess 和 AWSStorageGatewayFullAccess
![](/images/SetupStorageGW/IAMPolicy1.png)
![](/images/SetupStorageGW/IAMPolicy2.png)
最后需要记录下Access Key和Secret Access Key并妥善保存。
![](/images/SetupStorageGW/AKSK.png)

2.创建一个S3 Bucket
登录 AWS 管理控制台，并通过网址https://console.amazonaws.cn/s3/bucket/create?region=cn-northwest-1打开 Amazon S3 控制台，并开始创建一个新的 S3存储桶 
Create bucket (创建存储桶)，在 Bucket name 字段中，为新存储桶键入一个符合 DNS 标准的唯一名称，此处名称为“storagegateway-coldbackup-20200101xx”。对于 Region，选择作为要将存储桶放置到的区域，选择“China (Ningxia) cn-northwest-1”，然后点击”Create bukcet”。
![](/images/SetupStorageGW/createS3Bucekt.png)

