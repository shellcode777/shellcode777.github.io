---
title: edwith 부스트코스
excerpt: HTML/CSS, JS, JAVA, Spring, Spring MVC, Spring JDBC, SQL
categories: boost
---

## 웹 어플리케이션 풀스택 개발  
###### HTML/CSS, JS, JAVA, Spring, Spring MVC, Spring JDBC, SQL

> CHO HYUNWOO 
                



PART. 01 웹 프로그래밍 기초
===========================

CHAPTER. 01 웹 개발
-------------------

### Point. 01 HTTP (Hypertext Transfer Protocol) 작동방식

#### HTTP는 서버/클라이언트 모델을 따른다

1.  장점

    1.  불특정 다수를 대상을 하는 서비스에 적절

    2.  클라이언트와 서버가 계속 연결된 형태가 아니기 때문에
        클라이언트와 서버 간의 최대 연결 수보다 훨씬 많은 요청과 응답
        처리

2.  단점

    1.  연결을 끊어 버리기 때문에, 클라이언트의 이전 상황을 알 수 없음

    2.  이러한 특징을 무상태 라고 한다.

    3.  정보 유지를 위한 Cookie 같은 기술 등장

#### URL (Uniform Resource Locator)

1.  인터넷 상의 자원의 위치

2.  특정 웹 서버의 특정 파일에 접근하기 위한 경로, 주소  
![]({{site.url}}/assets/images/boost/image2.png)


#### HTTP

1.  요청 메서드: GET, PUT, POST, PUSH, OPTIONS 등의 요청 방식

    1.  GET: 정보 요청(SELECT)

    2.  POST: 정보를 밀어 넣음(INSERT)

    3.  PUT: 정보를 업데이트(UPDATE)

    4.  DELETE: 정보 삭제(DELETE)

    5.  HEAD: HTTP헤더 정보만 요청. 해당 자원은 존재유무 및 서버 이상
        확인

    6.  OPTIONS: 웹 서버가 지원하는 메서드 종류 요청

    7.  TRACE: 클라이언트 요청을 그대로 반환. echo 서비스로 서버 상태
        확인을 위해 주로 사용

2.  요청 URI: 요청하는 자원의 위치 명시

3.  HTTP 프로토콜 버전: 웹 브라우저가 사용하는 프로토콜 버전

### Point. 02 웹 Front-End Back-End

#### 웹 프론트 엔드

1.  웹 콘텐츠를 보여주기 위한 구조를 만듦 - HTML

2.  적절한 배치 일관된 디자인 등을 제공 - CSS

3.  사용자 요청 반영 - Javascript

#### 백 엔드

1.  프로그래밍 언어 - JAVA, Python, PHP, Javascript

2.  웹 동작의 원리 이해

3.  알고리즘, 자료구조 등 프로그래밍 기반 지식

4.  운영체제, 네트워크 등에 대한 이해

5.  프레임워크에 대한 이해 (ex. Spring)

6.  DBMS에 대한 이해와 사용 (Mysql, Oracle 등

CHAPTER. 02 HTML
----------------

### Point. 01 HTML Tags

#### HTML tag 종류

> 태그는 그 의미에 맞춰서 사용 해야함

- 링크

- 이미지

- 목록

- 제목

- **anchor, img, ul/li, heading, p 태그 등이 자주 사용된다.**

- **가장 많이 사용하는 태그는 div 태그**

- div 태그는 block 엘리먼트라고 하는데 일반적인 영역을 표현할 때
많이 사용된다.

### Point. 02 HTML Layout 태그

#### 레이아웃을 위한 태그

-   header

-   section

-   nav

-   footer

-   aside

  ![Page Layout]({{site.url}}/assets/images/boost/image3.png)  
    - HTML5 Layout tag

### Point 03. CLASS 와 ID

#### ID

-   고유한 속성으로 한 HTML 문서에 하나만 사용

-   고유한 ID 값이 있으면 하나하나에 특별한 제어를 할 수 있고 검색에도
    용이함

#### Class

-   하나의 HTML문서 안에 중복해서 사용 가능

-   하나의 태그에 여러 개의 다른 class 이름을 공백을 기준으로 나열 가능

-   홈페이지 전체적인 스타일을 일관성 있게 지정하기 위해서 사용

> 개발단계에서 약속(Convention)을 만들어서 자신들의 규칙을 사용하기도 함
>
> ID의 사용 금지, 클래스만 사용 하는 등 환경에 따라 다르다.

CHAPTER. 03 CSS
---------------

### Point 01. CSS 선언

#### CSS 구성
```css
span{
     color : red;
}
```
-   span: selector(선택자)

-   color: property

-   red: value

#### 스타일을 HTML 페이지 적용 방법

1)  **inline**

> HTML 태그 안에 적용
>
> 다른 CSS 파일에 적용한 것 보다 가장 먼저 적용

```css
<p style = “border:1px solid gray; color:red; font-size:2em;”>
```

2)  **internal**

> 스타일 태그로 지정함
>
> 구조와 스타일이 섞여 유지보수가 어려움
>
> 별도 CSS 파일을 관리하지 않아도 되며 서버에서 CSS 파일을 부르기 위해
> 브라우저가 요청을 보내지 않아도 된다.

```html
<head>
<style>
p {
   font-size : 2em;
   border:px solid gray;
   color:red;
}
</style>
</head>
```

3)  **external**

> 외부파일(.css)로 지정하는 방식
>
> 가급적 이 방법으로 구현
>
> 여러 개의 CSS 파일을 분리하고 또는 통합하여 서비스에 사용
>
> 별도의 파일을 만들고 link 태그로 추가

```html
<html>
    <head>
        <link rel = “stylesheet” herf=”style.css”>
    </head>

```

4)  우선 순위

> inline은 별도의 우선 순위를 가짐, internal과 external은 우선순위가
> 동등하다.

5)  상속과 우선순위

> ID \> CLASS \> ELEMENT 순으로 우선 순위 반영

### Point 02. CSS selector

#### element에 스타일 지정을 위한 기본 선택자

-   tag로 지정

```css
<style>
    span {
        color : red;
    }
</style>
```

-   id로 지정

```css
<style>
    #spantag {
        color : red;
    }
</style>
<body>
    <span id=”spantag”> HELLOW WORLD! </span>
</body>
```

-   class로 지정

```css
<style>
    .spanClass {
        color : red;
    }
</style>
<body>
    <span class=”spanClass”> HELLOW WORLD! </span>
</body>
```

#### CSS Selector 활용

-   id, class 요소 선택자와 함께 활용

```css
#myid { color : red }
div.myclassname { color : red }
```

-   그룹 선택 (여러 개 셀럭터에 같은 스타일 적용 시)

