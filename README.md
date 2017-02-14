# http


开局问：原生xhr怎么写？
答：创建一个xhr对象，readystate onload send open blabla
============================================================
var xmlhttp;
if (window.XMLHttpRequest)
  {// code for IE7+, Firefox, Chrome, Opera, Safari
  xmlhttp=new XMLHttpRequest();
  }
else
  {// code for IE6, IE5
  xmlhttp=new ActiveXObject("Microsoft.XMLHTTP");
  }
xmlhttp.onreadystatechange=function()
  {
  if (xmlhttp.readyState==4 && xmlhttp.status==200)
    {
    document.getElementById("myDiv").innerHTML=xmlhttp.responseText;
    }
  }
xmlhttp.open("POST","/ajax/demo_post.asp",true);
xmlhttp.send();
============================================================
接着问：怎么处理回调？
答：status等于200且readystate等于4的时候，取responseText处理。
接下来开启http协议分支任务
问：http状态码常见有哪些？
答：200，302，304，404，5xx

问：302是啥？304是啥？什么时候会返回304？你刚刚说浏览器缓存，具体缓存机制是怎么样的？
答：…
============================================================
200:请求已成功，请求所希望的响应头或数据体将随此响应返回。
304:如果客户端发送了一个带条件的 GET 请求且该请求已被允许，而文档的内容（自上次访问以来或者根据请求的条件）并没有改变，则服务器应当返回这个状态码。304响应禁止包含消息体，因此始终以消息头后的第一个空行结尾。 
404	请求失败，请求所希望得到的资源未被在服务器上发现。
403	服务器已经理解请求，但是拒绝执行它
============================================================

问：你刚刚说的是发起一个get请求，除此之外http method还有哪些？
答：常用的还有post，put，delete等。
问：post跟get有啥区别？
答：…
============================================================
GET一般用于获取/查询资源信息，而POST一般用于更新资源信息。
get传送的数据量较小，不能大于2KB。post传送的数据量较大，一般被默认为不受限制。但理论上，IIS4中最大量为80KB，IIS5中为100KB
============================================================
http分支聊得差不多啦，回主线，进入跨域和web前端安全分支。

问：http聊的差不多啦，我们回到xhr，你知道同源策略么？
答：同协议，同端口，同域名

问：怎么跨域发起请求
答：cors，jsonp等
接下来聊聊，cors的细节，jsonp的原理。
============================================================
利用在页面中创建<script>节点的方法向不同域提交HTTP请求的方法称为JSONP，这项技术可以解决跨域提交Ajax请求的问题。JSONP的工作原理如下所述：

假设在http://example1.com/index.php这个页面中向http://example2.com/getinfo.php提交GET请求，我们可以将下面的JavaScript代码放在http://example1.com/index.php这个页面中来实现：

1
var eleScript= document.createElement("script");
2
eleScript.type = "text/javascript";
3
eleScript.src = "http://example2.com/getinfo.php";
4
document.getElementsByTagName("HEAD")[0].appendChild(eleScript);
当GET请求从http://example2.com/getinfo.php返回时，可以返回一段JavaScript代码，这段代码会自动执行，可以用来负责调用http://example1.com/index.php页面中的一个callback函数。

JSONP的优点是：它不像XMLHttpRequest对象实现的Ajax请求那样受到同源策略的限制；它的兼容性更好，在更加古老的浏览器中都可以运行，不需要XMLHttpRequest或ActiveX的支持；并且在请求完毕后可以通过调用callback的方式回传结果。
============================================================
再接下来聊聊其他跨域的方案，postmessage，document.domain降域

接下来就着同源策略，跟面试者聊聊cookie，问题往csrf上走，csrf是啥，怎么防。顺着csrf，聊聊xss，概念，怎么防？

跨域和安全聊完，跟面试者聊聊模块化，seajs源码之类，这个跟xhr关系不大，主要为后边的问题铺垫。


作者：雕兄
链接：https://www.zhihu.com/question/41986174/answer/93491697
来源：知乎
著作权归作者所有，转载请联系作者获得授权。
