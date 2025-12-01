#  목차
1. [Spring Legacy Interview Summary](#1-spring-legacy-interview-summary)
2. [Java OOP Basic Q&A](#2-java-oop-basic-qa)
3. [Java & Spring Advanced Q&A](#3-java--spring-advanced-qa)
4. [Spring Bean Scope](#4-spring-bean-scope)
5. [JVM & GC Explained](#5-jvm--gc-explained)
6. [자바 접근 제어자 상세 설명](#6-자바-접근-제어자-상세-설명)
7. [개발 환경 / 기술 스택](#7-개발-환경--기술-스택)

---

# 1️. Spring Legacy Interview Summary

## ✔ DispatcherServlet 동작 순서
1. 클라이언트 요청 → DispatcherServlet이 받음  
2. HandlerMapping이 Controller 탐색  
3. HandlerAdapter가 실행 준비  
4. Controller → Service → DAO 순으로 비즈니스 로직 처리  
5. DAO → Service → Controller 순으로 반환  
6. ViewResolver가 JSP 경로로 변환  
7. JSP 렌더링 후 응답 반환  

---

## ✔ ViewResolver 역할
컨트롤러가 반환한 `"board/list"` 문자열을  
`/WEB-INF/views/board/list.jsp` 로 변환함.

---

## ✔ HandlerMapping vs HandlerAdapter

| 구분 | 역할 |
|------|------|
| HandlerMapping | 어떤 Controller를 실행할지 결정 |
| HandlerAdapter | Controller 실행을 가능하게 조정 |

---

## ✔ Service 계층이 필요한 이유
- 비즈니스 로직 집중  
- 중복 제거  
- 트랜잭션 처리 가능  
- Controller 비대화 방지  
- 유지보수성 향상  

---

## ✔ @Autowired 동작 방식
- 스프링 컨테이너가 **타입 기반**으로 Bean 탐색  
- 자동 주입  
- 동일 타입 여러 개이면 `@Qualifier` 필요  
- 객체 생성 new 없음 → DI 기반 관리  

---

## ✔ JDBC & DBCP 요약
### JDBC
- Connection / Statement / ResultSet 반복 코드 많음  

### DBCP(커넥션 풀)
- 커넥션 미리 생성 + 재사용  
- 성능 향상  
- DB 보호 및 누수 방지  

---

## ✔ JdbcTemplate 사용 이유
- 자원 정리 자동  
- SQL + RowMapper만 작성  

---

## ✔ RowMapper
ResultSet → Java 객체 매핑.

---

## ✔ GET vs POST

### GET
- URL에 데이터 노출  
- 조회에 적합  

### POST  
- Body로 데이터 전송  
- 등록/수정 용도  

---

## ✔ forward vs redirect

| 방식 | 특징 |
|------|------|
| forward | 서버 내부 이동, URL 유지 |
| redirect | 새로운 요청, URL 변경 |

---

# 2️. Java OOP Basic Q&A

## ✔ 오버라이딩 vs 오버로딩

### Override
- 상속받은 메서드 재정의  
- 이름/파라미터/반환타입 동일  

### Overload
- 같은 이름, 다른 파라미터  
- 컴파일 타임 결정  

---

## ✔ 추상 클래스 vs 인터페이스

| 항목 | 추상 클래스 | 인터페이스 |
|------|-------------|-------------|
| 일반 메서드 | O | default O |
| 변수 | 필드 존재 | 상수 |
| 상속 | 단일 상속 | 다중 구현 가능 |
| 목적 | 공통 기능 제공 | 역할 부여 |

---

## ✔ == vs equals()
- `==` : 기본형 값 / 참조 주소 비교  
- `equals()` : 주로 내용(value) 비교  

---

## ✔ String / StringBuilder / StringBuffer

| 타입 | 특징 |
|------|-------|
| String | 불변 |
| StringBuilder | 가변, 빠름 |
| StringBuffer | 가변, 동기화 O |

---

## ✔ final 키워드
- final 변수 : 재할당 불가  
- final 메서드 : 오버라이드 불가  
- final 클래스 : 상속 불가  

---

## ✔ static
- 클래스 레벨 멤버  
- 객체 생성 없이 사용  
- this 사용 불가  

---

## ✔ 접근 제어자
- public  
- protected  
- default  
- private  

---

# 3️. Java & Spring Advanced Q&A

## ✔ Checked vs Unchecked Exception
- Checked: IOException, SQLException  
- Unchecked: NPE, IllegalArgumentException  

---

## ✔ List vs Set vs Map
- List: 순서 O, 중복 O  
- Set: 순서 X, 중복 X  
- Map: key-value 구조  

---

## ✔ HashMap vs ConcurrentHashMap

| 타입 | 특징 |
|------|------|
| HashMap | 스레드 안전 X |
| ConcurrentHashMap | 스레드 안전 O |

---

## ✔ JVM 메모리 구조
- Method Area  
- Heap  
- Stack  
- PC Register  
- Native Method Stack  

---

## ✔ GC 핵심
- 사용되지 않는 객체 정리  
- Young / Old 영역  
- Stop-the-world 발생 가능  

---

## ✔ Spring Bean Scope
- singleton  
- prototype  
- request  
- session  

---

## ✔ AOP 핵심
- 공통 기능을 핵심 로직과 분리  
- Advice, Pointcut, JoinPoint  

---

## ✔ Filter vs Interceptor vs AOP

| 종류 | 실행 지점 |
|------|-----------|
| Filter | 서블릿 앞단 |
| Interceptor | Controller 전/후 |
| AOP | 메서드 실행 단위 |

---

## ✔ REST API 특징
- 무상태성  
- 캐싱 가능  
- 리소스 기반  
- 계층 구조  

---

## ✔ HTTP 상태 코드
200 / 201 / 400 / 401 / 403 / 404 / 500  

---

# 4️. Spring Bean Scope

## ✔ Singleton
- 컨테이너당 1개  
- 상태 공유 주의  

## ✔ Prototype
- 요청할 때마다 새 객체  

## ✔ Request Scope
- HTTP 요청마다 1개  

## ✔ Session Scope
- 사용자 세션당 1개  

---

# 5️. JVM & GC Explained

## ✔ JVM 구조
- Heap: 객체  
- Stack: 메서드 호출/지역변수  
- Method Area: 클래스 정보  

---

## ✔ GC란?
불필요한 객체를 JVM이 자동 삭제하는 기능.

### 왜 필요?
- 메모리 누수 방지  
- 개발자가 해제할 필요 없음  

### Young / Old
- Young: 금방 죽는 객체  
- Old: 오래 살아남은 객체  

### Stop-the-world
GC 실행 동안 모든 스레드 멈춤.

---

# 6️. 자바 접근 제어자 상세 설명

## ✔ public
모든 패키지에서 접근 가능

## ✔ protected
- 같은 패키지  
- or 다른 패키지라도 **상속 관계면 OK**

## ✔ default (package-private)
- 같은 패키지에서만 접근 가능  
- 접근 제어자 생략 시 기본값  

## ✔ private
- 같은 클래스 내부에서만 접근 가능  

---

# 7️. 개발 환경 / 기술 스택

## ✔ Java
- Java 8

## ✔ IDE & Tools
- Eclipse  
- EditPlus

## ✔ Framework
- Spring MVC (Legacy)  
- JSP / JSTL / EL  

## ✔ Build Tool
- Maven

## ✔ WAS
- Apache Tomcat

## ✔ DB
- MySQL  
- JDBC / JdbcTemplate / DBCP  

---
