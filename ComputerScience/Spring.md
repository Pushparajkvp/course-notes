# Spring

## Overview

1. What We Mean by "Spring"?
   1. The term "Spring" means different things in different contexts. It can be used to refer to the Spring Framework project itself
   2. The Spring Framework is divided into modules
   3. At the heart are the modules of the core container, including a configuration model and a dependency injection mechanism
   4. The Spring Framework provides foundational support for different application architectures
      1. messaging
      2. transactional data
      3. persistence
      4. Servlet-based Spring MVC web framework
2. History
   1. The Spring programming model does not embrace the Java EE platform specification; rather, it integrates with carefully selected individual specifications from the EE umbrella
      1. Servlet API (JSR 340)
      2. WebSocket API (JSR 356)
      3. Concurrency Utilities (JSR 236)
      4. JSON Binding API (JSR 367)
      5. Bean Validation (JSR 303)
      6. JPA (JSR 338)
      7. JMS (JSR 914)
      8. as well as JTA/JCA setups for transaction coordination, if necessary.
   2. It supports
      1. Dependency Injection
      2. Common Annotations
   3. Spring has other projects under it like Spring boot, Spring security, Spring data, Spring cloud, Spring batch.
3. Design Philosophy
   1. Provide choice at every level - For example, you can switch persistence providers through configuration without changing your code.
   2. Accommodate diverse perspectives
   3. Maintain strong backward compatibility
   4. Care about API design
   5. Set high standards for code quality

## Spring Core

### IOC Container

1. Introduction to Spring IoC Containers and Beans
   1. IoC is also known as dependency injection (DI)
      1. It is a process whereby objects define their dependencies (that is, the other objects they work with) only through,
         1. constructor arguments
         2. arguments to a factory method
         3. properties that are set on the object instance after it is constructed or returned from a factory method
      2. The container then injects those dependencies when it creates the bean
      3. This process is fundamentally the inverse (hence the name, Inversion of Control) of the bean itself controlling the instantiation or location of its dependencies by using direct construction of classes or a mechanism such as the Service Locator pattern.
   2. Base of IoC containers
      1. org.springframework.beans
      2. org.springframework.context
   3. The BeanFactory
      1. It provides the configuration framework and basic functionality
      2. It is an interface that provides an advanced configuration mechanism capable of managing any type of object
   4. ApplicationContext is a sub-interface of BeanFactory
      1. adds more enterprise-specific functionality like
         1. Easier integration with Spring’s AOP features
         2. Message resource handling (for use in internationalization) (i18n)
         3. Event publication
         4. Application-layer specific contexts such as the WebApplicationContext for use in web applications.
      2. The ApplicationContext is a complete superset of the BeanFactory
   5. Bean
      1. The objects that form the backbone of your application and that are managed by the Spring IoC container are called beans
      2. A bean is an object that is instantiated, assembled, and managed by a Spring IoC container
      3. Beans, and the dependencies among them, are reflected in the configuration metadata used by a container.
