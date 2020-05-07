# Spring Boot
## Project Components
### Spring Boot Annotation
**Core Spring Framework Annotations:**<br/>
***@Required***: It applies to the bean setter method. It indicates that the annotated bean must be populated at configuration time with the required property, else it throws an exception **BeanInitilizationException**.<br/><br/>
***@Autowired***: Spring provides annotation-based auto-wiring by providing @Autowired annotation. It is used to autowire spring bean on setter methods, instance variable, and constructor. When we use @Autowired annotation, the spring container auto-wires the bean by matching data-type.<br/><br/>
***@Configuration***: It is a class-level annotation. The class annotated with @Configuration used by Spring Containers as a source of bean definitions.<br/><br/>
***@Bean***: It is a method-level annotation. It is an alternative of XML <bean> tag. It tells the method to produce a bean to be managed by Spring Container.<br/><br/><br/>
  
**Spring Framework Stereotype Annotations:**<br/>
***@Component***: It is a class-level annotation. It is used to mark a Java class as a bean. A Java class annotated with @Component is found during the classpath. The Spring Framework pick it up and configure it in the application context as a **Spring Bean**.<br/><br/>
***@Controller***: The @Controller is a class-level annotation. It is a specialization of **@Component**. It marks a class as a web request handler. It is often used to serve web pages. By default, it returns a string that indicates which route to redirect. It is mostly used with **@RequestMapping** annotation.<br/><br/>
***@Service***: It is also used at class level. It tells the Spring that class contains the **business logic**.<br/><br/>
***@Repository***: It is a class-level annotation. The repository is a DAOs (Data Access Object) that access the database directly. The repository does all the operations related to the database.<br/><br/><br/>

**Spring Boot Annotations**:<br/>
***@SpringBootApplication***: It is a combination of three annotations @EnableAutoConfiguration, @ComponentScan, and @Configuration.<br/><br/><br/>

**Spring MVC and REST Annotations**:<br/>
***@RequestMapping***: It is used to map the web requests. It has many optional elements like consumes, header, method, name, params, path, produces, and value. We use it with the class as well as the method.<br/><br/>
***@GetMapping***: It maps the HTTP GET requests on the specific handler method. It is used to create a web service endpoint that fetches It is used instead of using: **@RequestMapping(method = RequestMethod.GET)**<br/><br/>
***@PostMapping***: It maps the HTTP POST requests on the specific handler method. It is used to create a web service endpoint that creates It is used instead of using: **@RequestMapping(method = RequestMethod.POST)**<br/><br/>
***@PutMapping***: It maps the HTTP PUT requests on the specific handler method. It is used to create a web service endpoint that creates or updates It is used instead of using: **@RequestMapping(method = RequestMethod.PUT)**<br/><br/>
***@DeleteMapping***: It maps the HTTP DELETE requests on the specific handler method. It is used to create a web service endpoint that deletes a resource. It is used instead of using: **@RequestMapping(method = RequestMethod.DELETE)**<br/><br/>
***@RestController***: It can be considered as a combination of @Controller and @ResponseBody annotations. The @RestController annotation is itself annotated with the @ResponseBody annotation. It eliminates the need for annotating each method with @ResponseBody.<br/><br/>
***@RequestAttribute***: It binds a method parameter to request attribute. It provides convenient access to the request attributes from a controller method. With the help of @RequestAttribute annotation, we can access objects that are populated on the server-side.<br/><br/><br/>

## Spring Boot Application Properties
Spring Boot provides various properties that can be configured in the **application.properties** file. The properties have default values. We can set a property(s) for the Spring Boot application. Spring Boot also allows us to define our own property if required.<br/>
The application.properties file allows us to run an application in a different **environment**.<br/><br/>
```java
#configuring application name  
spring.application.name = demoApplication  
#configuring port  
server.port = 8081
```
