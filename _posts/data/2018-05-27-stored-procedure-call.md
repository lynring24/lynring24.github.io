---
layout: post
title: call stored procedure 
categories: data
tags: [database, jdbc]
---

{% highlight java %}
Class.forName("드라이버이름");
// DriverManager.registerDriver("드라이버이름");
Conncetion conn = DriverManager.getConnection(url, id, pw);
CallableStatement cstmt = conn.prepareCall("{call 프로시져이름[파라미터]}");

CallableStatement cstmt = conn.prepareCall("{? = call 함수[파라미터]}");
// IN 파라미터
cstmt.setTYPE("번호", "값");

// OUT 파라미터 : 함수의 경우나 OUT이 있을 경우
cstmt.registerOutParameter("번호", "타입"); // 값은 자바 데이터 타입

// IN/OUT 파라미터
cstmt.set(n, "값");
cstmt.registerOutParameter(n, "타입");

// execute
cstmt.execute();

// read return
int result = cstmt.getInt("번호");

{% endhighlight %}
