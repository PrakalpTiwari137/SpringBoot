# Spring Boot
## Project Components
### Spring Boot Annotation
***@Required***: It applies to the bean setter method. It indicates that the annotated bean must be populated at configuration time with the required property, else it throws an exception **BeanInitilizationException**.<br/><br/>
***@Autowired***: Spring provides annotation-based auto-wiring by providing @Autowired annotation. It is used to autowire spring bean on setter methods, instance variable, and constructor. When we use @Autowired annotation, the spring container auto-wires the bean by matching data-type.<br/><br/>
***@Configuration***: It is a class-level annotation. The class annotated with @Configuration used by Spring Containers as a source of bean definitions.<br/><br/>
***@Bean***: It is a method-level annotation. It is an alternative of XML <bean> tag. It tells the method to produce a bean to be managed by Spring Container.<br/><br/>
  
