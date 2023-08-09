# JSTL 이란?
: JSTL(JavaServer Pages Standard Tag Library)은 JSP에서 자주 사용되는 작업을 더 편리하게 수행하기 위한 태그 라이브러리입니다. JSTL은 JSP 페이지 내에서 태그 형태로 작성되며, 자바 코드보다 간결하고 가독성이 높은 코드 작성을 도와줍니다. 주로 데이터 처리, 제어문, 반복문 등을 처리하는 데 사용됩니다.

# JSTL 태그 종류
1. Core Tags (코어 태그)
    + 일반 프로그래밍에서 제공하는 것과 유사한 변수선언
    + 실행 흐름의 제어 기능을 제공
    + 페이지 이동 기술 제공
    + URL : http://java.sun.com/jsp/jstl/core
    + 주요 기능 : 변수 출력, 조건문(if-else), 반복문(for-each) 등
    + ex) <c:out>, <c:if>, <c:forEach>
2. Formatting Tags (포맷팅 태그)
    + 국제화, 다국어 지원 기능 제공
    + URL : http://java.sun.com/jsp/jstl/fmt
    + 주요 기능 : 날짜, 시간, 숫자 등의 데이터 형식을 포맷팅
    + ex) <fmt:formatDate>, <fmt:formatNumber>
3. SQL Tags (SQL 태그)
    + DB의 데이터를 입력/수정/삭제/조회 하는 기능을 제공
    + URL : http://java.sun.com/jsp/jstl/sql
    + 주요 기능 : 데이터베이스 작업을 위한 태그 제공
    + ex) <sql:setDataSource>, <sql:update>
4. XML Tags (XML 태그)
    + URL : http://java.sun.com/jsp/jstl/xml
    + 주요 기능 : XML 데이터 처리를 위한 태그 제공
    + ex) <x:parse>, <x:forEach>
5. Functions Tags (함수 태그)
    + URL : http://java.sun.com/jsp/jstl/functions
    + 주요 기능 : 문자열 조작 및 변환 함수 제공
    + ex) <fn:length>, <fn:substring>

# JSTL의 Core Library
: JSTL(Core Library)은 JSP(JavaServer Pages) 개발을 더욱 편리하게 만들기 위해 제공되는 핵심 라이브러리입니다. JSTL 코어 라이브러리는 변수 출력, 조건문, 반복문 등을 처리하는 데 도움이 되는 태그들을 제공하며, 이를 사용하면 JSP 페이지의 코드를 간결하게 작성할 수 있습니다.

## JSTL Core 라이브러리 주요 기능
1. **변수 출력 및 값 처리** : ${expression} 형식으로 변수나 EL(Expression Language)을 사용하여 데이터를 출력하거나 계산합니다.
2. **조건문 (if-else)** : <c:if> 태그를 사용하여 조건식에 따라 다른 동작을 수행할 수 있습니다.
3. **반복문 (for-each)** : <c:forEach> 태그를 사용하여 배열, 리스트, 맵 등의 데이터를 순회하며 반복 작업을 수행할 수 있습니다.
4. **세션/요청 속성 설정 및 가져오기** : <c:set>, <c:get> 태그를 사용하여 세션 또는 요청 속성에 데이터를 설정하거나 가져올 수 있습니다.
5. **변수 범위(scope) 설정** : <c:set> 태그를 사용하여 변수의 스코프를 설정할 수 있습니다.
6. **URL 생성** : <c:url> 태그를 사용하여 상대 경로나 절대 경로의 URL을 생성할 수 있습니다.
7. **선택 옵션 생성** : <c:choose>, <c:when>, <c:otherwise> 태그를 사용하여 다중 조건을 처리하고 선택 옵션을 생성할 수 있습니다.

## 대표적인 JSTL Core 태그
+ **<c:out>** : 변수 값을 출력하는 태그로, HTML이나 XML에서 사용할 수 있는 문자열을 이스케이프하여 출력합니다.

        <c:out value='출력할 값' default='value가 null값일 경우 출력할 값' />

+ **<c:if>** : 조건문을 처리하는 태그로, 조건식에 따라 다른 동작을 수행합니다.

        <c:if test='조건식' var='조건을 검사하고 return되는 boolean값을 저장할 변수' scope='boolean 변수가 사용될 범위' />

+ **<c:forEach>** : 반복문을 처리하는 태그로, 배열이나 컬렉션 데이터를 반복하여 처리합니다.

        <c:foreach begin='시작값' end='끝값' step='증가값' var='count값이 저장될 변수' />
        <c:foreach var='변수' items='배열 or 컬렉션' />

    - status.index : 0부터 시작하는 루프의 인덱스 입니다.
    - status.count : 현재 몇번째 루프인지 값입니다. 1부터 시작합니다.
    - status.current : 현재 아이템입니다. var 속성의 값과 같습니다.
    - status.first : 현재가 첫번째 루프이면 참입니다.
    - status.last : 현재가 마지막 루프이면 참입니다.
    - status.begin : begin  속성을 사용했을 경우 그 값이 나옵니다.
    - status.end : end 속성을 사용했을 경우 그 값이 나옵니다.
    - status.step :  step 속성을 사용했을 경우 그 값이 나옵니다.

+ **<c:set>** : 변수 값을 설정하는 태그로, 세션 속성이나 요청 속성에 데이터를 저장합니다.

        <c:set var='변수' value='속성에 설정할 값 or EL 표현식' scope='기본값은 page' />

+ **<c:forTokens>** : 

        <c:forTokens items='배열 or 컬렉션' delims='구분자' var='변수' begin='시작값' end='끝값' step='증가값' />

+ **<c:url>** : URL을 생성하는 태그로, 상대 경로나 절대 경로의 URL을 생성합니다.

        <c:url value="URL 경로" />

+ **<c:choose>, <c:when>, <c:otherwise>** : 다중 조건문을 처리하는 태그로, 여러 개의 조건 중 하나를 선택하여 처리합니다.

        <c:choose>
            <c:when test='조건식1'>
                 <p>Welcome, Admin!</p>
            </c:when>
            <c:when test='조건식2'>
                <p>Welcome, User!</p>
            </c:when>
            <c:otherwise>   <-- 기본 동작 -->
                <p>Welcome, Guest!</p>
            </c:otherwise>
        </c:choose>


## JSTL 비교 연산자
+ **eq(==) - 같음** : 문자열 또는 숫자가 같으면 true, null 또는 빈 문자열 인지 확인할 수 있음.
+ **ne(!=) - 같지 않음** : 문자열 또는 숫자가 다르면 true
+ **lt(<) - 작음** : 왼쪽 연산자가 오른쪽 연산자보다 작으면 true
+ **le(<=) - 작거나 같음** : 왼쪽 연산자가 오른쪽 연산자보다 작거나 같으면 true
+ **gt(>) - 큼** : 왼쪽 연산자가 오른쪽 연산자보다 크면 true
+ **ge(>=) - 크거나 같음** : 왼쪽 연산자가 오른쪽 연산자보다 크거나 같으면 true
+ **empty - 비어있음 확인 여부** : 변수, 컬렉션, 문자열이 비어있으면 true, 비어있지 않으면 false
+ **not empty - 비어있지 않은지 확인 여부** : 변수, 컬렉션, 문자열이 비어있지 않으면 true, 비어있으면 false
