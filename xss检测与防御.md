xss检测与防御
------------
>> ## 一:  XSS介绍  
>>> ####  跨站攻击(XSS)  
>>>>是指攻击者利用网站程序对用户输入过滤不足，输入可以显示在页面上对其他用户造成影响的HTML代码，从而盗取用户资料、利用用户身份进行某种动作或者对访问者进行病毒侵害的一种攻击方式。  
>>>>XSS,全称跨站脚本，一种注入攻击方式  
>>>>成因：  
>>>>>	对于用户的输入没有严格控制而直接输出到页面  
>>>>>对非预期输入的信任 
>>>>危害：  
>>>>>盗取各类帐号 
>>>>>窃取数据  
>>>>>非法转账  
>>>>>挂马 。。。。  
>>>>POC “观点证明”。一段说明或者一个攻击的样例  
>>>>	EXP“漏洞利用”。一段对漏洞如何利用的详细说明或者一个演示的漏洞攻击代码  

>>> ####  XSS分类  
>>>>存储型（持久型） 
>>>>	反射型（飞持久型）：内容直接读取并且反射展示在页面上  
>>>> DOM型  
>>>>	mXSS(突变型XSS) 
>>>> UXSS（通用型xss）  
>>>>	Flash XSS  
>>>>	UTF-7 XSS    
>>>>	MHTML XSS  
>>>>	CSS XSS 
>>>>	VBScript XSS  
>>> ##二  XSS辅助工具介绍  
>>>>	HackBar 模拟请求  
>>>>	TamperData 修改提交的数据  
>>>>	Fiddler  

>>> #### XSS的一些基本转义  
>>>>	html_escape  
>>>>	javascript_string_escape   
>>>>	url_escape  
>>>>	css_string_escape   
>>>>	推荐：《给开发者的终极XSS防御备忘录》 

>>> #### 设置字符编码和content-type  
>>>> 字符编码：避免如utf-7 XSS等问题  
>>>> Conent-type：避免如Json的XSS等问题  

>>> #### HTTP响应头的一些XSS防护指令  
>>>>	X-XSS-Protection:1;mode=block 开启浏览器的防XSS过滤器  
>>>>	X-Frame-Options:deny 禁止页面被加载到框架  
>>>>	X-Content-Type-Options:nosniff 阻止浏览器做MIMEtype（互联网媒体类型）  
>>>>	Content-Security-Policy:default-src "self" 该响应头是防范XSS最有效的解决方法之一，他允许我们定义从URLS或内容中加载和执行对象的策略  
>>>>	Set-Cookie:key=value;HttpOnly  Set-Cookie响应头通过HttpOnly标签的设置将限制javascript访问你的cookie  
>>>>	Content-Type:type/subtype;charset=utf-8  始终设置响应的内容类型和字符集，例如返回json格式应该使用application/json,纯文本使用text/plain,html使用text/html等等，以及设置字符集为utf-8 



>>> ####  PHP的XSS防护  
>>>>	echo htmlspecialchars($string, ENT_QUOTES | ENT_XHTML, 'UTF-8');  

>>> ####  JAVA的XSS防护  
>>>>		使用WASP Java Encoder   

>>> ####  XSS的防御   
>>>>		Coverity Security Library(CSL)  
>>>>		cov:htmlEscape(string) 执行html编码  
>>>>		cov:jsStringEscape(string) 执行javascript编码  
>>>>		cov:asURL(string) 执行URL编码和净化危险的scheme,如javascript  
>>>>		cov:cssStringEscape(string) 执行css编码  
>>>>		cov:asNumber(string) 检查输入字符串是否为一个数值，默认值为0  
>>>>		cov:asCssColor(string) 允许将颜色字符串指定为文本或者十六进制并防止注入  
>>>>		cov:uriEncode(name) 执行URL编码  
