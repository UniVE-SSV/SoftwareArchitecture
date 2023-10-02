---
title: 2. The Spring Framework
category: 3. Java Spring
order: 2
---
<h2>Contents</h2>
* toc
{:toc}
We saw what Spring is and we deployed an example of a Spring application in a local server. We will now examine and enhance the getting started example that we have seen. Note that the Spring Framework is very huge and in these lessons, we want just to provide an intuition of how it works from a high-level perspective, without going too much on the details. Interested students are encouraged to have a look at the official documentation. However, all the information provided here should be enough for the scope of the final project.

## Configuration
The @SpringBootApplication annotation is used to mark a configuration class. In a configuration class, we insert our static main, which is the entry point of the application that instantiates and runs the Spring Application, with ***StringApplication.run***:
{% highlight java %}
@SpringBootApplication
public class SpringGettingStartedApplication {

    public static void main(String[] args) {
        SpringApplication.run(SpringGettingStartedApplication.class, args);
    }
}
{% endhighlight %}
Try to run the application without the @StringBootApplication. The server will not run. This is because the @StringBootApplication annotation (that comes from the Spring Boot dependency, that has we said before helps us to build a Spring Server application) tells the Spring framework how to be configured, doing the dirty job for us. This is great, but sometimes some changes to the default configuration are required. For example, maybe you want to change the default port, and there is a different way to do it. Let's see some of them.
### application.properties
In **/src/main/resources** folder, there should be a file named **application.properties**. If not, create it.   

In this file, we put properties that configure the behavior of our application. We can set the port with:
{% highlight properties %}
server.port=8888
{% endhighlight %}
Notice that the port changed by rebooting the application:
![Spring framework]({{ site.baseurl }}/images/spring_framework_1.png)
In <a target="_blank" rel="noopener noreferrer" href="https://docs.spring.io/spring-boot/docs/current/reference/html/application-properties.html">this</a> link, some properties are listed.
### Programmatic Configuration
Properties can be added directly in code in this way:
{% highlight java %}
@SpringBootApplication
public class CustomApplication {
    public static void main(String[] args) {
        SpringApplication app = new SpringApplication(CustomApplication.class);
        app.setDefaultProperties(Collections
          .singletonMap("server.port", "8887"));
        app.run(args);
    }
}
{% endhighlight %}
Instead of using the static method SpringApplication.run, we instantiate a StringApplication object and set the properties that we want before running the application.
Properties are defined using a Map<String, Object> data structure. If you run the application, probably you will notice that the port does not change. This is because the properties defined in application.properties have priority over what we define in the code. Remove the server.port property from the file and relaunch the app. Now the port should be the one defined in the setDefaultProperties function. This method, as the name suggests, sets default values for properties and should be used as a fallback for properties that are not defined in application.properties.
Another way to configure the application is by using a special Spring Component. A Spring component can be used for IoC and it is defined by using the @Component annotation. The framework collects all Component classes of our project and performs the required operation in a transparent manner. Let's see an example:
{% highlight java %}
@Component
package com.example.spring.customizers;

import org.springframework.boot.web.server.ConfigurableWebServerFactory;
import org.springframework.boot.web.server.WebServerFactoryCustomizer;
import org.springframework.stereotype.Component;

@Component
public class ServerPort implements WebServerFactoryCustomizer<ConfigurableWebServerFactory> {

    @Override
    public void customize(ConfigurableWebServerFactory factory) {
        factory.setPort(8886);
    }
}
{% endhighlight %}
Create a file ServerPort.java inside com.example.spring.customers package and insert the above snippet. The class implements the <a target="_blank" rel="noopener noreferrer" href="https://docs.spring.io/spring-boot/docs/current/api/org/springframework/boot/web/server/WebServerFactoryCustomizer.html">WebServerFactoryCustomizer</a> interface, which permits to customize the server creation. This implementation is then called internally by Spring (again, note the IoC in action). The core of this little class is defined inside the customize method, in which we set the port.  
Note that with Component we are not using properties: we are telling directly the Factory how it should initialize the server. This method overrides the value defined in the port property.
### Command-Line
You can also define arguments from the command line:
{% highlight java %}
./gradlew bootRun --args="--server.port=8885"
{% endhighlight %}
## Spring Components
We just mentioned Component. Classes annotated with @Component represent objects that the Spring framework manages. For the ServerPort example, Spring knows that this class represents a Component, and it is Spring's duty to understand where and when to use it. To indicate explicitly the role or purpose of a component, we can use stereotype annotations.
### Stereotype Component Annotations
Stereotype Annotation is specialized annotation used to define objects that have a particular role in the application. We saw @Component, who is also a stereotype and it is the most generic one. 
Stereotyped annotated classes can be seen, with some imagination, as "subclasses" of Component. We explain this in a moment.  
Remember the Controller app? We use an annotation, @RestController.
{% highlight java %}
@RestController
public class Hello {

    @RequestMapping("/") 
    public String index() {
        return "Greetings from Spring Boot!";
    }
}
{% endhighlight %}
RestController is a specification, a stereotype, of a component. So classes annotated with @RestController are components, that have a specific role in our application: to define, as the name suggests, a REST controller. We will talk about REST in a specific lesson, for now, we just need to know that a controller is a piece of code that takes in input some information and decides what to do with it and how to present the results.  
@RequestMapping says that in "/" we want to call the controller method index(). The returned value of the method, a string, is the body of the response of the server.  
Let's see now some basic Component stereotypes:
1. @Controller: exposes application functionality as RESTful web services. The @RestController used before is a specialization of @Controller.
2. @Repository: abstract persistence operations, and permits to find, save and delete operations. Simply, @Repository Components deals with CRUD (create, read, update, delete) operations.
3. @Service: this annotation denotes a component that acts as a service. This is used to mark classes as service providers. Services define the functionality provided by the application.  
<div>
Previous: <a href="/SoftwareArchitecture/spring/introduction">Java Spring - Introduction</a>
</div>
<div>
Next: <a href="/SoftwareArchitecture/spring/application-example">Java Spring - Example of a Spring Application</a>  
</div>