
---
title: jstl
date: 2017-09-24 21:14:49
categories: 
- java
tags:
- jstl
---
# JSTL(JavaServerPages Standard  Tag  Library)
---
>  JSP 标准标签库-->JSTL(JavaServerPages Standard  Tag  Library)
>  是一个JSP标签集合，它封装了JSP应用的通用核心功能。
>  JSTL支持通用的、结构化的任务，比如迭代，条件判断，XML文档操作，国际化标签 >  SQL标签。 除了这些，它还提供了一个框架来使用集成JSTL的自定义标签。
>  根据JSTL标签所提供的功能，可以将其分为5个类别。
> - 核心标签
> - 格式化标签
> - SQL 标签
> - XML 标签
> - JSTL 函数

---
## JSTL 库安装
> Apache Tomcat安装JSTL 库步骤如下：
> 从Apache的标准标签库中下载的二进包(jakarta-taglibs-standard-current.zip)。
> - [官方下载地址](http://archive.apache.org/dist/jakarta/taglibs/standard/binaries/)
> - [菜鸟地址](http://static.runoob.com/download/jakarta-taglibs-standard-1.1.2.tar.gz)

> 下载jakarta-taglibs-standard-1.1.2.zip包并解压，将jakarta-taglibs-standard-1.1.2/lib/下的两个jar文件：standard.jar和jstl.jar文件拷贝到/WEB-INF/l ib/下。
> 接下来我们在 web.xml 文件中添加以下配置：
>

```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app version="2.4" 
    xmlns="http://java.sun.com/xml/ns/j2ee" 
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://java.sun.com/xml/ns/j2ee 
        http://java.sun.com/xml/ns/j2ee/web-app_2_4.xsd">
    <jsp-config>
    <taglib>
    <taglib-uri>http://java.sun.com/jstl/fmt</taglib-uri>
    <taglib-location>/WEB-INF/fmt.tld</taglib-location>
    </taglib>
    <taglib>
    <taglib-uri>http://java.sun.com/jstl/fmt-rt</taglib-uri>
    <taglib-location>/WEB-INF/fmt-rt.tld</taglib-location>
    </taglib>
    <taglib>
    <taglib-uri>http://java.sun.com/jstl/core</taglib-uri>
    <taglib-location>/WEB-INF/c.tld</taglib-location>
    </taglib>
    <taglib>
    <taglib-uri>http://java.sun.com/jstl/core-rt</taglib-uri>
    <taglib-location>/WEB-INF/c-rt.tld</taglib-location>
    </taglib>
    <taglib>
    <taglib-uri>http://java.sun.com/jstl/sql</taglib-uri>
    <taglib-location>/WEB-INF/sql.tld</taglib-location>
    </taglib>
    <taglib>
    <taglib-uri>http://java.sun.com/jstl/sql-rt</taglib-uri>
    <taglib-location>/WEB-INF/sql-rt.tld</taglib-location>
    </taglib>
    <taglib>
    <taglib-uri>http://java.sun.com/jstl/x</taglib-uri>
    <taglib-location>/WEB-INF/x.tld</taglib-location>
    </taglib>
    <taglib>
    <taglib-uri>http://java.sun.com/jstl/x-rt</taglib-uri>
    <taglib-location>/WEB-INF/x-rt.tld</taglib-location>
    </taglib>
    </jsp-config>
</web-app>
```
> 使用任何库，你必须在每个JSP文件中的头部包含<taglib>标签。
## 核心标签
核心标签是最常用的JSTL标签。引用核心标签库的语法如下：
```
<%@ taglib prefix="c" 
           uri="http://java.sun.com/jsp/jstl/core" %>
```
|标签|	描述|
|---    | ---     |
|<c:out>|	用于在JSP中显示数据，就像<%= ... >|
|<c:set>|	用于保存数据|
|<c:remove>|	用于删除数据|
|<c:catch>|	用来处理产生错误的异常状况，并且将错误信息储存起来|
|<c:if>|	与我们在一般程序中用的if一样|
|<c:choose>|	本身只当做<c:when>和<c:otherwise>的父标签|
|<c:when>|	<c:choose>的子标签，用来判断条件是否成立|
|<c:otherwise>|	<c:choose>的子标签，接在<c:when>标签后，当<c:when>标签判断为false时被执行|
|<c:import>|	检索一个绝对或相对 URL，然后将其内容暴露给页面|
|<c:forEach>	|基础迭代标签，接受多种集合类型|
|<c:forTokens>|	根据指定的分隔符来分隔内容并迭代输出|
|<c:param>	|用来给包含或重定向的页面传递参数|
|<c:redirect>|	重定向至一个新的URL.|
|<c:url>	|使用可选的查询参数来创造一个URL|
---
- ## <c:out> 标签
`<c:out>`标签用来显示一个表达式的结果，与<%=%>作用相似，它们的区别就是`<c:o ut>`标签可以直接通过"."操作符来访问属性。
- 举例来说，如果想要访问`customer.address.street`，只需要这样写：`<c:out value="customer.address.street">`。
`<c:out>`标签会自动忽略XML标记字符，所以它们不会被当做标签来处理。
- 语法格式：
    
```
<c:out value="<string>" default="<string>" escapeXml="<true|false>"/>
```
-  ### 属性
    - <c:out>标签有如下属性：
    
    |属性|	描述|	是否必要|	默认值|
    |   ---     |  ---    |  ---| ---        |
    |value|	要输出的内容|	是|	无|
    |default	|输出的默认值	|否	|主体中的内容|
    |escapeXml|	是否忽略XML特殊字符|	否	|true|
    ---
- ### 程序示例

 ```xml
 <%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>

<html>
<head>
<title>c:out 标签实例</title>
</head>
<body>
<html>
    <head>
        <title>&lt;c:out&gt;实例</title>
    </head>
    <body>
        <h1>&lt;c:out&gt; 实例</h1>
            <c:out value="&lt要显示的数据对象（未使用转义字符）&gt" escapeXml="true" default="默认值"></c:out><br/>
              <c:out value="&lt要显示的数据对象（使用转义字符）&gt" escapeXml="false" default="默认值"></c:out><br/>
        <c:out value="${null}" escapeXml="false">使用的表达式结果为null，则输出该默认值</c:out><br/>
    </body>
</body>
</html>
 ```
- ### 结果展示

```
<c:out> 实例

&lt要显示的数据对象（未使用转义字符）&gt
<要显示的数据对象（使用转义字符）>
使用的表达式结果为null，则输出该默认值
```
---  
- ##  <c:set>标签
> `<c:set>`标签用于设置变量值和对象属性。`<c:set>`标签就是`<jsp:setProperty>`行为标签的孪生兄弟。

> 这个标签之所以很有用呢，是因为它会计算表达式的值，然后使用计算结果来设置 JavaBean 
对象或 java.util.Map 对象的值

- ### 语法格式

```xml
<c:set
   var="<string>"
   value="<string>"
   target="<string>"
   property="<string>"
   scope="<string>"/> 
```
- ### 属性

|属性|	描述|	是否必要|	默认值|
|:--- |    ---   |   ---:      |  ---:     |
|value|	要存储的值|	否|	主体的内容|
|target	|要修改的属性所属的对象	|否|	无|
|property|	要修改的属性|	否|	无|
|var	|存储信息的变量	|否	|无|
|scope	|var属性的作用域|	否	|Page|

**如果指定了target属性，那么property属性也需要被指定。**
- ### 实例演示

```xml
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<html>
<head>
<title>c:set 标签实例</title>
</head>
<body>
<c:set var="salary" scope="session" value="${2000*2}"/>
<c:out value="${salary}"/>
</body>
</html>
```
- ## <c:remove> 标签
> `<c:remove>`标签用于移除一个变量，可以指定这个变量的作用域，若未指定，则默认为变量第一次出现的作用域。

> **这个标签不是特别有用，不过可以用来确保JSP完成清理工作。**
- ### 语法格式 
> `<c:remove var="<string>" scope="<string>"/>`

- ### 属性
|属性|	描述|	是否必要|	默认值|
|---  |---  |---        |---|
|var|	要移除的变量名称|	是|	无|
|scope|	变量所属的作用域|	|否	|所有作用域|
---
- ### 实例演示

```xml
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<html>
<head>
<title>c:remove 标签实例</title>
</head>
<body>
<c:set var="salary" scope="session" value="${2000*2}"/>
<p>salary 变量值: <c:out value="${salary}"/></p>
<c:remove var="salary"/>
<p>删除 salary 变量后的值: <c:out value="${salary}"/></p>
</body>
</html>

```
- ### 运行结果
```
salary 变量值: 4000

删除 salary 变量后的值:
```
---
- ## <c:catch> 标签
> 主要用来处理产生错误的异常状况，并且将错误信息储存起来
- ### 语法格式
```xml
<c:catch var="<string>">
...
···
</c:catch>
```
- ### 属性
|属性|	描述|	是否必要|	默认值|
|--- |---   |---        |---:     |
|var|	用来储存错误信息的变量|	否|	None|
---
- ### 实例演示

```xml
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<html>
<head>
<title>c:catch 标签实例</title>
</head>
<body>

<c:catch var ="catchException">
   <% int x = 5/0;%>
</c:catch>

<c:if test = "${catchException != null}">
   <p>异常为 : ${catchException} <br />
   发生了异常: ${catchException.message}</p>
</c:if>

</body>
</html>
```
- ### 运行结果

```xml
异常为 : java.lang.ArithmeticException: / by zero 
发生了异常: / by zero
```
---
- ## <c:if> 标签
> <c:if>标签判断表达式的值，如果表达式的值为 true 则执行其主体内容。
- ### 语法格式：

```xml
<c:if test="<boolean>" var="<string>" scope="<string>">
   ...
</c:if>
```
- ### 属性

|属性|	描述|	是否必要|	默认值|
|---|   ---|---|---|
|test	|条件	|是	|无|
|var|	用于存储条件结果的变量|	否|	无|
|scope	|var属性的作用域	|否	|page|

---
- ### 演示实例

```xml
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<html>
<head>
<title>c:if 标签实例</title>
</head>
<body>
<c:set var="salary" scope="session" value="${2000*2}"/>
<c:if test="${salary > 2000}">
   <p>我的工资为: <c:out value="${salary}"/><p>
</c:if>
</body>
</html>
```
---
- ### 运行结果如下：

```
我的工资为: 4000
```
---
- ## <c:choose>, <c:when>, <c:otherwise> 标签
> <c:choose>标签与Java switch语句的功能一样，用于在众多选项中做出选择。
switch语句中有case，而<c:choose>标签中对应有<c:when>，switch语句中有default，而<c:choose>标签中有<c:otherwise
- ### 语法格式：

```xml
<c:choose>
    <c:when test="<boolean>">
        ...
    </c:when>
    <c:when test="<boolean>">
        ...
    </c:when>
    ...
    ...
    <c:otherwise>
        ...
    </c:otherwise>
</c:choose>
```
- ### 属性
  - <c:choose>标签没有属性。
  - <c:when>标签只有一个属性，在下表中有给出。
  - <c:otherwise>标签没有属性。
---
<c:when>标签的属性如下：
 |属性|	描述|	是否必要|	默认值|
 |---|---|---|---|
 |test|条件|	是	|无| 

---
- ### 实例演示

```xml
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<html>
<head>
<title>c:choose 标签实例</title>
</head>
<body>
<c:set var="salary" scope="session" value="${2000*2}"/>
<p>你的工资为 : <c:out value="${salary}"/></p>
<c:choose>
    <c:when test="${salary <= 0}">
       太惨了。
    </c:when>
    <c:when test="${salary > 1000}">
       不错的薪水，还能生活。
    </c:when>
    <c:otherwise>
        什么都没有。
    </c:otherwise>
</c:choose>
</body>
</html>
```
---
- ### 结果展示：

```
你的工资为 : 4000

不错的薪水，还能生活。
```
---
- ## <c:import> 标签
>` <c:import>`标签提供了所有`<jsp:include>`行为标签所具有的功能，同时也允许包含绝对URL。
举例来说，使用`<c:import>`标签可以包含一个 FTP 服务器中不同的网页内容。

- ### 语法格式

```xml
<c:import
   url="<string>"
   var="<string>"
   scope="<string>"
   varRender="<string>"
   context="<string>"
   charEncoding="<string>"/>
```
- ### 属性

|属性|	描述|	是否必要|	默认值|
|---|---|---|---|
|url|	待导入资源的URL，可以是相对路径和绝对路径，并且可以导入其他主机资源|	是|	无、|
|context|	当使用相对路径访问外部context资源时，context指定了这个资源的名字。|	否|	当前应用程序|
|charEncoding|	所引入的数据的字符编码集|	否|	ISO-8859-1|
|var|	用于存储所引入的文本的变量|	否|	无|
|scope|	var属性的作用域	|否|	page|
|varReader|	可选的用于提供java.io.Reader对象的变量|	否|	无|
---
- ### 实例演示

```xml
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<html>
<head>
<title>c:import 标签实例</title>
</head>
<body>
<c:import var="data" url="http://www.runoob.com"/>
<c:out value="${data}"/>
</body>
</html>
```
---
- ## <c:forEach>, <c:forTokens> 标签
> 这些标签封装了Java中的for，while，do-while循环。
相比而言，`<c:forEach>`标签是更加通用的标签，因为它迭代一个集合中的对象。
`<c:forTokens>`标签通过指定分隔符将字符串分隔为一个数组然后迭代它们。
- ### forEach 语法格式

```xml
<c:forEach
    items="<object>"
    begin="<int>"
    end="<int>"
    step="<int>"
    var="<string>"
    varStatus="<string>">

    ...
```
- ### forTokens 语法格式

```xml
<c:forTokens
    items="<string>"
    delims="<string>"
    begin="<int>"
    end="<int>"
    step="<int>"
    var="<string>"
    varStatus="<string>">
```
- ### 属性
  - <c:forEach>标签有如下属性：
  
|属性|	描述|	是否必要|	默认值|
|---|---|---|---|
|items	|要被循环的信息	|否	|无|
|begin|	开始的元素（0=第一个元素，1=第二个元素）|	否|	0|
|end	|最后一个元素（0=第一个元素，1=第二个元素）	|否|	Last element|
|step|	每一次迭代的步长|	否|	1|
|var|	代表当前条目的变量名称	|否	|无|
|varStatus|	代表循环状态的变量名称|	否|	无|
<c:forTokens>标签与<c:forEach>标签有相似的属性，不过<c:forTokens>还有另一个属性：

|属性|	描述|	是否必要|	默认值|
|---|---|---|---|
|delims|分隔符|	是|	无|
---
- ### <c:forEach>实例演示


```xml
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<html>
<head>
<title>c:forEach 标签实例</title>
</head>
<body>
<c:forEach var="i" begin="1" end="5">
   Item <c:out value="${i}"/><p>
</c:forEach>
</body>
</html>
```
- ### 结果展示


```
Item 1
Item 2
Item 3
Item 4
Item 5
```
- ### <c:forTokens>演示实例

```xml
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<html>
<head>
<title>c:forTokens 标签实例</title>
</head>
<body>
<c:forTokens items="google,runoob,taobao" delims="," var="name">
   <c:out value="${name}"/><p>
</c:forTokens>
</body>
</html>
```
- ### 运行结果如下：

```
google
runoob
taobao
```
---
- ## <c:param> 标签
> <c:param>标签用于在<c:url>标签中指定参数，而且与URL编码相关。
在<c:param>标签内，name属性表明参数的名称，value属性表明参数的值。
- ### 语法格式

```xml
<c:param name="<string>" value="<string>"/>
```
- ### 属性


|属性|	描述|	是否必要|	默认值|
|--- |--- |--- |--- |
|name|	URL中要设置的参数的名称|	是|	无|
|value|参数的值	|否	|Body|
---
- ### 程序示例

```xml
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<html>
<head>
<title>c:forTokens 标签实例</title>
</head>
<body>
    <h1>&lt;c:param&gt; 实例</h1>
    <c:url var="myURL" value="main.jsp">
        <c:param name="name" value="Runoob"/>
        <c:param name="url" value="www.runoob.com"/>
    </c:url>
      <a href="/<c:out value="${myURL}"/>">
 使用 &lt;c:param&gt; 为指定URL发送两个参数。</a>
</body>
</html>
```
---
- ## <c:redirect> 标签
> <c:redirect>标签通过自动重写URL来将浏览器重定向至一个新的URL，它提供内容相关的URL，并且支持c:param标签。
- ### 语法格式

```
<c:redirect url="<string>" context="<string>"/>
```
- ### 属性
|属性|	描述|	是否必要|	默认值|
|:---|:---|:---|:---|
|url	|目标URL|	是|	无|
|context|	紧接着一个本地网络应用程序的名称|	否	|当前应用程序|
---
- ### 示例演示
> 如果你需要向 <c:import> 标签传递参数, 请先用 <c:url> 标签来创建URL地址，如下所示：

```xml
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<html>
<head>
<title>c:redirect 标签实例</title>
</head>
<body>
<c:redirect url="http://www.runoob.com"/>
</body>
</html>
```

```xml
 浏览器打开以上页面将跳转至 `http://www.runoob.com`。
 ```
---
- ## <c:url> 标签
> `<c:url>`标签将URL格式化为一个字符串，然后存储在一个变量中。
这个标签在需要的时候会自动重写URL。
var属性用于存储格式化后的URL。
`<c:url>`标签只是用于调用`response.encodeURL()`方法的一种可选的方法。它真正的优势在于提供了合适的URL编码，包括`<c:param>`中指定的参数。

- ### 语法格式

```xml
<c:url
  var="<string>"
  scope="<string>"
  value="<string>"
  context="<string>"/>
```
- ### 属性
|属性|	描述|	是否必要|	默认值|
|---|:---|---|---|
|value	|基础URL	|是	|无|
|context|	本地网络应用程序的名称|	否|	当前应用程序|
|var	|代表URL的变量名	|否|	Print to page|
|scope|	var属性的作用域|	否|	Page|
----
- ### 实例演示

```xml
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<html>
<head>
<title>c:url 标签实例</title>
</head>
<body>
    <h1>&lt;c:url&gt实例 Demo</h1>
    <a href="<c:url value="http://www.runoob.com"/>">
     这个链接通过 &lt;c:url&gt; 标签生成。
    </a>
</body>
</html>
```
- # 格式化标签
> JSTL格式化标签用来格式化并输出文本、日期、时间、数字。引用格式化标签库的语法如下：

```xml
<%@ taglib prefix="fmt" 
           uri="http://java.sun.com/jsp/jstl/fmt" %>
```
> 只需掌握下面两个

- `<fmt:formatNumber>`	使用指定的格式或精度格式化数字
- `<fmt:formatDate>`	使用指定的风格或模式格式化日期和时间
---
- ## <fmt:formatNumber>标签
> <fmt:formatNumber>标签用于格式化数字，百分比，货币。
- ### 语法格式

```xml
<fmt:formatNumber
  value="<string>"
  type="<string>"
  pattern="<string>"
  currencyCode="<string>"
  currencySymbol="<string>"
  groupingUsed="<string>"
  maxIntegerDigits="<string>"
  minIntegerDigits="<string>"
  maxFractionDigits="<string>"
  minFractionDigits="<string>"
  var="<string>"
  scope="<string>"/>
```
- ### 属性

|属性|	描述|	是否必要|	默认值|
|---|---|---|---|
|value	|要显示的数字|	是|	无|
|type|	NUMBER，CURRENCY，或 PERCENT类型|	否|	Number|
|pattern	|指定一个自定义的格式化模式用与输出|	否|	无|
|currencyCode|	货币码（当type="currency"时）|	否|	取决于默认区域|
|currencySymbol|	货币符号 (当 type="currency"时)|否|	取决于默认区域|
|groupingUsed|	是否对数字分组 (TRUE 或 FALSE)|	否|	true|
|maxIntegerDigits	|整型数最大的位数|	|否|	无|
|minIntegerDigits|	整型数最小的位数|	否|	无|
|maxFractionDigits|	小数点后最大的位数|	否|	无|
|minFractionDigits|	小数点后最小的位数|	否|	无|
|var|	存储格式化数字的变量|	否|	Print to page|
|scope|	var属性的作用域|否|	page|
---
> 如果`type`属性为`percent`或`number`，那么您就可以使用其它几个格式化数字属性。`maxIntegerDigits`属性和`minIntegerDigits`属性允许您指定整数的长度。若实际数字超过了`maxIntegerDigits`所指定的最大值，则数字将会被截断。
有一些属性允许您指定小数点后的位数。`minFractionalDigits`属性和`maxFractionalDigits`属性允许您指定小数点后的位数。若实际的数字超出了所指定的范围，则这个数字会被截断。
数字分组可以用来在每三个数字中插入一个逗号。groupingIsUsed属性用来指定是否使用数字分组。当与`minIntegerDigits`属性一同使用时，就必须要很小心地来获取预期的结果了。

---

> 您或许会使用pattern属性。这个属性可以让您在对数字编码时包含指定的字符。接下来的表格中列出了这些字符。

----

|符号|	描述|
|---|---|
|0	|代表一位数字|
|E	|使用指数格式|
|#|	代表一位数字，若没有则显示 0，前导 0 和追尾 0 不显示。|
|.|	小数点|
|,|	数字分组分隔符|
|;|	分隔格式|
|-|	使用默认负数前缀|
|%|	百分数|
|?|	千分数|
|¤|	货币符号，使用实际的货币符号代替|
|X|	指定可以作为前缀或后缀的字符|
|'|	在前缀或后缀中引用特殊字符|
---
- ### 实例演示

```xml
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
<%@ taglib prefix="fmt" uri="http://java.sun.com/jsp/jstl/fmt" %>

<html>
<head>
  <title>JSTL fmt:formatNumber 标签</title>
</head>
<body>
<h3>数字格式化:</h3>
<c:set var="balance" value="120000.2309" />
<p>格式化数字 (1): <fmt:formatNumber value="${balance}" 
            type="currency"/></p>
<p>格式化数字 (2): <fmt:formatNumber type="number" 
            maxIntegerDigits="3" value="${balance}" /></p>
<p>格式化数字 (3): <fmt:formatNumber type="number" 
            maxFractionDigits="3" value="${balance}" /></p>
<p>格式化数字 (4): <fmt:formatNumber type="number" 
            groupingUsed="false" value="${balance}" /></p>
<p>格式化数字 (5): <fmt:formatNumber type="percent" 
            maxIntegerDigits="3" value="${balance}" /></p>
<p>格式化数字 (6): <fmt:formatNumber type="percent" 
            minFractionDigits="10" value="${balance}" /></p>
<p>格式化数字 (7): <fmt:formatNumber type="percent" 
            maxIntegerDigits="3" value="${balance}" /></p>
<p>格式化数字 (8): <fmt:formatNumber type="number" 
            pattern="###.###E0" value="${balance}" /></p>
<p>美元 :
<fmt:setLocale value="en_US"/>
<fmt:formatNumber value="${balance}" type="currency"/></p>
</body>
</html>
```
---
- ### 运行结果如下：

```
数字格式化:

格式化数字 (1): ￥120,000.23

格式化数字 (2): 000.231

格式化数字 (3): 120,000.231

格式化数字 (4): 120000.231

格式化数字 (5): 023%

格式化数字 (6): 12,000,023.0900000000%

格式化数字 (7): 023%

格式化数字 (8): 120E3

美元 : $120,000.23
```
---
- ## <fmt:formatDate> 标签
> <fmt:formatDate>标签用于使用不同的方式格式化日期
> ### 语法格式

```xml
<fmt:formatDate
  value="<string>"
  type="<string>"
  dateStyle="<string>"
  timeStyle="<string>"
  pattern="<string>"
  timeZone="<string>"
  var="<string>"
  scope="<string>"/>
```
- ### 属性

|属性|	描述|	是否必要|	默认值|
|:---|---|---|---:|
|value	|要显示的日期	|是	|无|
|type|	DATE, TIME, 或 BOTH|	否|date|
|dateStyle|	FULL, LONG, MEDIUM, SHORT, 或 DEFAULT	|否|default|
|timeStyle|	FULL, LONG, MEDIUM, SHORT, 或 DEFAULT|	否	|default|
|pattern|	自定义格式模式|	否|	无|
|timeZone|	显示日期的时区	|否|	默认时区|
|var	|存储格式化日期的变量名	|否|显示在页面|
|scope|	存储格式化日志变量的范围|	否|	页面|
---
- ### <fmt:formatDate> 标签格式模式
|代码	|描述|	实例|
|---|---|---|
|G|时代标志|AD|
|y|不包含纪元的年份。如果不包含纪元的年份小于 10，则显示不具有前导零的年份。|2002|
|M|月份数字。一位数的月份没有前导零。|April & 04|
|d|月中的某一天。一位数的日期没有前导零。|20|
|h|12 小时制的小时。一位数的小时数没有前导零。|12|
|H|24 小时制的小时。一位数的小时数没有前导零。|0|
|m|分钟。一位数的分钟数没有前导零|45|
|s|秒。一位数的秒数没有前导零。|52|
|S|毫秒|970|
|E|周几|Tuesday|
|D|一年中的第几天|180|
|F|一个月中的第几个周几|2 (一个月中的第二个星期三)|
|w|一年中的第几周r|27|
|W|一个月中的第几周|2|
|a|a.m./p.m. 指示符|PM|
|k|小时(12 小时制的小时)|24|
|K|小时(24 小时制的小时)|0|
|z|时区|中部标准时间|
|'|转义文本|'|
|'||单引号|
---
- ### 实例演示

```xml
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
<%@ taglib prefix="fmt" uri="http://java.sun.com/jsp/jstl/fmt" %>

<html>
<head>
  <title>JSTL fmt:dateNumber 标签</title>
</head>
<body>
<h3>日期格式化:</h3>
<c:set var="now" value="<%=new java.util.Date()%>" />

<p>日期格式化 (1): <fmt:formatDate type="time" 
            value="${now}" /></p>
<p>日期格式化 (2): <fmt:formatDate type="date" 
            value="${now}" /></p>
<p>日期格式化 (3): <fmt:formatDate type="both" 
            value="${now}" /></p>
<p>日期格式化 (4): <fmt:formatDate type="both" 
            dateStyle="short" timeStyle="short" 
            value="${now}" /></p>
<p>日期格式化 (5): <fmt:formatDate type="both" 
            dateStyle="medium" timeStyle="medium" 
            value="${now}" /></p>
<p>日期格式化 (6): <fmt:formatDate type="both" 
            dateStyle="long" timeStyle="long" 
            value="${now}" /></p>
<p>日期格式化 (7): <fmt:formatDate pattern="yyyy-MM-dd" 
            value="${now}" /></p>

</body>
</html>
```
---
- ### 结果展示

```xml
日期格式化:

日期格式化 (1): 11:19:43

日期格式化 (2): 2016-6-26

日期格式化 (3): 2016-6-26 11:19:43

日期格式化 (4): 16-6-26 上午11:19

日期格式化 (5): 2016-6-26 11:19:43

日期格式化 (6): 2016年6月26日 上午11时19分43秒

日期格式化 (7): 2016-06-26
```
---

<html>
<!--在这里插入内容-->
<span style="color:red ;float:right;"> 笔记整理于菜鸟教程
更多内容请点击<a href="http://www.runoob.com/jsp/jsp-jstl.html">官网</a>
</span>
</html>


































     