```css
h1, span, div { color : red }
h1, span, div#id { color : red }
h1.span, div.classname { color : red }
```

-   요소 선택 (공백) : 차일드 요소

-   아래 모든 span 태그에 red 색상 적용

```css
<div id = “elementID”>
    <div>
        <span> tag </span>
    </div>
    <span> tag2 </span>
</div>
```

```css
#elementID span { color : red }
```

-   n번째 자식요소 선택 (nth-child)

-   h2 하위 첫 번째 요소에 red 색상이 적용됨

```css
<div id = “elementID”>
    <h2>단락 선택</h2>
    <p> 첫 번째 </p>
    <p> 두 번째 </p>
    <p> 세 번째 </p>
    <p> 네 번째 </p>
</div>
```

```css
# elementID > p:nth-child(2) { color : red }
```


### Point 03. CSS 기본 스타일 변경

#### font 색상 변경

-   color: red;

-   color: rgba(255, 0, 0, 0.5)

-   color: \#ff0000; (16진수 표기법 가장 많이 사용 됨)

#### font 사이즈 변경

-   font-size : 16px;

-   font-size : 1em;

#### 배경색

-   background-color : \#ff0;

-   background-image, position, repeat 등의 속성

-   background : \#0000ff url(".../gif") no-repeat center top; 한 줄로
    정의

#### 글씨체/글꼴

-   font-family: "Gulim";

-   font-family: monospace;

#### 웹 폰트

> 브라우저에서 기본 지원하지 않는 폰트를 다운로드 받아 사용
>
> 대표적으로 구글 웹 폰트가 있다.
>
> 유니코드를 사용하여 아이콘 표현 가능

### Point 04. Element가 배치되는 방법(CSS layout)

#### 엘리먼트 배치 방식

> **엘리먼트를 배치하는 것은 layout 작업 또는 Rendering 과정이라고 한다**

-   diplay(block, inline, inline-block)

-   position(static, absolute, relative, fixed)

-   float(left, right)

#### 블록으로 쌓이는 엘리먼트 (display : block)

> display 속성이 block이거나 inline-block인 경우 블록을 가지고 쌓인다.  

![]({{site.url}}/assets/images/boost/image4.png)


#### 엘리먼트 배치(display:inline)

![]({{site.url}}/assets/images/boost/image5.png)


#### Position 속성 (position:static, relative, absolute)

1.  position 속성으로 특별한 배치

2.  position 속성의 기본값은 static 순서대로 배치 된다.

3.  absolute는 기준점에 따라 위치한다.

4.  top / left / right / bottom으로 설정

5.  기준점을 상위엘리먼트로 단계적으로 찾아가고 static이 아닌 position이
    기준점

6.  relative는 원래 자신이 위치해야 할 곳을 기준으로 이동

7.  top / left / right / bottom으로 설정

8.  fixed는 viewport(전체화면) 좌측, 맨 위를 기준으로 동작

CHAPTER. 04 개발 환경
---------------------

### Point. 01 JDK

#### JDK(Java Developer Kit) 다운로드

![]({{site.url}}/assets/images/boost/image6.png)

![]({{site.url}}/assets/images/boost/image7.png)

#### 환경변수 설정


![]({{site.url}}/assets/images/boost/image8.png)


-   고급 시스템 설정 \> 환경 변수

![]({{site.url}}/assets/images/boost/image9.png)



![]({{site.url}}/assets/images/boost/image10.png)

-   새로 만들기 클릭


![]({{site.url}}/assets/images/boost/image11.png)


-   "JAVA_HOME" 변수 값에 JDK 설치 경로 입력

![]({{site.url}}/assets/images/boost/image12.png)


-   "CLASSPATH" 환경변수 추가


![]({{site.url}}/assets/images/boost/image13.png)


-   시스템변수 "PATH" 편집, `%JAVA_HOME%\bin` 또는
    `C:\JDK\java\jdk1.8.0_211\bin` 추가


![]({{site.url}}/assets/images/boost/image14.png)


-   명령 프롬프트 실행 java -version으로 설치 확인

![]({{site.url}}/assets/images/boost/image15.png)


-   자바 프로그램 javac 컴파일 및 실행과 결과 "hello java" 출력

### Point. 02 이클립스

#### 이클립스 다운로드 및 압축해제


![]({{site.url}}/assets/images/boost/image16.png)  

![]({{site.url}}/assets/images/boost/image17.png)


#### 이클립스 실행 및 인코딩 설정

![]({{site.url}}/assets/images/boost/image18.png)  
![]({{site.url}}/assets/images/boost/image19.png)  
![]({{site.url}}/assets/images/boost/image20.png)  


-   windows \> Preferences 선택

![]({{site.url}}/assets/images/boost/image21.png)

-   General \> Workspace 메뉴의 Text file encoding의 Other을 선택
    UTF-8로 선택

-   CSS Files HTML Files JSP Files 모두 인코딩 설정 UTF-8로 변경

### Point. 04 아파치 톰캣 설치

#### 아파치 톰캣 다운로드

![]({{site.url}}/assets/images/boost/image22.png)  


#### 톰캣 압축해제 및 실행


![]({{site.url}}/assets/images/boost/image23.png)

![]({{site.url}}/assets/images/boost/image24.png)  

![]({{site.url}}/assets/images/boost/image25.png)  


-   톰캣 폴더 내에 bin 폴더의 startup.bat 실행

#### 기본 포트 변경 및 실행 

> (불필요 시 변경 하지 않아도 무관, 오라클 XE와 포트 충돌돼서 변경)  

![]({{site.url}}/assets/images/boost/image26.png)  


-   conf 폴더의 server.xml 수정

![]({{site.url}}/assets/images/boost/image27.png)  


-   "Connector port"를 사용가능 한 포트 번호로 변경 및 톰캣 재시작

![]({{site.url}}/assets/images/boost/image28.png)  

-   localhost: \<포트번호\> (이 프로젝트에서는 localhost:8888)로 접속 후
    톰캣 동작 확인

CHAPTER. 05 Servlet
-------------------

### Point. 01 Servlet 컴파일 및 실행

#### perspective 선택


![]({{site.url}}/assets/images/boost/image29.png)  



-   java EE perspective 선택

#### 프로젝트 생성


![]({{site.url}}/assets/images/boost/image30.png)  

-   file \> New \> Dynamic Web Project 선택

![]({{site.url}}/assets/images/boost/image31.png)  

-   프로젝트 이름 지정 Target runtime \> New Runtime 선택 (사용할 WAS
    선택)


![]({{site.url}}/assets/images/boost/image32.png)  
![]({{site.url}}/assets/images/boost/image33.png)  


-   사용할 WAS 종류 및 버전 선택 \> Next \> Browse 설치 된 WAS 경로
    지정 \> Finish

