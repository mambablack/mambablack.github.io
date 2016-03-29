---

layout: post
title: Spring boot 使用
category: Java
date: 2016-03-29
duoshuo: false

---

## Spring Boot使用总结

## Overview


* [1. Velocity相关](#1)
* [2. SOAP and REST相关](#2)



<h2 id="1"> Velocity相关</h2>

待补充



<h2 id="1">SOAP and REST相关</h2>

1. 在spring boot 里面添加SOAP支持

	````
	
	   <dependency>
		    <groupId>org.apache.cxf</groupId>
			<artifactId>cxf-rt-frontend-jaxws</artifactId>
			<version>3.1.4</version>
		</dependency>
		<dependency>
			<groupId>org.apache.cxf</groupId>
			<artifactId>cxf-rt-transports-http-jetty</artifactId>
			<version>3.1.4</version>
		</dependency>
		
		
	````
	
	````
	
	@Bean
	public ServletRegistrationBean cxfServletRegistration() {
		return new ServletRegistrationBean(new CXFServlet(), "/services/*");
	}
	
	@Bean(name= Bus.DEFAULT_BUS_ID)
	public SpringBus springBus() {
		return new SpringBus();
	}
	
	//如果要同时使用spring mvc 和 SOAP两个servlet需要添加以下代码
	@Bean(name = DispatcherServletAutoConfiguration.DEFAULT_DISPATCHER_SERVLET_BEAN_NAME)
	public DispatcherServlet dispatcherServlet()
	{
		return new DispatcherServlet();
	}

	
	````

````
注：添加CXF SOAP支持会覆盖spring boot默认的servlet，需要再重新初始化一下spring boot默认的servlet

如果不添加会有spring mvc 和soap不能同时访问的问题

````