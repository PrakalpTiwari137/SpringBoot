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
// configuring application name  
spring.application.name = demoApplication  
// configuring port  
server.port = 8081
```

<br/>

## RESTful - springboot
### Creating a Hello World Service
**Step 1:** Create a new class with the name HelloWorldController in the package com.javatpoint.server.main.<br/>
**Step 2:** Whenever we create a web service, we need to define two things Get method and the URI. Now create the **helloWorld()** method which returns the string "Hello World." If we want to tell the spring MVC that it is going to handle the REST request, we have to add **@RestController** annotation. Now it becomes a rest controller which can handle the Rest request.<br/><br/>
The next thing we have to do is create a mapping for the method. Add **@GetMapping** annotation just above the helloWorld() method.<br/>
```java
@RestController  
public class HelloWorldController {  
    //using get method and hello-world as URI  
    @GetMapping(path="/hello-world")  
    public String helloWorld() {  
        return "Hello World";  
    }  
}  
```

<br/>

### Spring Boot Auto Configuration and Dispatcher Servlet
**Spring Boot Auto Configuration:**<br/>
Spring Boot automatically configures a spring application based on dependencies present or not present in the classpath as a jar, beans, properties, etc.<br/>
Auto-configuration can be enabled by adding **@SpringBootApplication** or **@EnableAutoConfiguration** annotation in startup class. It indicates that it is a spring context file.<br/>
It enables something called **auto-configuration**.<br/>
It enable something called **components scan**. It is the features of Spring where it will start automatically scanning classes in the package and sub package for any bean file.<br/>
<br/>Classes can be **excluded** from auto-configuration by adding:
```java
@SpringBootApplication (exclude={JacksonAutoConfiguration.class, JmxAutoConfiguration.class})
```
Or add the following statement in the **application.properties** file.
```java
spring.autoconfiguration.exclude=org.springframework.boot.autoconfigure.jackson.JacksonAutoConfiguration
```

<br/><br/>
**Dispatcher Servlet:**<br/>
In Spring MVC all incoming requests go through a single servlet is called Dispatcher Servlet (front controller). The front controller is a design pattern in web application development. A single servlet receives all the request and transfers them to all other components of the application.<br/>
The job of DispatcherServlet is to take an incoming URI and find the right combination of **handlers** (Controller classes) and **views** (usually JSPs). When the DispatcherServlet determines the view, it renders it as the response. Finally, the DispatcherServlet returns the Response Object to back to the client.<br/>
It configures the **basicErrorController, errorAttributes, ErrorMvcAutoConfiguration, and DefaultErrorViewResolverConfiguration**. It creates the default error page which is known as **Whitelabel Error Page**.<br/><br/>

### Enhancing the Hello World Service with a Path Variable
The **@PathVariable** annotation is used to extract the value from the URI. It is most suitable for the RESTful web service where the URL contains some value. Spring MVC allows us to use multiple @PathVariable annotations in the same method. A path variable is a critical part of creating rest resources.<br/><br/>
```java
//passing a path variable  
@GetMapping(path="/hello-world/path-variable/{name}")  
public HelloWorldBean helloWorldPathVariable(@PathVariable String name) {  
    return new HelloWorldBean(String.format("Hello World, %s", name)); //%s replace the name  
}
```
Whatever value we will pass to the path variable is picked up by the controller and returned to the response.<br/>
Type URL: http://localhost:8080/hello-world/path-variable/Prakalp<br/>
Output: `{"message":"Hello World",Prakalp"}`<br/><br/>

### Implementing the POST Method to create User Resource
**@RequestBody**<br/>
The @RequestBody annotation maps body of the web request to the method parameter. The body of the request is passed through an HttpMessageConverter. It resolves the method argument depending on the content type of the request.<br/><br/>
The **@PostMapping** annotation is the specialized version of the @RequestMapping annotation which acts as a shortcut for **@RequestMapping(method=RequestMethod=POST)**. @PostMapping method handles the Http POST requests matched with the specified URI.<br/><br/>
```java
//method that posts a new user detail   
@PostMapping("/users")  
public void createUser(@RequestBody User user) {  
    User sevedUser=service.save(user);    
}  
```

<br/>

### Enhancing POST Method to Return Correct HTTP Code and Status Location
**ResponseEntity Class**<br/>
The ResponseEntity is a class which extends HttpEntity and HttpStatus class. It is defined in org.springframework.http.RequestEntity.<br/>
It is used in **RestTemplate** and **@Controller** methods.<br/>
It is used as parameter in **getForEntity()** and **exchange()** method.<br/>



