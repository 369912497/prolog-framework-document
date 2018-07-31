### 快速使用

使用prolog framework快速开发一个微服务，以一个资源服务为示例

1、引入依赖

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>

  <groupId>com.prolog.framework</groupId>
  <artifactId>plg-cs-resource</artifactId>
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

    <!--引入数据持久层框架-->
    <dependency>
        <groupId>com.prolog.framework</groupId>
        <artifactId>plg-fx-starter-dao</artifactId>
        <version>${prolog.framework.version}</version>
    </dependency>

    <!--引入web层框架-->
     <dependency>
        <groupId>com.prolog.framework</groupId>
        <artifactId>plg-fx-starter-web</artifactId>
        <version>${prolog.framework.version}</version>
    </dependency>

    <!--引入api自动生成框架-->
    <dependency>
        <groupId>com.prolog.framework</groupId>
        <artifactId>plg-fx-starter-apidoc</artifactId>
        <version>${prolog.framework.version}</version>
    </dependency>

    <!--引入通用功能模块-->
    <dependency>
        <groupId>com.prolog.framework</groupId>
        <artifactId>plg-fx-common</artifactId>
        <version>${prolog.framework.version}</version>
    </dependency>

    <!--引入权限框架框架-->
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

    <!--微服务框架-->
    <dependency>
        <groupId>com.prolog.framework</groupId>
        <artifactId>plg-fx-microservice</artifactId>
        <version>${prolog.framework.version}</version>
    </dependency>

    <!--springboot测试依赖-->
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

    <!--springboot开发工具，实现热部署-->
    <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-devtools</artifactId>
            <optional>true</optional>
        </dependency>



  </dependencies>


</project>
```

2、定义数据模型层

```java
package com.prolog.framework.cs.authorization.model;

import com.prolog.framework.core.annotation.AutoKey;
import com.prolog.framework.core.annotation.Id;
import com.prolog.framework.core.annotation.Table;

import io.swagger.annotations.ApiModelProperty;

@Table(value="plg_fx_resource",columnPrefix="p_")
public class Resource {
	
	@Id
	@AutoKey(type=AutoKey.TYPE_UUID)
	@ApiModelProperty(value = "id")
	private String id;
	@ApiModelProperty(value = "服务名")
	private String serviceName;
	
	@ApiModelProperty(value = "权限编号")
	private String authNumber;
	
	@ApiModelProperty(value = "方法")
	private String method;
	
	@ApiModelProperty(value = "url资源")
	private String source;
	
	@ApiModelProperty(value = "备注")
	private String notes;
	
	public String getId() {
		return id;
	}
	public void setId(String id) {
		this.id = id;
	}
	public String getServiceName() {
		return serviceName;
	}
	public void setServiceName(String serviceName) {
		this.serviceName = serviceName;
	}
	public String getAuthNumber() {
		return authNumber;
	}
	public void setAuthNumber(String authNumber) {
		this.authNumber = authNumber;
	}
	public String getMethod() {
		return method;
	}
	public void setMethod(String method) {
		this.method = method;
	}
	public String getSource() {
		return source;
	}
	public void setSource(String source) {
		this.source = source;
	}
	public String getNotes() {
		return notes;
	}
	public void setNotes(String notes) {
		this.notes = notes;
	}
	
	
	
}

```



