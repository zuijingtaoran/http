# http
作者：雕兄
链接：https://www.zhihu.com/question/41986174/answer/93491697
来源：知乎
著作权归作者所有，转载请联系作者获得授权。

开局问：原生xhr怎么写？
答：创建一个xhr对象，readystate onload send open blabla
接着问：怎么处理回调？
答：status等于200且readystate等于4的时候，取responseText处理。
接下来开启http协议分支任务
问：http状态码常见有哪些？
答：200，302，304，404，5xx

问：302是啥？304是啥？什么时候会返回304？你刚刚说浏览器缓存，具体缓存机制是怎么样的？
答：…

问：你刚刚说的是发起一个get请求，除此之外http method还有哪些？
答：常用的还有post，put，delete等。
问：post跟get有啥区别？
答：…

http分支聊得差不多啦，回主线，进入跨域和web前端安全分支。

问：http聊的差不多啦，我们回到xhr，你知道同源策略么？
答：同协议，同端口，同域名

问：怎么跨域发起请求
答：cors，jsonp等
接下来聊聊，cors的细节，jsonp的原理。

再接下来聊聊其他跨域的方案，postmessage，document.domain降域

接下来就着同源策略，跟面试者聊聊cookie，问题往csrf上走，csrf是啥，怎么防。顺着csrf，聊聊xss，概念，怎么防？

跨域和安全聊完，跟面试者聊聊模块化，seajs源码之类，这个跟xhr关系不大，主要为后边的问题铺垫。
