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

---

### 기본 객체들

