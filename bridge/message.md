## 消息列表
<!-- 
### @打开URL
```javascript
request
{
    eventType: "openUrl",
    data: {
      //打开的url地址
      linkStr:"https://www.baidu.com",
      // webview:使用默认webview打开
      // browser:用原生浏览器打开
      // webviewByNav:需要带原生导航栏的webview打开,原生导航栏需要带返回按键功能及标题展示，标题取html的<title>标签内容
      type:"webview",
    }
}
``` -->

<!-- 
### @关闭当前webview
```javascript
request
{
    //如果当前webview是唯一的webview则不需要做任何处理，除非force为true
    eventType : "closePage",
    data : {
      //默认是:false
      //true:强行关闭窗口
      force:false,
    }
}
``` -->



### @使用隐藏的webview打开url

该功能用于让H5可以提前预加载一些URL
> 如果第一次调用 openHideUrl 后，第二次再次调用 openHideUrl ，则首先用原来的webview打开新的linkStr，然后根据本条消息的定时器来决定是否需要关闭
```javascript
request
{
    eventType: "openHideUrl",
    data: {
      //打开的url地址
      linkStr:"https://www.baidu.com",
      //多少(秒)后自动关闭这个后台webview
      //0:为永不关闭
      autoCloseTimer:10,
      // 是否显示隐藏的webview窗口
      // '0':隐藏，默认是'0'
      // '1':显示
      showWindow:'0',

    }
}
```



### @获取用户信息
```javascript
request
{
    eventType : "getUserInfo",
    data : {}
}
response
{
  data:{
    // 用户数据
    name:'',
    ...
  }
}
```
