
### @Handler约定
* H5发送消息给APP时，APP需要监听`BridgeAppHandler`消息
  ```javascript
    // 消息调用举例
    bridge.callHandler('BridgeAppHandler', msg, callback)
  ```
* APP给H5发送消息，H5需要监听`BridgeH5Handler`消息  

#### @消息数据结构定义
bridge通信中`msg`是`json格式的字符串`进行了`urlencode后的字符串`, app拿到后进行`urldecode`然后转换成json对象解析  
同样app返回给h5的也是需要将json转换为字符串后进行urlencode

* reqeust消息模板
```javascript
{
    eventType: "消息类型名称",
    data: {
      type:'xx',
      other:'cccc'
    }
}
```
* response返回数据的模板
```javascript
{
    data:{//返回的数据放在data内
      name:'',
    }
}
```


[消息列表查看](/bridge/message.md)

### @H5初始化的代码，H5需要嵌入
```javascript

if (window.WebViewJavascriptBridge) {
  return callback(WebViewJavascriptBridge);
}
if (window.WVJBCallbacks) {
  return window.WVJBCallbacks.push(callback);
}
window.WVJBCallbacks = [callback];
var WVJBIframe = document.createElement('iframe');
WVJBIframe.style.display = 'none';
WVJBIframe.src = 'https://__bridge_loaded__';
document.documentElement.appendChild(WVJBIframe);
setTimeout(function () {
  document.documentElement.removeChild(WVJBIframe)
}, 0)
```