#### 서블릿 파일 생성


![]({{site.url}}/assets/images/boost/image34.png)

-   생성한 프로젝트에서 New \> Servlet

![]({{site.url}}/assets/images/boost/image35.png)  


-   패키지이름 클래스이름 지정 \> Next

![]({{site.url}}/assets/images/boost/image36.png)  

-   URL mapping : 접근 할 URL Edit으로 지정 혹은 기본 값 이후 Next

![]({{site.url}}/assets/images/boost/image37.png)  

-   doGet 이외에 나머지는 체크박스 해제 후 Finish

![]({{site.url}}/assets/images/boost/image38.png)  

-   생성 된 서블릿 파일

```java
response.setContentType("text/html;charset=utf-8");
PrintWriter out = response.getWriter();
out.print("<h1>HELLO WORLD</h1>");
```

-   protected void doGet 부분 -\> doGet 메서드

-   GET 메서드에 요청이 들어오면 동작해서 출력 할 코드 작성 후 저장
    (ctrl + s)

-   PrintWriter 객체 out -\> response 객체로부터 가져온 객체 응답결과를
    보내줌


![]({{site.url}}/assets/images/boost/image39.png)  
![]({{site.url}}/assets/images/boost/image40.png)

-   상단 메뉴 바 Run \> Run As \> Run on Server \> Finish: 작성 웹 앱
    컴파일

![]({{site.url}}/assets/images/boost/image41.png)  

-   서블릿 파일 동작 확인

### Point. 02 Servlet 작성

#### 버전에 따른 Servlet 작성

1.  **Servlet 3.0 스펙 이상**

    1.  web.xml 파일을 사용하지 않음

    2.  자바 어노테이션 사용

- 자바 어노테이션 (annotation)

> @를 이용한 주석, 자바코드에 주석을 달아 의미를 부여 한다.  
> 컴파일러가 프로그램 코드의 일부가 아닌 프로그램에 관한 데이터를 제공,
> 코드에 정보 추가하는 정형화된 방법

```java
import javax.servlet.annotation.WebServlet;      
//javax.servlet.annotation 패키지 import

@WebServlet("/net") //WebServlet어노테이션 속성 사용
```

2.  **Servlet 3.0 미만에서 사용**

    1.  servlet 등록 시 web.xml 파일에 등록

```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://java.sun.com/xml/ns/javaee" xsi:schemaLocation="http://java.sun.com/xml/ns/javaee http://java.sun.com/xml/ns/javaee/web-app_2_5.xsd" id="WebApp_ID" version="2.5">
  <display-name>exam25</display-name>
  <welcome-file-list>
    <welcome-file>index.html</welcome-file>
    <welcome-file>index.htm</welcome-file>
    <welcome-file>index.jsp</welcome-file>
    <welcome-file>default.html</welcome-file>
    <welcome-file>default.htm</welcome-file>
    <welcome-file>default.jsp</welcome-file>
  </welcome-file-list>
  <servlet>
    <description></description>
    <display-name>TenServlet</display-name>
    <servlet-name>TenServlet</servlet-name>
    <servlet-class>exam.TenServlet</servlet-class>
  </servlet>
  <servlet-mapping>
    <servlet-name>TenServlet</servlet-name>
    <url-pattern>/ten</url-pattern>
  </servlet-mapping>
</web-app>
```

-   18\~24라인 서블릿 클래스 작성 및 url 지정

### Point. 03 Servlet 라이프사이클

#### LifecycleServlet 클래스 생성

![]({{site.url}}/assets/images/boost/image42.png)  

#### 서블릿 생명주기 확인을 위한 init, service, destroy 메서드 override

![]({{site.url}}/assets/images/boost/image43.png)  

#### 생성된 메서드 동작 확인을 위해 콘솔창에 출력

```java
package testweb;

import java.io.IOException;
import javax.servlet.ServletConfig;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

@WebServlet("/LifecycleServlet")
public class LifecycleServlet extends HttpServlet {
	private static final long serialVersionUID = 1L;
       
public LifecycleServlet() {
        System.out.println("LifecycleServlet Create");
        // TODO Auto-generated constructor stub
    }
	public void init(ServletConfig config) throws ServletException {
		// TODO Auto-generated method stub
		System.out.println("init 호출!");				
	}
	public void destroy() {
		// TODO Auto-generated method stub
		System.out.println("destroy 호출");
	}

	protected void service(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// TODO Auto-generated method stub
		System.out.println("service 호출");
	}
}
```
-   System.out -\> PrintWrite와 다르게 응답 결과가 아닌 콘솔에 결과 출력

![]({{site.url}}/assets/images/boost/image44.png)  

-   서블릿을 생성과 초기화 서비스 호출 동작 콘솔로 확인

-   WAS내 메모리에 서비스가 올라가 있지 않은 경우 생성과 초기화 후
    서비스가 동작

```java
System.out.println("destroy 호출");
System.out.println("destroy 호출!"); // 호출 -> 호출! 수정 후 저장
```
![]({{site.url}}/assets/images/boost/image45.png)  

-   서블릿이 수정되면 destroy 메소드를 호출한 후 다시 메모리에 로드 할
    수 있게 한다.

-   메모리내에 서블릿이 로드 되어있다면 서비스 메소드만 호출된다.

#### Servlet 생명주기

-   WAS는 서블릿 요청을 받으면 해당 서블릿이 메모리에 로드 되어있는지
    확인

-   메모리에 없을 경우

> 해당 서블릿 클래스를 메모리에 올린다
>
> init() 메소드 실행

-   메모리에 로드 되어있는 경우

> service() 메소드 실행

-   WAS가 종료되거나, 웹 어플리케이션이 갱신될 경우 destroy() 메소드
    실행

-   service() 메소드를 오버라이드 하지 않은 경우

> 부모인 HttpServlet의 service() 메소드가 실행된다.

![]({{site.url}}/assets/images/boost/image46.jpeg)  

#### service(request, response) 메소드

```java 
	@Override
	protected void doGet(HttpServletRequest requset, HttpServletResponse response) throws ServletException, IOException {
		// TODO Auto-generated method stub
		response.setContentType("text/html");
		PrintWriter out = response.getWriter();
		out.println("<html>");
		out.println("<haed><title>form</title></head>");
		out.println("<body>");
		out.println("<form method = 'post' action='/firstweb/LifecycleServlet'>");
		out.println("name : <input type='text' name='name'><br>");
		out.println("<input type='submit' value='ok'><br>");
		out.println("</form>");
		out.println("</body>");
		out.println("</html>");
		out.close();
	}

	@Override
	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// TODO Auto-generated method stub
		response.setContentType("text/html");
		PrintWriter out = response.getWriter();
		String name = request.getParameter("name");
		out.println("<h1> hello" + name + "</h1>");
	}
```
![]({{site.url}}/assets/images/boost/image47.png)  
![]({{site.url}}/assets/images/boost/image48.png)  

