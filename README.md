# toyproject-spring_security_form_Authentication

Email: b635032_@daum.net

본 프로젝트는 스프링 시큐리티의 Form 인증을 통해 인증 및 인가 기능을 제작하기 Thymeleaf 템플릿을 활용해 웹 페이지를 생성한다.

스프링 시큐리티의 Form 인증 방식과 스프링 시큐리티의 인증 아키텍처를 숙달하는데 의의가 있다.

아래는 구현 단계와 인증 

## 1. Domain, Repository, Service

### 1.1 Domain

DB에 저장하기 위한 엔티티 클래스를 생성한다. Lombok 라이브러리, 영속(persistence) 라이브러리를 활용하였다. 

추가적으로 엔티티 생성의 가독성을 높이기 위해 Builder 패턴을 활용했다.

### 1.2 Repository

Spring Data JPA 기술을 활용했다. 스프링 싱글톤 빈으로 등록하기 위해 @Repository 애노테이션을 사용했다.

### 1.3 Service

싱글톤으로 관리하기 위해 스프링의 @Service 애노테이션을 활용했고 Lombok 라이브러리를 통해 Repository의 DI, Ioc를 담당하였다.

