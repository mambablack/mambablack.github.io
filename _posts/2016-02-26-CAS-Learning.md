---
layout: post
title: CAS Learning
category: CAS
date: 2016-02-26
---

#CAS Learning

##名词解释

###CAS Server

	用spring 构建的web工程，主要的职责是认证用户和授权访问CAS下的系统(CAS-Client)
	
	当服务器发出一个TGT，用户成功登录后，用户的SSO session创建。
	
	
	
###CAS Clients


###Software Components

CAS通过下面三个子系统建立

 * Web (Spring MVC/Spring Webflow)
 * Ticketing
 * Authentication

web 层负责与client 进行交互，委托Ticketing生成Ticket供，client层使用。


##搭建、使用

###下载基础的cas-server 工程

https://github.com/Jasig/cas-overlay-template

###通常需要修改的内容

1.	Authentication handlers (i.e. LdapAuthenticationHandler)
2. Storage backend (i.e. MemcachedTicketRegistry)
3. View layer files (JSP/CSS/Javascript)


##相关学习网址
http://www.cnblogs.com/vhua/tag/cas/
http://blog.csdn.net/xiexl/article/details/6411496