-   클라이언트 요청이 GET일 경우 doGet 메소드 호출

-   클라이언트 요청이 POST일 경우 doPost 메소드를 호출

### Point. 04 Request, Response 객체

#### WAS가 브라우저로부터 Servlet 요청을 받는 경우

-   요청할 때 가지고 있는 정보는 HttpServletRequest 객체를 생성하여 저장

-   웹 브라우저에게 응답을 보내기 위한 HttpServletResponse 객체 생성

-   생성된 HttpServletRequest, HttpServletResponse 객체를 서블릿에 전달

#### HttpServletRequest

-   http 프로토콜의 요청 정보를 서블릿에 전달하기 위해 사용

-   헤더정보, 파라미터, 쿠키, URI, URL 등의 정보를 읽어 들이는 메소드를
    가진다.

-   body의 Stream을 읽어 들이는 메소드를 가지고 있다.

#### HttpServletResponse

-   요청을 보낸 클라이언트에게 응답을 보내기 위한 객체를 생성하여
    서블릿에 전달

-   서블릿은 해당 객체를 이용하여 content type, 응답코드, 응답 메시지
    등을 전송

![]({{site.url}}/assets/images/boost/image49.png)  

- 요청헤더 정보  

![]({{site.url}}/assets/images/boost/image50.png)  

- 응답헤더 정보  


PART. 02 DB 연동 웹 어플리케이션
================================

CHAPTER. 01 JavaScript - FrontEnd
---------------------------------

### Point. 01 JavaScript 개발용 에디터

#### Visual Studio Code 다운로드

![]({{site.url}}/assets/images/boost/image51.png)  