2. Container Overview
   1. ApplicationContext interface represents the Spring IoC container and is responsible for instantiating, configuring, and assembling the beans.
   2. The container gets its instructions on what objects to instantiate, configure, and assemble by reading configuration metadata
   3. The configuration metadata is represented in
      1. XML
      2. Java annotations
      3. Java code
   4. ApplicationContext implementations
      1. ClassPathXmlApplicationContext
      2. FileSystemXmlApplicationContext
   5. Configuration Metadata
      1. This configuration metadata represents how you, as an application developer, tell the Spring container to instantiate, configure, and assemble the objects in your application.
      2. XML-based configuration metadata configures these beans as ``<bean/> elements inside a top-level <beans/>``
      3. Java configuration typically uses @Bean-annotated methods within a @Configuration class.
      4. Typically, you define service layer objects
         1. data access objects (DAOs)
         2. presentation objects such as Struts Action instances
         3. infrastructure objects such as Hibernate SessionFactories
         4. JMS Queues

            ```xml
            <?xml version="1.0" encoding="UTF-8"?>
            <beans xmlns="http://www.springframework.org/schema/beans"
                xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
                xsi:schemaLocation="http://www.springframework.org/schema/beans
                    https://www.springframework.org/schema/beans/spring-beans.xsd">

                <bean id="..." class="...">  
                    <!-- collaborators and configuration for this bean go here -->
                </bean>

                <bean id="..." class="...">
                    <!-- collaborators and configuration for this bean go here -->
                </bean>

                <!-- more bean definitions go here -->

            </beans>
            ```

         5. The id attribute is a string that identifies the individual bean definition.
         6. The class attribute defines the type of the bean and uses the fully qualifiedclassname.
   6. Instantiating a Container
       1. Instantiations

            ```java
            ApplicationContext context = new ClassPathXmlApplicationContext("services.xml", "daos.xml");
            ```

       2. service.xml

            ```xml
            <?xml version="1.0" encoding="UTF-8"?>
            <beans xmlns="http://www.springframework.org/schema/beans"
                xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
                xsi:schemaLocation="http://www.springframework.org/schema/beans
                    https://www.springframework.org/schema/beans/spring-beans.xsd">

                <!-- services -->

                <bean id="petStore" class="org.springframework.samples.jpetstore.services.PetStoreServiceImpl">
                    <property name="accountDao" ref="accountDao"/>
                    <property name="itemDao" ref="itemDao"/>
                    <!-- additional collaborators and configuration for this bean go here -->
                </bean>

                <!-- more bean definitions for services go here -->

            </beans>
            ```

       3. daos.xml

            ```xml
            <?xml version="1.0" encoding="UTF-8"?>
            <beans xmlns="http://www.springframework.org/schema/beans"
                xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
                xsi:schemaLocation="http://www.springframework.org/schema/beans
                    https://www.springframework.org/schema/beans/spring-beans.xsd">

                <bean id="accountDao"
                    class="org.springframework.samples.jpetstore.dao.jpa.JpaAccountDao">
                    <!-- additional collaborators and configuration for this bean go here -->
                </bean>

                <bean id="itemDao" class="org.springframework.samples.jpetstore.dao.jpa.JpaItemDao">
                    <!-- additional collaborators and configuration for this bean go here -->
                </bean>

                <!-- more bean definitions for data access objects go here -->

            </beans>
            ```

       4. The property name element refers to the name of the JavaBean property, and the ref element refers to the name of another bean definition
       5. Composing XML-based Configuration Metadata

            ```xml
            <beans>
                <import resource="services.xml"/>
                <import resource="resources/messageSource.xml"/>
                <import resource="/resources/themeSource.xml"/>

                <bean id="bean1" class="..."/>
                <bean id="bean2" class="..."/>
            </beans>
            ```

   7. Using the Container

        ```java
        // create and configure beans
        ApplicationContext context = new ClassPathXmlApplicationContext("services.xml", "daos.xml");

        // retrieve configured instance
        PetStoreService service = context.getBean("petStore", PetStoreService.class);

        // use configured instance
        List<String> userList = service.getUsernameList();
        ```

