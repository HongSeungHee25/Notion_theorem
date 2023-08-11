# JSP Mybatis 란?
: MyBatis는 Java 기반의 오픈 소스 SQL 매핑 프레임워크로서, 데이터베이스와 상호 작용하는 애플리케이션을 개발하기 위해 사용되는 도구이다. MyBatis는 SQL 쿼리와 Java 객체 간의 매핑을 관리하고, 데이터베이스와의 효율적인 상호 작용을 도와준다.

# ORM 이란? 
: ORM은 "Object-Relational Mapping"의 약자로, 객체와 관계형 데이터베이스 간의 데이터 변환과 상호 작용을 추상화하는 프로그래밍 기술 및 패러다임을 나타낸다. ORM은 객체 지향 프로그래밍 언어와 관계형 데이터베이스 간의 간격을 줄이고, 개발자가 객체를 사용하여 데이터베이스와 상호 작용할 수 있도록 돕는 목적으로 개발되었다.

# ORM 주요 기능
1. **객체와 테이블 매핑** : ORM은 객체와 관계형 데이터베이스 테이블 간의 매핑을 정의합니다. 클래스와 테이블 간의 속성과 관계를 정의하여 데이터를 변환하고 동기화합니다.
2. **CRUD 작업 간소화** : ORM은 데이터베이스에서의 생성(Create), 읽기(Read), 갱신(Update), 삭제(Delete) 작업을 객체 지향적인 방식으로 처리할 수 있도록 돕습니다.
3. **객체 간 관계 처리** : 객체 간의 관계를 효율적으로 관리하고 조작할 수 있는 기능을 제공합니다. 예를 들어, 일대다, 다대다 관계를 객체로 표현하고 처리할 수 있습니다.
4. **데이터베이스 독립성** : ORM은 데이터베이스 시스템에 대한 의존성을 줄여줍니다. 개발자는 ORM을 통해 추상화된 인터페이스를 사용하여 다양한 데이터베이스 시스템과 상호 작용할 수 있습니다.
5. **SQL 자동 생성** : ORM은 개발자가 직접 SQL 쿼리를 작성하지 않고도 필요한 작업을 처리하기 위한 SQL 쿼리를 자동으로 생성합니다.
6. **캐싱 및 성능 최적화** : 일부 ORM 프레임워크는 캐싱과 같은 성능 최적화 기능을 제공하여 데이터베이스 작업의 성능을 향상시킵니다.

# JSP Mybatis 주요 기능
1. **SQL 매핑** : MyBatis는 SQL 쿼리를 별도의 XML 파일이나 어노테이션을 통해 작성하고 관리할 수 있습니다. 이를 통해 쿼리와 Java 객체 간의 매핑을 명확하게 정의할 수 있습니다.
2. **파라미터 매핑** : MyBatis는 SQL 쿼리의 매개변수를 자동으로 매핑하여 데이터베이스와 효율적으로 상호 작용할 수 있도록 지원합니다.
3. **결과 매핑** : 데이터베이스 결과를 Java 객체에 매핑하여 편리하게 사용할 수 있도록 도와줍니다. 이를 통해 복잡한 데이터 변환 로직을 줄일 수 있습니다.
4. **동적 SQL** : 동적인 SQL 쿼리를 생성할 수 있는 기능을 제공하여 조건에 따라 쿼리를 유연하게 조작할 수 있습니다.
5. **캐싱** : MyBatis는 쿼리 결과를 캐시하여 반복적인 쿼리 수행을 최적화할 수 있습니다.
6. **트랜잭션 관리** : MyBatis는 트랜잭션 관리를 지원하여 데이터베이스 작업의 ACID 특성을 보장할 수 있습니다.
7. **다양한 데이터베이스 지원** : MyBatis는 다양한 데이터베이스 시스템과 호환되며, 데이터베이스에 독립적으로 작업할 수 있는 환경을 제공합니다.

