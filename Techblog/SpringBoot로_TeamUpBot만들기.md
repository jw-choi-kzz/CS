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
Configuration 파일에 ```@Configuration``` ```@PropertySource(ignoreResourceNotFound = true,value = {"classpath:~~","file:~~"})```  
환경변수 통합 관리를 위한 ```@Component``` 생성: ```@Value("${~~}")```  
  
Spring에서 RESTful 서비스 사용 편의를 위해 제공하는 RestTemplate 객체.  API 통신을 위한 Bean 생성.  
##### ThreadPoolTaskExecutor
ThreadPool : 작업처리에 사용되는 Thread 개수 제한 후, 작업 Queue에 들어오는 작업 Thread가 하나씩 맡아 처리. 이벤트 병렬 처리용.  
  
#### Oauth2 인증
##### Oauth2Template
auth 통신하는 Template 구현체  
```
* accessToken이 null이면 (password로 새로 발급)/아니면(refresh) 하는 방식으로 accessToken 발급하는 메서드
*(accessToken이 null일때) TokenUrl에서 받은 response의 body에서 accessToken을 받아오는 메서드
* header에 client_id, client_secret, username, password, refresh_token 담는 메서드
```
##### TokenManager
토근 받아오고, 없으면 생성, 만료 시 갱신한 토큰 전달  
  
#### BaseTemplate
RESTful 서비스 제공 상위 구현체  
#### RealTime Message Event
BaseTemplate를 상속하여 event에 대한 API 통신만 하는 구현체  
실시간 메세지 처리를 위한 Queue 사용, ```@Schedule``` 사용하여 메서드 실행  
