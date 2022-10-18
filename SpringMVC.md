# 🟢 Spring MVC Prj ( **Sign up & Login** ) 🟢

_본 포스팅는 notion 을 export 한 포스팅으로 [notion](https://soo-ji.notion.site/Spring-MVC-2f750ac0ddf14325942250afffff27bb) 링크를 첨부 !_

STS 스프링 legacy project로 웹 프로젝트 만들고 **회원가입과 로그인**을 구현해보자 !

- **주석 외에 필기 내용**
  **_JDBC , mySql ⇒ pom.xml [dependency 추가 !](https://mvnrepository.com/artifact/mysql/mysql-connector-java/8.0.30)_**

  **_비동기 submit 사용하지 않는다 Button Type 사용 !_**

  **_member.xml #사용하는 이유 는 보안 .. !_**

  ```xml
  <mapper>
  <insert id="" parameterType="member">
  insert into member(name,id,pw) values(#{name},#{id},#{pw})
  </insert>
  </mapper>
  ```

# **Spring MVC Project 생성**

### 시작 환경부터 만들자 !

STS 에서 Spring legacy project 를 선택한 후 Spring MVC Project 를 생성한다

이때 프로젝트를 생성한 후 com.ssafy.myapp 이라고 명시하게 되면

실행한 결과 화면에서 포트 뒤에 /myapp이 명시되는데 이를 **Context Path** 라고 한다

실행예제에서는 [com.ssafy.cafe](http://com.ssafy.cafe) 라고 명시하였다

### Bootstrap 붙여넣기

프로젝트를 생성한 후 webapp 디렉토리 하단에 Bootstarp 소스를 붙여넣는다

### web.xml <url-pattern> 수정하기

```xml
<servlet-mapping>
		<servlet-name>appServlet</servlet-name>
		<url-pattern>*.shop</url-pattern>
	</servlet-mapping>
```

이제 프로젝트를 가동하여 index.html 화면이 잘 보이는지 확인한다 !

잘 나오면 아래의 단계로 넘어가자 !

---

# 회원가입

### 먼저 index.html 회원가입 링크를 만들어주자

index.html 의 적당한 위치에 회원가입 링크를 만들어주고

```html
<a
  class="nav-link"
  href="#"
  onclick="window.open('html/memberInsertForm.html', '_blank', 'toolbar=yes,scrollbars=yes,resizable=yes,top=50,left=500,width=400,height=750');"
>
  회원가입
</a>
```

webapp/html 폴더를 생성하여 memberInsertForm.html 를 작성하자

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <title>Insert title here</title>
    <!-- Latest compiled and minified CSS -->
    <link
      rel="stylesheet"
      href="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/css/bootstrap.min.css"
    />

    <!-- jQuery library -->
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>

    <!-- Latest compiled JavaScript -->
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/js/bootstrap.min.js"></script>

    <!-- my.js 참조 -->
    <script type="text/javascript" src="../js/my.js"></script>
  </head>
  <body>
    <article class="container">
      <div class="page-header">
        <div class="col-md-6 col-md-offset-3">
          <h3>회원가입 Form</h3>
        </div>
      </div>
      <div class="col-sm-6 col-md-offset-3">
        <form role="form">
          <div class="form-group">
            <label for="inputName">성명</label>
            <input
              type="text"
              class="form-control"
              id="name"
              placeholder="이름을 입력해 주세요"
            />
          </div>
          <div class="form-group">
            <label for="InputEmail">ID</label>
            <input
              type="text"
              class="form-control"
              id="id"
              placeholder="ID를 입력해주세요"
            />
          </div>
          <div class="form-group">
            <label for="inputPassword">비밀번호</label>
            <input
              type="password"
              class="form-control"
              id="pw"
              placeholder="비밀번호를 입력해주세요"
            />
          </div>
          <div class="form-group">
            <label for="inputPasswordCheck">비밀번호 확인</label>
            <input
              type="password"
              class="form-control"
              id="inputPasswordCheck"
              placeholder="비밀번호 확인을 위해 다시한번 입력 해 주세요"
            />
          </div>
          <div class="form-group">
            <label for="inputMobile">휴대폰 번호</label>
            <input
              type="tel"
              class="form-control"
              id="inputMobile"
              placeholder="휴대폰번호를 입력해 주세요"
            />
          </div>
          <div class="form-group">
            <label for="inputtelNO">사무실 번호</label>
            <input
              type="tel"
              class="form-control"
              id="inputtelNO"
              placeholder="사무실번호를 입력해 주세요"
            />
          </div>

          <div class="form-group">
            <label>약관 동의</label>
            <div data-toggle="buttons">
              <label class="btn btn-primary active">
                <span class="fa fa-check"></span>
                <input id="agree" type="checkbox" autocomplete="off" checked />
              </label>
              <a href="#">이용약관</a>
              에 동의합니다.
            </div>
          </div>

          <div class="form-group text-center">
            <input
              type="button"
              id="memberInsertBtn"
              class="btn btn-primary"
              value="회원가입"
            />
            <button type="submit" class="btn btn-warning">
              가입취소
              <i class="fa fa-times spaceLeft"></i>
            </button>
          </div>
        </form>
      </div>
    </article>
  </body>
</html>
```

### my.js 작성

회원가입 처리를 위해 webapp/js 폴더 내에 my.js 코드를 작성해보자 !

```jsx
$(document).ready(function(){

	$("#memberInsertBtn").click(function(){ // 회원가입
		let name = $("#name").val();
		let id = $("#id").val();
		let pw = $("#pw").val();

		$.get("../memberInsert.shop", {name, id, pw}, function(data){
			alert(data);

			// 회원가입 후 창 닫힘
			window.close();
		});

	});
```

### HomeController 작성

```java
@Controller
public class HomeController {

  @RequestMapping(
    value = "memberInsert.shop",
    method = { RequestMethod.POST },
    produces = "application/text; charset=utf8"
  )
  @ResponseBody
  public String memberInsert(
    HttpServletRequest request,
    HttpServletResponse response
  )
    throws Exception {
    String id = request.getParameter("id");
    String pw = request.getParameter("pw");
    String name = request.getParameter("name");
    System.out.println("memberInsert:" + id + "\t" + pw + "\t" + name);

    return name;
  }
}
```

이제 프로젝트를 가동하여 alert 창에 이름이 뜨는지 확인한다 !

잘 나오면 중간정도 성공이다 ^^

### myBatis 를 사용하자 !

myBatis 를 사용하기 위해서 pom.xml 에 **의존성을 추가**해주자

```xml
<!-- https://mvnrepository.com/artifact/commons-beanutils/commons-beanutils -->
<dependency>
    <groupId>commons-beanutils</groupId>
    <artifactId>commons-beanutils</artifactId>
    <version>1.8.0</version>
</dependency>

<!-- https://mvnrepository.com/artifact/commons-dbcp/commons-dbcp -->
<dependency>
    <groupId>commons-dbcp</groupId>
 <artifactId>commons-dbcp</artifactId>
    <version>1.2.2</version>
</dependency>

<!-- https://mvnrepository.com/artifact/cglib/cglib -->
<dependency>
    <groupId>cglib</groupId>
    <artifactId>cglib</artifactId>
    <version>2.2</version>
</dependency>

<dependency>
    <groupId>org.mybatis</groupId>
    <artifactId>mybatis</artifactId>
    <version>3.1.0</version>
 </dependency>

    <!-- https://mvnrepository.com/artifact/org.mybatis/mybatis-spring -->
<dependency>
    <groupId>org.mybatis</groupId>
    <artifactId>mybatis-spring</artifactId>
    <version>1.1.0</version>
</dependency>
```

### 기존의 WEB-INF/spring/root-context.xml 를 사용하자 !

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<beans
  xmlns="http://www.springframework.org/schema/beans"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xmlns:aop="http://www.springframework.org/schema/aop"
  xmlns:c="http://www.springframework.org/schema/c"
  xmlns:cache="http://www.springframework.org/schema/cache"
  xmlns:context="http://www.springframework.org/schema/context"
  xmlns:jdbc="http://www.springframework.org/schema/jdbc"
  xmlns:jee="http://www.springframework.org/schema/jee"
  xmlns:lang="http://www.springframework.org/schema/lang"
  xmlns:mvc="http://www.springframework.org/schema/mvc"
  xmlns:p="http://www.springframework.org/schema/p"
  xmlns:task="http://www.springframework.org/schema/task"
  xmlns:tx="http://www.springframework.org/schema/tx"
  xmlns:util="http://www.springframework.org/schema/util"
  xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd
        http://www.springframework.org/schema/aop http://www.springframework.org/schema/aop/spring-aop-3.1.xsd
        http://www.springframework.org/schema/cache http://www.springframework.org/schema/cache/spring-cache-3.1.xsd
        http://www.springframework.org/schema/context http://www.springframework.org/schema/context/spring-context-3.1.xsd
        http://www.springframework.org/schema/jdbc http://www.springframework.org/schema/jdbc/spring-jdbc-4.3.xsd
        http://www.springframework.org/schema/jee http://www.springframework.org/schema/jee/spring-jee-3.1.xsd
        http://www.springframework.org/schema/lang http://www.springframework.org/schema/lang/spring-lang-3.1.xsd
        http://www.springframework.org/schema/mvc http://www.springframework.org/schema/mvc/spring-mvc-3.1.xsd
        http://www.springframework.org/schema/task http://www.springframework.org/schema/task/spring-task-3.1.xsd
        http://www.springframework.org/schema/tx http://www.springframework.org/schema/tx/spring-tx-4.3.xsd
        http://www.springframework.org/schema/util http://www.springframework.org/schema/util/spring-util-3.1.xsd"
>
    
    <bean
    id="propertyPlaceholderConfigurer"
    class="org.springframework.beans.factory.config.PropertyPlaceholderConfigurer"
  >
        <property name="locations">
            <list>
                <value>/WEB-INF/config/jdbc/jdbc.properties</value>
            </list>
        </property>
    </bean>
    
    <bean
    id="dataSource"
    class="org.apache.ibatis.datasource.pooled.PooledDataSource"
  >
        <property name="driver" value="${jdbc.driverClassName}" />
        <property name="url" value="${jdbc.url}" />
        <property name="username" value="${jdbc.username}" />
        <property name="password" value="${jdbc.password}" />
    </bean>
    
    <bean
    id="sqlSessionFactoryBean"
    class="org.mybatis.spring.SqlSessionFactoryBean"
  >
        <property name="dataSource" ref="dataSource" />
        <property
      name="configLocation"
      value="classpath:mybatis/model/modelConfig.xml"
    />
        <property
      name="mapperLocations"
      value="classpath:mybatis/mappers/*.xml"
    />
    </bean>
    
    <bean id="sqlSession" class="org.mybatis.spring.SqlSessionTemplate">
        <constructor-arg index="0" ref="sqlSessionFactoryBean" />
    </bean>
    
    <bean
    id="txManager"
    class="org.springframework.jdbc.datasource.DataSourceTransactionManager"
  >
        <property name="dataSource" ref="dataSource" />        
    </bean>
    
    <tx:annotation-driven transaction-manager="txManager" />

</beans>
```

### WEB-INF/config/jdbc/jdbc.properties 와

```
jdbc.driverClassName=com.mysql.cj.jdbc.Driver
jdbc.url=jdbc:mysql://localhost:3306/database-name
jdbc.username=username
jdbc.password=password
```

### src/main/resources/mybatis/model/modelConfig.xml 를 작성해주자 !

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE configuration PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
  "http://mybatis.org/dtd/mybatis-3-config.dtd">
<configuration>

	<typeAliases>
		<typeAlias type="com.ssafy.cafe.dto.Member" alias="member" />
	</typeAliases>

</configuration>
```

### **src/main/resources/mybatis/mappers/member.xml 를 넣어준다 !**

이때 작성한 namespace 는 dao에서 사용된다

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
  "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="mapper.member">

	<insert id="memberInsert" parameterType="member">
		Insert into member(name, id, pw) values(#{name},#{id},#{pw})
	</insert>

</mapper>
```

### MemberDto / MemberDao / MemberService 를 차례로 작성해주자 !

```java
// MemberDto
package com.ssafy.cafe.dto;

public class Member {
  private String name, id, pw;

  @Override
  public String toString() {
    return "Member [name=" + name + ", id=" + id + ", pw=" + pw + "]";
  }

  public Member() {
    super();
    // TODO Auto-generated constructor stub
  }

  public Member(String name, String id, String pw) {
    super();
    this.name = name;
    this.id = id;
    this.pw = pw;
  }

  public Member(String id, String pw) {
    this.id = id;
    this.pw = pw;
  }

  public String getName() {
    return name;
  }

  public void setName(String name) {
    this.name = name;
  }

  public String getId() {
    return id;
  }

  public void setId(String id) {
    this.id = id;
  }

  public String getPw() {
    return pw;
  }

  public void setPw(String pw) {
    this.pw = pw;
  }
}
```

```java
// MemberDao
package com.ssafy.cafe.dao;

import com.ssafy.cafe.dto.Member;
import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.SQLException;
import javax.sql.DataSource;
import org.apache.ibatis.session.SqlSession;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Repository;

@Repository
public class MemberDao {
  @Autowired
  SqlSession sqlSession;

  public void memberInsert(Member m) throws Exception {
    System.out.println("MemberDAO : " + m);
    System.out.println("MemberDAO : " + sqlSession);

    sqlSession.insert("mapper.member.memberInsert", m);
  }

  public String login(Member m) {
    return sqlSession.selectOne("mapper.member.login", m);
  }
}
```

```java
// memberService
package com.ssafy.cafe.service;

import com.ssafy.cafe.dao.MemberDao;
import com.ssafy.cafe.dto.Member;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

@Service
public class MemberService {
  @Autowired
  MemberDao memberDao;

  public void memberInsert(Member m) throws Exception {
    System.out.println("MemberSerivce : " + m);
    memberDao.memberInsert(m);
  }

  public String login(Member m) {
    return memberDao.login(m);
  }
}
```

### HomeController 수정하고 DB 에 잘 반영되는지 확인하면 끝 !

```java
@Controller
public class HomeController {
  @Autowired
  MemberService memberService;

  @RequestMapping(
    value = "memberInsert.jes",
    method = { RequestMethod.POST },
    produces = "application/text; charset=utf8"
  )
  @ResponseBody
  public String memberInsert(
    HttpServletRequest request,
    HttpServletResponse response
  ) {
    String id = request.getParameter("id");
    String pw = request.getParameter("pw");
    String name = request.getParameter("name");
    System.out.println("memberInsert:" + id + "\t" + pw + "\t" + name);

    try {
      MemberVO m = new MemberVO(id, pw, name);
      memberService.memberInsert(m);
      return name + "님 회원가입 되셨습니다";
    } catch (Exception e) {
      return e.getMessage();
    }
  }
}
```

---

# 로그인 처리

회원가입이 잘 처리되어 DB 까지 잘 반영이 된 후 로그인으로 넘어오자 !

로그인도 회원가입과 동일하게 index.html 에 입력양식을 적당한 곳에 위치시키고 시작하자

```html
<div class="navbar-brand" href="#">
  <div id="msgDiv">
    ID
    <input size="5" id="id" />
    PW
    <input size="5" id="pw" type="password" />
    <input type="button" id="loginBtn" value="login" />
  </div>
</div>
```

body 태그 하단에 my.js 를 참조할 수 있도록 선언해주어야한다 !

```html
<!-- jQuery library -->
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>

<!-- Latest compiled JavaScript -->
<script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/js/bootstrap.min.js"></script>

<script type="text/javascript" src="js/my.js"></script>
```

### my.js 로그인 로직 추가

로그인시에 로그인 처리와 로그아웃 버튼이 구현될 수 있도록 로직을 추가해준다

```jsx
$('#loginBtn').click(function () {
  //로그인 처리

  let id = $('#id').val()
  let pw = $('#pw').val()

  //alert(id+":"+pw);

  $.post(
    'login.shop',
    {
      id: id,
      pw: pw,
    },
    function (data, status) {
      var obj = JSON.parse(data)
      if (obj.name) {
        data =
          obj.name +
          "<input type='button' value='logout' id='logoutBtn' class='btn btn-primary'>"

        $.cookie('logined', data)
        $('#msgDiv').html(data)
      } else {
        alert(obj.msg)
        location.reload()
      }
    }, // end function
  ) //end post()
}) //end 로그인 처리
```

### HomeController 로그인처리 메소드 추가

```java
@RequestMapping(value = "login.shop",
			method= {RequestMethod.POST},
			produces = "application/text; charset=utf8")
	@ResponseBody
	public String login(HttpServletRequest request, HttpServletResponse response){
		String id=request.getParameter("id");
		String pw=request.getParameter("pw");

		try {
			Member m=new Member(id,pw);
			String name=memberService.login(m);
			if(name!=null) {
				HttpSession session=request.getSession();
				session.setAttribute("member", m);
				return id+"님 접속중";
			}else {
				return "로그인 실패";
			}
		}catch(Exception e) {
			return e.getMessage();
		}
	}
```

### MemberService 와 MemberDao도 로그인처리 메소드를 추가시켜주자 !

```java
// MemberService
public String login(Member m) {
		return memberDao.login(m);
	}
```

```java
// MemberDao
public String login(Member m) {
		return sqlSession.selectOne("mapper.member.login",m);
	}
```

### member.xml 에 로그인 처리를 위한 SQL 쿼리를 작성하면 로그인 완료 !

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
  "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="mapper.member">

	<insert id="memberInsert" parameterType="member">
		Insert into member(name, id, pw) values(#{name},#{id},#{pw})
	</insert>
	
	<select id="login" resultType="String" parameterType="member">
		select name from member where id=#{id} and pw=#{pw}
	</select>

</mapper>
```

---

# 로그인 ( 쿠키 )

로그인 성공된 것을 확인하면 끝이라고 생각하겠지만 ..

세션 할당 후에도 **새로고침하면 로그인이 유지되지 않는다** 계속 로그인해서 될일이 아님 ..

**쿠키를 만들어서 유지시키자 !**

로그인 정보가 남아있지 않은 경우 로그인 입력 양식이 보여지도록 하고 로그인 정보가 남은 경우

그 정보를 보여지게 하기 위해서 !!!!!!!!!

index.html 의 하단 </body></html> 사이에 아래의 코드를 넣어주자

```html
</body>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery-cookie/1.4.1/jquery.cookie.min.js"></script>
	<script>
	$(function(){
		var login=$.cookie('logined');
		$("#msgDiv").html(login);
	});
	</script>
</html>
```

로그인 성공시 쿠키로 정보를 남기기 위해 my.js 에도 아래의 코드를 추가해주면 !!!!!!!!!!!

```jsx
$("#loginBtn").click(function(){//로그인 처리

			let id=$("#id").val();
			let pw=$("#pw").val();

			//alert(id+":"+pw);

			$.post("login.shop",
				  {
				    id:id,
				    pw:pw
				  },
				  function(data, status){
					  var obj=JSON.parse(data);
					  	if(obj.name){
					  		data = obj.name+ "<input type='button' value='logout' id='logoutBtn' class='btn btn-primary'>";

					  		**$.cookie("logined",data);**	// 추가한 코드
					  		$("#msgDiv").html(data);
					  	} else{
					  		alert(obj.msg);
							location.reload();
					  	}
				  } // end function
			);//end post()
		});//end 로그인 처리
```

새로고침 후에도 로그인이 유지된다 따 - 란
