# toyproject-spring_security_form_Authentication

Email: b635032_@daum.net

본 프로젝트는 스프링 시큐리티의 Form 인증을 통해 인증 및 인가 기능을 제작하기 Thymeleaf 템플릿을 활용해 웹 페이지를 생성한다.

스프링 시큐리티의 Form 인증 방식과 스프링 시큐리티의 인증 아키텍처를 숙달하는데 의의가 있다.

아래에서는 구현 단계와 아키텍처를 설명하도록 한다.

## 1. Domain, Repository, Service

### 1.1 Domain

DB에 저장하기 위한 엔티티 클래스를 생성한다. Lombok 라이브러리, 영속(persistence) 라이브러리를 활용하였다. 

추가적으로 엔티티 생성의 가독성을 높이기 위해 Builder 패턴을 활용했다.

### 1.2 Repository

Spring Data JPA 기술을 활용했다. 스프링 싱글톤 빈으로 등록하기 위해 @Repository 애노테이션을 사용했다.

### 1.3 Service

싱글톤으로 관리하기 위해 스프링의 @Service 애노테이션을 활용했고 Lombok 라이브러리를 통해 Repository의 DI, Ioc를 담당하였다.

## 2. Form 인증 아키텍처

...

## 3. UserDetailsService 인터페이스 구현

UserDetailsService 인터페이스 구현하여 CustomUserDetailsService 클래스를 생성한다. CustomUserDetailsService는 Repository를 필드로 Dependency Injection(DI)한다.

UserDetailsService의 loadUserByUsername(Authentication authentication) 메소드 구현이 핵심이다.

loadUserByUsername 메소드를 통해 Authentication 객체의 ID와 일치하는 회원이 Repository에 존재하는지 검색한다.

만약 존재한다면 AccountContext(account, roles) 객체를 생성한 후 반환한다.


## 4. AuthenticationProvider 인터페이스 구현

AuthenticationManager(ProviderManager)에서 사용하기 위한 AuthenticationProvider 인터페이스를 구현한다.

Authentication 객체와 UserDetailsService의 loadUserByUsername을 통해 가져온 Account 객체의 ID와 Password를 비교한다.

비교가 완료되면 ID, Password, 그리고 권한정보를 AuthenticationToken 객체에 추가하며 반환한다. 

## 5. WebAuthenticationDetails, AuthenticationDetailsSource 구현

AuthenticationProvider에서 ID와 Password 뿐만 아니라 추가정보를 검증할 필요성이 존재할 수 있다.

이때 추가정보를 담은 객체가 WebAuthenticationDetails이다. 이는 인터페이스이므로 구현이 필요하다.

AuthenticationDetailsSource는 WebAuthenticationDetails를 생성하기 위한 객체이다. 마찬가지로 인터페이스이므로 구현이 필요하다.