다운로드 URL:[https://code.visualstudio.com/insiders/](https://code.visualstudio.com/insiders/){: target="_blank"}

#### 압축해제 또는 설치 후 Code.exe 실행

![]({{site.url}}/assets/images/boost/image52.png)

#### 디버깅 확장프로그램 code runner 설치


![]({{site.url}}/assets/images/boost/image53.png)  

![]({{site.url}}/assets/images/boost/image54.png)  

- 설치 완료되면 Run 버튼 생성  

#### Node.js 설치 (미설치 시 디버깅 불가)

![]({{site.url}}/assets/images/boost/image55.png)
URL: [https://nodejs.org/ko/](){: target="_blank"}  

![]({{site.url}}/assets/images/boost/image56.png)  

- Node.js 설치 확인  

#### VS Code 재시작 후 사용

![]({{site.url}}/assets/images/boost/image57.png)  


### Point. 02 자바스크립트

#### 자바스크립트 버전

-   ECMAScript(ES)의 버전에 따라서 결정되고, 이를 실행 엔진이 반영

-   ES5, ES6(ES2015) 등의 버전 이후 버전은 ES6+로 통칭 하기도 한다.

#### 변수

-   ES6 이전에는 var로 변수 선언

-   ES6 이후에는 let, const로도 변수 선언

-   종류에 따라 scope라는 변수의 유효범위가 달라진다.

-   const는 한 번 할당한 값에 재할당이 안 된다.

#### 연산자

-   우선순위는 ()를 사용하면 된다.

-   or 연산자

```js
//or 연산자 활용
const name = "crong";
const result = name || "codesquad";
console.log(result);
//result -> crong
var name = "";
var result = name || "codesquad";
console.log(result);
//result -> codesquad
//활용도에 따라 if 대신 사용도 가능
```

-   and 연산자

```js
const name = "crong";
const result = name && "codesquad";
console.log(result);
//result -> codesquad
//and 연산자 이후 값이 변수에 들어감
```

-   삼항연산자 간단한 조건문 표현 가능

```js
const data = 11;
const result = (data > 10) ? "ok" : "fail";
console.log(result);
```
-   연산자 - 비교연산자

```js
0 == false;           //true
"" == false;           //true
null == false;         //null은 객체이기 때문에 결과 false
0 == "0";             //true 타입은 비교 안함
0 === "0";            //false 타입까지 비교
null==undefined;
```
> 비교연산자 "=="은 자주 사용하지 않음 "==="을 주로 사용

#### 자바스크립트 Type

>`undefined, null, boolean, number, string, object, function, array, Date, RegExp`  

![]({{site.url}}/assets/images/boost/image58.png)  

-   자바스크립트는 함수 안에서의 파라미터나 변수의 타입은 선언할 때가
    아니고 실행타임에 결정

-   type of 키워드나 toString.call 함수를 이용해서 타입 체크가능

#### 문자열 처리

-   자바스크립트의 문자와 문자열은 같은 타입

```js
typeof "abc";  //string
typeof "a";    //string
typeof 'a';    //string. single quote도 사용가능.
```

-   문자열 메서드

-   문자열은 자바스크립트 내부적으로 객체로 변환되기 때문에 객체 내에
    있는 메서드를 사용할 수 있다.

```js
"ab:cd".split(":"); //["ab","cd"] 
               // split 배열을 만들어주는 메서드
"ab:cd".replace(":", "$"); //"ab$cd"
" abcde  ".trim();  //"abcde"
```

#### 함수

-   함수의 선언

> 함수는 여러 개의 인자를 받아서 결과를 출력
>
> 파라미터의 개수와 인자의 개수가 일치하지 않아도 오류가 발생하지
> 않는다.
>
> 파라미터 한 개가 정의된 함수를 인자 개수를 0개만 넣어 실행하면
> 파라미터는 `undefined` 값을 갖게된다.

```js
function printName(firstname){
    return "name is" + firstname
}
//함수 선언문
```
```js
function printName(firstname){
    var result = inner();
    console.log(typeof inner);
    console.log("it is" + result);

    function inner(){
        return "inner value"
    }
    
}

printName();
//함수 선언문 + 함수 표현식
[Running] node "c:\Users\a-10t\WorkingDirectory\JS\sample.js"
function
it isinner value

//실행 결과
 var result = inner();
//함수 표현식
```
-   반환 값

> 자바스크립트는 반환 값이 존재 하지 않으면 반드시 `undefined`가 반환된다.

#### 호이스팅

-   호이스팅이란 자바스크립트의 변수는 다른 언어들과 다르게 동작하는
    특징이다.

-   ES2015 이후 let, const를 사용하여 예방 가능

-   변수 선언문을 유효 범위의 최상단으로 올라가서 선언과 할당을 분리
    시키는 것을 호이스팅 이라고 한다.

```js
//작성한 코드
if(true){
var number = 777;
}
console.log(number)

[Running] node "c:\Users\a-10t\WorkingDirectory\JS\hoisting.js"
777

//자바스크립트에서 호이스팅 되어 동작하는 코드
var number;
if(true){
    number = 777;
}
console.log(number)

[Running] node "c:\Users\a-10t\WorkingDirectory\JS\hoisting.js"
777
```
- 위와 같이 내부적으로 변수선언을 상단에서 하는 형태로 동작된다.  

-   호이스팅 우선순위

> 변수 선언 \> 함수 선언 \> 할당

#### argument 객체

-   함수가 실행될 때 자동으로 생성되는 지역변수, 배열형태의 객체

-   오브젝트 형태에 가까움

-   array 타입이 아니라서 배열의 메서드를 사용할 수 없음

```js
function a(){
    console.log(arguments);
    console.log(typeof arguments);
}
a(1,2,3)

[Running] node "c:\Users\a-10t\WorkingDirectory\JS\arg.js"
[Arguments] { '0': 1, '1': 2, '2': 3 }.
object
```

-   자바스크립트 함수는 선언한 파라미터보다 더 많은 인자를 보낼 수 있음

-   파라미터로 전달된 인자를 arguments로 배열의 형태로 접근 가능

```js
function sum(){
    var a = 0;
    var len = arguments.length;
    for (var i=0; i < len; i++){
         a+=arguments[i];
    }
    return a

}
console.log(sum(1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16));
//arguments로 파라미터에 전달 된 인자들의 합을 구함
[Running] node "c:\Users\a-10t\WorkingDirectory\JS\test.js"
136
```

#### window 객체(setTimeout)와 비동기

-   window객체: 전역 객체이기 때문에 생략가능, 많은 메서드가 존재한다.

```js
window.setTimeout()
setTimeout()
```

-   setTimeout 동작

> 인자로 함수를 받고 이 함수는 콜백함수라고도 한다.
>
> 자바스크립트는 함수를 인자로 받을 수 있고, 반환할 수 있는 특징이 있다.
```js
function run(){
    setTimeout(function(){
        var msg = "hello";
        console.log(msg);
    }, 2000);
}	
run();
//setTimeout에 전달된 함수는 2초뒤에 실행된다.
```

```js
function run(){
    console.log("START");
    setTimeout(function(){
        var msg = "hello";
        console.log(msg);
    }, 2000);
    console.log("END")
}
run();

[Running] node "c:\Users\a-10t\WorkingDirectory\JS\setTimeout.js"
START
END
hello
//콜백함수는 호출스택에 쌓인 함수들의 실행이 끝난 후 실행된다. 
```

\*호출스택 참고:[https://developer.mozilla.org/ko/docs/Glossary/Call_stack](https://developer.mozilla.org/ko/docs/Glossary/Call_stack){: target="_blank"}


### Point. 03 WEB UI

#### DOM과 querySelector

-   DOM

> 브라우저는 HTML 코드를 DOM(Document Object Model:문서 객체 모델)이라는
> 객체형태의 모델로 저장하고 DOM Tree라고 부르고, HTML 요소들은 트리
> 형태로 저장된다.
>
> DOM이라는 개념을 통해 DOM Tree를 용이하게 탐색 및 조작을 위한 메서드나
> 함수들을 DOM API를 통해 브라우저가 제공한다.

![]({{site.url}}/assets/images/boost/image59.png)
- Dom Tree구조  

-   getElementById

> HTML 최상위 Element인 document 객체에서 제공되는 DOM API를 사용

![]({{site.url}}/assets/images/boost/image60.png)  

- Element 속성 중의 id가 nav-cart-count인 것을 찾는다.
-   querySelector

> DOM을 찾는데 유영한 메서드
>
> CSS Selector 문법을 활용해 DOM에 접근 할 수 있다.
>
> querySelectorAll을 통해 특정요소를 모두 찾을 수 있다.

![]({{site.url}}/assets/images/boost/image61.png)  

```js 
Element.querySelector()
```
![]({{site.url}}/assets/images/boost/image62.png)  

- CSS Selector: id는 '\#', class명은 앞에 '.' 을 붙인다  
  
![]({{site.url}}/assets/images/boost/image63.png)  
- querySelectorAll(): 모든 요소들을 찾는다.  

####  브라우저 이벤트, 이벤트 객체, 이벤트 핸들러

-   **이벤트, 이벤트 등록**

> HTML 엘리먼트 별로 특정 이벤트가 발생했을 때 특정 행위를 하도록 대상
> 엘리먼트를 찾고 동작을 등록하면 된다.
>
> 이벤트 등록 표준: addEventListener 함수를 사용할 수 있다.  
  
```js
var element = document.querySelector(".outside");
element.addEventListener("click", function(){
    console.log('CLICKED');
});
```
- 마우스 클릭 이벤트 등록  

![]({{site.url}}/assets/images/boost/image64.png)  

> addEventListener 함수의 두 번째 인자의 함수는 이벤트가 발생할 때
> 실행되는 함수로 이벤트핸들러, 이벤트리스너라고 한다.

#### AJAX (Asynchronous Javascript And Xml: 비동기식 자바스크립트와 xml)통신의 이해

1)  **Ajax(Asynchronous Javascript And Xml)**

    -   브라우저의 XMLHttpRequest 객체를 이용하여 페이지의 일부 데이터를
        로드하는 기법

    -   HTML과 XHTML, Cascading Style Sheet, JS, DOM, XML, XSLT,
        XMLHttpRequest 객체를 비롯한 여러 기술을 사용하는 새로운 접근법

    -   기술들을 AJAX 모델을 통해 결합하여 웹 어플리케이션을 빠르게 동작
        시킬 수 있다.

    -   **JSON**(JavaScript Object Notation): 비동기 브라우저/서버
        통신을 위한 "키-값"으로 이루어진 데이터 포맷

2)  **AJAX 실행실습**

    -   실습을 위한 간단한 서버 실행용 VScode 확장 프로그램

![]({{site.url}}/assets/images/boost/image65.png)  
- Live Server 설치  
![]({{site.url}}/assets/images/boost/image66.png)  
- Go Live를 클릭하면 실행된다.  
-   Ajax 실행 코드: 같은 디렉토리의 JSON 파일을 읽어온다

```html
<html>
    <head></head>
    <body>
        <div class="outside">outside Element</div>
    </body>
    <script src="test.js"></script>
    <script src="ajax.js"></script>

</html>  
```
- html 에서는 ajax.js를 불러온다.  

```js
var oReq = new XMLHttpRequest();
oReq.addEventListener("load",function(){
    console.log(this.responseText);
});
oReq.open("GET", "./ajax.json");
oReq.send();

{
    "name" : "code777",
    "favorites" : ["code","snow"]
}
```
- JSON 파일  

![]({{site.url}}/assets/images/boost/image67.png)  
- 개발자 도구로 확인해보면 JSON파일의 데이터가 전달된 것을 알 수 있다.  

CHAPTER. 02 JSP(Java Server Page)
---------------------------------

### Point. 01 JSP 라이프사이클

#### JSP 프로젝트 생성

-   JSP는 서블릿으로 변환되어 실행된다.

-   JSP 프로젝트 생성

![]({{site.url}}/assets/images/boost/image68.png)  
- JSP file 생성  

![]({{site.url}}/assets/images/boost/image69.png)  

- 자동으로 생성된 JSP 파일  

![]({{site.url}}/assets/images/boost/image70.png)  

-   스크립트릿(Scriptlet) JSP 페이지에서 자바코드를 실행할 수 있는 코드
    블록  

![]({{site.url}}/assets/images/boost/image71.png)  


> 스크립트릿: `<% ..... %>` 이러한 구조를 가진다.


#### JSP를 Servlet 코드로 변환

-   변환된 코드 경로  

```
%userprofile%\\eclipse-workspace\\.metadata\\.plugins\\org.eclipse.wst.server.core\\tmp0\\work\\Catalina\\localhost\\firstweb\\org\\apache\\jsp
```


-   서블릿으로 변환된 코드  

![]({{site.url}}/assets/images/boost/image72.png)  

![]({{site.url}}/assets/images/boost/image73.png)  

- 변환된 서블릿코드의 Init, Destroy, Service 메소드  


#### JSP의 실행순서

-   브라우저가 웹서버에 JSP에 대한 요청 정보 전달

-   브라우저가 요청한 JSP가 최초로 요청했을 경우

> JSP로 작성된 코드가 서블릿 코드로 변환 (.java 파일 생성)
>
> 서블릿 코드를 컴파일해서 실행가능한 bytecode로 변환 (.class 파일 생성)
>
> 서블릿 클래스를 로딩하고 인스턴스 생성 (모든 절차는 JSP 엔진이 처리)

-   서블릿이 실행되어 요청을 처리하고 응답 정보 생성

#### JSP 라이프싸이클 실습

-   lifecycle.jsp 파일 작성

```jsp

<%@ page language="java" contentType="text/html; charset=EUC-KR"
    pageEncoding="EUC-KR"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="EUC-KR">
<title>Insert title here</title>
</head>
<body>
	Hello
	<%
		System.out.print("jspService()");
	%>
	<%!
	//선언식 
		public void jspInit(){
		System.out.print("jspInit()!");
	}
	%>
	
	<%!
	//선언식 
		public void jspDestroy(){
		System.out.print("jspDestroy()!");
	}
	%>	
</body>
</html>
``` 

![]({{site.url}}/assets/images/boost/image74.png)  

- 선언식을 이용하여 Service메서드 외에 메서드도 작성 할 수 있다. (lifecycle.java 파일)


![]({{site.url}}/assets/images/boost/image75.png)  
- `System.out.print`로 메서드가 호출될 때 콘솔에 출력되어 나온다  

-   다른 메서드를 호출하지 않으면 Service 메서드만 호출된다.

-   선언식을 이용하여 Init Destroy 메서드를 작성하여 각각 최초 실행,
    수정 시 해당 메서드가 호출된다.

-   라이프 사이클

![]({{site.url}}/assets/images/boost/image76.png)  

[https://www.studytonight.com/jsp/lifecycle-of-jsp.php](https://www.studytonight.com/jsp/lifecycle-of-jsp.php){: target="_blank"}


### Point. 02 JSP 문법

#### 스크립트 요소

-   선언문, 스크립트릿, 표현식이라는 스크립트 요소 제공

> 선언문 (Declaration) - `<%! %>` 전역변수 선언, 멤버변수 선언 및 메소드 선언                                                          
>
> 스크립트릿 (Scriptlet) - `<% %>` 프로그래밍 코드 기술
>
> 표현식 (Expression) - `<%= %>` 화면에 출력할 내용 기술


#### 선언문

-   선언문 문법: `<%! %>`

-   선언문 실습  

```jsp
<%@ page language="java" contentType="text/html; charset=EUC-KR"
    pageEncoding="EUC-KR"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="EUC-KR">
<title>Insert title here</title>
</head>
<body>
	id : <%=getId() %>
	<%!
		String id = "U001"; // 멤버변수 선언
		public String getId(){
			return id;
		}
	%>
</body>
</html>
```
![]({{site.url}}/assets/images/boost/image77.png)  

#### 스크립트릿(Scriptlet)

-   스크립트릿: \<% %\>

-   가장 많이 쓰이는 스크립트 요소

-   프로그래밍 로직 기술

-   선언된 변수는 지역변수

-   스크립트릿 실습

```jsp
<%@ page language="java" contentType="text/html; charset=EUC-KR"
    pageEncoding="EUC-KR"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="EUC-KR">
<title>Insert title here</title>
</head>
<body>
	<%
		for(int i = 1; i <=5; i++){
	%>
		<H<%=i %>>한글</H<%=i %>>
	<%
		}
	%>
</body>
</html>
```
> ![]({{site.url}}/assets/images/boost/image78.png)  
>
> 변환된 코드
>
> ![]({{site.url}}/assets/images/boost/image79.png)  
>
> 반복문 응답 결과  


#### 표현식

-   JSP 페이지에 웹 브라우저에 출력할 부분

-   스크립트릿 내에서 출력할 부분은 내장객체 out객체의 print(),
    println() 메소드를 사용해서 출력

#### JSP 사용 주석

-   HTML, 자바, JSP

-   HTML 주석

> 주석 형태: \<!\-- \--\>
>
> 웹에서 서비스할 때 화면에 주석 내용이 표시되지 않는다

-   JSP 주석

> JSP페이지에서만 사용 \<%\-- \--%\>
>
> 웹 브라우저를 통해 출력 결과가 표시 되지만 웹브라우저 소스에서 표시
> 되지않고, JSP 주석 내에 실행코드는 실행되지 않는다.

-   자바주석

> 자바주석: //, /\* \*/
>
> 자바가 서블릿으로 실행할 때에 실행되지 않는다.

### Point. 03 JSP 내장객체

#### 내장객체

-   JSP를 실행하면 서블릿 소스가 생성되고 실행된다.

-   JSP에 입력한 대부분 코드는 서블릿의 `_jspService()` 메소드 안에
    삽입되는 코드로 생성

-   `_jspService()`에 삽입된 코드 위쪽에 미리 선언된 객체들을 jsp에서
    사용 가능하다.

#### 내장객체 종류

![]({{site.url}}/assets/images/boost/image80.png)  

-   내장객체 실습

```java
<%@ page language="java" contentType="text/html; charset=EUC-KR"
    pageEncoding="EUC-KR"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="EUC-KR">
<title>Insert title here</title>
</head>
<body>
	<%
		StringBuffer url = request.getRequestURL();
		out.print("url :" + url.toString());
		out.print("<br>");
	%>
</body>
</html>
```
> ![]({{site.url}}/assets/images/boost/image81.png)  
>
> 내장객체를 사용한 응답결과


### Point. 04 redirect & forward

#### 리다이렉트 (redirect)

-   서버가 클라이언트의 요청에 대해 특정 URL로 이동 요청을 하는 것

-   서버는 클라이언트에게 HTTP 상태코드 302로 응답하고 헤더 Location
    값에 이동할 URL을 추가한다.

-   클라이언트가 서버로부터 상태코드 302를 받으면 헤더의 Location의
    URL로 재요청을 보낸다.

-   서블릿이과 JSP는 HttpServletResponse 클래스의 sendRedirect()
    메소드를 사용한다.

#### 실습코드

-   웹 브라우저가 redirect01.jsp 요청

-   redirect01.jsp 는 redirect02.jsp로 리다이렉팅하는 로직 실행 후 결과
    확인

```jsp
<!-- redirect01.jsp -->
<%@ page language="java" contentType="text/html; charset=EUC-KR"
    pageEncoding="EUC-KR"%>
<%	
	response.sendRedirect("redirect02.jsp");

%>


<!-- redirect02.jsp -->
<%@ page language="java" contentType="text/html; charset=EUC-KR"
    pageEncoding="EUC-KR"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="EUC-KR">
<title>Insert title here</title>
</head>
<body>
	redirect 페이지
	
</body>
</html>
```
![]({{site.url}}/assets/images/boost/image82.png)  

![]({{site.url}}/assets/images/boost/image83.png)  

- 상태코드 302 받으면 URL을 요청한다.  

- 리다이렉트된 URL로 상태코드 200 성공 된 것을 확인 할 수 있다.  

#### forward

-   FrontServlet 파일 생성

-   URL은 front로 매핑, service 메소드만 오버라이드

![]({{site.url}}/assets/images/boost/image84.png)  
![]({{site.url}}/assets/images/boost/image85.png)  


-   NextServlet 파일 생성

-   URL next로 매핑 service 메소드 오버라이딩


-   **실습코드**   

```java  
// FrontServlet.java

int diceVal = (int)(Math.random() *  6) + 1;
request.setAttribute("dice", diceVal);
//dice는 diceVal 객체를 넘겨주기 위한 string (객체의 값을 넘겨줌)
RequestDispatcher requestDispatcher = request.getRequestDispatcher("/next");
//RequestDispatcher 객체의 변수를 얻어내고 request 객체로부터 얻어낸다 인자 값은 이동할 경로
requestDispatcher.forward(request, response);
// RequestDispatcher가 가지고 있는 forward 메서드로 request, response 객체를 넘긴다
```  

```java
// NextServlet.java

response.setContentType("text/html");
PrintWriter out = response.getWriter();
out.println("<html>");
out.println("<head><title>form</title></head>");
out.println("<body>");

int dice = (Integer)request.getAttribute("dice");
out.println("dice : " + dice);
//setAttribute로 전달된 dice 오브젝트를 getAttribute로 받고 dice 오브젝트 값을 integer로 형 변환 한다.
    for(int i = 0; i < dice; i++) {
            out.print("<br>hello");
        }
out.println("</body>");
out.println("</html>");
		
```
-   실행결과

![]({{site.url}}/assets/images/boost/image86.png)  


### Point. 05 Servlet과 JSP 연동

#### Servlet & JSP

-   서블릿은 자바 파일이기 때문에 프로그램 로직이 수행되기에 유리하다.

-   JSP는 브라우저에 결과를 출력하기에 서블릿보다 유리하다.

-   서블릿과에서 프로그램 로직을 수행하고 JSP에게 포워딩하는 방법을
    사용한다.

#### 실습코드

-   실습코드의 동작

![]({{site.url}}/assets/images/boost/image87.png)  

- jsp파일이 reponse 객체에 응답결과를 담아서 클라이언트에 전달한다.  

-   LogicServlet.java

```java
	protected void service(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		int v1 = (int)(Math.random() * 100) + 1;
		int v2 = (int)(Math.random() * 100) + 1;
		int result = v1 + v2;
		
		request.setAttribute("v1", v1);
		request.setAttribute("v2", v2);
		request.setAttribute("result", result);
		
		RequestDispatcher rd =request.getRequestDispatcher("/result.jsp");
		rd.forward(request, response);
	}
```

-   result.jsp

```jsp

<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
</head>
<body>
	Java코드<br>
	<%
		int v1 = (int)request.getAttribute("v1");
		int v2 = (int)request.getAttribute("v2");
		int result = (int)request.getAttribute("result");
	%>
	
	<%=v1 %> + <%=v2 %> = <%=result %><br>
	
	EL표기법<br>
	${v1 } + ${v2 } = ${result }
</body>
</html>
```
- 자바코드를 줄이기 위해서 EL표기법이나 JSTL을 사용한다.  

-   실행결과

![]({{site.url}}/assets/images/boost/image88.png)  


### Point. 06 Scope

#### Scope 종류

-   Application Scope: 웹 어플리케이션이 시작되고 종료될 때까지 변수가
    유지되는 경우 사용한다.

-   Session: 웹 브라우저 별로 변수가 관리되는 경우 사용한다.

-   Request: HTTP request를 WAS가 받아서 웹 브라우저에게 response 할
    때까지 변수가 유지되는 경우 사용한다.

-   page: 페이지 내에서 지역변수처럼 사용한다.

#### Page Scope

-   PageContext 추상 클래스를 사용한다.

![]({{site.url}}/assets/images/boost/image89.png)
- pageContext 내장 객체  

-   JSP 페이지에서 pageContext라는 내장 객체로 사용가능

-   forward가 될 경우 Page scope에 지정된 변수 사용불가

-   사용방법은 다른 scoperemf과 동일하다.

-   지역변수처럼 사용된다.

-   JSP에서 pageScope에 값을 저장한 후 해당 값을 EL표기법 등에서 사용

-   JSP나 서블릿이 실행되는 동안에만 정보 유지

#### request Scope

-   http 요청을 WAS가 받아서 웹 브라우저에게 응답할 때까지 변수값을
    유지하고자 할 경우 사용한다.

-   서블릿에서 HttpServletRequest 객체를 사용하고 JSP에서는 request 내장
    변수 사용

-   값 저장에는 request 객체의 setAttribute() 메소드 사용

-   값을 읽어 들일 때에는 request 객체의 getAttribute() 메소드 사용

-   forward시 값을 유지하고자 사용한다.

![]({{site.url}}/assets/images/boost/image90.png)
- Request scope 예시  

#### Session scope

-   웹 브라우저별 변수를 관리 할 경우 사용한다.

-   웹 브라우저의 탭들은 세션정보가 공유된다.

-   HttpSession 인터페이스를 구현한 객체를 사용한다.

-   JSP 에서는 session 내장 변수 사용

-   서블릿에서는 HttpServletRequest의 getSession()메소드를 이용하여
    session 객체를 얻는다.

-   값 저장할 때: session.setAttribute()

-   값을 읽을 때: session.getAttribute()

-   사용자별로 정보가 유지되어야 할 때 사용한다. (ex. 장바구니)

![]({{site.url}}/assets/images/boost/image91.png)
- session 객체 선언 부분

#### Application Scope

1)  **Application scope 정리**

-   웹 어플리케이션이 시작되고 종료될 때까지 변수를 사용할 수 있다.

-   원하는 값들을 저장해놓고 사용하는 것

-   ServletContext 인터페이스를 구현한 객체 사용

-   JSP에서는 application 내장 객체를 이용한다.

-   서블릿의 getServletContext() 메소드를 이용하여 application 객체
        이용

-   웹 어플리케이션 하나당 하나의 application 객체가 사용된다.

-   값 저장: application 객체의 setAttribute() 메소드

-   값 읽기: application 객체의 getAttribute() 메소드

-   모든 클라이언트가 동통으로 사용해야 할 값들이 있을 때 사용한다.

2)  **실습코드**

