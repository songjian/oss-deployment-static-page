# 使用阿里云OSS部署静态网站
参考：

https://help.aliyun.com/document_detail/31872.html


阿里云OSS（Object Storage Service）是一个对象存储服务，可以用来存储图片、音频、视频等各种类型文件，也可以存储HTML格式文件。OSS允许配置访问域名和设置静态入口页，可以用来部署一个简单的静态网站。

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

1. 本地创建两个HTML格式文件
    * 默认首页
    ```html
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
    ```html
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
2. 将网页文件上传到目标Bucket
    1. 登录OSS管理控制台
    2. 单击Bucket列表，然后单击目标Bucket
    3. 单击文件管理，然后单击上传文件
    4. 在上传文件面板的上传文件区域，单击直接上传并选中刚刚创建的两个网页文件。其他参数均保持默认配置

步骤3：配置静态网站托管

1. 单击基础设置 > 静态页面
2. 单击设置，将index.html设置为默认首页；将error.html设置为默认404页。
3. 单击保存

步骤4：绑定自定义域名

现在，您已有了根域名example.com和名为examplebucket的Bucket，接下来您需要将域名绑定到Bucket，以便能够使用您的域名访问Bucket。

1. 在Bucket管理页面，单击传输管理 > 域名管理。
2. 单击绑定域名。
3. 在域名文本框输入example.com，并打开自动添加CNAME记录开关。
4. 单击确定。

步骤5：测试网站

在浏览器中访问以下URL以验证网站是否正常运行：
* 访问静态网站首页`http://example.com`，配置正确时显示如下页面：
* 访问Bucket中不存在的文件`http://example.com/example.txt`，配置正确时显示如下页面：