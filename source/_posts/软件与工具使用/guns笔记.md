---
toc:
  depth_from: 2
  depth_to: 6
  ordered: false
---
# 大道至简

## 目标：系统架构师系列课程
## 系统高可用：
- 负载均衡
- 限流措施
- 分布式事务
- 分布式session
- 压力测试

## 系统高并发
- 缓存应用
- 异步并发处理
- http缓存
- jvm的优化
- 队列应用
- 动静分离

## 构建应用
- 目标：快速构建应用系统
- 引入guns框架

---
# guns入门
## 基本概念
- 快速构建后台管理系统的开源框架
- guns默认提供诸多业务系统的基本功能
- guns集成诸多优秀开源框架

## 权限管理
- 用户管理
- 角色管理
- 部门管理
- 菜单管理
- 字典管理
- 业务日志
- 登录日志
- 监控日志
- 通知管理
- 代码生成

## guns部署
- 使用idea open->guns-parents

- 修改数据源
 目标：guns-admin\src\main\resources\application.yml<br>
 修改内容：<br>
 修改端口，修改连接本地数据库账户密码
 [1] spring.datasource<br>
 [2] guns.flowable.datasource<br>
 [3] guns.flowable.muti-datasource
	
- 启动guns：
	1. 运行java文件【spring boot】:<br>
	guns-admin\src\main\java\com\stylefeng\guns\GunsApplication.java\com\stylefeng\guns\GunsApplication<br>
	run as即可

	2. 直接运行jar文件<br>
	2.1 对guns进行打包部署<br>
	2.1.1 找到guns-parents<br>
	2.1.2 运行命令 mvn clean package -Dmaven.test.skip=true
	2.1.3 拷贝jar包至运行目录
		java -jar guns-admin-1.0.0-SNAPSHOT.jar
	
	3. 运行war包
	3.1. 修改guns-admin中的pom文件打包方式
	3.2. 对guns进行打包部署
	3.2.1  找到guns-parents<br>
	3.2.2 运行命令 mvn clean package -Dmaven.test.skip=true
	3.2.3 拷贝war包至web服务器的webapp目录中
		java -jar guns-admin-1.0.0-SNAPSHOT.jar
		
# guns结构组成

## 技术组成
- spring boot
- mybatis-plus
- swagger
- shiro
- spring mvc

 ## 模块组成
 - guns-parent:guns的maven父工程
 - guns-admin:guns的业务子模块
 - guns-rest：guns的restful子模块
		
	
# 展望
1. guns的rest和权限
2. 将业务代码放置在tomcat中
3. tomcat集群优化和搭建
 msm-> memcached-session-manager[分布式session处理]
memcached->最好的缓存管理中间件



