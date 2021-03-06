---
date: 2020-07-23
categories: JSP
---

# 一、JSP：入门学习

1. 概念：
	* Java Server Pages： java服务器端页面
		* 可以理解为：一个特殊的页面，其中既可以指定定义html标签，又可以定义java代码
		* 用于简化书写！！！

2. 原理
	* JSP本质上就是一个Servlet


![](https://raw.githubusercontent.com/Rainbow0526/PictureGithub/master/2020_07/30.png)

3. JSP的脚本：JSP定义Java代码的方式
   1. <%  代码 %>：定义的java代码，在service方法中。service方法中可以定义什么，该脚本中就可以定义什么。
   2. <%! 代码 %>：定义的java代码，在jsp转换后的java类的成员位置。
   3. <%= 代码 %>：定义的java代码，会输出到页面上。输出语句中可以定义什么，该脚本中就可以定义什么。
4. JSP的内置对象：
   * 在jsp页面中不需要获取和创建，可以直接使用的对象
   * jsp一共有9个内置对象，今天学习3个：
     1. request
     2. response
     3. out：字符输出流对象。可以将数据输出到页面上。和response.getWriter()类似
        * `response.getWriter()`和`out.write()`的区别：
          1. 在tomcat服务器真正给客户端做出响应之前，会先找response缓冲区数据，再找out缓冲区数据。
          2. response.getWriter()数据输出永远在out.write()之前

# 二、指令

1. 作用：用于配置JSP页面，导入资源文件

2. 格式：`<%@ 指令名称 属性名1=属性值1 属性名2=属性值2 ... %>`

3. 分类

   1. page：配置JSP页面的

      * contentType：等同于`response.setContentType()`
        1. 设置响应体的mime类型以及字符集
        2. 设置当前jsp页面的编码（只能是高级的IDE才能生效，如果使用低级工具，则需要设置pageEncoding属性设置当前页面的字符集）
      * import：导包
      * errorPage：当前页面发生异常后，会自动跳转到指定的错误页面
      * isErrorPage：标识当前也是是否是错误页面
        1. true：是，可以使用内置对象exception
        2. false：否。默认值。不可以使用内置对象exception

   2. include：页面包含的。导入页面的资源文件

      `<%@include file="top.jsp"%>`

   3. taglib：导入资源

      `<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>` 

      * prefix：前缀，自定义的

# 三、注释

1. html注释
    `<!-- -->`：只能注释html代码片段
2. jsp注释：推荐使用
    `<%-- --%>`：可以注释所有

# 四、内置对象

1. 在jsp页面中不需要创建，直接使用的对象

2. 九大内置对象

   前4个为四大域对象

|   变量名    | 真实类型            | 作用                                         |
| :---------: | ------------------- | -------------------------------------------- |
| pageContext | PageContext         | 当前页面共享数据，还可以获取其他八个内置对象 |
|   request   | HttpServletRequest  | 当前页面共享数据，还可以获取其他八个内置对象 |
|   session   | HttpSession         | 一次会话的多个请求间                         |
| application | ServletContext      | 所有用户间共享数据                           |
|  response   | HttpServletResponse | 响应对象                                     |
|    page     | Object              | 当前页面(Servlet)的对象  this                |
|     out     | JspWriter           | 输出对象，数据输出到页面上                   |
|   config    | ServletConfig       | Servlet的配置对象                            |
|  exception  | Throwable           | 异常对象                                     |

