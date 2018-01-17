## Android Scheme应用跳转协议

#### market协议拼接规则如下:

>  scheme://host/relativapath?query
>
>  #### 1.如在应用市场通过PkgName搜索应用拼接如下url：

> ```java
> url = "market://search?q=<pkgName>";
> ```
>
> ####  2.在应用市场通过PkgName直接定位到App下载页面:
>
> ```java
> url = "market://details?id=<pkgName>"
> ```
>
> #### 3.通过关键字和开发者名称跳转到应用下载页面:
>
> q = query，也可以通过组合查询的方式去跳转到应用商店
>
> ```java
> url = "market://search?q=微信"
> url = "market://search?q=pub:<开发者>"
> url = "market://search?q=微信 pub:开发者"
> ```
>

| AppStore | market://search | market://detail | market://launch |
| -------- | :-------------- | :-------------- | --------------- |
| 小米商店     | 1               | 1               | 1               |
| 360助手    | 1               | 1               | 0               |
| 应用宝      | ？               | ？               | ？               |
| 豌豆荚      | 0               | 1               | 0               |
上述market协议来启动应用是通用的url拼接方式

应用宝在AndroidManifest.xml文件里没有声明host，在小米手机上直接通过market协议来启动应用宝，会被小米拦截。各自应用商店也有自己独自的应用声明，一般可以通过这种方式从应用内跳转到应用商店，一般服务器下发的scheme url也是这个协议开始的。服务器下发的url如下：

```
tmast://appdetails?r=0.45871717478886165&pname=com.tencent.sgame&oplist=2
```

如应用宝可通过如下拼接直接跳转

```
tmast://download?pname=com.tencent.sgame&oplist=2
tmast://detail?pname=com.tencent.sgame&oplist=2
```

