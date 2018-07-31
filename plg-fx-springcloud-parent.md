### plg-fx-springcloud-parent

本模块是一个maven pom项目，集成了plg-fx-springboot项目，主要做了四个方面的配置

1. springboot配置，配置了spring-boot-starter、spring-boot-starter-aop、spring-boot-starter-web
2. spring事务模块配置，spring-tx
3. 日志配置，spring-boot-starter-log4j2
4. spingboot编译插件配置及源码打包插件配置

具体配置如下：

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>

  <artifactId>plg-fx-springcloud-parent</artifactId>
  <packaging>pom</packaging>

  <name>plg-fx-springcloud-parent</name>
  <url>http://maven.apache.org</url>

	<properties>
		<project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
		<spring.cloud.version>1.4.4.RELEASE</spring.cloud.version>
	</properties>
	
	<parent>
        <groupId>com.prolog.framework</groupId>
  		<artifactId>plg-fx-springboot-parent</artifactId>
  		<version>1.0.0</version>
    </parent>
    
  <dependencies>
  </dependencies>
  
  <dependencyManagement>
	<dependencies>
		<dependency>
			 <groupId>org.springframework.cloud</groupId>
			<artifactId>spring-cloud-starter-parent</artifactId>
			<version>Finchley.M8</version>
			<type>pom</type>
			<scope>import</scope>
		</dependency>
	</dependencies>
</dependencyManagement>
	
    <repositories>
	    <repository>
	        <id>spring-milestones</id>
	        <name>Spring Milestones</name>
	        <url>https://repo.spring.io/libs-milestone</url>
	        <snapshots>
	            <enabled>false</enabled>
	        </snapshots>
	    </repository>
	</repositories>
	
</project>

```



