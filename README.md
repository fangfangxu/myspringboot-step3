# myspringboot-step3

1、SSM开发流程：

    配置环境（jdk、tomcat）--->创建工程--->构建目录结构
                                    --->组件依赖管理（pom）
                                    --->配置web容器（web.xml）
                                    --->设置组件参数（applicationContext.xml）
                                    --->业务开发
                                   --->测试与构建
                                   --->手动部署（打war）
                                   --->运维与监控
                                   
2、SpringBoot开发：

     配置环境（只需jdk即可，无需tomcat）--->Spring Initializr组件（
                            一键生成SpringBoot应用）
                            --->配置参数（可选）
                            --->业务开发
                            --->自动构建
                            --->自动部署
                            --->运维与监控



   使用Springboot后，组件依赖，容器配置，目录结构等基础工作springboot都会自动帮我们完成。

3、SpringBoot核心特性：

        （1）极低的学习成本
        （2）可独立运行的Spring项目（传统的web项目，需要将项目编译为war包，在服务器上安装tomcat后，将war包上传至服务器，启动tomcat才能完成整个项目的部署，单台服务器上当然没问题，若是几千台服务器，那么这样部署很麻烦），SpringBoot不再需要手动安装tomcat，在项目构建的时候，SpringBoot会自动将依赖的tomcat组件内嵌到当前的工程中，随着SpringBoot的启动，Tomcat一并提供服务。在Springboot编译时不再提供war还是jar，可以将jar批量上传服务器，通过服务器端脚本批量启动，无论是一台还是千台服务器都可以通过一个命令完成上线部署
        （3）“约定优于配置”极大的提高了开发效率
        （4）极简的组件依赖，自动发现与自动装配
        （5）提供运行时的应用监控
        （6）与分布式架构和云计算的天然集成

4、利用maven创建工程

  
     一、pom：
        
        <?xml version="1.0" encoding="UTF-8"?>
        <project xmlns="http://maven.apache.org/POM/4.0.0"
                 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
                 xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
            <modelVersion>4.0.0</modelVersion>     
       <groupId>com.xuff</groupId>
       <artifactId>myspringboot</artifactId>
       <version>1.0-SNAPSHOT</version>
       <parent>
           <groupId>org.springframework.boot</groupId>
           <artifactId>spring-boot-starter-parent</artifactId>
           <version>2.0.1.RELEASE</version>
       </parent>
   
       <dependencies>
           <dependency>
               <groupId>org.springframework.boot</groupId>
               <artifactId>spring-boot-starter-web</artifactId>
           </dependency>
       </dependencies>
   
       <build>
           <plugins>
               <plugin>
                   <groupId>org.springframework.boot</groupId>
                   <artifactId>spring-boot-maven-plugin</artifactId>
               </plugin>
           </plugins>   
       </build>   
     </project>
     
    
    二、SpringBoot应用入口类：
  
        package com.xuff.myspringboot;
        import org.springframework.boot.SpringApplication;
        import org.springframework.boot.autoconfigure.SpringBootApplication;
        //SpringBoot应用的入口类
        @SpringBootApplication
        public class MySpringBootApplication {
            public static void main(String[] args){
                //启动SpringBoot应用
                SpringApplication.run(MySpringBootApplication.class);
            }
        }
        
5、Spring Boot入口类


    （1）入口类命名通常以*Application结尾
    （2）入口类上增加@SpringBootApplication注解：注明当前类是启动SpringBoot的入口
    （3）利用SpringApplication.run()方法启动应用

6、SpringBoot启动流程：
      
      --->加载配置文件（application.properties）
      --->自动装配（spring-boot-starter-web         增加web支持
                              spring-boot-starter-data-jpa  对JPA支持，集成Hibernate 
                              spring-boot-starter-logging   增加logback日志的支持
                              spring-boot-starter-test）      集成JUnit单元测试框架
      --->加载组件@Repository @Service @Controller @Component @Entity
      --->应用初始化（启动Tomcat、初始化日志组件、数据源、各种连接池、处理池）

7、SpringBoot常用配置

    server.port      端口号（8080）
    server.servlet.context-path     应用上下文(/)
    logging.file      日志文件输出路径
    logging.level.root    最低日志输出级别（info）
                           #设置日志的级别(级别依次升高：debug（调试）-->info
                           （一般输出信息，默认）-->warn（警告）-->error（异常信息）
                           -->fatal（灾难级别，比如服务器宕机）)
    debug              开启/关闭调试模式（false）
    spring.datasource.* 与数据库相关设置        
        #连接数据源
        spring.datasource.driver-class-name=com.mysql.jdbc.Driver
        spring.datasource.url=jdbc:mysql://localhost:3306/oa
        spring.datasource.username=root
        spring.datasource.password=xiaohui134757898