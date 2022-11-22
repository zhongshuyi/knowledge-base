# NacosDiscovery--服务治理

在需要服务治理的模块添加依赖

```xml
<!--nacos服务发现客户端-->
<dependency>
	<groupId>com.alibaba.cloud</groupId>
	<artifactId>spring-cloud-starter-alibaba-nacos-discovery</artifactId>
</dependency>
```

在application.yml中添加nacos服务的地址

```yaml
spring:  
  cloud:  
    nacos:  
      discovery:  
        server-addr: 127.0.0.1:8848
```


在启动类使用 `@EnableDiscoveryClient` 注解

```java
@SpringBootApplication
@EnableDiscoveryClient
public class LingGatewayApplication {
    public static void main(String[] args) {
        SpringApplication.run(LingGatewayApplication.class, args);
    }
}
```

