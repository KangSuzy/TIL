# π’ Spring MVC Prj ( **Sign up & Login** ) π’

_λ³Έ ν¬μ€νλ notion μ export ν ν¬μ€νμΌλ‘ [notion](https://soo-ji.notion.site/Spring-MVC-2f750ac0ddf14325942250afffff27bb) λ§ν¬λ₯Ό μ²¨λΆ !_

STS μ€νλ§ legacy projectλ‘ μΉ νλ‘μ νΈ λ§λ€κ³  **νμκ°μκ³Ό λ‘κ·ΈμΈ**μ κ΅¬νν΄λ³΄μ !

- **μ£Όμ μΈμ νκΈ° λ΄μ©**
  **_JDBC , mySql β pom.xml [dependency μΆκ° !](https://mvnrepository.com/artifact/mysql/mysql-connector-java/8.0.30)_**

  **_λΉλκΈ° submit μ¬μ©νμ§ μλλ€ Button Type μ¬μ© !_**

  **_member.xml #μ¬μ©νλ μ΄μ  λ λ³΄μ .. !_**

  ```xml
  <mapper>
  <insert id="" parameterType="member">
  insert into member(name,id,pw) values(#{name},#{id},#{pw})
  </insert>
  </mapper>
  ```

# **Spring MVC Project μμ±**

### μμ νκ²½λΆν° λ§λ€μ !

STS μμ Spring legacy project λ₯Ό μ νν ν Spring MVC Project λ₯Ό μμ±νλ€

μ΄λ νλ‘μ νΈλ₯Ό μμ±ν ν com.ssafy.myapp μ΄λΌκ³  λͺμνκ² λλ©΄

μ€νν κ²°κ³Ό νλ©΄μμ ν¬νΈ λ€μ /myappμ΄ λͺμλλλ° μ΄λ₯Ό **Context Path** λΌκ³  νλ€

μ€νμμ μμλ [com.ssafy.cafe](http://com.ssafy.cafe) λΌκ³  λͺμνμλ€

### Bootstrap λΆμ¬λ£κΈ°

νλ‘μ νΈλ₯Ό μμ±ν ν webapp λλ ν λ¦¬ νλ¨μ Bootstarp μμ€λ₯Ό λΆμ¬λ£λλ€

### web.xml <url-pattern> μμ νκΈ°

```xml
<servlet-mapping>
		<servlet-name>appServlet</servlet-name>
		<url-pattern>*.shop</url-pattern>
	</servlet-mapping>
```

μ΄μ  νλ‘μ νΈλ₯Ό κ°λνμ¬ index.html νλ©΄μ΄ μ λ³΄μ΄λμ§ νμΈνλ€ !

μ λμ€λ©΄ μλμ λ¨κ³λ‘ λμ΄κ°μ !

---

# νμκ°μ

### λ¨Όμ  index.html νμκ°μ λ§ν¬λ₯Ό λ§λ€μ΄μ£Όμ

index.html μ μ λΉν μμΉμ νμκ°μ λ§ν¬λ₯Ό λ§λ€μ΄μ£Όκ³ 

```html
<a
  class="nav-link"
  href="#"
  onclick="window.open('html/memberInsertForm.html', '_blank', 'toolbar=yes,scrollbars=yes,resizable=yes,top=50,left=500,width=400,height=750');"
>
  νμκ°μ
</a>
```

webapp/html ν΄λλ₯Ό μμ±νμ¬ memberInsertForm.html λ₯Ό μμ±νμ

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

    <!-- my.js μ°Έμ‘° -->
    <script type="text/javascript" src="../js/my.js"></script>
  </head>
  <body>
    <article class="container">
      <div class="page-header">
        <div class="col-md-6 col-md-offset-3">
          <h3>νμκ°μ Form</h3>
        </div>
      </div>
      <div class="col-sm-6 col-md-offset-3">
        <form role="form">
          <div class="form-group">
            <label for="inputName">μ±λͺ</label>
            <input
              type="text"
              class="form-control"
              id="name"
              placeholder="μ΄λ¦μ μλ ₯ν΄ μ£ΌμΈμ"
            />
          </div>
          <div class="form-group">
            <label for="InputEmail">ID</label>
            <input
              type="text"
              class="form-control"
              id="id"
              placeholder="IDλ₯Ό μλ ₯ν΄μ£ΌμΈμ"
            />
          </div>
          <div class="form-group">
            <label for="inputPassword">λΉλ°λ²νΈ</label>
            <input
              type="password"
              class="form-control"
              id="pw"
              placeholder="λΉλ°λ²νΈλ₯Ό μλ ₯ν΄μ£ΌμΈμ"
            />
          </div>
          <div class="form-group">
            <label for="inputPasswordCheck">λΉλ°λ²νΈ νμΈ</label>
            <input
              type="password"
              class="form-control"
              id="inputPasswordCheck"
              placeholder="λΉλ°λ²νΈ νμΈμ μν΄ λ€μνλ² μλ ₯ ν΄ μ£ΌμΈμ"
            />
          </div>
          <div class="form-group">
            <label for="inputMobile">ν΄λν° λ²νΈ</label>
            <input
              type="tel"
              class="form-control"
              id="inputMobile"
              placeholder="ν΄λν°λ²νΈλ₯Ό μλ ₯ν΄ μ£ΌμΈμ"
            />
          </div>
          <div class="form-group">
            <label for="inputtelNO">μ¬λ¬΄μ€ λ²νΈ</label>
            <input
              type="tel"
              class="form-control"
              id="inputtelNO"
              placeholder="μ¬λ¬΄μ€λ²νΈλ₯Ό μλ ₯ν΄ μ£ΌμΈμ"
            />
          </div>

          <div class="form-group">
            <label>μ½κ΄ λμ</label>
            <div data-toggle="buttons">
              <label class="btn btn-primary active">
                <span class="fa fa-check"></span>
                <input id="agree" type="checkbox" autocomplete="off" checked />
              </label>
              <a href="#">μ΄μ©μ½κ΄</a>
              μ λμν©λλ€.
            </div>
          </div>

          <div class="form-group text-center">
            <input
              type="button"
              id="memberInsertBtn"
              class="btn btn-primary"
              value="νμκ°μ"
            />
            <button type="submit" class="btn btn-warning">
              κ°μμ·¨μ
              <i class="fa fa-times spaceLeft"></i>
            </button>
          </div>
        </form>
      </div>
    </article>
  </body>
</html>
```

### my.js μμ±

νμκ°μ μ²λ¦¬λ₯Ό μν΄ webapp/js ν΄λ λ΄μ my.js μ½λλ₯Ό μμ±ν΄λ³΄μ !

```jsx
$(document).ready(function(){

	$("#memberInsertBtn").click(function(){ // νμκ°μ
		let name = $("#name").val();
		let id = $("#id").val();
		let pw = $("#pw").val();

		$.get("../memberInsert.shop", {name, id, pw}, function(data){
			alert(data);

			// νμκ°μ ν μ°½ λ«ν
			window.close();
		});

	});
```

### HomeController μμ±

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

μ΄μ  νλ‘μ νΈλ₯Ό κ°λνμ¬ alert μ°½μ μ΄λ¦μ΄ λ¨λμ§ νμΈνλ€ !

μ λμ€λ©΄ μ€κ°μ λ μ±κ³΅μ΄λ€ ^^

### myBatis λ₯Ό μ¬μ©νμ !

myBatis λ₯Ό μ¬μ©νκΈ° μν΄μ pom.xml μ **μμ‘΄μ±μ μΆκ°**ν΄μ£Όμ

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

### κΈ°μ‘΄μ WEB-INF/spring/root-context.xml λ₯Ό μ¬μ©νμ !

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

### WEB-INF/config/jdbc/jdbc.properties μ

```
jdbc.driverClassName=com.mysql.cj.jdbc.Driver
jdbc.url=jdbc:mysql://localhost:3306/database-name
jdbc.username=username
jdbc.password=password
```

### src/main/resources/mybatis/model/modelConfig.xml λ₯Ό μμ±ν΄μ£Όμ !

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

### **src/main/resources/mybatis/mappers/member.xml λ₯Ό λ£μ΄μ€λ€ !**

μ΄λ μμ±ν namespace λ daoμμ μ¬μ©λλ€

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

### MemberDto / MemberDao / MemberService λ₯Ό μ°¨λ‘λ‘ μμ±ν΄μ£Όμ !

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

### HomeController μμ νκ³  DB μ μ λ°μλλμ§ νμΈνλ©΄ λ !

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
      return name + "λ νμκ°μ λμ¨μ΅λλ€";
    } catch (Exception e) {
      return e.getMessage();
    }
  }
}
```

---

# λ‘κ·ΈμΈ μ²λ¦¬

νμκ°μμ΄ μ μ²λ¦¬λμ΄ DB κΉμ§ μ λ°μμ΄ λ ν λ‘κ·ΈμΈμΌλ‘ λμ΄μ€μ !

λ‘κ·ΈμΈλ νμκ°μκ³Ό λμΌνκ² index.html μ μλ ₯μμμ μ λΉν κ³³μ μμΉμν€κ³  μμνμ

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

body νκ·Έ νλ¨μ my.js λ₯Ό μ°Έμ‘°ν  μ μλλ‘ μ μΈν΄μ£Όμ΄μΌνλ€ !

```html
<!-- jQuery library -->
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>

<!-- Latest compiled JavaScript -->
<script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/js/bootstrap.min.js"></script>

<script type="text/javascript" src="js/my.js"></script>
```

### my.js λ‘κ·ΈμΈ λ‘μ§ μΆκ°

λ‘κ·ΈμΈμμ λ‘κ·ΈμΈ μ²λ¦¬μ λ‘κ·Έμμ λ²νΌμ΄ κ΅¬νλ  μ μλλ‘ λ‘μ§μ μΆκ°ν΄μ€λ€

```jsx
$('#loginBtn').click(function () {
  //λ‘κ·ΈμΈ μ²λ¦¬

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
}) //end λ‘κ·ΈμΈ μ²λ¦¬
```

### HomeController λ‘κ·ΈμΈμ²λ¦¬ λ©μλ μΆκ°

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
				return id+"λ μ μμ€";
			}else {
				return "λ‘κ·ΈμΈ μ€ν¨";
			}
		}catch(Exception e) {
			return e.getMessage();
		}
	}
```

### MemberService μ MemberDaoλ λ‘κ·ΈμΈμ²λ¦¬ λ©μλλ₯Ό μΆκ°μμΌμ£Όμ !

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

### member.xml μ λ‘κ·ΈμΈ μ²λ¦¬λ₯Ό μν SQL μΏΌλ¦¬λ₯Ό μμ±νλ©΄ λ‘κ·ΈμΈ μλ£ !

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

# λ‘κ·ΈμΈ ( μΏ ν€ )

λ‘κ·ΈμΈ μ±κ³΅λ κ²μ νμΈνλ©΄ λμ΄λΌκ³  μκ°νκ² μ§λ§ ..

μΈμ ν λΉ νμλ **μλ‘κ³ μΉ¨νλ©΄ λ‘κ·ΈμΈμ΄ μ μ§λμ§ μλλ€** κ³μ λ‘κ·ΈμΈν΄μ λ μΌμ΄ μλ ..

**μΏ ν€λ₯Ό λ§λ€μ΄μ μ μ§μν€μ !**

λ‘κ·ΈμΈ μ λ³΄κ° λ¨μμμ§ μμ κ²½μ° λ‘κ·ΈμΈ μλ ₯ μμμ΄ λ³΄μ¬μ§λλ‘ νκ³  λ‘κ·ΈμΈ μ λ³΄κ° λ¨μ κ²½μ°

κ·Έ μ λ³΄λ₯Ό λ³΄μ¬μ§κ² νκΈ° μν΄μ !!!!!!!!!

index.html μ νλ¨ </body></html> μ¬μ΄μ μλμ μ½λλ₯Ό λ£μ΄μ£Όμ

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

λ‘κ·ΈμΈ μ±κ³΅μ μΏ ν€λ‘ μ λ³΄λ₯Ό λ¨κΈ°κΈ° μν΄ my.js μλ μλμ μ½λλ₯Ό μΆκ°ν΄μ£Όλ©΄ !!!!!!!!!!!

```jsx
$("#loginBtn").click(function(){//λ‘κ·ΈμΈ μ²λ¦¬

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

					  		**$.cookie("logined",data);**	// μΆκ°ν μ½λ
					  		$("#msgDiv").html(data);
					  	} else{
					  		alert(obj.msg);
							location.reload();
					  	}
				  } // end function
			);//end post()
		});//end λ‘κ·ΈμΈ μ²λ¦¬
```

μλ‘κ³ μΉ¨ νμλ λ‘κ·ΈμΈμ΄ μ μ§λλ€ λ° - λ
