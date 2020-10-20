# SpringBoot 笔记

## 什么是SpringBoot

spring提供了aop和ioc，提供了开发的边界，可是有很多的配置文件，还得依赖很多的pom文件，需要解决依赖版本冲突问题。SpringBoot解决了这些问题，提出了“自动配置”,”起步依赖“二个功能。另外，SpringBoot发布，部署，运维都更方便了。SpringBoot提供了jar包运行，可以部署到docker容器，云平台发布，提供了Spring Boot Actuator模块，提供了应用一些指标的监控。


## SpringBoot有哪些优点

按照”约定优于配置“的思想，起步依赖功能方便了开发，集成其他功能组件。

利用Javaconfig做的自动配置，代替了xml，简化了开发者写xml的工作。

提供的jar的运行方式，统一了项目部署的方式。

集成了tomcat,Jetty等web容器，方便启动项目。

SpringBoot  Actuator 提供了指标，方便了运维监控。



## SpringBoot核心注解有哪些？主要是哪些注解组成？

@SpringBootApplication 由 @Configuration、@EnableAutoConfiguration、@ComponentScan组成。

@Configuration 注解的类是一个Javaconfig类，实现了非xml的ioc容器类。

@EnableAutoConfiguration是自动配置的核心类，配合@import导入配置类，借助springfactoryLoader 扫描META-INFO/spring.factories里面配置的组件类和listener，再注入到spring的ApplicationContext的容器内。

