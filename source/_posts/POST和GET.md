---
title: POST和GET
date: 2017-02-21 14:09:53
tags:
---
## 区别
根源上来说,参看[RFC2616](https://tools.ietf.org/html/rfc2616#page-53)
### GET
The GET method means retrieve whatever information (in the form of an
   entity) is identified by the Request-URI. If the Request-URI refers
   to a data-producing process, it is the produced data which shall be
   returned as the entity in the response and not the source text of the
   process, unless that text happens to be the output of the process.

   The semantics of the GET method change to a "conditional GET" if the
   request message includes an If-Modified-Since, If-Unmodified-Since,
   If-Match, If-None-Match, or If-Range header field. A conditional GET
   method requests that the entity be transferred only under the
   circumstances described by the conditional header field(s). The
   conditional GET method is intended to reduce unnecessary network
   usage by allowing cached entities to be refreshed without requiring
   multiple requests or transferring data already held by the client.

   The semantics of the GET method change to a "partial GET" if the
   request message includes a Range header field. A partial GET requests
   that only part of the entity be transferred, as described in section
   14.35. The partial GET method is intended to reduce unnecessary
   network usage by allowing partially-retrieved entities to be
   completed without transferring data already held by the client.

   The response to a GET request is cacheable if and only if it meets
   the requirements for HTTP caching described in section 13.

   See section 15.1.3 for security considerations when used for forms.
### POST
The POST method is used to request that the origin server accept the
   entity enclosed in the request as a new subordinate of the resource
   identified by the Request-URI in the Request-Line. POST is designed
   to allow a uniform method to cover the following functions:

      - Annotation of existing resources;

      - Posting a message to a bulletin board, newsgroup, mailing list,
        or similar group of articles;

      - Providing a block of data, such as the result of submitting a
        form, to a data-handling process;

      - Extending a database through an append operation.

   The actual function performed by the POST method is determined by the
   server and is usually dependent on the Request-URI. The posted entity
   is subordinate to that URI in the same way that a file is subordinate
   to a directory containing it, a news article is subordinate to a
   newsgroup to which it is posted, or a record is subordinate to a
   database.

   The action performed by the POST method might not result in a
   resource that can be identified by a URI. In this case, either 200
   (OK) or 204 (No Content) is the appropriate response status,
   depending on whether or not the response includes an entity that
   describes the result.

   If a resource has been created on the origin server, the response
   SHOULD be 201 (Created) and contain an entity which describes the
   status of the request and refers to the new resource, and a Location
   header (see section 14.30).

   Responses to this method are not cacheable, unless the response
   includes appropriate Cache-Control or Expires header fields. However,
   the 303 (See Other) response can be used to direct the user agent to
   retrieve a cacheable resource.

   POST requests MUST obey the message transmission requirements set out
   in section 8.2.

   See section 15.1.3 for security considerations.

可知,二者**最本质**的区别在于:
    - GET 方法意思是获取被请求 URI（Request-URI）指定的信息（以实体的格式).
    - POST 方法被用于请求源服务器接受请求中的实体作为请求资源的一个新的从属物.
除此之外,二者**较为本质**的区别还有:
    - GET幂等,POST不幂等.
    - GET强制服务器支持,而POST在规范(HTTP/1.1)中为可选支持.
    - GET请求的相应是可缓存的,POST 方法的响应是不可缓存的。除非响应里有合适的 Cache-Control 或者 Expires 头域。然而,303响应能被用户代理利用去获得可缓存的响应
我们再去看一下目前充斥于搜索引擎搜索结果的所谓二者的区别:
    - 后退/刷新时,get无害(相当于重新获取),post会重新提交(重新修改):基于二者**本质区别**
    - GET 请求可被缓存,POST不可以:正确.
    - GET 请求参数保留在浏览器历史记录中,而POST不可以:因为GET参数就在url中,显然.
    - GET 请求可被收藏为书签,POST不可以:同上,显然.
    - GET 请求不应在处理敏感数据时使用:显然.
    - GET 请求有长度限制:错误,GET请求长度体现在url,而http相关规范**从来没有**规定过url的长度限制,所谓的限制只是**特定浏览器**的限制.多为2048B或者1024B
    - GET 请求只应当用于取回数据
    - GET编码类型限定为application/x-www-form-urlencoded,POST有多种类型(下面会总结一些常用的类型)
    - GET只允许ASCII数据类型,POST无限制:大多数浏览器服务器如此实现
    - GET方法产生一个TCP数据包；POST方法产生两个TCP数据包:同上,比如Firefox就不是这么玩的.
    - 安全性,呵呵呵呵呵
    - 可见性,同上.
一言以蔽之,除了上述的**本质区别**,**较为本质的区别**,其他GET和POST的玩法都是浏览器,服务器的规定而已,我们可以给POST用url传参,也可以给GET加上报文体,毕竟HTTP规范只在语义上规定了二者嘛.
## POST的content-type
比较常见的
- application/x-www-form-urlencoded 在报文体里以和GET相同的格式传输数据
- application/json 消息主体是序列化的JSON字符串
- multipart/form-data 传文件
## 表单的content-type
正常情况下,默认application/x-www-form-urlencoded,可换成multipart/form-data,具体参见[W3C相关资料](https://www.w3.org/TR/html401/cover.html#minitoc)

部分信息为道听途说,未经验证,如有谬误,欢迎指正.



