# 인프런 강의(스프링 MVC 2편 - 백엔드 웹 개발 활용 기술)의 코드 실습

## 정리

타임리프는 html 파일에 선언 가능하며, <br>

```html
<html xmlns:th="http://www.thymeleaf.org">
```
를 head태그 위에 붙여 넣으면 된다.
<br><br>

#### Spring EL
```html
<span th:text="${user.username}"> 
```

- 다음과 같이 태그 안에 th:text를 이용해 선언 가능하며,
- 별도의 태그 없이는 [[${data}]] 와 같이 데이터 출력 가능하다.

#### 지역변수 선언

```html
<div th:with="first = ${users[0]}"> <!--first라는 지역 변수를 users[0]으로 설정-->
     <span th:text="${first.username}"></span>
</div>
```
다음과 같이 th:with를 이용해 지역변수를 선언하고 사용할 수 있다.

#### 주의할 점

```thymeleafexpressions
    <span th:text="Hello"> </span>
    
    //아래는 에러가 발생한다.
    <span th:text="Hello world!"> </span> 
    
    //띄어쓰기가 있는 문자열은 싱글 따옴표(\')로 감싸야 한다.)
    <span th:text="'Hello world!'"> </span> 
    
    //다음과 같은 표현식도 유효하다.
    <span th:text="'Hello' +${param.val}"> </span>
    <span th:text="|Hello ${param.val}|"> </span>
    
```

---

### 기본 객체들

```html
//HTTP요청 파라미터 접근: param
${param.paramData}

//세션 접근: session
${session.sessionData}

//빈 접근: @
${@helloBean.hello('Spring!')}

```

### 유틸리티 객체와 날짜

https://www.thymeleaf.org/doc/tutorials/3.0/usingthymeleaf.html#expression-utility-objects
https://www.thymeleaf.org/doc/tutorials/3.0/usingthymeleaf.html#appendix-b-expression-utility-objects

#### 날짜
```html
<span th:text=
   "${#temporals.format(localDateTime, 'yyyy-MM-dd HH:mm:ss')}">
</span>
```

### URL링크
URL링크는```<a th:href="@{ 위치 }">```와 같은 방식으로 사용한다.
```thymeleafexpressions
    1. 경로만 표현
    <li><a th:href="@{/hello}">basic url</a></li>
    
    2. url값 주입방식
    <li><a th:href="@{/hello/{val}(val=${param.val})}">param 값 url</a></li> 
    
    3. url값 주입방식2
    <li><a th:href="@{/hello/{param1}/{param2}(param1=${param1}, param2=${param2})}">path variable</a></li>
    
    4. get방식으로 param값 주입(별도의 {}값 지정이 없으면 param값으로 주입된다.)
    <li><a th:href="@{/hello(param1=${param1}, param2=${param2})}">hello query param</a></li>
    
    5. 혼합방식
    <li><a th:href="@{/hello/{param1}(param1=${param1}, param2=${param2})}">path variable + query parameter</a></li>
```