-   **ApplicationScope01.java**

```java
protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
	response.setContentType("text/html; charset=utf-8");
	PrintWriter out = response.getWriter();
	
	ServletContext application = getServletContext();
	
	int value = 1;
	application.setAttribute("value", value);
	
	out.print("<h1>value : " + value + "</h1>");
}
```

-   **ApplicationScope02.java**

```java
protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
	response.setContentType("text/html; charset=utf-8");
	
	PrintWriter out = response.getWriter();
	
	try {
		ServletContext application = getServletContext();
		int value = (int)application.getAttribute("value");
		value++;
		application.setAttribute("value", value);
		
		out.print("<h1>" + value + "</h1>");
	}catch (NullPointerException e) {
		out.print("value의 값이 설정되지 않았습니다");
	} 
}
```
-   **ApplicationScope.jsp**

```jsp
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
</head>
<body>
	<%
		try {
			int value = (int)application.getAttribute("value");
			value = value + 2;
			application.setAttribute("value", value);
	%>
			<h1><%=value %></h1>
	<%
		}catch(NullPointerException ex){			
	%>
			<h1>설정된 값이 없습니다.</h1>
	<%
		}
	%>			
</body>
</html>
```

3)  **실행결과**

-   **서블릿의 value가 null이기 때문에 jsp를 실행하면 예외처리가 된다**