3. Bean Overview
   1. Within the container itself, these bean definitions are represented as BeanDefinition objects, which contain (among other information) the following metadata:
      1. A package-qualified class name: typically, the actual implementation class of the bean being defined
      2. Bean behavioral configuration elements, which state how the bean should behave in the container (scope, lifecycle callbacks, and so forth).
      3. References to other beans that are needed for the bean to do its work. These references are also called collaborators or dependencies.
      4. Other configuration settings to set in the newly created object — for example, the size limit of the pool or the number of connections to use in a bean that manages a connection pool.
   2. This metadata translates to a set of properties that make up each bean definition. The following table describes these properties:
      1. Class
      2. Name
      3. Scope
      4. Constructor arguments
      5. Properties
      6. Autowiring mode
      7. Lazy initialization mode
      8. Initialization method
      9. Destruction method
   3. Naming bean
       1. You are not required to supply a name or an id for a bean. If you do not supply a name or id explicitly, the container generates a unique name for that bean 
       2. The convention is to use the standard Java convention for instance field names when naming beans. That is, bean names start with a lowercase letter and are camel-cased from there. Examples of such names include accountManager, accountService, userDao, loginController, and so forth.
   4. Aliasing a Bean outside the Bean Definition

        ```xml
        <alias name="fromName" alias="toName"/>
        <alias name="myApp-dataSource" alias="subsystemA-dataSource"/>
        <alias name="myApp-dataSource" alias="subsystemB-dataSource"/>
        ```

   5. Instantiating Beans
      1. A bean definition is essentially a recipe for creating one or more objects
      2. This class attribute (which, internally, is a Class property on a BeanDefinition instance) is usually mandatory.
      3. Nested class names -> com.example.SomeThing$OtherThing
         1. You can use the Class property in one of two ways:
            1. Using constructor
            2. Using static factory meathod
      4. Instantiation with a Constructor

            ```xml
            <bean id="exampleBean" class="examples.ExampleBean"/>
            ```

      5. Instantiation with a Static Factory Method

            ```xml
            <bean id="clientService"
                class="examples.ClientService"
                factory-method="createInstance"/>
            ```

            ```java
            public class ClientService {
                private static ClientService clientService = new ClientService();
                private ClientService() {}

                public static ClientService createInstance() {
                    return clientService;
                }
            }
            ```

      6. Instantiation by Using an Instance Factory Method

            ```xml
            <!-- the factory bean, which contains a method called createInstance() -->
            <bean id="serviceLocator" class="examples.DefaultServiceLocator">
                <!-- inject any dependencies required by this locator bean -->
            </bean>

            <!-- the bean to be created via the factory bean -->
            <bean id="clientService"
                factory-bean="serviceLocator"
                factory-method="createClientServiceInstance"/>
            ```

            ```java
            public class DefaultServiceLocator {

                private static ClientService clientService = new ClientServiceImpl();

                public ClientService createClientServiceInstance() {
                    return clientService;
                }
            }
            ```

      7. Determining a Bean’s Runtime Type
         1. The recommended way to find out about the actual runtime type of a particular bean is a BeanFactory.getType
