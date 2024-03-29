### Spring cloud Gateway 限流

首先spring cloud gateway 是一个网关，高级用法中包含使用 限流

#### 一、常见限流的场景

缓存、降级、和限流。被称为高并发、分布式、系统的三驾马车。网关作为真个分布式系统中的第一道关卡，被限流功能自然必不可少，通过限流可以控制服务请求的速率，从而提高系统的应对高并发大流量的功能。让系统更有弹性。

##### 1.1限流的对象 

通过上面的介绍，我们对限流的概念可能感觉还是很模糊，到底限流限制的是什么，顾名思义，限流就是限制访问流量，但这里的流量和比较笼统的概念。如果考虑各种不同的场景，限流的非常复杂，而且和具体的业务规则密切相关，可以考虑以下几种常见的场景：

* 限制某个接口一分钟内最多请求100次
* 限制某个用户的下载速度最多100kb/s
* 限制某个用户同时只能对某个接口发起5次请求
* 限制某个ip来源禁止访问请求

从上面的离职可以看到，根据不同的请求者和请求资源，可以组合出不同的限流规则。可以很具请求者的ip来限流。或者根据请求的用户来限制，又或者根据某个特定的请求参数来限流。而限流的对象可以是请求的频率，传输速率或者并发量等。其中最常见的两个限流对象是请求的频率和并发量，他们对应的限流被称为请求频率限流和并发量限流。传输速率在现在场景下限制比较常用。比如一些资源下载站会限制普通用户的下载速度，只有购买会员才能提速，这种限流的做法实际上和请求频率限流类似，只不过一个限流的请求量的多少，一个限制的是请求数据报文的大小这篇文章主要介绍请求频率限流和并发量限流。

##### 1.2限流的处理方式

在系统中设计限流的方案时，有一个问题值得设计者仔细去思考，当请求被限流规则拦截之后，我们应该符合返回结果。一般我们有如下三种处理方式：

* 拒绝服务
* 排队等待
* 服务降级

最简单的做法就是拒绝访问，直接抛出异常，返回错误信息（b比如返回HTTP状态码429 Too Many Requests），或者给前端返回302重定向到一个错误页面，提示用户资源没有了或稍后再试。但是对一些比较重要的接口不能直接拒绝，比如秒少，下单等接口，我们既不能希望用户请求太快也不希望请求失败，这种情况一般会将请求放到消息队列中排队等待，消息队列可以期待哦削峰和限流的作用，第三种处理方式时服务降级，当触发限流条件直接返回兜底的数据，比如查询商品库存的接口，可以默认返回没有货物。

##### 1.3限流的架构

针对不同的系统架构，需要使用不同的限流方案，如图所示，服务部署的方式一般可以分为单机模式和集群模式。 **单机限流**的非常简单，可以直接**基于内存**就可以实现。而**集群模式的限流**必须依赖于某个**中心化的组件**，比如网关或者redis,从而引出两种不同的限流架构：**网关限流**和**中间件限流**

* 网关作为整个分布式的入口，承担了所有的用户的请求，所以在网关中进行限流时最合适不过的。网关层限流有时会被称为**接入层限流**。除了我们使用的spring cloud gateway ，最常见的网关组件还有**nginx**,可以通过它的**ngx_http_limit_req_module模块**，使用limit_conn_zone、limit_req_zone、limit_rate等指令很容易实现并发量限流和请求频率限流和传输速率限流。
* 另一种限流的架构时中间件限流，可以将限流的逻辑下沉到服务层，但是集群中的每个服务必须敬爱嗯自己的流量信息统一汇总到某个地方提供其他服务读取。一般来说用redis 的比较多。



