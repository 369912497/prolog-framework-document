### 快速使用

使用prolog framework快速开发一个微服务，以一个资源服务为示例

1、引入依赖

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>

  <groupId>com.prolog.framework</groupId>
  <artifactId>plg-cs-authorization</artifactId>
  <version>1.0.0</version>
  <packaging>jar</packaging>

  <name>plg-cs-authorization</name>
  <url>http://maven.apache.org</url>

  <properties>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    <prolog.framework.version>1.0.0</prolog.framework.version>
  </properties>

	<parent>
        <groupId>com.prolog.framework</groupId>
  		<artifactId>plg-fx-springcloud-parent</artifactId>
  		<version>1.0.0</version>
    </parent>
    

  <dependencies>
    <dependency>
      <groupId>junit</groupId>
      <artifactId>junit</artifactId>
      <scope>test</scope>
    </dependency>
    
    <dependency>
    	<groupId>com.prolog.framework</groupId>
    	<artifactId>plg-fx-starter-dao</artifactId>
    	<version>${prolog.framework.version}</version>
    </dependency>
    
     <dependency>
    	<groupId>com.prolog.framework</groupId>
    	<artifactId>plg-fx-starter-web</artifactId>
    	<version>${prolog.framework.version}</version>
    </dependency>
    
    <dependency>
    	<groupId>com.prolog.framework</groupId>
    	<artifactId>plg-fx-starter-apidoc</artifactId>
    	<version>${prolog.framework.version}</version>
    </dependency>
    
	
	<dependency>
    	<groupId>com.prolog.framework</groupId>
    	<artifactId>plg-fx-common</artifactId>
    	<version>${prolog.framework.version}</version>
    </dependency>
    
    <dependency>
    	<groupId>com.prolog.framework</groupId>
    	<artifactId>plg-fx-authorization-core</artifactId>
    	<version>${prolog.framework.version}</version>
    </dependency>
    
    <dependency>
    	<groupId>com.prolog.framework</groupId>
    	<artifactId>plg-cs-authorization-facade</artifactId>
    	<version>${prolog.framework.version}</version>
    </dependency>
    
	 <dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-test</artifactId>
			<exclusions>
		        <exclusion>
		            <groupId>org.springframework.boot</groupId>
		            <artifactId>spring-boot-starter-logging</artifactId>
		        </exclusion>
		    </exclusions>
			<scope>test</scope>
		</dependency>
		
    <dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-devtools</artifactId>
			<optional>true</optional>
		</dependency>
		
	<dependency>
    	<groupId>com.prolog.framework</groupId>
		<artifactId>plg-fx-microservice</artifactId>
		<version>${prolog.framework.version}</version>
    </dependency>
    
  </dependencies>
  
    
</project>

```