4. Dependencies
         1. Dependency Injection
             1. Constructor-based Dependency Injection

                ```java
                package x.y;

                public class ThingOne {

                    public ThingOne(ThingTwo thingTwo, ThingThree thingThree) {
                        // ...
                    }
                }
                ```

                ```xml
                <beans>
                    <bean id="beanOne" class="x.y.ThingOne">
                        <constructor-arg ref="beanTwo"/>
                        <constructor-arg ref="beanThree"/>
                    </bean>

                    <bean id="beanTwo" class="x.y.ThingTwo"/>

                    <bean id="beanThree" class="x.y.ThingThree"/>
                </beans>
                ```

                ```java
                package examples;

                public class ExampleBean {

                    // Number of years to calculate the Ultimate Answer
                    private int years;

                    // The Answer to Life, the Universe, and Everything
                    private String ultimateAnswer;

                    public ExampleBean(int years, String ultimateAnswer) {
                        this.years = years;
                        this.ultimateAnswer = ultimateAnswer;
                    }
                }
                ```

                ```xml
                <bean id="exampleBean" class="examples.ExampleBean">
                    <constructor-arg type="int" value="7500000"/>
                    <constructor-arg type="java.lang.String" value="42"/>
                </bean>
                <!-- constructor arg indexing-->
                <bean id="exampleBean" class="examples.ExampleBean">
                    <constructor-arg index="0" value="7500000"/>
                    <constructor-arg index="1" value="42"/>
                </bean>
                <!-- constructor name based arg indexing -->
                <bean id="exampleBean" class="examples.ExampleBean">
                    <constructor-arg name="years" value="7500000"/>
                    <constructor-arg name="ultimateAnswer" value="42"/>
                </bean>
                ```

                ```java
                package examples;

                public class ExampleBean {

                    // Annotation

                    @ConstructorProperties({"years", "ultimateAnswer"})
                    public ExampleBean(int years, String ultimateAnswer) {
                        this.years = years;
                        this.ultimateAnswer = ultimateAnswer;
                    }
                }
                ```

         2. Setter based dependency injection

            ```java
            public class ExampleBean {

                private AnotherBean beanOne;

                private YetAnotherBean beanTwo;

                private int i;

                public void setBeanOne(AnotherBean beanOne) {
                    this.beanOne = beanOne;
                }

                public void setBeanTwo(YetAnotherBean beanTwo) {
                    this.beanTwo = beanTwo;
                }

                public void setIntegerProperty(int i) {
                    this.i = i;
                }
            }
            ```

            ```xml
            <bean id="exampleBean" class="examples.ExampleBean">
                <!-- setter injection using the nested ref element -->
                <property name="beanOne">
                    <ref bean="anotherExampleBean"/>
                </property>

                <!-- setter injection using the neater ref attribute -->
                <property name="beanTwo" ref="yetAnotherBean"/>
                <property name="integerProperty" value="1"/>
            </bean>
            <bean id="anotherExampleBean" class="examples.AnotherBean"/>
            <bean id="yetAnotherBean" class="examples.YetAnotherBean"/>
            ```

   1. Dependencies and Configuration in Detail
      1. Straight values

            ```xml
            <bean id="myDataSource" class="org.apache.commons.dbcp.BasicDataSource" destroy-method="close">
                <!-- results in a setDriverClassName(String) call -->
                <property name="driverClassName" value="com.mysql.jdbc.Driver"/>
                <property name="url" value="jdbc:mysql://localhost:3306/mydb"/>
                <property name="username" value="root"/>
                <property name="password" value="misterkaoli"/>
            </bean>
            <property name="properties">
                <value>
                    jdbc.driver.className=com.mysql.jdbc.Driver
                    jdbc.url=jdbc:mysql://localhost:3306/mydb
                </value>
            </property>
            ```

      2. Idref -> error proof way to supply bean id

            ```xml
            <bean id="theTargetBean" class="..."/>

            <bean id="theClientBean" class="...">
                <property name="targetName">
                    <idref bean="theTargetBean"/>
                </property>
            </bean>
            ```

      3. References to Other Beans (Collaborators)
         1. using ref

            ```xml
            <ref bean="someBean"/>
            ```

         2. using parent

            ```xml
             <!-- in the parent context -->
            <bean id="accountService" class="com.something.SimpleAccountService">
                <!-- insert dependencies as required as here -->
            </bean>
            <!-- in the child (descendant) context -->
            <bean id="accountService" <!-- bean name is the same as the parent bean -->
                class="org.springframework.aop.framework.ProxyFactoryBean">
                <property name="target">
                    <ref parent="accountService"/> <!-- notice how we refer to the parent bean -->
                </property>
                <!-- insert other configuration and dependencies as required here -->
            </bean>
            ```

      4. Inner Beans

            ```xml
            <bean id="outer" class="...">
                <!-- instead of using a reference to a target bean, simply define the target bean inline -->
                <property name="target">
                    <bean class="com.example.Person"> <!-- this is the inner bean -->
                        <property name="name" value="Fiona Apple"/>
                        <property name="age" value="25"/>
                    </bean>
                </property>
            </bean>
            ```

      5. Collections

            ```xml
            <bean id="moreComplexObject" class="example.ComplexObject">
                <!-- results in a setAdminEmails(java.util.Properties) call -->
                <property name="adminEmails">
                    <props>
                        <prop key="administrator">administrator@example.org</prop>
                        <prop key="support">support@example.org</prop>
                        <prop key="development">development@example.org</prop>
                    </props>
                </property>
                <!-- results in a setSomeList(java.util.List) call -->
                <property name="someList">
                    <list>
                        <value>a list element followed by a reference</value>
                        <ref bean="myDataSource" />
                    </list>
                </property>
                <!-- results in a setSomeMap(java.util.Map) call -->
                <property name="someMap">
                    <map>
                        <entry key="an entry" value="just some string"/>
                        <entry key ="a ref" value-ref="myDataSource"/>
                    </map>
                </property>
                <!-- results in a setSomeSet(java.util.Set) call -->
                <property name="someSet">
                    <set>
                        <value>just some string</value>
                        <ref bean="myDataSource" />
                    </set>
                </property>
            </bean>
            ```

      6. Collection Merging (Cannot merge different collection types)

            ```xml
            <beans>
                <bean id="parent" abstract="true" class="example.ComplexObject">
                    <property name="adminEmails">
                        <props>
                            <prop key="administrator">administrator@example.com</prop>
                            <prop key="support">support@example.com</prop>
                        </props>
                    </property>
                </bean>
                <bean id="child" parent="parent">
                    <property name="adminEmails">
                        <!-- the merge is specified on the child collection definition -->
                        <props merge="true">
                            <prop key="sales">sales@example.com</prop>
                            <prop key="support">support@example.co.uk</prop>
                        </props>
                    </property>
                </bean>
            </beans>
            ```

      7. XML Shortcut with the p-namespace (instead of using ``<property/>`` we can use p:)

            ```xml
            <beans xmlns="http://www.springframework.org/schema/beans"
                xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
                xmlns:p="http://www.springframework.org/schema/p"
                xsi:schemaLocation="http://www.springframework.org/schema/beans
                    https://www.springframework.org/schema/beans/spring-beans.xsd">

                <bean name="john-classic" class="com.example.Person">
                    <property name="name" value="John Doe"/>
                    <property name="spouse" ref="jane"/>
                </bean>

                <bean name="john-modern"
                    class="com.example.Person"
                    p:name="John Doe"
                    p:spouse-ref="jane"/>

                <bean name="jane" class="com.example.Person">
                    <property name="name" value="Jane Doe"/>
                </bean>
            </beans>
            ```

      8. XML Shortcut with the c-namespace (instand of using ``<constructor-arg/>`` we can use c:)

            ```xml
            <beans xmlns="http://www.springframework.org/schema/beans"
                xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
                xmlns:c="http://www.springframework.org/schema/c"
                xsi:schemaLocation="http://www.springframework.org/schema/beans
                    https://www.springframework.org/schema/beans/spring-beans.xsd">

                <bean id="beanTwo" class="x.y.ThingTwo"/>
                <bean id="beanThree" class="x.y.ThingThree"/>

                <!-- traditional declaration with optional argument names -->
                <bean id="beanOne" class="x.y.ThingOne">
                    <constructor-arg name="thingTwo" ref="beanTwo"/>
                    <constructor-arg name="thingThree" ref="beanThree"/>
                    <constructor-arg name="email" value="something@somewhere.com"/>
                </bean>

                <!-- c-namespace declaration with argument names -->
                <bean id="beanOne" class="x.y.ThingOne" c:thingTwo-ref="beanTwo"
                    c:thingThree-ref="beanThree" c:email="something@somewhere.com"/>

            </beans>
            ```

      9. Using depends-on
         1. Typically you accomplish this with the ``<ref/>`` element in XML-based configuration metadata. However, sometimes dependencies between beans are less direct

            ```xml
            <bean id="beanOne" class="ExampleBean" depends-on="manager,accountDao">
                <property name="manager" ref="manager" />
            </bean>

            <bean id="manager" class="ManagerBean" />
            <bean id="accountDao" class="x.y.jdbc.JdbcAccountDao" />
            ```

      10. Lazy-initialized Beans
          1. By default, ApplicationContext implementations eagerly create and configure all singleton beans as part of the initialization process.
          2. A lazy-initialized bean tells the IoC container to create a bean instance when it is first requested, rather than at startup

            ```xml
            <bean id="lazy" class="com.something.ExpensiveToCreateBean" lazy-init="true"/>
            <bean name="not.lazy" class="com.something.AnotherBean"/>
            <!--change default behaviour-->
            <beans default-lazy-init="true">
                <!-- no beans will be pre-instantiated... -->
            </beans>
            ```

      11. Autowiring Collaborators
          1. You can let Spring resolve collaborators (other beans) automatically for your bean by inspecting the contents of the ApplicationContext
          2. advantages
             1. Autowiring can significantly reduce the need to specify properties or constructor arguments.
             2. Autowiring can update a configuration as your objects evolve
          3. Modes
             1. No - default. Bean references must be defined by ref elements.
             2. byName -  Spring looks for a bean with the same name as the property that needs to be autowired. For example, if a bean definition is set to autowire by name and it contains a master property (that is, it has a setMaster(..) method), Spring looks for a bean definition named master and uses it to set the property.
             3. byType - Lets a property be autowired if exactly one bean of the property type exists in the container.
             4. Analogous to byType but applies to constructor arguments.
          4. disadvantages of autowiring:
             1. You cannot autowire simple properties such as primitives, Strings, and Classes (and arrays of such simple properties). This limitation is by-design.
             2. Autowiring is less exact than explicit wiring
             3. Wiring information may not be available to tools that may generate documentation from a Spring container.
             4. Multiple bean definitions within the container may match the type specified by the setter method or constructor argument to be autowired
      12. Method injection
          1. Used when we have a prototype scoped bean inside a singleton bean

                ```java
                package fiona.apple;

                    // no more Spring imports!

                    public abstract class CommandManager {

                        public Object process(Object commandState) {
                            // grab a new instance of the appropriate Command interface
                            Command command = createCommand();
                            // set the state on the (hopefully brand new) Command instance
                            command.setState(commandState);
                            return command.execute();
                        }

                        // okay... but where is the implementation of this method?
                        protected abstract Command createCommand();
                }
                ```

                ```xml
                <!-- a stateful bean deployed as a prototype (non-singleton) -->
                <bean id="myCommand" class="fiona.apple.AsyncCommand" scope="prototype">
                    <!-- inject dependencies here as required -->
                </bean>

                <!-- commandProcessor uses statefulCommandHelper -->
                <bean id="commandManager" class="fiona.apple.CommandManager">
                    <lookup-method name="createCommand" bean="myCommand"/>
                </bean>
                ```