![]({{site.url}}/assets/images/boost/image92.png)  


-   **서블릿을 실행하여 변수에 값을 넣는다**

![]({{site.url}}/assets/images/boost/image93.png)  


-   **두번째 서블릿 실행**

![]({{site.url}}/assets/images/boost/image94.png)  

-   **application scope 예제 결과**

![]({{site.url}}/assets/images/boost/image95.png)  

- **다른 브라우저에서도 웹 어플리케이션이 종료되기 전까지 정보를 유지한다.**

![]({{site.url}}/assets/images/boost/image96.png)  

-   **서버를 중지 후 jsp를 다시 실행하면 변수가 초기화 된 것을 확인**

![]({{site.url}}/assets/images/boost/image97.png)  

### Point. 07 EL(Expression Language)

#### 표현언어 기능

-   JSP 기본문법을 보완하는 역할

-   JSP 스코프(Scope)에 맞는 속성 사용

-   집합 객체(컬렉션,프레임워크에서 제공하는 객체)에 대한 접근 방법 제공

-   변수의 수치 연산, 관계 연산, 논리 연산자 제공

-   자바클래스 메소드 호출 기능

-   EL 기본 객체 제공

-   비활성화 방법: \<%@ page isELIgnored = "true" %\>를 JSP에 명시

