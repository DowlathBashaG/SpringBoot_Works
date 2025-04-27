# SpringBoot_Works

Set the logs in the property file.

application.properties :

    logging.level.org.springframework = debug

How are our requests handled?

	DispatcherServlet - Front Controller Pattern
	
	* Mapping Servlets : dispatcherServler urls = [ / ]
	

Who is configuring error mapping?

    AutoConfiguration (ErrorMvcAutoConfiguration)

Note :

	if you are giving wrong path (url) getting 404.
	
	ErrorMvcAutoConfiguration  giving -> error page automatically . ie. Whitelabel Error Page


How are all jars available (Spring, Spring MVC , Jackson and Tomcat) ?

	Starter Projects. [ spring boot starter web ]

Starter POM

    . META-INF/spring.factories
    
    1. Enable
    2. Disable

Based on @Conditional and @Configuration

    SpringApplication.run(...);

High level flow of how spring boot works.

From the run method, the main application context is kicked off which in turn searches for the classes annotated with @configuration, initializes all the declared beans in those configuration classes, and stores those beans in JVM, specifically in a space inside JVM which is known as IOC container. After creation of all the beans, automatically configures the dispatcher servlet and registers the default handler mappings, message converts and all other basic things.

    run(..) internal flow :

    1. Create Application Context
    
    2. Check Application Type
    
    3. Register the annotated class beans with the context
    
    4. Creates an instance of TomcateEmbeddedServletContainer and adds the context.
