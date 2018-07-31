```
快速使用
```

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
package com.prolog.framework.cs.resource.model;

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

3、dao层

```java
package com.prolog.framework.cs.resource.dao;

import com.prolog.framework.cs.resource.model.Resource;
import com.prolog.framework.dao.mapper.BaseMapper;

public interface ResourceMapper extends BaseMapper<Resource> {

}
```

4、服务接口层

```java
package com.prolog.framework.cs.resource.service;

import java.util.List;

import com.prolog.framework.core.pojo.Page;
import com.prolog.framework.cs.resource.model.Resource;

public interface IResourceService {
    void add(Resource resource) throws Exception;
    void delete(String id);
    void update(Resource resource) throws Exception;
    Page<Resource> getLike(String serviceName,String authNumber,String resource,int pageNo,int pageSize);
    List<Resource> getByServiceName(String serviceName);
    List<Resource> getAll();
}
```

5、服务实现层

```java
package com.prolog.framework.cs.resource.service.impl;

import java.util.List;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

import com.github.pagehelper.PageHelper;
import com.prolog.framework.core.exception.ParameterException;
import com.prolog.framework.core.exception.RepetitionException;
import com.prolog.framework.core.pojo.Page;
import com.prolog.framework.core.restriction.Criteria;
import com.prolog.framework.core.restriction.Order;
import com.prolog.framework.core.restriction.Restriction;
import com.prolog.framework.core.restriction.Restrictions;
import com.prolog.framework.cs.resource.dao.ResourceMapper;
import com.prolog.framework.cs.resource.model.Resource;
import com.prolog.framework.cs.resource.service.IResourceService;
import com.prolog.framework.dao.util.PageUtils;
import com.prolog.framework.utils.MapUtils;
import com.prolog.framework.utils.StringUtils;

@Service
public class RecourceServiceImpl implements IResourceService{

    @Autowired
    private ResourceMapper resourceMapper;

    @Override
    public void add(Resource resource) throws Exception {

        if(resource==null){
            throw new ParameterException("参数为null");
        }
        if(StringUtils.isEmpty(resource.getServiceName()))
            throw new ParameterException("service name is null");

        if(StringUtils.isEmpty(resource.getAuthNumber()))
            throw new ParameterException("auth number is null");

        if(StringUtils.isEmpty(resource.getSource()))
            throw new ParameterException("souce is null");

        if(StringUtils.isEmpty(resource.getMethod()))
            throw new ParameterException("method is null");

        //去重
        long count = resourceMapper.findCountByMap(MapUtils.put("serviceName", resource.getServiceName()).put("authNumber", resource.getAuthNumber()).getMap(), Resource.class);
        if(count>0){
            throw new RepetitionException("权限编号已存在");
        }
        resourceMapper.save(resource);
    }

    @Override
    public void delete(String id) {
        resourceMapper.deleteById(id, Resource.class);
    }

    @Override
    public void update(Resource resource) throws Exception {
        if(resource==null || StringUtils.isEmpty(resource.getId())){
            throw new ParameterException("id is null");
        }
        if(StringUtils.isEmpty(resource.getServiceName()))
            throw new ParameterException("service name is null");

        if(StringUtils.isEmpty(resource.getAuthNumber()))
            throw new ParameterException("auth number is null");

        if(StringUtils.isEmpty(resource.getSource()))
            throw new ParameterException("souce is null");

        if(StringUtils.isEmpty(resource.getMethod()))
            throw new ParameterException("method is null");

        resourceMapper.update(resource);
    }

    @Override
    public Page<Resource> getLike(String serviceName, String authNumber, String resource, int pageNo, int pageSize) {
        PageHelper.startPage(pageNo, pageSize);
        Criteria c = Criteria.forClass(Resource.class);
        Restriction r1=null;
        if(!StringUtils.isEmpty(serviceName)){
            r1 = Restrictions.like("serviceName","%"+serviceName+"%");
        }
        if(!StringUtils.isEmpty(authNumber)){
            r1 = r1==null?Restrictions.like("authNumber","%"+authNumber+"%"):Restrictions.or(r1, Restrictions.like("authNumber","%"+authNumber+"%"));
        }

        if(!StringUtils.isEmpty(resource)){
            r1 = r1==null?Restrictions.like("resource","%"+resource+"%"):Restrictions.or(r1, Restrictions.like("resource","%"+resource+"%"));
        }
        c.setRestriction(r1);
        c.setOrder(Order.asc("authNumber"));
        Page<Resource> page = PageUtils.getPage(resourceMapper.findByCriteria(c));

        return page;
    }

    @Override
    public List<Resource> getByServiceName(String serviceName) {
        return resourceMapper.findByMap(MapUtils.put("serviceName", serviceName).getMap(), Resource.class);
    }

    @Override
    public List<Resource> getAll() {
        // TODO Auto-generated method stub
        return resourceMapper.findByMap(null, Resource.class);
    }

}
```

