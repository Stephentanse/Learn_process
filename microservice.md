Spring ConfigServer在配置spring.cloud.config.server.git.uri=https://github.com/Stephentanse/microservice.git时候要注意。github上的配置文件的文件名
必须为{application}-{profile}.properties

https://blog.csdn.net/true1cc/article/details/81170079

-----

 1 配置中心　　　　


1、config 默认Git加载
通过spring.cloud.config.server.git.uri指定配置信息存储的git地址，比如：https://github.com/spring-cloud-samples/config-repo
2、加载本地开发环境
### config server native
spring.profiles.active=native
spring.cloud.config.server.native.searchLocations=classpath:/config
3、加载 本地物理环境
spring.profiles.active=native
spring.cloud.config.server.native.searchLocations=file:E:\\Java\\Workspaces\\sts\\doc\\file\\config
 
4、加载svn环境  http://localhost:8888/{application}/{profile}/{label}，比如：http://localhost:8888/dmeo/development/trunk
### config server svn
spring.cloud.config.server.svn.uri=http://localhost:8888/dmeo/development/trunk
spring.cloud.config.server.svn.username=xxx
spring.cloud.config.server.svn.password=xxx
spring.profiles.active=subversion
　特别注意  svn 环境 需要 引入 SVN jar包 
<groupId>org.tmatesoft.svnkit</groupId>
<artifactId>svnkit</artifactId>


----