5. Bean Scopes
   1. Supported scopes
      1. Singleton - Scopes a single bean definition to a single object instance for each Spring IoC container.
      2. prototype - Scopes a single bean definition to any number of object instances.
      3. request -Scopes a single bean definition to the lifecycle of a single HTTP request. That is, each HTTP request has its own instance of a bean created off the back of a single bean definition. Only valid in the context of a web-aware Spring ApplicationContext.
      4. session - Scopes a single bean definition to the lifecycle of an HTTP Session. Only valid in the context of a web-aware Spring ApplicationContext.
      5. application - Scopes a single bean definition to the lifecycle of a ServletContext. Only valid in the context of a web-aware Spring ApplicationContext.
      6. websocket - Scopes a single bean definition to the lifecycle of a WebSocket. Only valid in the context of a web-aware Spring ApplicationContext.
   2. Singleton Scope
      1. Only one shared instance of a singleton bean is managed, and all requests for beans with an ID or IDs that match that bean definition result in that one specific bean instance being returned by the Spring container.
      2. It is the default scope
   3. Prototype Scope
      1. new bean is created whenever getBean() is called or another bean references this bean.
      2. As a rule, you should use the prototype scope for all stateful beans and the singleton scope for stateless beans.
   4. Request, Session, Application, and WebSocket Scopes
      1. The request, session, application, and websocket scopes are available only if you use a web-aware Spring ApplicationContext implementation (such as XmlWebApplicationContext)
   5. Custom Scopes
      1. We can create custom scopes by implementing the Scope interface and implement the following 4 methods
         1. get
         2. remove
         3. registerDestructionCallback
         4. getConversationId
