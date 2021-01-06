
## 打开H5混合开发地址的规则

* 第一步：获取到需要打开的目标URL
* 第二步：查询URL内是否有`{token}`的参数标识，如果有，则将`{token}`完整替换为urlencode后的用户`token`  
    举例说明：假设用户`token`值为 `abc!@#`，则urlencode后的值为 `abc!%40%23`
    ```
    1、 给到的页面地址: http://abc.com/#/?token={token}
        则拼接后打开地址： http://abc.com/#/?token=abc!%40%23

    2、 给到的页面地址: http://abc.com/#/?token=abcdefg
        则拼接后打开地址： http://abc.com/#/?token=abcdefg

    3、 给到的页面地址: http://abc.com/#/?token={token}&id=123
       则拼接后打开地址： http://abc.com/#/?token=abc!%40%23&id=123
    ```
* 如果有额外的参数需要拼接，则拼接格式为  `key1=value1&key2=value2` ，其中value需要进行urlencode,第一个key前如果没有问号需要增加一个问号
  举例说明：如果需要增加`id=123`的参数和`name=马云`的参数
   ```
    1、 给到的页面地址: http://abc.com/
        则拼接后打开地址： http://abc.com/?id=123&name=%E9%A9%AC%E4%BA%91

    2、 给到的页面地址: http://abc.com/#/?token=abc
        则拼接后打开地址： http://abc.com/#/?token=abc&id=123&name=%E9%A9%AC%E4%BA%91

    ```
    
> 通过url-scheme打开的url也同样处理