# JSP Mybatis 사용법
1. MyBatis 설정 및 환경 설정 : 먼저, 프로젝트에 MyBatis와 관련된 라이브러리를 추가하고, 데이터베이스 연결 정보 및 MyBatis 설정을 작성한다.
    + https://blog.mybatis.org/ 해당 사이트에서 zip 파일 다운로드
    + zip 파일 안에 있는 mybatis-버전-jar 파일을 라이브러리에 추가

2. SQL 매핑 XML 작성 : SQL 쿼리와 그에 대한 매핑을 작성하기 위한 XML 파일을 생성합니다. 이 파일은 SQL 쿼리와 Java 객체 간의 매핑을 정의하는 역할을 합니다.

        <?xml version="1.0" encoding="UTF-8" ?>
        <!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
        <mapper namespace="order"> <!-- namespace 는 다른 mapper가 있을수도 있어서 이름 설정은 해주는게 좋음 -->
        <!-- sql 실행에 필요한 값 또는 조회결과 값 과 자바 객체를 매핑합니다. -->
        <!-- mybatis 는 자동 매핑이에요. 따라서, 컬럼명과 dto, 매개변수 명이 동일해야 합니다.
 	    단, insert 할 때에는 quantity 처럼 정수타입이 1개 일때는 매핑을 해 줄 수 있습니다.  -->
 	    <select id="selectOrderByEmail" resultType="String">
            select 
                distinct email 
            from 
                orders
            </select>
            
            <select id="selectByEmail" resultType="sample.DTO.OrderDTO" parameterType="String">
            select * from 
                orders 
            where email = #{email}
            </select>
            
            <!-- insert,update,delete 는 기본 리턴타입이 int -->
            <insert id="insert" parameterType="sample.DTO.OrderDTO">
            insert into 
                orders 
            values
                (#{email},#{pcode},#{quantity},sysdate)
            </insert>
            <!-- ${} 는 출력, #{} 저장(파라미터 변수명 표시) -->
            
        </mapper>

3. MyBatis 설정 파일 작성 : MyBatis 설정을 위한 XML 파일을 생성하고, 데이터베이스 연결 정보와 SQL 매핑 파일의 경로 등을 설정합니다.

        <?xml version="1.0" encoding="UTF-8"?>
        <!DOCTYPE configuration
        PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-config.dtd">
			<!-- mybatis가 데이터베이스에 연결하기 위한 설정(config)파일 
			https://mybatis.org/mybatis-3/ko/getting-started.html 참고  -->
        <!-- db 설정 -->
        <configuration>  
        <!--  datasource 태그 안에 4개의 프로퍼티값이 저장된 파일 : 파일 위치한 패키지이름을 디렉토리형식(/)으로 작성-->
        <properties resource="mybatis/db.properties"/>
        
        <!--  db 연결정보 -->
        <environments default="development">
            <environment id="development">
            <transactionManager type="JDBC"/>
        <!-- 데이터베이스 연결 풀 DBCP 설정 :  ${ } 기호안의 값은 properties 파일에서 읽어옵니다.
            db연결 정보가 바뀔때 properties 파일의 값만 변경하거나 파일을 교체하면 되므로 관리가 쉽습니다.
        -->
            <dataSource type="POOLED">  
            <!-- DataBase Connection Pool(저장소) : 커넥션 객체를 여러개 생성해서 저장하고
                사용자 요청이 있을때 풀에서 객체를 할당해 줍니다.요청에 대한 응답이 완료되면 다시 풀에 반환.
                풀 관리는 톰캣에서 하고 구현시는 dataSource 객체를 설정해 주면 됩니다.   -->
                <property name="driver" value="${driver}"/>
                <property name="url" value="${url}"/>
                <property name="username" value="${username}"/>
                <property name="password" value="${password}"/>
            </dataSource>
            </environment>
        </environments>
        
        <!-- SQL 매퍼 파일을 등록.    -->
        <mappers>
            <!-- JDBC로 처리하는 상당부분의 코드와 파라미터 설정 및 조회결과와 dto객체 매핑을 해줍니다. -->
            <!-- 실행할 SQL 쿼리 저장한 파일. mapper파일위치와 파일명 오류나지 않도록 확인!! 테이블컬럼과 자바객체 변수(프로퍼티) 를 바로 매핑. -->
            <mapper resource="mybatis/orders.xml"/>
            <!-- resource 속성일 때 파일의 패키지명은 . 아니고 / 기호 사용합니다. sql mapper 파일은 여러개 사용될 수 있습니다. -->
        </mappers>
        </configuration>

4. JSP에서 MyBatis 사용 : JSP 페이지에서 MyBatis를 사용하기 위해 MyBatis의 SqlSessionFactory를 생성하고, SQL 세션을 이용하여 쿼리를 실행합니다.

        package mybatis;

        import java.io.IOException;
        import java.io.InputStream;
        //Mybatis 프레임웍의 클래스들..
        import org.apache.ibatis.io.Resources;
        import org.apache.ibatis.session.SqlSession;
        import org.apache.ibatis.session.SqlSessionFactory;
        import org.apache.ibatis.session.SqlSessionFactoryBuilder;

        public class SqlSessionBean {
        /*
        * Mybatis 라이브러리의 SqlSession 구현 객체가 dao에서 Connection 과 PreparedStatement 역할을 합니다.
        * SqlSesseionFactoryBuilder 가  SqlSessionFactory 객체 생성
        * SqlSessionFactory 객체가 SqlSession 객체 생성  : 클래스 의존관계
        *  => SqlSession 객체로 db sql을 실행합니다.
        * 
        * https://mybatis.org/mybatis-3/ko/getting-started.html 참고로 작성합니다.
        * 위의 사이트에서 알려준 코드는 아래 3줄 입니다. ----------------------
        * String resource = "org/mybatis/example/mybatis-config.xml";
        InputStream inputStream = Resources.getResourceAsStream(resource);
        SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder().build(inputStream);
        * 
        */
            public static SqlSessionFactory sqlSessionFactory;
            static {   //변수들이 static 영역에 저장됩니다.
                String resource = "mybatis/mybatis-config.xml";    //mybatis 설정파일
                InputStream inputStream=null;			//파일을 읽기위한 입력 스트림
            
            
                try {
                    inputStream = Resources.getResourceAsStream(resource);   //리소스 파일 자원 읽어오기
                }catch(IOException e) {
                    System.out.println("mybatis 설정 파일 읽기 오류입니다.");
                }
                sqlSessionFactory = new SqlSessionFactoryBuilder().build(inputStream);   
                //읽어온 파일로 factory 생성
            }
            
            public static SqlSession getSession() {    
                return sqlSessionFactory.openSession();
            }
        }

5. db 연결정보 설정
    + (4) 번에서 만든 SqlSessionFactory 에서 데이터베이스 연결 정보 입력하기<br>
    + ex) `driver=oracle.jdbc.driver.OracleDriver`<br>
         `url=jdbc:oracle:thin:@//localhost:1521/xe`<br>
         `username= #1245`<br>
         `password= 1111`<br>

6. DAO 에서 사용하기 
    
        public class OrderDAO {

        private static OrderDAO dao = new OrderDAO();
        private OrderDAO() {}
        public static OrderDAO getOrderDAO() {
            return dao;
        }
        //SqlSession 의 메소드 selectList, insert 의 첫번째 인자는 mapper xml 의 sql id 와 동일하게 합니다.
        //					 두번째 인자는 전달한 파라미터.
        public List<String> selectOrderByEmail() throws SQLException{
            SqlSession mapper = SqlSessionBean.getSession();
            List<String> list = mapper.selectList("selectOrderByEmail");
            mapper.close();
            return list;
        }
        
        public int insert(OrderDTO order) throws SQLException{
            SqlSession mapper = SqlSessionBean.getSession();
            int count = mapper.insert("insert",order);
            //insert, update, delete 는 commit 명령이 필요합니다. (mybatis 는 autocommit 이 아닙니다.)
            mapper.commit();
            mapper.close();
            return count;
        }
        
        public List<OrderDTO> selectByEmail(String email) throws SQLException{
            SqlSession mapper = SqlSessionBean.getSession();
            List<OrderDTO> list = mapper.selectList("selectByEmail",email);
            mapper.close();
            return list;
            }
        }






 
 
 
 
 
 