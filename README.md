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

