## webview的基本设置


* 建议使用wkwebview
* webview默认隐藏原生导航栏
* webview位置为在`时间栏`下方开始，撑满全屏，如果需要显示原生导航栏，则在导航栏下方开始撑满全屏
* webview的进度条需要显示，不用隐藏

* 允许webview内长按图片保存
* 关闭webview左滑返回功能、关闭下拉回弹功能
* 关闭手指双击放大功能

* 设置webview的user-agent,在后面增加app相关信息,格式为appVersion(APP包名称,APP包当前版本号,设备唯一ID,状态高度)  
  参考如下：
  ```
  原始数据如
  "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_13_6) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/71.0.3578.98 Safari/537.36"
  ```
  ```
  修改后数据
  增加app相关信息后
  "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_13_6) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/71.0.3578.98 Safari/537.36 appVersion(com.app,1.0.0,3E4DIIF88,20)"
  ```
