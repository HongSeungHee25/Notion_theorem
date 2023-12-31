# 프로시저 
+ PL/SQL : Procedure(절차,순서) Language , 기존의 단순한 SQL이 확장된 언어(SQL로 만드는 프로그램)
+ 변수,제어문(if,반복문)을 사용하여 프로그래밍언어와 같이 sql 실행의 흐름을 제어
----------
+ 선언부(DECLARE), 실행부(BEGIN), 예외처리부 (EXCEPTION)로 구성됨
+ 1. Anonymous PL/SQL Block(익명블록) 
    + 익명 블록은 주로 일회성으로 사용할 경우 많이 사용됩니다.
+ 2. Stored PL/SQL Block 
    + 저장된 블록은 서버에 파싱해서 저장해 놓고 주기적으로 반복해서 사용할 경우 사용됩니다. 서브프로그램 또는 프로그램 단위라고도 하며,스키마를 구성하는 오브젝트로서 파싱 된 후 오라클 서버 내부에 저장되거나 오라클 툴 안에 라이브러리 형태로 저장되어 있습니다.

----------------

## 프로시저 예시 코드 해석
    DECLARE 								    --변수선언부
	    --vname VARCHAR2(40);				            --스킬라변수
	    --vage NUMBER(3,0);
	    vname tbl_custom.name %TYPE;	                	    --참조변수(타입변수)
	    vage tbl_custom.age %TYPE;		
    BEGIN								    --프로시저 시작(실행부)
	    --프로시저 내부에는 주로 DML 명령문들을 작성.(함께 실행해야할 에러 SQL : 트랜잭션)
	    SELECT name,age
	    INTO vname, vage						    --프로시저 구문 : 검색결과를 프로시저 일반 변수 vname,vage 에 저장
	    FROM "TBL_CUSTOM" tc
	    WHERE CUSTOM_ID = 'twice';					    --1개 행만 결과 조회되는 조건
									    -- 여러개 행 조회될때는 다른 cursor 필요.

	-- DBMS_OUTPUT 는 콘솔에 출력하는 오라클 패키지의 하나이며 PUT_LINE 함수
	    DBMS_OUTPUT.PUT_LINE('고객이름 : ' || vname);	--|| 는 문자열 연결 연산
	    DBMS_OUTPUT.PUT_LINE('고객나이 : ' || vage);
	    EXCEPTION
	    WHEN no_data_found THEN 					    -- no_data_found : 예외 이름
		    DBMS_OUTPUT.PUT_LINE('찾는 데이터가 없습니다.');
    END;

---------------
## 인자와 리턴을 주는 형식. 저장프로시저 코드 해석
    CREATE OR REPLACE PROCEDURE search_custom(		    		--프로시저 이름 설정
	    c_id IN tbl_custom.CUSTOM_ID %TYPE 	            		--매개변수 IN
    )
    IS 
	    --참조 변수 선언
	    vname tbl_custom.NAME %TYPE 		                --저장된 테이블의 컬럼과 동일형식의 변수
	    vage tbl_custom.AGE %TYPE 
    BEGIN 
	    SELECT name,age
		    INTO vname, vage
	    FROM tbl_custom tc
	    WHERE custom_id = c_id;				            
        -- 1개 행만 결과 조회되는 조건. 매개변수로 전달된 값으로 조건 실행

	    DBMS_OUTPUT.PUT_LINE('고객이름 : ' || vname);	 	--|| 는 문자열 연결 연산
	    DBMS_OUTPUT.PUT_LINE('고객나이 : ' || vage);
	    EXCEPTION
	    WHEN no_data_found THEN 					-- no_data_found : 예외 이름
		    DBMS_OUTPUT.PUT_LINE('찾는 데이터가 없습니다.');
    END;

--------------

## 만들어진 저장 프로시저 실행하는 코드
    BEGIN
	    search_custom('twice');         
        -- search_custom 프로시저에 c_id 가 twice 인 고객이름과 고객나이 출력
    END;

------------

## 구매 수량이 최대값인 사용자의 이름,나이를 출력하기 
### 매개변수가 IN (입력값) 이 있고, OUT (출력,리턴) 은 없습니다.
    CREATE OR REPLACE PROCEDURE max_custom(
	    c_name OUT tbl_custom.NAME %TYPE,	            		-- 출력(리턴) 매개 변수
	    c_age OUT tbl_custom.AGE %TYPE
    )		    --프로시저 이름 설정
    IS 
	    --참조 변수 선언
	    maxval number(5); 
	    cid tbl_custom.custom_id %TYPE;
    --	vname tbl_custom.name %TYPE;	                		--참조변수(타입변수)
    --	vage tbl_custom.age %TYPE;
    BEGIN 
	    SELECT max(qty)
		    INTO maxval
	    FROM tbl_buy tb;
	    SELECT customid		
		    INTO cid
	    FROM tbl_buy
	    WHERE qty = maxval;
	    SELECT name,age
		    INTO c_name,c_age
	    FROM tbl_custom tc
	    WHERE custom_id = cid;
	    DBMS_OUTPUT.PUT_LINE('고객이름 : ' || c_name);	         --|| 는 문자열 연결 연산
	    DBMS_OUTPUT.PUT_LINE('고객나이 : ' || c_age);
	    EXCEPTION
	    WHEN no_data_found THEN 					 -- no_data_found : 예외 이름
		    DBMS_OUTPUT.PUT_LINE('찾는 데이터가 없습니다.');
    END;

--------------
 ## OUT(출력) 매개변수가 있는 프로시저 실행하는 형식
    DECLARE 
	    vname tbl_custom.name %TYPE;
	    vage tbl_custom.age %TYPE;
    BEGIN 
	    max_custom(vname,vage);					-- vname, vage 은 OUT 매개변수 값을 받을 실제 변수입니다.
	    DBMS_OUTPUT.PUT_LINE('*고객 이름 : ' || vname);
	    DBMS_OUTPUT.PUT_LINE('*고객 나이 : ' || vage);
    END;

------------

## 프로시저 삭제 코드
    DROP PROCEDURE search_custom;

-------------
## 생성한 max_custom 프로시저 JDBC 에서 실행 코드
	Connection conn = OracleUtility.getConnection();
		String sql = "{ call max_custom(?,?) }";	-> 저장 프로시저 max_custom 호출 sql. {} 안에서 호출하기
			try(
				CallableStatement cstmt = conn.prepareCall(sql);	
				┗> prepareCall는 저장프로시저 실행하지 위한 객체 생성 메소드
					) {
				*참고 : IN 매개변수가 있으면 cstmt.setXXXX() 메소드로 값을 줍니다.
				
				
				cstmt.registerOutParameter(1, Types.VARCHAR);	-> 매개변수 인덱스, 오라클 데이터 타입 지정
				cstmt.registerOutParameter(2, Types.NUMERIC);
				cstmt.executeUpdate();	-> 실행
				
				System.out.println("가장 많은 구매 수량으로 제품을 구입한 고객 정보");
				System.out.println("고객 성명 : "+cstmt.getString(1));		-> 프로시저 출력값 첫번째 가져오기
				System.out.println("고객 나이 : "+cstmt.getInt(2));			-> 프로시저 출력값 두번째 가져오기
				
			} catch (SQLException e) {
				System.out.println("프로시저 실행 오류 : "+e.getMessage());
			}
			
	┗> 실행 결과 : 가장 많은 구매 수량으로 제품을 구입한 고객 정보
				  고객 성명 : 김미나
				  고객 나이 : 20