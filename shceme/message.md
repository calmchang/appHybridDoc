
### @用新窗口打开URL  

  schema: `h5schema://openurl/?url=url&type=webview&closeMe=0`  
  参数说明:  
  * url:需要打开的url地址，urlencode编码，拿到后进行一次urldecode拿到完整url，然后注意要经过[url规则](/webview/urlrule.md)处理后打开
  * type:打开的方式，默认可以不传代表 webview
    * webview:使用默认webview打开
    * browser:用原生浏览器打开
    * webviewByNav:需要带原生导航栏的webview打开,原生导航栏需要带返回按键功能及标题展示，标题取html的`<title>`标签内容
  * closeMe:是否关闭当前的webview，1为关闭，默认是:0  
    > 这里要注意是使用新窗口打开url，并且closeMe是0的时候，老的页面需要保留，因为新页面中按返回是可以回到老的webview页面的

### @关闭当前webview
  schema： `h5schema://closeWebview`  
  > 当用户在h5部分按导航栏回退已没有页面可以回退时，会调用这个schema


### @唤起原生页面  

  schema: `h5schema://open/?page=页面名称&closeMe=0`  
  参数说明:  
  * page:页面名称
    * report：举报页面
    * feedback：建议页面
  * closeMe:是否关闭当前的webview，1为关闭，默认是:0
    > 当closeMe为0时，在目标页面按导航栏返回的时候需要能回到当前webview

### @重新登录  

  schema: `h5schema://relogin/?redirect=url`  
  参数说明:
  * redirect:登录成功后跳转的url地址，如果没有则app首页，url地址按照[url规则](/webview/urlrule.md)处理
  > 注意这里url也可能是一个schema