#### EL 표현방법

-   \${ }

-   기본객체 사용 예시

![]({{site.url}}/assets/images/boost/image98.png)  
![]({{site.url}}/assets/images/boost/image99.png)  
- EL 기본객체

#### EL 객체 접근

-   문법 \${expr1.expr2}

-   expr1 또는 expr2가 NULL이면 NULL을 반환

-   expr1이 Map일 경유 expr2를 key로 한 값을 반환

-   expr1이 List나 배열 일 경우 expr2에 해당하는 인덱스의 값을 반환,
    정수가 아닐경우 에러

-   expr1이 객체일 경우 expr2에 해당하는 getter메소드에 해당하는
    메소드를 호출한 결과 반환

#### EL 실습

![]({{site.url}}/assets/images/boost/image100.png)  

![]({{site.url}}/assets/images/boost/image101.png)  

![]({{site.url}}/assets/images/boost/image102.png)  

`<%@ page isELIgnored = "true" %>`를 jsp에 작성하면 EL을 무시하게 된다  

### Point. 08 JSTL (JSP Standard Tag Library)

#### JSTL?

-   JSP페이지에서 조건문, 반복문 처리 등을 HTML태그 형태로 작성할 수
    있도록 한다.

-   태그 형식으로 로직을 수행할 수 있도록 도와준다.

-   JSTL 사용을 위한 태그 라이브러리 Impl, Spec, EL 다운로드  

    [https://tomcat.apache.org/download-taglibs.cgi](https://tomcat.apache.org/download-taglibs.cgi){: target="_blank"}
-   프로젝트의 WEB-INF\\lib에 위치 시킨다.

![]({{site.url}}/assets/images/boost/image103.png)  
![]({{site.url}}/assets/images/boost/image104.png)  
![]({{site.url}}/assets/images/boost/image105.png)  

#### JSTL 태그 종류

-   코어 (접두어 c)

> 변수지원, 흐름제어, URL 처리

-   XML (접두어 x)

> XML코어, 흐름 제어, XML 변환

-   국제화 (접두어 fmt)

> 지역, 메시지 형식, 숫자 및 날짜 형식

-   데이터베이스 (접두어 sql)

-   함수

> 콜렉션처리, String 처리

-   코어태그: 변수 지원태그 - 프로퍼티, 맵의 처리

> (프로퍼티: 객체의 값을 변경하거나 값을 읽어들이기 위한 getter, setter 메서드 역할)
