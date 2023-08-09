+ **< jsp:useBean >** : 자바 인스턴스를 준비한다. 보관소에서 자바 인스턴스를 꺼내거나 자바 인스턴스를 새로 만들어 보관소에 저장하는 코드를 생성한다. 자바 인스턴스를 자바 빈(Java Bean)이라고 부른다.
+ **< jsp:setProperty >** : 자바 빈의 프로퍼티 값을 설정한다.자바 객체의 setter()를 호출하는 코드를 생성한다.
+ **< jsp:getProperty >** : 자바 빈의 프로퍼티 값을 꺼낸다.자바 객체의 getter()를 호출하는 코두를 생성한다.
+ **< jsp:include >** : 정적(HTML, 텍스트 파일 등) 또는 동적(서블릿/JSP) 자원을 including하는 자바 코드를 생성한다.
+ **< jsp:forward >** : 현재 페이지의 실행을 멈추고 다른 정적, 동적 자원으로 forwarding하는 자바 코드를 생성한다. 
+ **< jsp:param >** : 	jsp:include, jsp:forard, jsp:params의 자식 태그로 사용한다.ServletRequest 객체에 매개변수를 추가하는 코드를 생성한다.
+ **< jsp:plugin >** : OBJECT 또는 EMBED HTML 태그를 생성한다.
+ **< jsp:element >** : 임의의 XML 태그나 HTML 태그를 생성한다.

# jsp:useBean 
: 이 액션은 자바빈(JavaBean)이라고 불리는 자바 객체를 생성하거나 가져와서 현재 페이지나 원하는 범위(page, request, session, application)에 변수로 저장합니다. 만약 해당 자바빈이 이미 존재한다면 가져오고, 존재하지 않는 경우 새로운 인스턴스를 생성합니다. class 속성은 생성할 자바빈의 클래스를 지정합니다.
+ **id** : 생성될 자바빈 객체(인스턴스) 이름을 명시
+ **class** : 객체가 생성될 자바빈 클래스를 기술(패키지명을 포함한 자바클래스)
+ **scope** : 자바빈 객체의 유효 범위로 자바빈 객체가 공유되는 범위 지정.<br>생략 시 default : page (page, request, session, application)

         ex) <jsp:useBean id="dto" class="sample.DTO.MemberDTO"/>

# jsp:setProperty
: 이 액션은 자바빈의 속성값을 설정합니다. 지정된 자바빈의 속성에 해당하는 값을 요청 파라미터 또는 다른 값으로 설정합니다. name 속성은 속성값을 설정할 자바빈의 이름을 지정하고, property 속성은 설정할 속성의 이름을 지정합니다.
+ **name** : 자바빈 객체의 이름 명시 (필수)
+ **property** : property 명을 기술 (필수)
+ **value** : property에 저장할 값을 기술

        ex) <jsp:setProperty property="*" name="dto"/>

# jsp:getProperty
: 이 액션은 자바빈에서 속성값을 가져와서 화면에 출력합니다. 지정된 자바빈의 속성값을 가져와서 JSP 결과에 포함시킵니다. name 속성은 속성값을 가져올 자바빈의 이름을 지정하고, property 속성은 가져올 속성의 이름을 지정합니다.
+ **name** : 자바빈 객체의 이름 명시 (필수)
+ **property** : property 명 기술 (필수)

        ex) <jsp:getProperty property="custno" name="dto"/><br>
            <jsp:getProperty property="custname" name="dto"/><br>
            <jsp:getProperty property="phone" name="dto"/><br>
            <jsp:getProperty property="address" name="dto"/><br>
            <jsp:getProperty property="grade" name="dto"/><br>
            <jsp:getProperty property="city" name="dto"/><br>

# jsp:include
: 이 액션은 다른 JSP나 정적 리소스(HTML, 텍스트 등)의 내용을 현재 JSP 페이지에 포함시킵니다. 지정된 JSP나 리소스의 결과가 현재 위치에 포함되어 출력됩니다. 포함시킬 리소스는 상대 경로나 절대 경로를 사용할 수 있습니다.

    ex) <jsp:include page="7top.jsp">
        <jsp:include page="8bottom.jsp" />

# jsp:forward
: 이 액션은 현재 요청을 다른 JSP나 서블릿으로 전달합니다. 현재 페이지의 처리를 중단하고 지정된 JSP나 서블릿으로 제어를 넘깁니다. 브라우저의 URL은 변경되지 않으며, 전달된 페이지의 결과가 원래 요청에 반환됩니다.

    ex) <jsp:forward page="anotherPage.jsp"/>

# jsp:param
: 이 액션은 < jsp:include > 또는 < jsp:forward >와 함께 파라미터(이름-값 쌍)를 전달하는 데 사용됩니다. 목적 페이지나 리소스로 추가 데이터를 전달하는 데에 사용됩니다.

    ex) <jsp:include page="7top.jsp">
	        <jsp:param value="kim" name="username"/>
        </jsp:include>

# jsp:plugin
: 이 액션은 브라우저 특정 플러그인(애플릿, 플래시 콘텐츠 등)을 표시하기 위해 < object > 또는 < embed > HTML 태그를 생성합니다.

    ex) <jsp:plugin type="applet" code="AppletClass.class" codebase="/applets/">
            <!-- 애플릿에 대한 추가 매개변수들 -->
        </jsp:plugin>

# jsp:element
: 이 액션은 임의의 XML 또는 HTML 태그를 동적으로 생성할 수 있습니다. 조건에 따라 런타임에 태그를 생성하는 데 사용됩니다.

    ex) <jsp:element name="div">
            <!-- 동적으로 생성된 <div> 태그의 내용 -->
        </jsp:element>
