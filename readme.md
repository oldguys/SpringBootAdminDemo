> spring-boot-admin 一个监控SpringBoot项目状态的应用
> github (server 端）： https://github.com/oldguys/SpringBootAdminDemo
> github (client端) ：https://github.com/oldguys/SpringBootAdminClientDemo


与Eureka相似，引入Maven直接作为注册中心。

modal 1. 服务端使用
1. Maven：
    ~~~
    <dependency>
        <groupId>de.codecentric</groupId>
        <artifactId>spring-boot-admin-starter-server</artifactId>
    </dependency>
    ~~~
2. 使用注解开启服务
    ~~~
    @EnableAdminServer
    @SpringBootApplication
    public class BootAdminDemoApplication {
    
        public static void main(String[] args) {
            SpringApplication.run(BootAdminDemoApplication.class, args);
        }
    
    }
    ~~~

访问地址：http://localhost:8080/

model 2. 客户端使用

1. maven
~~~
    <!-- 引入可以对接admin 注册中心-->
       <dependency>
            <groupId>de.codecentric</groupId>
            <artifactId>spring-boot-admin-starter-client</artifactId>
        </dependency>
     <!-- 引入可以使用监控操作--> 
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-actuator</artifactId>
        </dependency>
~~~
2. 配置文件：
~~~
spring:
  boot:
    admin:
      client:
        url: http://localhost:8080
server:
  port: 0
management:
  endpoints:
    web:
      exposure:
        include: "*"
~~~

到此完成了SpringBootAdmin Server和Client的配置

