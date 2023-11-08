# Missing spring-core from compile tree

The minimal example to reproduce an issue, when `spring-core` is not represented for `-Dscope=compile`.

Run `./mvnw dependency:tree -Dscope=compile -DoutputFile=result.log`.

result.log will look like:

```
com.example:bom-tree:jar:0.0.1-SNAPSHOT
\- org.springframework.boot:spring-boot-starter-oauth2-resource-server:jar:3.1.5:compile
   +- org.springframework.boot:spring-boot-starter:jar:3.1.5:compile
   |  +- org.springframework.boot:spring-boot:jar:3.1.5:compile
   |  +- org.springframework.boot:spring-boot-autoconfigure:jar:3.1.5:compile
   |  +- org.springframework.boot:spring-boot-starter-logging:jar:3.1.5:compile
   |  |  +- ch.qos.logback:logback-classic:jar:1.4.11:compile
   |  |  |  \- ch.qos.logback:logback-core:jar:1.4.11:compile
   |  |  +- org.apache.logging.log4j:log4j-to-slf4j:jar:2.20.0:compile
   |  |  |  \- org.apache.logging.log4j:log4j-api:jar:2.20.0:compile
   |  |  \- org.slf4j:jul-to-slf4j:jar:2.0.9:compile
   |  +- jakarta.annotation:jakarta.annotation-api:jar:2.1.1:compile
   |  \- org.yaml:snakeyaml:jar:1.33:compile
   +- org.springframework.security:spring-security-config:jar:6.1.5:compile
   |  +- org.springframework:spring-aop:jar:6.0.13:compile
   |  +- org.springframework:spring-beans:jar:6.0.13:compile
   |  \- org.springframework:spring-context:jar:6.0.13:compile
   +- org.springframework.security:spring-security-core:jar:6.1.5:compile
   |  +- org.springframework.security:spring-security-crypto:jar:6.1.5:compile
   |  +- org.springframework:spring-expression:jar:6.0.13:compile
   |  \- io.micrometer:micrometer-observation:jar:1.11.5:compile
   |     \- io.micrometer:micrometer-commons:jar:1.11.5:compile
   +- org.springframework.security:spring-security-oauth2-resource-server:jar:6.1.5:compile
   |  +- org.springframework.security:spring-security-oauth2-core:jar:6.1.5:compile
   |  |  \- org.springframework:spring-web:jar:6.0.13:compile
   |  \- org.springframework.security:spring-security-web:jar:6.1.5:compile
   \- org.springframework.security:spring-security-oauth2-jose:jar:6.1.5:compile
      \- com.nimbusds:nimbus-jose-jwt:jar:9.24.4:compile
         \- com.github.stephenc.jcip:jcip-annotations:jar:1.0-1:compile
```

No `spring-core`. Although if we run `./mvnw package`, `spring-core.jar` will be present in `BOOT-INF/lib`.
