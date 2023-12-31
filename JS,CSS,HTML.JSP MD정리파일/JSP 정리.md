# JSP 란? 
: JSP(JavaServer Pages)는 서버 측에서 동적 웹 페이지를 생성하는 데 사용되는 Java 기반의 웹 프로그래밍 기술입니다. JSP는 HTML 코드에 Java 코드를 삽입하여 웹 페이지를 생성하고, 웹 애플리케이션의 비즈니스 로직과 데이터 처리를 처리하는 데 사용됩니다. 

1. **동적 웹 페이지 생성** : JSP는 동적으로 웹 페이지를 생성할 수 있습니다. 서버에서 실행되는 Java 코드와 클라이언트로 전송되는 HTML 코드가 결합되어 최종 웹 페이지가 생성됩니다.
2. **HTML 코드에 Java 코드 삽입** : JSP 파일(.jsp)은 일반적인 HTML 코드와 Java 코드를 포함할 수 있습니다. Java 코드는 <% %> 태그 내에 삽입하며, 이를 통해 동적으로 웹 페이지를 생성하는 로직을 구현할 수 있습니다.
3. **서블릿으로 변환** : JSP 파일은 서블릿으로 변환되어 웹 애플리케이션의 서블릿 컨테이너(예: Apache Tomcat)에서 실행됩니다. 서블릿으로 변환되는 과정에서 JSP 내의 Java 코드가 서블릿 클래스로 컴파일됩니다.
4. **내장 객체** : JSP에는 JSP 컨테이너가 제공하는 여러 내장 객체들이 있습니다. 예를 들어, request, response, session, application과 같은 객체들은 JSP에서 직접 사용할 수 있으며, 웹 애플리케이션의 데이터를 처리하는 데 유용합니다.
5. **태그 라이브러리** : JSP는 커스텀 태그를 사용할 수 있는 태그 라이브러리를 제공합니다. JSP 페이지 내에서 태그를 사용하여 자주 사용되는 로직을 추상화하고 재사용할 수 있습니다.
6. **MVC 패턴** : 일반적으로 JSP는 웹 애플리케이션의 뷰(View) 역할을 담당하고, 비즈니스 로직은 서블릿(Controller)에서 처리하는 것이 일반적인 웹 애플리케이션의 MVC (Model-View-Controller) 패턴을 따릅니다.
7. **태그 라이브러리와 커스텀 태그** : JSP에서는 <jsp:useBean>, <jsp:setProperty>, <jsp:getProperty> 등의 JSP 내장 태그를 활용하여 JavaBeans와 상호작용할 수 있습니다. 또한, 개발자가 직접 커스텀 태그를 만들어서 JSP에서 자신만의 태그를 정의하여 재사용성과 가독성을 높일 수 있습니다.
8. **안전성 고려** : JSP 코드에는 보안상 주의가 필요합니다. 입력값 검증, 인증과 권한 부여 등에 대한 처리를 신중하게 해야합니다.

# JSP 태그 
+ **스크립트릿 태그<% %>** : Java 코드를 포함하고자 할 때 사용. 서버 측 로직을 구현하는 데 사용.
+ **표현식 <%= %>** : Java 코드의 결과 값을 출력할 때 사용. 결과 값은 문자열로 변환되어 HTML 출력에 포함.
+ **선언<%! %>** : 메서드나 변수를 선언할 때 사용. 주로 메서드를 정의하는 데 활용.

|문법명|형식|설명|
|------|---|---|
|주석문|<%-- --%>|1줄 주석문은 없다.<br>html주석문 < !-- --> 도 사용가능하다.|
|page 지시문|<%@ %>|인코딩 클래스 가져 오기, 세션 관리 등 JSP 프로그램 전체의 동작에<br>관한 정의합니다.<br><br>예시) <@page 속성 명 = "속성 값" 속성 명="속성 값"...%>|
|선언부|<%! %>|전역변수, class, function를 선언하는 영역이다.<br>변수, 메소드 선언시 반드시; (세미콜론)가 필요합니다.<br>선언에서 선언 된 변수, 메소드는 처음 요청이있을 때 한 번만 호출됩니다.<br>따라서 계속되는 요구에도 변수의 값은 초기화되지 않고, JSP 컨테이너(Tomcat 등)를<br>다시 시작할 때까지 값이 유지됩니다.<br>위치는 관계없지만 대부분 문서 윗쪽에 작성한다.|
|scriptlet|<% %>|실제 코드들이 들어가있는 부분이다.( == 코드부)<br>스크립틀릿은 JSP 태그에서는 표현할 수없는 작업을 Java 코드를 작성하고 자유로운<br>작업을 수행하는 경우에 사용합니다. <br>Java 코드를위한 각 코드에는 반드시; (세미콜론)가 필요합니다.<br>scriptlet에서 선언 된 변수는 요청 때마다 호출됩니다. <br>따라서 그 요청이 있을 때마다 변수의 값이 초기화됩니다.|
|표현식|<%= %>|Java 코드를 작성하고 그 결과를 표시합니다. <br>따라서 실행 결과를 반환 코드 밖에 기술할 수는 없습니다. <br>실행 결과를 리턴하지 void 메소드나 변수의 선언만 식으로 설명 할 수 없습니다. <br>표현식에서는 ; (세미콜론)을 작성하지 않습니다.|

***참고 파일 : jspEx.jsp***