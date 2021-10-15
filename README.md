# 使用阿里云OSS部署静态网站

OSS是对象存储服务

步骤1：创建Bucket

您需要创建一个公共读的Bucket，用以设置静态网站托管及存放网站数据。

1. 登录OSS管理控制台
2. 单机Bucket列表，创建Bucket
3. 创建Bucket面板配置参数：
    * 设置Bucket名称，例如examplebucket
    * 地域，例如 华东1（杭州）
    * 存储类型，选择标准存储
    * 读写权限，选择公共读

步骤2：创建网页文件并上传

您需要创建静态网站首页和404错误页面的网页文件，并上传至目标Bucket。

* 默认首页
  * ```html
    <html>
        <head>
            <title>Hello OSS!</title>
            <meta charset="utf-8">
        </head>
        <body>
            <p>开始阿里云OSS托管</p>
            <p>这是索引页面</p>
        </body>
     </html>
    ```
  * 默认404页
    * ```html
<html>
<head>
   <title>Hello OSS!</title>
   <meta charset="utf-8">
</head>
<body>
   <p>这是404错误页面</p>
</body>
</html> 
    ```
