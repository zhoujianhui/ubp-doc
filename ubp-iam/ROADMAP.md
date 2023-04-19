## 认证TODO

* 续命模式 (开启续命模式后 在有效时间内 访问任意接口 则自动续命).
* 限制登录数量 -1 为无限大.
* 限制登录拒绝策略 after为后者 before为前者.
* 认证类 登录 失败N次后弹出验证码 （超过验证码阈值 弹出验证码）.
* 认证类 登录 失败次数.
* 认证类 登录 失败锁定时间(秒).

Prevent Brute Force Authentication Attempts with Spring Security
https://www.baeldung.com/spring-security-block-brute-force-authentication-attempts

Spring Security Limit Login Attempts Example
https://www.codejava.net/frameworks/spring-boot/spring-security-limit-login-attempts-example

## banner.txt

https://www.baeldung.com/spring-boot-custom-banners
https://devops.datenkollektiv.de/banner.txt/index.html

## 角色权限分配

* 【DONE】新建角色时，如果没有分配权限会导致该角色的用户无法登录，因为无法获得路由也无法获得个人信息，是否可以设置默认分配权限???
* 单租户下权限分配是否要区分权限分类
* 【优先】API权限粒度太粗，比如更新用户信息可以更新用户基本信息也可以分配用户角色！！！！！！
* 【优先】初始角色的维护

## 用户分类

* 管理员和普通用户的区别，是否可以做到人物扮演（impersonate），人物扮演是否需要得到当事人的同意

## Token Sidejacking

https://github.com/OWASP/CheatSheetSeries/blob/master/cheatsheets/JSON_Web_Token_for_Java_Cheat_Sheet.md#token-sidejacking
它还包含了其他的安全最佳实践

LocalStorage vs Cookie for JWT Access Token war in short
https://coolgk.medium.com/localstorage-vs-cookie-for-jwt-access-token-war-in-short-943fb23239ca

## 优化表结构增加Bean验证


重构认证、注册、找回密码之间的使能关系
