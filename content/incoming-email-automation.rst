Incoming Email Automation
==========================

:date: 2011-12-09
:tags:
    - email
    - api
    - saas

Jamie Zawinski 说::

  >> Every program attempts to expand until it can read mail. Those programs which cannot so expand are replaced by ones which can.

互联网上, 大家都会 ``Write`` Email （注册邮件,找回密码邮件,广告邮件), 但是能够 ``Read`` 邮件的应用就少多了。

当然我们还是可以找到不少支持 ``Read`` 邮件的应用的:

* 邮件列表 - 通过发送邮件来订阅或退订
* Ticket系统 - 通过发送邮件来回复Ticket, 关闭Ticket等.
* Kindle - 通过附件方式发送文件的方式传输文件到Kindle
* Google Doc / Evernote 等 - 通过发送内容到特定到邮件地址来保存文件或笔记 

但是相对于编写处理HTTP请求的脚本，要编写一个可以 ``Read`` Email 的Web应用并不轻松。

* 架设一个Email服务器要比架设一个Web服务器复杂多了
* 解析Email 并不容易

我们是如此的乐于和善于使用HTTP, 解决这个问题最佳的方案当然是将Email转换成HTTP协议。

比如说下面这些服务:

* cloundmailin http://cloudmailin.com/
* mailgun  http://mailgun.net
* Email Yak http://www.emailyak.com/

这三个服务都支持接受和解析Email然后通过HTTP 协议将邮件的内容POST到你的Web应用中。 

   User Send Email --> Email Server --> Your Web App

这三个服务我首先发现的是cloudmailin, 之后看见dotcloud 在推荐mailgun, 而Email Yak 是前几天在
`Hacker News <https://news.ycombinator.com/item?id=3325330>`_ 看到的.

有了这些服务，我们不需要架设Email服务器就让应用可以支持 ``Read`` Email了.

比如说我们就可以:

* 通过Email接受报表数据, 解析后保存到数据库就可以做历史趋势的统计了
* 通过Email来完成注册,找回密码等等常见操作。
* 更多...


最后如果你对这些第三方服务不信任，一定要在自己的服务器上接受并解析Email, `lamsonproject <http://lamsonproject.org>`_ 可能是一个不错的选择.

