### plg-fx-springboot-parent

本模块是为了统一开发中对springboot依赖版本控制，在做springboot项目时可直接继承此模块，其配置如下：

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>

  <groupId>com.prolog.framework</groupId>
  <artifactId>plg-fx-springboot-parent</artifactId>
  <version>1.0.0</version>
  <packaging>pom</packaging>

  <name>plg-fx-springboot-parent</name>
  <url>http://www.prolog.com</url>

  <properties>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
  </properties>

	<parent>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-parent</artifactId>
		<version>2.0.0.RELEASE</version>
		<!-- 始终从仓库中获取，不从本地路径获取 -->
		<relativePath />
	</parent>
	
  <dependencies>
    
    	<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter</artifactId>
			<exclusions>
		        <exclusion>
		            <groupId>org.springframework.boot</groupId>
		            <artifactId>spring-boot-starter-logging</artifactId>
		        </exclusion>
		    </exclusions>
		</dependency>
		
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-aop</artifactId>
		</dependency>
		
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-tx</artifactId>
		</dependency>
		
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-web</artifactId>
			<exclusions>
		        <exclusion>
		            <groupId>org.springframework.boot</groupId>
		            <artifactId>spring-boot-starter-logging</artifactId>
		        </exclusion>
		    </exclusions>
		</dependency>
		
		<dependency>
		    <groupId>org.springframework.boot</groupId>
		    <artifactId>spring-boot-starter-log4j2</artifactId>
		</dependency>
    
  </dependencies>
  
  <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
            
            <plugin>
				<artifactId>maven-source-plugin</artifactId>
				<configuration>
					<attach>true</attach>
				</configuration>
				<executions>
					<execution>
						<phase>compile</phase>
						<goals>
							<goal>jar</goal>
						</goals>
					</execution>
				</executions>
			</plugin>
			
        </plugins>
    </build>
    
    
</project>

```



