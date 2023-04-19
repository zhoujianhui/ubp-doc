# ubp-iam

多租户的身份认证和访问控制

## 快速开始

### 引入starter

```xml

<dependency>
    <groupId>org.zhoujianhui.iam</groupId>
    <artifactId>iam-spring-boot-starter</artifactId>
    <version>2.15.0-SNAPSHOT</version>
</dependency>
```

### 配置iam

```yaml
# IAM配置
iam:
  # 认证配置
  authentication:
    account-password:
      enable: true  # 是否开启账户密码认证（可选，默认为：true/开启）
      login-url: /account-password-login # 账户密码认证URL（可选，默认为："/account-password-login"）
    sms-captcha:
      enable: true  # 是否开启短信验证码认证（可选，默认为：true/开启）
      login-url: /sms-captcha-login # 短信验证码认证URL（可选，默认为："/sms-captcha-login"）
      login-register-all-in-one:
        enable: false  # 是否开启短信验证码登录注册一体化（可选，默认为：false/不开启）
        enable-send-init-password: false # 是否开启发送初始密码（可选，默认为：false/不开启）
        init-password-sms-sender: # 初始密码短信发送器名称
    jwt:
      login-url: /token-login # Token认证URL（可选，默认为："/token-login"）
      secret: ThisIsOurSecretKeyToSignOurTokens # Token加密秘钥，长度必须大于32位
      access-token-header: x-access-token # 访问Token头名称（可选，默认为："x-access-token"）
      access-token-lifetime: 900000 # 访问Token有效期，单位：毫秒（可选，默认：15分钟）
      refresh-token-header: x-refresh-token # 刷新Token头名称（可选，默认为："x-refresh-token"）
      refresh-token-lifetime: 432000000 # 刷新Token有效期，单位：毫秒（可选，默认：7天）
      enable-auto-refresh-token: true # 是否支持自动刷新token（可选，默认为：true/支持）
      authed-user-dto-token-header: user # 认证后返回给客户端的用户DTO对应的token头（可选，默认为：user）
  # 注册配置
  register:
    user-type: ErpUser # 注册用户类型，用于扩展用户时设置（可选，默认为：User）
    # admin-avatar: admin.png # 用（租）户注册时，默认租户管理员头像（可选，默认为：admin.png）
    username-password:
      enable: true # 是否开启用户名密码注册（可选，默认为：true/开启）
    sms-captcha:
      enable: true # 是否开启短信验证码注册（可选，默认为：true/开启）
      enable-send-init-password: false # 是否开启发送初始密码（可选，默认为：false/不开启）
      init-password-sms-sender: # 初始密码短信发送器名称
    mail-captcha:
      enable: false # 是否开启邮件验证码注册（可选，默认为：false/开启）
  # 密码重置配置
  password-reset:
    sms-captcha:
      enable: true # 是否开启短信验证码密码重置（可选，默认为：true/开启）
    mail-captcha:
      enable: false # 是否开启邮件验证码密码重置（可选，默认为：false/开启）
  # 授（鉴）权配置
  authorization:
    enable: true # 是否开启授（鉴）权（可选，默认为：true/开启）
```

## 发布说明

[点击查看](RELEASENOTES.md)

## 路线图

[点击查看](RELEASENOTES.md)