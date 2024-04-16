https://zuminternet.github.io/TEAMUP-BOT-START/

#### Dependency
##### build.gradle
```java
compile('org.springframework.boot:spring-boot-starter-web')
```  
=> 내장 Tomcat, RESTful 등 웹서버 구축 기본 의존성 제공  
```java
compile('org.springframework.security.oauth:spring-security-oauth2:2.0.8.RELEASE')
```  
=> Oauth2 Token 사용 편의를 위해 사용  
  
#### Configuration
##### POJO
: Plain Old Java Object :: JAVA로 생성하는 순수한 객체  
##### Properties
변경 가능성, 민감, 정적 설정값을 외부 설정 파일로 관리하는 편.  
```@PropertySource``` 로 기본 제공 ```application.properties``` 외 별도 생성 한 설정값으로 환경 변수 할당.  
