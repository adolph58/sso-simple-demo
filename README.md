## 使用 Spring Boot 2.0.8.RELEASE 和 OAuth2.0 实现 SSO 单点登录

### 简介
1. 存储 token 使用的是 redis，所以需要本地启动一个redis服务
2. 使用数据库保存客户端信息、用户角色等信息，所以需要在数据库执行 sql 脚本
3. 包含一个认证服务器，一个资源服务器，一个单点登录客户端

### 单点登录流程
1. 先启动 oauth-server 项目，然后再启动 oauth-client 项目
2. 输入客户端地址 http://localhost:8082/user
3. 进入到认证服务器登录页面
4. 登录完成后，自动重定向回客户端地址

### 资源请求方法
#### 1.请求 token（工具-Postman）
http://localhost:80/oauth/token?grant_type=password&username=admin&password=123456

填写 clientId 和 密码  
图片地址：
oauth-server:\resources\images\request-token.png

#### 2.带上 token 请求资源
图片地址：  
oauth-server:\resources\images\request-resource.png
