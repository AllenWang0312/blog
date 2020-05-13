
# Spring学习笔记
[教程](https://www.cnblogs.com/wmyskxz/p/9010832.html)

### 关键词
- 注解
  * @Component
  
  * @Configuration //当前类是一个配置类
    * @Bean 可作用于方法 相当于 配置了 方法名: 返回体

  * @Value

  * @ConfigurationProperties(prefix = "person")//读取默认配置文件 application.prooperties
  * @PropertySource(value ="classpath:person.properties" ) //读取指定默认文件
  * @ImportResource(locations = {"classpath:beans.xml"}) //读取xml文件中的配置

  * @Validated
    * @Email  
## 笔记

配置切换 
1. 多profile
2. yml 多文档块
3. --spring.profiles.active=dev //[虚拟机配置]-Dspring.profiles.active=dev
4. 路径优先级    /config
               /
               /resources/config
               /resources
5. spring.config.location 设置配置文件位置

## bootstrap
## webjars
## 模板引擎
jsp velocity freemarket thymeleaf