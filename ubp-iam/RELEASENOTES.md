# 发布说明

## v1.1.0

* 修改GroupId为“org.zhoujianhui.iam"
* 按照最佳实践约定更新了pom.xml
* 重构Controller集成测试，验证setUp中的login是否成功
* 增加Spring配置元数据，便于IDE配置时显示提示
* 更新基础依赖

## v2.0.0

* 统一了单租户和多租户的实现

## v2.2.0（2022-03-30）

* 修复了用户转换时未转换是否是管理员的问题
* 为Permission实体添加审计
* 为路由实体添加分类元数据
* 实现了单/多租户实现的分离，支持配置是否开启多租户模式，默认开启多租户
* 区别开租户注册和租户创建
* 去掉用户名和密码认证
* 添加账户密码、短信验证码认证
* 添加用户名密码、短信验证码注册
* 设置配置属性默认值，减少配置复杂性
* 可灵活配置登录、注册、重置密码、授权
* 设置用户名和手机号唯一性限制
* 将路由名改为路由路径、默认设置为菜单、路由分类默认为BUSINESS
* 添加登录日志审计
* 更新spring-rest-query-language到1.1.0

## v2.3.0（2022-04-06）

* 修复认证失败错误无法响应到前端的问题
* 修复初始角色维护功能误用角色维护功能
* 将方法名和url中的include改为with
* 禁止超级管理员用户的删除和超级管理员角色的删除和分配
* 修复用户过期后任然能够通过验证码登录的问题

## v2.4.0 (2022-04-15)

* 修复API权限未分配的情况下安全元数据获取为空的问题
* 重构rbac授权控制
* 实现基于vote的水平权限控制
* 实现认证后扩展用户备注信息机制
* 修复账户认证条件化默认配置错误
* 严格区分401和403
* 重构JWT认证模块

## v2.5.0（2022-04-22）

* 重构用户扩展机制
* 重构平台初始化脚本
* 实现自定义RoleVoter
* 重构认证异常处理和异常信息提示
* 重构认证失败异常处理类

## v2.6.0（2022-04-27）

* 防止账户（用户名和手机号）穷举
* 实现userWithRolesCache缓存
* 实现accessibleRoutes缓存

## v2.7.0（2022-05-21）

* 重构单租户实现
* 重构RouteService，实现获取路由可访问性API，并重命名缓存为routeAccessibilities
* 实现租户的可扩展删除
* 提取租户的实现为独立的starter
* 重构认证生成的JWT只存储用户ID
* 增加AuthedUser用于存储认证后的用户但是不保存在Token中（不落地客户端）
* 重构JWT认证不需要同时发送访问Token和刷新Token
* 重构Permission相关API
* 实现可扩展租户合并机制
* 重构路由资源同步
* 解决所有的TODO
* 使用构造注入替换@Autowired
* 使用Sonar检测并修改代码问题

## v2.8.0（2022-05-28）

* 将路由资源和路由权限管理合并
* 使用新的web安全配置方式
* 简化starter
* 将JPA审计实现类提取到独立的starter中，作为默认实现
* 删除UserContext实现
* 重构Token中含有多个claims包括：用户ID和用户名两个不变的信息

## v2.9.0（2022-06-29）

* 将单租户和多租户实现分离
* 更新租户依赖到0.3.0；更新审计的依赖到0.6.0；更新mapstruct到1.5.1
* 重构认证授权模块，支持和网关搭配使用
* 为用户模型User添加头像avatar字段
* 删除AuthedUser改用AuthenticationUserDto作为登录成功后的响应体
* 实现并提炼出用户上下文UserContext及其中继拦截器
* 重构匿名访问和授权异常处理
* 重命名sql文件;重构IAM平台表
* 重构用户备注信息提供器模块UserRemarksProvider
* 实现租户和权限模块的扩展点，用于和IAM扩展模块联动
* 区分H2和MySQL两套脚本，但H2以兼容MySQL模式运行
* 更新swagger依赖到1.3.0

## v2.9.1（2022-08-02）

* 重构platform-iam-data.sql，修复权限类型、初始角色权限、路由资源路径等问题
* 修复RouteSyncService中同步路由的回归性BUG
* 设置平台租户管理员默认密码为：root@iam#No1!
* 重构AuthenticationEntryPointImpl，修改匿名访问的提示信息
* 重构租户注册，增加管理员用户同名和同手机号检查

## v2.10.0（2022-09-05）

* 将platform-iam-data.sql中的“访问路由权限管理页面”权限改为“访问路由资源管理页面”
* 修复InitRoleRepository中笔误，将实体名“Role”改为“InitRole"
* 实现用户中心
* 实现短信验证码类型和发送前提条件

## v2.11.0（2022-10-18）

* 实现初始密码的短信发送
* 更新captcha依赖，解决短信验证码类型无法valueOf转换的问题
* 修复同名同手机号检测错误的问题
* 解决通过短信验证码进行密码重置时没有清除userWithRolesCache缓存的问题
* 实现页面元素权限控制
* 更新SpringBoot到2.7.4

## v2.12.0（2023-02-16）

* 更新SpringBoot到2.7.8
* 完全采用H2的语法，不使用MySQl兼容模式
* 重构认证模块
* 添加租户新增后处理扩展点，支持租户的自定义初始化
* 重构并统一初始密码短信发送服务并支持自定义扩展
* 将日志审计starter移除，由项目自主添加
* 添加用户删除处理扩展点，支持用户自定义删除
* 重构短信验证码登录模块，将captchaToken改为captchaSignature
* 重构所有模块的日志输出信息
* 重构上下文设置，将上下文中继移至网关IAM中实现
* 将ultra-iam重命名为iam
* 支持配置注册时租户管理员的默认头像
* 实现了认证前后处理扩展点
* 使用认证前后处理扩展点实现登录日志
* 采用Caffeine替换Ehcache作为默认缓存实现

## v2.12.1（2023-02-19）

* 修复认证会话被强退后，刷新页面重新登录成功的问题
* 将扩展点的包名”handler“改为”extension“

## v2.12.2（2023-02-28）

* 修复短信验证码密码重置模块，将captchaToken改为captchaSignature

## v2.13.0（2023-03-07）

* 引入ubp-cache-insight并实现IAM相关缓存信息的注册
* 重构认证处理扩展接口中的认证预处理方法

## v2.14.0（2023-03-09）

* 实现JWT生成时断言claim的扩展接口，用于在Token中添加自定义断言
* 重构JwtAuthenticationToken添加isOncePerRequestToken和isAuthenticatedByRefreshToken标识
* 更新captcha和exception相关依赖
* 将exception-spring-boot-starter移除，由项目自主添加

## v2.14.1（2023-03-13）

* 重构JwtAuthenticationOncePerRequestFilter，在认证后设置isOncePerRequestToken标识
* 新增IAM相关的错误码枚举IamErrorCode

## v2.15.0

* 从用户模块和密码重置模块中重构出个人中心模块并分配权限；将用户水平权限控制重构为个人信息水平权限控制
* 重构账户密码认证，支持邮箱密码登录
* 实现邮箱验证码注册和密码重置以及使能控制
* 实现IamCacheManager，用于IAM相关缓存的统一管理
* 实现邮箱注册扩展接口
* 重构IAM配置，默认只开启用户密码认证；可按需引入短信和邮件starter并开启对应认证