6. Customizing beans
   1. Lifecycle Callbacks

        ```java
        public class AnotherExampleBean implements InitializingBean, DisposableBean {

            @Override
            public void afterPropertiesSet() {
                // do some initialization work
            }
            @Override
            public void destroy() {
                // do some destruction work (like releasing pooled connections)
            }
        }
        ```

        ```java
        public class DefaultBlogService implements BlogService {

            private BlogDao blogDao;

            public void setBlogDao(BlogDao blogDao) {
                this.blogDao = blogDao;
            }

            // this is (unsurprisingly) the initialization callback method
            public void init() {
                if (this.blogDao == null) {
                    throw new IllegalStateException("The [blogDao] property must be set.");
                }
            }
        }
        ```

        ```xml
        <beans default-init-method="init">

            <bean id="blogService" class="com.something.DefaultBlogService">
                <property name="blogDao" ref="blogDao" />
            </bean>

        </beans>
        ```

   2. Shutting Down the Spring IoC Container Gracefully in Non-Web Applications
      1. This can be done using registerShutdownHook() function and close() function.
      2. close() will immediately close the container
      3. registerShutdownHook() will close the container when the main thread is exited
   3. ApplicationContextAware and BeanNameAware
      1. When an ApplicationContext creates an object instance that implements the org.springframework.context.ApplicationContextAware interface, the instance is provided with a reference to that ApplicationContext. The following listing shows the definition of the ApplicationContextAware interface:
      2. Thus, beans can programmatically manipulate the ApplicationContext that created them, through the ApplicationContext
   4. Other aware interfaces
      1. ApplicationContextAware -> Declaring ApplicationContext
      2. ApplicationEventPublisherAware -> Event publisher of the enclosing ApplicationContext.
      3. BeanClassLoaderAware -> Class loader used to load the bean classes.
      4. BeanFactoryAware -> Declaring BeanFactory.
      5. BeanNameAware -> Name of the declaring bean
      6. LoadTimeWeaverAware -> Defined weaver for processing class definition at load time
      7. MessageSourceAware -> Configured strategy for resolving messages (with support for parametrization and internationalization)
      8. NotificationPublisherAware -> Spring JMX notification publisher
      9. ResourceLoaderAware -> Configured loader for low-level access to resources
      10. ServletConfigAware -> Current ServletConfig the container runs in. Valid only in a web-aware Spring ApplicationContext
      11. ServletContextAware -> Current ServletContext the container runs in. Valid only in a web-aware Spring ApplicationContext
