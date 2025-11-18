

---
title: Postgresql, JPA  연결하기
date: 2022-10-21
type:  blog
author: harris baek
email: baekjh09@naver.com
---
tags: #spring, #jpa, #postgresql

## PostgreSQL 

### application.properties 연결하기

https://ttl-blog.tistory.com/267?category=910686

```
spring.output.ansi.enabled=always  
  
# postgres db setting  
spring.datasource.driverClassName=org.postgresql.Driver  
spring.datasource.url=jdbc:postgresql://localhost:5432/testdb  
spring.datasource.username=prop  
spring.datasource.password=5424  
spring.datasource.show-sql=true  
  
# hibernate setting  
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.PostgreSQLDialect  
spring.jpa.properties.hibernate.use_sql_comments=true  
spring.jpa.properties.hibernate.format_sql=true  
spring.jpa.properties.hibernate.show_sql=true  
spring.jpa.hibernate.ddl-auto=create  
spring.jpa.generate-ddl=true  
logging.level.org.hibernate.SQL=DEBUG  
logging.level.org.hibernate.type.descriptor.sql.BasicBinder=TRACE
```


### Kotlin으로 NoArg 자동생성 플러그인

```kotlin
  
plugins { 
	...
   kotlin("plugin.jpa") version "1.6.10"  
}
```


### Kotlin으로 Allopen 설정하기
JPA는 프록시 기반으로 Lazy 로딩을 하는데, Proxy는 상속 기반이므로 final이 붙은 클래스를 open 해줘야 한다. 그래서 JPA를 사용하는 경우 다음과 같은 설정을 추가한다.
```kotlin
allOpen {
    annotation("javax.persistence.Entity")
    annotation("javax.persistence.MappedSuperclass")
    annotation("javax.persistence.Embeddable")
}
```

