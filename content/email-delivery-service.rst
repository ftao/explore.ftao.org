Email 发送服务
===============

:date: 2011-12-10
:tags:
    - email
    - send
    - saas

发送Email是几乎每一个Web应用都要考虑的问题。
传统的方案都是在自己的服务器上搭建邮件服务器,但是这种方案经常会碰到发出的邮件被当成垃圾邮件的问题。
特别是如果你在使用类似Amazon EC2 这样的云服务器，邮件接收方甚至可能直接拒绝接受你的邮件。连进用户的垃圾邮件箱的机会都没有.

解决这个问题最简单的一个方案是使用第三方的邮件发送服务器，他们的IP地址一般各个ISP/邮件服务商等的白名单中，能有比较高的到达率.
(当然到达率不只和发送者的IP地址有关,这些服务还做了很多其他的努力来保证到达率。)

邮件发送服务不完全列表
-----------------------------

=================  ===============  =========  ====================  =============
服务               支持SMTP         支持API    支持附件              免费额度     
=================  ===============  =========  ====================  =============
`Amazon SES`_      是 [#ses_smtp]_  是         部分支持 [#ses_att]_   
`SendGrid`_        是               是         支持                  200封/天
`Elastic Email`_   是               是         支持                  1000封
`PostmarkApp`_     是               是         支持                  1000封
`CritSend`_        是               否         支持                  1000封
`MailGun`_         是               是         支持                  200封/天
`MailJet`_         是               否         支持                  200封/天
`SocketLabs`_      是               否         支持                  500封/月
`Dyn Email`_       是               否         支持                  
=================  ===============  =========  ====================  =============

.. _Amazon SES: http://aws.amazon.com/ses/
.. _SendGrid: http://sendgrid.com
.. _Elastic Email: http://elasticemail.com/
.. _PostmarkApp: http://postmarkapp.com/
.. _CritSend: http://www.critsend.com/
.. _MailGun: http://mailgun.net
.. _MailJet: http://www.mailjet.com/
.. _SocketLabs: http://socketlabs.com/
.. _Dyn Email: http://dyn.com/email/
.. [#ses_smtp] Amazon SES 从2011年12月16日开始支持SMTP协议.
.. [#ses_att] Amazon SES 只支持一些 `特定类型 <http://docs.amazonwebservices.com/ses/latest/DeveloperGuide/index.html?AppendixMIME.html>`_ 的文件作为附件.



你的应用可以通过连接它们的SMTP Relay 或者HTTP API的方式,通过他们的平台发送邮件.

这些服务都提供了SMTP 接口, 现有的应用程序一般都不用修改，只需将邮件服务器地址改成他们提供的服务器就可以了.

这些服务,我实际使用的有 Amazon SES 和 SendGrid. 从我的经验来看，使用都不复杂, 价格也不贵, 比维护自己的SMTP服务器成本低多了.


参考资料:

* http://stackoverflow.com/questions/4798141/sendgrid-vs-postmark-vs-amazon-ses-and-other-email-smtp-api-providers
* http://stackoverflow.com/questions/3746213/sendgrid-vs-postmark/3830175#3830175