7. Bean definition Inheritance

    ```xml
    <bean id="inheritedTestBeanWithoutClass" abstract="true">
        <property name="name" value="parent"/>
        <property name="age" value="1"/>
    </bean>

    <bean id="inheritsWithClass" class="org.springframework.beans.DerivedTestBean"
            parent="inheritedTestBeanWithoutClass" init-method="initialize">
        <property name="name" value="override"/>
        <!-- age will inherit the value of 1 from the parent bean definition-->
    </bean>
    ```

8. Customizing IoC
   1. Spring's IoC implementation using context can be customized by extending the ApplicationContext and overriding the methods
9. Annotation-based Container Configuration
   1. Are annotations better than XML for configuring Spring?
      1. “it depends.”
      2. Due to the way they are defined, annotations provide a lot of context in their declaration, leading to shorter and more concise configuration
      3. However, XML excels at wiring up components without touching their source code or recompiling them.

## Spring MVC

1. DispatcherServlet
   1. Designed around the front controller pattern where a central Servlet, the DispatcherServlet
   2. The DispatcherServlet, as any Servlet, needs to be declared and mapped according to the Servlet specification by using Java configuration or in web.xml

        ```xml
        <web-app>

            <listener>
                <listener-class>org.springframework.web.context.ContextLoaderListener</listener-class>
            </listener>

            <context-param>
                <param-name>contextConfigLocation</param-name>
                <param-value>/WEB-INF/app-context.xml</param-value>
            </context-param>

            <servlet>
                <servlet-name>app</servlet-name>
                <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
                <init-param>
                    <param-name>contextConfigLocation</param-name>
                    <param-value></param-value>
                </init-param>
                <load-on-startup>1</load-on-startup>
            </servlet>

            <servlet-mapping>
                <servlet-name>app</servlet-name>
                <url-pattern>/app/*</url-pattern>
            </servlet-mapping>

        </web-app>
        ```