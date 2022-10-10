# knife4j项目说明

knife4j的前身是`swagger-bootstrap-ui`，为了契合微服务的架构发展,由于原来`swagger-bootstrap-ui`采用的是后端Java代码+前端Ui混合打包的方式,在微服务架构下显的很臃肿,因此项目正式更名为`knife4j`

更名后主要专注的方面

- 前后端Java代码以及前端Ui模块进行分离,在微服务架构下使用更加灵活
- 提供专注于Swagger的增强解决方案,不同于只是改善增强前端Ui部分

目前`knife4j`的项目结构：

| 模块名称                                    | 说明                                                                                     |
|-----------------------------------------|----------------------------------------------------------------------------------------|
| knife4j-aggregation-spring-boot-starter | 基于Servlet体系下的聚合中间件                                                                     |
| knife4j-core                            | 核心类,包含一些工具包、增强注解等                                                                      |
| knife4j-dependencies                    | knife4j提供的dependencies工程，引入该工程后，knife4j\springfox\swagger\springdoc-openapi等版本号不用在独自声明 |
| knife4j-openapi2-ui                     | 增强Ui文档,该包是一个webjar,只包含前端代码，支持openapi2                                                  |
| knife4j-openapi3-ui                     | 增强Ui文档,该包是一个webjar,只包含前端代码，支持openapi3                                                  |
| knife4j-openapi2-spring-boot-starter    | 基于OpenAPI2规范，在Spring Boot的单体架构下可以直接引用此starter,该模块包含了Ui部分,底层依赖springfox-swagger2.10.5项目                               |
| knife4j-openapi3-spring-boot-starter    | 基于OpenAPI3规范，在Spring Boot的单体架构下可以直接引用此starter,该模块包含了Ui部分,底层基于springdoc-openapi项目                              |


## 业务场景

### 不使用增强功能,纯粹换一个swagger的前端皮肤

不使用增强功能,纯粹换一个swagger的前端皮肤，这种情况是最简单的,你项目结构下无需变更

可以直接引用swagger-bootstrap-ui的最后一个版本1.9.6或者使用knife4j-spring-ui

老版本引用

```xml
<dependency>
    <groupId>io.springboot</groupId>
    <artifactId>swagger-bootstrap-ui</artifactId>
    <version>1.9.6</version>
</dependency>
```

新版本引用

```xml
<dependency>
    <groupId>io.springboot</groupId>
    <artifactId>knife4j-openapi2-ui</artifactId>
    <version>${lastVersion}</version>
</dependency>
```

### Spring Boot项目单体架构使用增强功能

在Spring Boot单体架构下,knife4j提供了starter供开发者快速使用

```xml
<dependency>
    <groupId>io.springboot</groupId>
    <artifactId>knife4j-openapi2-spring-boot-starter</artifactId>
    <version>${knife4j.version}</version>
</dependency>
```

该包会引用所有的knife4j提供的资源，包括前端Ui的jar包
 
## 另外说明

不管是knife4j还是swagger-bootstrap-ui

对外提供的地址依然是doc.html

访问：http://ip:port/doc.html

即可查看文档

**这是永远不会改变的**
