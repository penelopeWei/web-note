Web 安全介绍与基础入门知识  
------------
>> ## 一: http协议与会话管理 
>>> #### Url:  
>>>>	协议名称、（http）  
>>>>层级URL标记符号（// 固定不变，语法规定）、  
>>>>访问资源需要的凭证信息（可选）、  
>>>>从哪个服务器获取数据、需要连接的端口、  
>>>>	指向资源的层级文件路径、查询字符串、  
	>>>>片段ID
>>> #### https 和http 的差别:  
>>>>  https协议需要到ca申请证书，一般免费证书很少，需要交费。
>>>>  http是超文本传输协议，信息是明文传输，https 则是具有安全性的ssl加密传输协议。  
>>>> 	http和https使用的是完全不同的连接方式用的端口也不一样,前者是80,后者是443。   
>>>>	http的连接很简单,是无状态的。
>>>>	HTTPS协议是由SSL+HTTP协议构建的可进行加密传输、身份认证的网络协议 要比http协议安全。   

>>> #### Cookie   
>>>>	Name cookie名称  
>>>>	Value cookie的值  
>>>>	Domain 指定cookie的有效域  
>>>>	Path 指定cookie的有效URL路径  
>>>>	Expires 设定cookie的有效时间  
>>>>	Secure 如果设置该属性，仅在HTTPS请求中提交cookie  
>>>>	http 应该是httponly，如果设置，则客户端javascript无法获取cookie值  

>>> #### Session  
>>>>	Key session的key  
>>>>	Value session key对应的值  

>>> #### Cookie和session的区别  
>>>>	1、cookie数据存放在客户的浏览器上，session数据放在服务器上。  
>>>>	2、服务端保存状态机制需要在客户端做标记，所以session可能借助cookie机制  
>>>>	3、cookie通常用于客户端保存用户的登录状态  
>>>>	4、单个cookie保存的数据不能超过4K，很多浏览器都限制一个站点最多保存20个cookie。  

>>> ## 二 web应用的组成与网页的渲染   
>>>>	浏览器的解析顺序：  
>>>>	Html -> css ->javascript  
>>>>	浏览器解码顺序：  
>>>>	Html->url->javascript  

>>>> DOM 文档对象模型  

>>> ##  三 浏览器特性与安全策略  
>>>>	同源特性：不同域的客户端脚本在没明确授权的情况下，不能读对方的资源  
>>>>		同域  
>>>>>			协议相同(http https)  
>>>>>			域名相同(http://www.test.com http://test.com (顶级域) http:fooying.test.com)  
>>>>>			端口相同  
>>>>	授权：http响应头返回  

>>> ####	沙盒框架(sandbox)：  
>>>>		对常规<iframe>变现行为的扩展，他能让顶级页面对其嵌入的子页面及这些子页面的子资源设置一些额外的限制  
>>>>		通过设置<iframe>的参数实现限制   
>>>>		Allow-scripts 是否允许执行javascript，没有则不执行  
>>>>		Allow-froms 是否允许使用form表单，没有则不许  
>>>>		Allow-top-navigation 是否允许嵌入子页面控制顶级窗口的跳转，没有则不许  
>>>>		Allow-same-origin 是否允许访问同源数据，没有则不许  
>>> ####	Flash安全沙箱   
>>>>		分为本地沙箱与远程沙箱  
>>>>		类似于同源策略，在同一个域内的资源会被放到一个安全组下，成为安全沙箱  
>>>>		Web站点通过crossdomain.xml文件配置可以提供允许的域跨域访问本域上内容府权限（放置于站点根目录）  





>>> ####	Cookie的安全策略  
>>>>		Domain 指定cookie的有效域  
>>>>		Path 指定cookie的有效URL路径  
>>>>		Secure 如果设置该属性，仅在HTTPS请求中提交cookie  
>>>>		http 应该是httponly，如果设置，则客户端javascript无法获取cookie值  


>>> ####	内容安全策略  
>>>>		通过编码在http响应头中的指令来实施策略  
>>>>				default-src 针对所有类型资源采取默认的加载策略，可覆盖  
>>>>				script-src  针对JavaScript的加载策略  
>>>>				style-src 针对样式的加载策略  
>>>>				img-src  针对图片的加载策略  
>>>>				connect-src 针对Ajax、webSocket等请求的加载策略，不允许时浏览器返回400  
>>>>				front-src 针对web font的加载策略  
>>>>				object-src 针对<object><embed><applet>等flash插件的加载策略  
>>>>				media-src <audio><video>等标签引入的html多媒体的加载策略  
>>>>				frame-src 针对frame的加载策略，不推荐使用，在CSP Level 2被舍弃  
>>>>				sandbox 对请求的资源启用sandbox，类似于iframe的sandbox  
>>>>				report-uri 记录页面请求不被策略允许资源的日志信息，并上报到该地址  
>>>>				base-uri 限制当前页的url  
>>>>				child-src 限制子窗口（iframe、弹窗）的源，取代frame-src  
>>>>				form-action 限制表单能够提交到的源  
>>>>				frame-ancestors 限制了当前页面可以被哪些页面以iframe,frame,object等方式加载  
>>>>				plugin-types 限制插件的类型，例如pdf  

