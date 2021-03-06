# baidubce
Baidubce百度云DOC，YII2组件封装

百度云文档服务DOC（Document Service）是百度云 BCE (Baidu Cloud Engine) 提供的面向文档处理的 PaaS (Platform as a Service) 服务平台，为开发者提供Office、WPS等多种格式文档的存储、管理及在线浏览服务。您无需了解文档存储、转码、分发、在线浏览等技术细节，即可快速搭建安全可靠、高可定制的文档处理平台和应用，助力在线教育、企业网盘等业务的转型升级。

>终于把百度云的坑踩完了，大家都知道接入第三方平台接口，授权签名是特别麻烦的事情，任何一个步骤都不能出错。于是我抽空整理并上传到GitHub希望以后如有该需求，就可以直接拿来用了，也许能还能帮到其他人。

### 遇到的坑
百度云的其他服务基本都有PHP的SDK，目前为止就文档服务DOC只有java的SDK没有PHP的SDK，没办法只能自己来啃API了。
>坑一：文档没有清晰说明业务流程（让程序员猜去吧）

>坑二：api错误提示不友好（继续猜）

>坑三：文档表意不清楚（导致走很多弯路）

### 百度云文档服务DOC接入方式
这个地方官方说的不是很清楚，我也是摸索出来的。
>第一种：首先注册文档会返回BOS信息，接下来用BOS信息将文件传入BOS，最后发布文档

>第二种：直接从BOS导入，然后发布。这种方式对BOS有要求限制，见官方文档。

### 使用说明
由于时间关系，代码没有做dome，核心代码都都封装好，稍微研究下直接拿来用即可，集成到自己项目中要根据自己的框架适当调整，注意自己引入文件的路径。
#### 安装Guzzle
使用composer安装 [官方文档](https://guzzle-cn.readthedocs.io/zh_CN/latest/overview.html#installation)
```
composer require guzzlehttp/guzzle:~6.0
```
#### 配置
`baidubce/bce-php-sdk-0.9.2/SampleConf.php`文件中配置自己的ak和sk
#### 调用
```php
 //调用上传文档方法，也可以自己重构此方法来传更多参数
 $doc = Doc::instance()->upload($file,$title);
 //更多方法见Doc类
```


### 目录文件说明
>`bce_php_sdk-0.9.2`  是直接从百度云下载的通用sdk，因为文档源文件是上传到BOS，注意这里绕到了其它服务上了，但是这一步真的不能少。

>`bce-doc`  中是对DOC的授权签名验证的封装，包括http请求，核心类BceApi，这个文件的类注意命名空间，改成自己的命名空间。

>`Doc.php` 是针对Yii2的封装的DOC组件，你要调用的东西就在这里面，注释很详细的一看就懂。

### web直传
>直传的dome在`index.php',踩了很多坑，注释里有，如果有什么不明白的，请给博主github一个星然后加我QQ和我交流！

### 关于
有什么疑问可以加入QQ群和群主讨论
<div>
<a target="_blank" href="https://jq.qq.com/?_wv=1027&amp;k=4945coR"><img border="0" src="http://yunyii.oss-cn-beijing.aliyuncs.com/public/join_qq.jpg" alt="云宿直播技术开发" title="云宿直播技术开发">
</a>
</div>