6、资源服务/权限拦截实现类，实现IAuthorityService接口

```java
package com.prolog.framework.cs.resource.service.impl;

import java.util.ArrayList;
import java.util.List;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.stereotype.Service;

import com.prolog.framework.authority.core.service.IAuthorityService;
import com.prolog.framework.authority.core.vo.AuthorityVO;
import com.prolog.framework.cs.resource.model.Resource;
import com.prolog.framework.cs.resource.service.IResourceService;

@Service
public class MyAuthorityServiceImpl implements IAuthorityService{


    @Value("${spring.application.name:}")
    private String applicationName;
    @Autowired
    private IResourceService resourceService;

    @Override
    public List<AuthorityVO> loadAuthorities() {
        List<AuthorityVO> list = new ArrayList<AuthorityVO>();
        List<Resource> resources = resourceService.getByServiceName(applicationName);
        for(Resource res:resources){
            list.add(new AuthorityVO(String.format("%s:%s", applicationName,res.getAuthNumber()),res.getMethod(),res.getSource()));
        }
        return list;
    }

    @Override
    public String[] loadPermitResource() {
        return new String[]{"/*.html","/**/*.css","/**/*.js","/**/*.ico","/**/*.png","/**/*.gif","/**/*.jpg","/**/font/*","/v2/api-docs","/oauth/**"};
    }

}
```

7、启动类

```java
package com.prolog.framework.cs.resource;

import org.mybatis.spring.annotation.MapperScan;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.transaction.annotation.EnableTransactionManagement;

import com.prolog.framework.authority.core.annotation.EnablePrologSecurityServer;
import com.prolog.framework.microservice.annotation.EnablePrologService;

@SpringBootApplication()
@EnablePrologService
@EnablePrologSecurityServer(resourceConfig=true,webConfig=false)
@EnableTransactionManagement
@MapperScan("com.prolog.framework.cs.resource.dao")
public class ResourceApplication {

    public static void main( String[] args )
    {
        SpringApplication.run(ResourceApplication .class, args);
    }

}
```

8、application.yml配置

```yaml
#eureka client配置
eureka:
  client:
    serviceUrl:
      defaultZone: http://127.0.0.1:8761/eureka/
  instance: 
    # 注册时使用ip而不是主机名
    preferIpAddress: true
    instanceId: ${server.ipAddress}:${server.port}
    health-check-url-path: /actuator/health
    # 状态地址为api地址
    statusPageUrlPath: /${server.servlet.contextpath}/apidoc.html


server:
  ipAddress: 127.0.0.1
  port: 8800  
  servlet: 
    contextpath: 

management:
  endpoints: 
    web: 
      exposure: 
        include: "*"

spring:
  application:
    name: service-authorization
  datasource: 
    url: jdbc:mysql://localhost:3306/springboottest?useSSL=false&serverTimezone=CTT&useUnicode=true&characterEncoding=utf-8&allowMultiQueries=true
    username: root
    password: 123
    driverClassName: com.mysql.jdbc.Driver
  redis:
    host: 127.0.0.1
    port: 6379
    password: prolog0212 
  zipkin: 
    base-url: http://localhost:9411
  sleuth: 
    enable: true
    sampler: 
      probability: 1.0
  devtools: 
    restart: 
      enabled: true

prolog: 
  resourceId: ${spring.application.name}
  security: 
    oauth: 
      accessTokenExpires: 720 #分钟
      refreshTokenExpires: 10080 #分钟
    manager: 
      username: root
      password: root
  apidoc: #api文档配置文件
    title: 客户端权限服务
    basePackage: com.prolog
    description: 客户端权限服务
    version: 1.0
  dao: 
    dialect: mysql
    pagehelper: #pagehelper分页插件配置
      helperDialect: ${prolog.dao.dialect}
      reasonable: true
      supportMethodsArguments: true
      pageSizeZero: false
      params: count=countSql
    #公共配置与profiles选择无关 mapperLocations指的路径是src/main/resources
    mybatis:
      typeAliasesPackage: com.prolog.cs.authorization.client.model
      mapperLocations: classpath:mappers/*.xml
```

9、jdbc配置

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/springboottest?useSSL=false&serverTimezone=CTT&useUnicode=true&characterEncoding=utf-8&allowMultiQueries=true
#url: jdbc:oracle:thin:@//192.168.0.84:1521/cloudpltfm
spring.datasource.username=root
spring.datasource.password=123
spring.datasource.driverClassName=com.mysql.jdbc.Driver
#driver-class-name: oracle.jdbc.OracleDriver
# 使用druid数据源
#初始化大小
spring.datasource.initialSize=0
#最小空閒
spring.datasource.minIdle=5
#最大連接數
spring.datasource.maxActive=50
#最大等待時間
spring.datasource.maxWait=60000
#最小生存時間
spring.datasource.minEvictableIdleTimeMillis=25200000
```



