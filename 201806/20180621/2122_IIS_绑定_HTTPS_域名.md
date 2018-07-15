
## [IIS 绑定 HTTPS 域名](https://www.cnblogs.com/ubshoes/p/9161881.html)

<div class="postbody">

<div id="cnblogs_post_body" class="blogpost-body">

HTTPS为SSL安全通道，虽然并不清楚具体有什么用，但至少网站看上去比HTTP上档次，访问速度也没什么影响，所以有条件的话，还是做下，可以做噱头忽悠人。

WIN2008系统 因为端口443冲突，只能部署一个站点，切记；WIN2012不限制。

SSL证书有免费的，有收费的，五花八门，免费的有些不受GOOGLE认证，所以挑的时候很麻烦。

还好有个Certify软件，可自动申请去Let's
Encrypt申请证书，并部署IIS上，包括自动续，很方便，本来HTTPS配置难度系数10，有这软件后，顶多剩1了。

操作如下：

1、先按正常HTTP在IIS搭建目标站点

2、到Certify官网 <http://certify.webprofusion.com/>  下载并安装软件至服务器，注意其依赖 NET
Framework4.5 环境。

3、打开软件，第一次会提示注册邮箱，按提示填写；

4、左上角新建证书－〉选择对应的IIS站点，其它不用动，点击保存；

5、保存完毕，点击右边 请求证书，等待返回 success

6、成功后，软件左边会有一个显示站点及到期时间，打开IIS对应站点，会发现域名绑定也添加对应https头绑定。

至此完成，建议做301，将其它域名都跳到HTTPS主域名，这样网站域名不会乱。

建站至现在，未发现有什么不妥的地方。

参考文章：<https://www.cnblogs.com/duanweishi/p/8483161.html>

