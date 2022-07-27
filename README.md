Java Functional Interfaces
An Interface that contains exactly one abstract method is known as functional interface. 
It can have any number of default, static methods but can contain only one abstract method. 
It can also declare methods of object class.

Important Points:
Interfaces can have default methods with implementation in Java 8 on later.
Interfaces can have static methods as well, similar to static methods in classes.
Default methods were introduced to provide backward compatibility for old interfaces so that they can have new methods without affecting existing code.

Java SE 8 included four main kinds of functional interfaces which can be applied in multiple situations. These are:
Consumer-> Consumer<Integer> consumer = (value) ->System.out.println(value);  ->It accepts only one argument has no return value.
Predicate-> Predicate predicate = (value) -> value != null; ->accepts an argument and, in return, generates a boolean value
Function-> that receives only a single argument and returns a value after the required processing
Supplier->public interface Supplier<T>{T.get();} -> does not take any input or argument and yet returns a single output. 

Consumer -> Bi-Consumer
Predicate -> Bi-Predicate
Function -> Bi-Function, Unary Operator, Binary Operator 

@FunctionalInterface  
interface sayable{  
    void say(String msg);   // abstract method  
    // It can contain any number of Object class methods.  
    int hashCode();  
    String toString();  
    boolean equals(Object obj);  
}  

Java 8 provides following features for Java Programming:
Lambda expressions,
Method references,
Functional interfaces,
Stream API,
Default methods,
Optional class,
Collectors class,
ForEach() method,
IO Enhancements,
Concurrency Enhancements,
JDBC Enhancements etc.

Lambda Expressions
Lambda expression helps us to write our code in functional style.
Method References
Java 8 Method reference is used to refer method of functional interface . It is compact and easy form of lambda expression. 
Functional Interface
An Interface that contains only one abstract method is known as functional interface. 
Optional
Java introduced a new class Optional in Java 8. It is a public final class which is used to deal with NullPointerException in Java application.
forEach
Java provides a new method forEach() to iterate the elements. It is defined in Iterable and Stream interfaces.
Date/Time API
Java has introduced a new Date and Time API since Java 8. The java.time package contains Java 8 Date and Time classes.
Default Methods
Java provides a facility to create default methods inside the interface. Methods which are defined inside the interface and tagged with default keyword are known as default methods. These methods are non-abstract methods and can have method body.
Collectors
Collectors is a final class that extends Object class. It provides reduction operations, such as accumulating elements into collections, summarizing elements according to various criteria etc.

Difference between map and flatmap
Both map and flatMap can be applied to a Stream<T> and they both return a Stream<R>. The difference is that the map operation produces one output value for each input value, whereas the flatMap operation produces an arbitrary number (zero or more) values for each input value. This is reflected in the arguments to each operation.

Types of Method References
There are following types of method references in java:
Reference to a static method. -> ContainingClass::staticMethodName  
Reference to an instance method. -> containingObject::instanceMethodName  
Reference to a constructor.-> Messageable hello = Message::new;  

Java Lambda Expression Syntax
(argument-list) -> {body}  
Java lambda expression is consisted of three components.
1) Argument-list: It can be empty or non-empty as well.
2) Arrow-token: It is used to link arguments-list and body of expression.
3) Body: It contains expressions and statements for lambda expression.


why streams in java 8
Introduced in Java 8, the Stream API is used to process collections of objects. A stream is a sequence of objects that supports various methods which can be pipelined to produce the desired result. A stream is not a data structure instead it takes input from the Collections, Arrays or I/O channels.

why streas are lazy in java?
Streams are lazy because intermediate operations are not evaluated until terminal operation is invoked.
Each intermediate operation creates a new stream, stores the provided operation/function and return the new stream.
The pipeline accumulates these newly created streams.
The time when terminal operation is called, traversal of streams begins and the associated function is performed one by one.

    List<Product> productsList = new ArrayList<Product>();  
        //Adding Products  
        productsList.add(new Product(1,"HP Laptop",25000f));  
        productsList.add(new Product(2,"Dell Laptop",30000f));  
        productsList.add(new Product(3,"Lenevo Laptop",28000f));  
        productsList.add(new Product(4,"Sony Laptop",28000f));  
        productsList.add(new Product(5,"Apple Laptop",90000f));  
        List<Float> productPriceList = new ArrayList<Float>();  
		
		 List<Float> productPriceList2 =productsList.stream()  
                                     .filter(p -> p.price > 30000)// filtering data  
                                     .map(p->p.price)        // fetching price  
                                     .collect(Collectors.toList()); // collecting as list  
        System.out.println(productPriceList2);  
		
		 productsList.stream()  
                            .filter(product -> product.price == 30000)  
                            .forEach(product -> System.out.println(product.name));    
							
Stream<String> streamBuilder = Stream.<String>builder().add("a").add("b").add("c").build();

Increase salary by 20
List<Employee> newEployees = a1.stream().map(e -> {e.setSalary(e.getSalary() * 20);return e;}).collect(Collectors.toList());
		
Source − Stream takes Collections, Arrays, or I/O resources as input source.
Aggregate operations − Stream supports aggregate operations like filter, map, limit, reduce, find, match, and so on.
Pipelining − Most of the stream operations return stream itself so that their result can be pipelined. These operations are called intermediate operations and their function is to take input, process them, and return output to the target. collect() method is a terminal operation which is normally present at the end of the pipelining operation to mark the end of the stream.


Generating Streams
With Java 8, Collection interface has two methods to generate a Stream.

stream() − Returns a sequential stream considering collection as its source.
parallelStream() − Returns a parallel Stream considering collection as its source.

List<String> strings = Arrays.asList("abc", "", "bc", "efg", "abcd","", "jkl");
List<String> filtered = strings.stream().filter(string -> !string.isEmpty()).collect(Collectors.toList());

Random random = new Random();
random.ints().limit(10).forEach(System.out::println);

List<Integer> numbers = Arrays.asList(3, 2, 2, 3, 7, 3, 5);

//get list of unique squares
List<Integer> squaresList = numbers.stream().map( i -> i*i).distinct().collect(Collectors.toList());
==========================================================================================================================================================
How Hash map works internally
Hashmap stores the value in the form of key value pair.each key value pair is called as entry set.
Hapmap internally uses the buckets,ech bucket act as singlelly linked list.
Internally HashMap uses a hashCode of the key Object and this hashCode is further used by the hash function to find the index of the bucket where the new entry can be added.

The Fail-Fast system terminates the operation as-fast-as-possible that are exposing failures and stop the entire operation. 
Whereas, Fail-Safe system doesn't terminate the operation that are exposing failures. The Fail-safe system tries to avoid raising Failures as much as possible.

Fail-fast Iterator
When we use the Fail-fast iterator, it immediately throws ConcurrentModificationException
when an element is added or removed from the collection while the thread is iterating over the collection. Examples: Iterator in HashMap, Iterator on ArrayList, etc.

Fail-safe Iterator
The Java SE specification doesn't use the Fail-safe term. It is better to call it a Non-Fail-fast Iterator. The Fail-safe iterator doesn't throw the ConcurrentModificationException, and it tries to avoid raising the exception. The Fail-safe iterator creates a copy of the original collection or object array and iterates over that copied collection. Any structural modification made in the iterator affects the copied collection, not the original collection. Therefore, the original collection remains structurally unchanged.

==========================================================================================================================================================
Different ways to create objects in Java
Using new keyword
Using new instance
Using clone() method
Using deserialization
Using newInstance() method of Constructor class

Object class has below methods
toString() Method.
hashCode() Method.
equals(Object obj) Method.
getClass() method.
finalize() method.
clone() method.
wait(), notify() notifyAll() Methods.

Superclass and sublass exception
1. If an overridden method does not throw an exception using throws clause then

The overriding method can not throw any checked or compile-time exception.
The overriding method can throw any unchecked or runtime exception.
2. If an overridden method throws an unchecked or runtime exception then

The overriding method can throw any unchecked or runtime exception.
The overriding method can throw the same exception which is thrown by the overridden method.
The overriding method can ignore the method level exception.
3. If the superclass method throws checked or compile-time exception then

Subclass method can throw an exception which is a subclass of the superclass method’s exception.
Subclass method cannot throw the exception which is a superclass of the superclass method’s exception.
Subclass method can throw any unchecked or runtime exception.

HTTP status codes are divided into 5 classes based on the first digit of the status code:
1xx – informational – the request was received, continuing process
2xx – successful – the request was received successfully and accepted
3xx – redirection – further action needs to be taken to complete the request
4xx – client error – request contains bad syntax or cannot be fulfilled
5xx – server error – the server failed to fulfill an apparently valid request

5 different ways to create objects in Java
1. Using new keyword.

Tester tester1 = new Tester();
2. Using Class.forName() method

Tester tester2 = (Tester)Class.forName("Tester").newInstance();
3. Using clone method.

Tester tester3 = tester1.clone();
4. Using Constructor.forName() method

Tester tester4 = Tester.class.getConstructor().newInstance();
5. Using Deserialization

ObjectInputStream objectInputStream = new ObjectInputStream(inputStream );
Tester tester5 = (MyObject) objectInputStream.readObject();
 Using new keyword is the most preferred one.
 
var a = true;
var b = 1;
var c = true;
console.log (a == b); //true first convert 1 into boolean true then compare
console.log (a === c); //true both are of same type no conversion required simple compare.
console.log (a === b); //false no conversion performed and type of both operands are not of same type so expected result is false.
==========================================================================================================================================================
Serialization is process of converting object into byte stream. 
 Serialized object (byte stream) can be:
 >Transferred over network.
 >Persisted/saved into file.
 >Persisted/saved into database.
 
OutputStream fout = new FileOutputStream("ser.txt");
ObjectOutput oout = new ObjectOutputStream(fout);
System.out.println("Serialization process has started, serializing employee objects...");
oout.writeObject(object1);

InputStream fin=new FileInputStream("ser.txt");
ObjectInput oin=new ObjectInputStream(fin);
System.out.println("DeSerialization process has started, displaying employee objects...");
Employee emp;
emp=(Employee)oin.readObject();

Java Serialization with the static data member
If there is any static data member in a class, it will not be serialized because static is the part of class not object.

Java Transient Keyword
If you don't want to serialize any data member of a class, you can mark it as transient.

What is serialVersionUID?
Answer. The serialization at runtime associates with each serializable class a version number, called a serialVersionUID, which is used during deserialization to verify that the sender and receiver of a serialized object have loaded classes for that object that are compatible with respect to serialization. 

 Why static member variables are not part of java serialization process (Important)?
Answer. Serialization is applicable on objects or primitive data types only, but static members are class level variables, therefore, different object’s of same class have same value for static member. 
So, serializing static member will consume unnecessary space and time.
Also, if modification is made in static member by any of the object, it won’t be in sync with other serialized object’s value.

What is significance of transient variables?
Answer. Serialization is not applicable on transient variables (it helps in saving time and space during Serialization process), we must mark all rarely used variables as transient. We can initialize transient variables during deSerialization by customizing deSerialization process.

Is constructor of class called during DeSerialization process?
Answer. This question which will check your in depth knowledge of Serialization and constructor chaining concepts. It depends on whether our object has implemented Serializable or Externalizable.
If Serializable has been implemented - constructor is not called during DeSerialization process.
But, if Externalizable has been implemented - constructor is called during DeSerialization process.

15. Find out the difference between Serialization and Externalizable?
For default serialization, we use the Serializable interface but with the Externalization interface, we can have more control over serialization. Serializable is a marker interface. That’s why there are no user-defined methods. But in Externalization, we can write the method inside the interface and implement it to the child classes. For this reason, we have more control over serialization and deserialization. The Externalizable interface also extends Serializable interface

Serializable like below snapshot:
public interface Serializable {

}

An externalizable interface like below snapshot:
public interface Externalizable extends java.io.Serializable {
void writeExternal(ObjectOutput out) throws IOException;
void readExternal(ObjectInput in) throws IOException, ClassNotFoundException;
}

What are the most important classes and interfaces using the Serialization?
Most commonly used classes and interfaces are listed below:
a) java.io.Serializable
b) java.io.Externalizable
c) java.io.ObjectInputStream
d) java.io.ObjectOutputStream
e) java.io.FileInputStream
f) java.io.FileOutputStream

==========================================================================================================================================================


==========================================================================================================================================================
Collections

10. How the Collection objects are sorted in Java?
Sorting in Java Collections is implemented via Comparable and Comparator interfaces. When Collections.sort()  method is used the elements get sorted based on the natural order that is specified in the compareTo() method. On the other hand when Collections.sort(Comparator) method is used it sorts the objects based on compare() method of the Comparator interface. 

==========================================================================================================================================================

1) What is hibernate?
Hibernate is an open-source and lightweight ORM tool that is used to store, manipulate, and retrieve data from the database.

2) What are some of the important interfaces of Hibernate framework?
Hibernate core interfaces are:
Configuration
SessionFactory
Session
Criteria
Query
Transaction

What is the use of CascadeType all in hibernate?
The property cascade = CascadeType. ALL indicates that when we persist, remove, refresh or merge this entity all the entities held in this field would be persist, remove, delete or update.

@OneToOne(mappedBy = "employee")
   @Cascade(value = org.hibernate.annotations.CascadeType.ALL)
   private Address address;

2) What is a Session in Hibernate?
A session is an object that maintains the connection between Java object application and database. 
Session also has methods for storing, retrieving, modifying or deleting data from database 
using methods like persist(), load(), get(), update(), delete(), etc. Additionally, 
It has factory methods to return Query, Criteria, and Transaction objects.

diffrence between
Save SaveOrUpdate
save method will return exception if id is already present.
SaveOrUpdate it will save if id is not present and updates if id already exists.

save and persist
The first difference between save and persist is there return type. 
Similar to save method, persist also INSERT records into the database,
but return type of persist is void while return type of save is Serializable Object.

update and merge
update : if we closed the session and object is present in cashe means it will throw exception()
merge : if we closed the session and object is present in cashe means it will not throw exception it will insert the data in database
Merge: if you want to save your modifications at any time with out knowing about the state of an session, then use merge() in hibernate.

get and load
get is early loading means it will hit database and return the object
load is lazy loading means it will return the object from cashe.


3) What is a SessionFactory?
SessionFactory provides an instance of Session. It is a factory class that gives the Session objects based on the configuration parameters in order to establish the connection to the database.
As a good practice, the application generally has a single instance of SessionFactory. The internal state of a SessionFactory which includes metadata about ORM is immutable, i.e once the instance is created, it cannot be changed.

This also provides the facility to get information like statistics and metadata related to a class, query executions, etc. It also holds second-level cache data if enabled.

4) What do you think about the statement - “session being a thread-safe object”?
No, Session is not a thread-safe object which means that any number of threads can access data from it simultaneously.

5) Can you explain what is lazy loading in hibernate?
Lazy loading is mainly used for improving the application performance by helping to load the child objects on demand.

It is to be noted that, since Hibernate 3 version, this feature has been enabled by default. This signifies that child objects are not loaded until the parent gets loaded.

2)Properties of transaction
Database system ensures ACID property −

Atomicity − Either all or none of the transaction operation is done.

Consistency − A transaction transfer from one consistent (correct) state to another consistent state.

Isolation − A transaction is isolated from other transactions. i.e. A transaction is not affected by another transaction. Although multiple transactions execute concurrently it must appear as if the transaction are running serially (one after the other).

Durability − The results of transactions are permanent i.e. the result will never be lost with subsequent failure, durability refers to long lasting i.e. permanency.

Difference between Transient, Persistent, and Detached Objects in Hibernate
==========================================================================================================================================================
What is the role of IOC container in spring?
IOC container is responsible to:
create the instance
configure the instance, and
assemble the dependencies

What are the types of IOC container in spring?
There are two types of IOC containers in spring framework.
BeanFactory
ApplicationContext

What is the difference between BeanFactory and ApplicationContext?
BeanFactory is the basic container whereas ApplicationContext is the advanced container. 
ApplicationContext extends the BeanFactory interface. 
ApplicationContext provides more facilities than BeanFactory such as integration with spring AOP, message resource handling for i18n etc.

Dependency Injection
The Dependency Injection is a design pattern that removes the dependency of the programs. 
In such case we provide the information from the external source such as XML file. It makes our code loosely coupled and easier for testing. 

Spring framework provides two ways to inject dependency
By Constructor
By Setter method

What is autowiring in spring? What are the autowiring modes?
Autowiring enables the programmer to inject the bean automatically. We don't need to write explicit injection logic.

<bean id="emp" class="com.javatpoint.Employee" autowire="byName" />  
The autowiring modes are given below:

No.	Mode	Description
1)	no			this is the default mode, it means autowiring is not enabled.
2)	byName		injects the bean based on the property name. It uses setter method.
3)	byType		injects the bean based on the property type. It uses setter method.
4)	constructor	It injects the bean using constructor

<!-- A bean definition with singleton scope -->
<bean id = "..." class = "..." scope = "singleton">
   <!-- collaborators and configuration for this bean go here -->
</bean>

What are the different bean scopes in spring?
There are 5 bean scopes in spring framework.

No.	Scope		Description
1)	singleton	The bean instance will be only once and same instance will be returned by the IOC container. It is the default scope.
2)	prototype	The bean instance will be created each time when requested.
3)	request		The bean instance will be created per HTTP request.
4)	session		The bean instance will be created per HTTP session.
5)	globalsession	The bean instance will be created per HTTP global session. It can be used in portlet context only.

In which scenario, you will use singleton and prototype scope?
Singleton scope should be used with EJB stateless session bean and prototype scope with EJB stateful session bean.

How can you fetch records by spring JdbcTemplate?
You can fetch records from the database by the query method of JdbcTemplate. There are two interfaces to do this:

ResultSetExtractor
RowMapper

==========================================================================================================================================================
SPRINGBOOT 

@SpringBootApplication: It is a combination of three annotations @EnableAutoConfiguration, @ComponentScan, and @Configuration.

@EnableAutoConfiguration: It auto-configures the bean that is present in the classpath and configures it to run the methods. The use of this annotation is reduced in Spring Boot 1.2.0 release because developers provided an alternative of the annotation, i.e. @SpringBootApplication.
@EnableAutoConfiguration annotation enables Spring Boot to auto-configure the application context.

@Configuration: It is a class-level annotation. The class annotated with @Configuration used by Spring Containers as a source of bean definitions.

@ComponentScan: It is used when we want to scan a package for beans. It is used with the annotation @Configuration. We can also specify the base packages to scan for Spring Components.

@Required: It applies to the bean setter method. It indicates that the annotated bean must be populated at configuration time with the required property, else it throws an exception BeanInitilizationException.

@Bean: It is a method-level annotation. It is an alternative of XML <bean> tag. It tells the method to produce a bean to be managed by Spring Container.

@Component: It is a class-level annotation. It is used to mark a Java class as a bean. A Java class annotated with @Component is found during the classpath. The Spring Framework pick it up and configure it in the application context as a Spring Bean.

@Controller: The @Controller is a class-level annotation. It is a specialization of @Component. It marks a class as a web request handler. It is often used to serve web pages. By default, it returns a string that indicates which route to redirect. It is mostly used with @RequestMapping annotation.

@Service: It is also used at class level. It tells the Spring that class contains the business logic.

@Repository: It is a class-level annotation. The repository is a DAOs (Data Access Object) that access the database directly. The repository does all the operations related to the database.

@RequestMapping: It is used to map the web requests. It has many optional elements like consumes, header, method, name, params, path, produces, and value. We use it with the class as well as the method.

The @Qualifier annotation is used to resolve the autowiring conflict, when there are multiple beans of same type.

Controller Advice : The @ControllerAdvice is an annotation, to handle the exceptions globally.

Exception Handler : The @ExceptionHandler is an annotation used to handle the specific exceptions and sending the custom responses to the client.

@GetMapping: It maps the HTTP GET requests on the specific handler method. It is used to create a web service endpoint that fetches It is used instead of using: @RequestMapping(method = RequestMethod.GET)
@PostMapping: It maps the HTTP POST requests on the specific handler method. It is used to create a web service endpoint that creates It is used instead of using: @RequestMapping(method = RequestMethod.POST)
@PutMapping: It maps the HTTP PUT requests on the specific handler method. It is used to create a web service endpoint that creates or updates It is used instead of using: @RequestMapping(method = RequestMethod.PUT)
@DeleteMapping: It maps the HTTP DELETE requests on the specific handler method. It is used to create a web service endpoint that deletes a resource. It is used instead of using: @RequestMapping(method = RequestMethod.DELETE)
@PatchMapping: It maps the HTTP PATCH requests on the specific handler method. It is used instead of using: @RequestMapping(method = RequestMethod.PATCH)
@RequestBody: It is used to bind HTTP request with an object in a method parameter. Internally it uses HTTP MessageConverters to convert the body of the request. When we annotate a method parameter with @RequestBody, the Spring framework binds the incoming HTTP request body to that parameter.
@ResponseBody: It binds the method return value to the response body. It tells the Spring Boot Framework to serialize a return an object into JSON and XML format.
@PathVariable: It is used to extract the values from the URI. It is most suitable for the RESTful web service, where the URL contains a path variable. We can define multiple @PathVariable in a method.
@RequestParam: It is used to extract the query parameters form the URL. It is also known as a query parameter. It is most suitable for web applications. It can specify default values if the query parameter is not present in the URL.
@RequestHeader: It is used to get the details about the HTTP request headers. We use this annotation as a method parameter. The optional elements of the annotation are name, required, value, defaultValue. For each detail in the header, we should specify separate annotations. We can use it multiple time in a method
@RestController: It can be considered as a combination of @Controller and @ResponseBody annotations. The @RestController annotation is itself annotated with the @ResponseBody annotation. It eliminates the need for annotating each method with @ResponseBody.
@RequestAttribute: It binds a method parameter to request attribute. It provides convenient access to the request attributes from a controller method. With the help of @RequestAttribute annotation, we can access objects that are populated on the server-side.
==========================================================================================================================================================
1.Describe key points of OOP like Inheritance, Polymorphism, Encapsulation, and Abstraction. 

Encapsulation in Java is a mechanism of wrapping the data (variables) and code acting on the data (methods) together as a single unit. In encapsulation, the variables of a class will be hidden from other classes, and can be accessed only through the methods of their current class.

2.Difference between Overloading and Overriding. 

3.Can protected method be overridden? 
Yes, the protected method of a superclass can be overridden by a subclass. If the superclass method is protected, the subclass overridden method can have protected or public

4.What is String Constant Pool? 
A string constant pool is a separate place in the heap memory where the values of all the strings which are defined in the program are stored. When we declare a string, an object of type String is created in the stack, while an instance with the value of the string is created in the heap.21

5.Why we make String as immutable? 
Being immutable automatically makes the String thread safe since they won't be changed when accessed from multiple threads. 
Hence immutable objects, in general, can be shared across multiple threads running simultaneously.

Why do we create immutable class in Java?
Immutable objects are thread-safe so you will not have any synchronization issues.

Immutable class in java means that once an object is created, we cannot change its content. In Java, all the wrapper classes (like Integer, Boolean, Byte, Short) and String class is immutable. 

6.	Steps to make our own immutable class? 
	1.	Declare the class as final so it can’t be extended.
	2.	Make all fields private so that direct access is not allowed.
	3.	Don’t provide setter methods for variables.
	4.	Make all mutable fields final so that its value can be assigned only once.
	5.	Initialize all the fields via a constructor performing deep copy.
	6.	Perform cloning of objects in the getter methods to return a copy rather than returning the actual object reference.
	
7.	What is String Tokenizer? 
The string tokenizer class allows an application to break a string into tokens. The tokenization method is much simpler than the one used by the StreamTokenizer class. 
The StringTokenizer methods do not distinguish among identifiers, numbers, and quoted strings, nor do they recognize and skip comments.

8.	Which type of Collection you have used in your project? 

9.	Difference between Array List and Linked List?    

10.	Describe all main Collections? like List, Set & Map. 

11.	If we have bulk of data, then which type of collection you have used for memory utilization? 

12.	Hash Map internal working. 

13.	What is Hash Collision? 
A collision occurs when two keys are hashed to the same index in a hash table. Collisions are a problem because every slot in a hash table is supposed to store a single element. ... All key-value pairs mapping to the same index will be stored in the linked list of that index.

14.	What is difference between ClassNotFoundException and ClassNotDefFoundError? 
ClassNotFoundException is an exception while NoClassDefFoundError is an error.
ClassNotFoundException occurs when classpath does not get updated with required JAR files while error occurs when the required class definition is not present at runtime.

15.	What is difference between new operator & newInstance() method? 
Unlike the new operator which can call both no-args and parameterized constructors, but the newInstance() method will only be able to call only the no-args constructor when a class has only parameterized constructors we cannot use newInstance() method.

16.	What are the inbuild functional interface in Java8 like Consumer,Predicate,Supplier,Function FI? 

17.	What is Peek() method in java8? 

18.	What is difference between map() and flatMap() in Java8? 
The difference is that the map operation produces one output value for each input value, whereas the flatMap operation produces an arbitrary number (zero or more) values for each input value.
19.	A employee class are there in which different parameter like id,name,gender,department,salary, age, dateOfJoninig are there , find name of employee and their salary based on their department .   

20.	Key Features of Spring Boot. 

21.	Key Annotations of Spring boot. 

22.	How to get information about all the beans in the spring boot? 
private ApplicationContext appContext;
String[] beans = appContext.getBeanDefinitionNames();

23.	How to make Custom Endpoint? 

24.	Junit and Mockito testing- how to test Exception? 


==========================================================================================================================================================

1) how hashmap works internally 

2) what is peek method 

3) where you use multithreading in your project 

4)clone () implementation 

5)how to get date and time in java 8 

6)explain functional interface 

7)spring MVC flow 

8)explain @springbootapplication annotation 

9)java 8 features 

10) why we use microservices  

11) difference b/w spring and springboot 

12)logical questions on StreamAPI  java 8 

13)weekhashmap and identityhashmap 

==========================================================================================================================================================
1)spring singleton disadvantages. 

2)String reverse number using recursion 

3)Parallel v's Sequential Stream in Java 

4)If you have 4Gb Ram, and if you want to iterate 8Gb data?  How to overcome this 

5)Can we make serialization class for singleton? 

6)Spring IOC 

7)Why spring default singleton scope? elaborate spring scope. 

8)java 8 options 

9)Why we make Generics in java. 

10)How to iterate 8Gb of data in java 

11)What is the use of enums in java? 

12)If you have deployed your application in two servers? how to communicate each server? 

13)Cannot Create Instances of Type Parameters. 

14)generics limitations in java 

15)How to prevent Singleton Pattern from Reflection, Serialization and Cloning 
throw a run-time exception in the constructor if the instance already exists

16)How to deal with Singleton along with Serialization 

17)Singleton multithreading java 

18)Sort large in java 

19)Java 8 Optional In Depth 

20)Spring actuator example 

==========================================================================================================================================================

what are the java 8 features you have worked? 

2- what are the types of stream in java 8. Explain them. 

3- what is functional interface and optional in java 8. what does predicate method do. 

4- suppose in a class we have a field, dept of string type and list<Emp> name.So I need to find  

   out the list of employees based on dept. Which datastructure we can use & How to do in java 8. 

5- Suppose we have List<Number> num = new ArrayList<Integer>(); So whether it will throw any error or it will work correctly. 

6- Suppose in an Employee class we have dept and empName fields and 1 constructor to initialize those fields. and in main method we call like  

   Employee e1 = new Employee("it","abc"); 

   Employee e2 = new Employee("it","abc");  

   After that we need to add these e1 and e2 in set. So what is the size of the set? 

7- Suppose we have list of elements and i want to do any delete operation. So which is preferable linked List or ArrayList. 

8- Give a real time example where to use Abstract class and where to use interface and why. 

9- internal working of HashSt & HashMap. 

10- what is actuator 

11- suppose we have a .jar file and classes A, B, C uses this .jar file and I want to use 1 feature in class A but not in classes B & C. 

    So how can we do that. 

12- Why we need to override equals().  

13- What is generics. Use of generics. What are the limitations of generics. 

==========================================================================================================================================================

1. Constructors used in different patterns 

2. Hands on example of encapsulation 

3. Hashset and treeset 

4. Multiple Inheritance in java 

5. Abstract class vs abstract method vs interface 

6. Explain with handson exp Synchronisation vs non - synchronisation. 

==========================================================================================================================================================

==========================================================================================================================================================

1.  Describe key points of OOP like Inheritance, Polymorphism, Encapsulation, and Abstraction. 

2.	Difference between Overloading and Overriding. 

3.	Can protected method be overridden? 
Yes, the protected method of a superclass can be overridden by a subclass. If the superclass method is protected, the subclass overridden method can have protected or public

4.	What is String Constant Pool? 
A string constant pool is a separate place in the heap memory where the values of all the strings which are defined in the program are stored. When we declare a string, an object of type String is created in the stack, while an instance with the value of the string is created in the heap.21

5.	Why we make String as immutable? 
Being immutable automatically makes the String thread safe since they won't be changed when accessed from multiple threads. Hence immutable objects, in general, can be shared across multiple threads running simultaneously.

6.	Steps to make our own immutable class? 
1.	Declare the class as final so it can’t be extended.
2.	Make all fields private so that direct access is not allowed.
3.	Don’t provide setter methods for variables.
4.	Make all mutable fields final so that its value can be assigned only once.
5.	Initialize all the fields via a constructor performing deep copy.
6.	Perform cloning of objects in the getter methods to return a copy rather than returning the actual object reference.

7.	What is String Tokenizer? 
The string tokenizer class allows an application to break a string into tokens. The tokenization method is much simpler than the one used by the StreamTokenizer class. The StringTokenizer methods do not distinguish among identifiers, numbers, and quoted strings, nor do they recognize and skip comments.
8.	Which type of Collection you have used in your project? 

9.	Difference between Array List and Linked List?    

10.	Describe all main Collections? like List, Set & Map. 

11.	If we have bulk of data, then which type of collection you have used for memory utilization? 

12.	Hash Map internal working. 

13.	What is Hash Collision? 
A collision occurs when two keys are hashed to the same index in a hash table. Collisions are a problem because every slot in a hash table is supposed to store a single element. ... All key-value pairs mapping to the same index will be stored in the linked list of that index.

14.	What is difference between ClassNotFoundException and ClassNotDefFoundError? 
ClassNotFoundException is an exception while NoClassDefFoundError is an error. ClassNotFoundException occurs when classpath does not get updated with required JAR files while error occurs when the required class definition is not present at runtime.

15.	What is difference between new operator & newInstance() method? 
Unlike the new operator which can call both no-args and parameterized constructors, but the newInstance() method will only be able to call only the no-args constructor when a class has only parameterized constructors we cannot use newInstance() method.

16.	What are the inbuild functional interface in Java8 like Consumer,Predicate,Supplier,Function FI? 

17.	What is Peek() method in java8? 

18.	What is difference between map() and flatMap() in Java8? 
The difference is that the map operation produces one output value for each input value, 
whereas the flatMap operation produces an arbitrary number (zero or more) values for each input value.

19.	A employee class are there in which different parameter like id,name,gender,department,salary, age, dateOfJoninig are there , find name of employee and their salary based on their department .   

20.	Key Features of Spring Boot. 

21.	Key Annotations of Spring boot. 

22.	How to get information about all the beans in the spring boot? 
private ApplicationContext appContext;
String[] beans = appContext.getBeanDefinitionNames();

23.	How to make Custom Endpoint? 

24.	Junit and Mockito testing- how to test Exception? 

==========================================================================================================================================================

1) how hashmap works internally 

2) what is peek method 

3) where you use multithreading in your project 

4)clone () implementation 

5)how to get date and time in java 8 

6)explain functional interface 

7)spring MVC flow 

8)explain @springbootapplication annotation 

9)java 8 features 

10) why we use microservices  

11) difference b/w spring and springboot 

12)logical questions on StreamAPI  java 8 

13)weekhashmap and identityhashmap 

 
==========================================================================================================================================================
1)spring singleton disadvantages. 

2)String reverse number using recursion 

3)Parallel v's Sequential Stream in Java 

4)If you have 4Gb Ram, and if you want to iterate 8Gb data?  How to overcome this 

5)Can we make serialization class for singleton? 

6)Spring IOC 

7)Why spring default singleton scope? elaborate spring scope. 

8)java 8 options 

9)Why we make Generics in java. 

10)How to iterate 8Gb of data in java 

11)What is the use of enums in java? 

12)If you have deployed your application in two servers? how to communicate each server? 

13)Cannot Create Instances of Type Parameters. 

14)generics limitations in java 

15)How to prevent Singleton Pattern from Reflection, Serialization and Cloning 
throw a run-time exception in the constructor if the instance already exists

16)How to deal with Singleton along with Serialization 

17)Singleton multithreading java 

18)Sort large in java 

19)Java 8 Optional In Depth 

20)Spring actuator example 

==========================================================================================================================================================
1- what are the java 8 features you have worked?

2- what are the types of stream in java 8. Explain them. 

3- what is functional interface and optional in java 8. what does predicate method do. 

4- suppose in a class we have a field, dept of string type and list<Emp> name.So I need to find  

   out the list of employees based on dept. Which datastructure we can use & How to do in java 8. 

5- Suppose we have List<Number> num = new ArrayList<Integer>(); So whether it will throw any error or it will work correctly. 

6- Suppose in an Employee class we have dept and empName fields and 1 constructor to initialize those fields. and in main method we call like  

   Employee e1 = new Employee("it","abc"); 

   Employee e2 = new Employee("it","abc");  

   After that we need to add these e1 and e2 in set. So what is the size of the set? 

7- Suppose we have list of elements and i want to do any delete operation. So which is preferable linked List or ArrayList. 

8- Give a real time example where to use Abstract class and where to use interface and why. 

9- internal working of HashSt & HashMap. 

10- what is actuator 

11- suppose we have a .jar file and classes A, B, C uses this .jar file and I want to use 1 feature in class A but not in classes B & C. 

    So how can we do that. 

12- Why we need to override equals().  

13- What is generics. Use of generics. What are the limitations of generics. 
==========================================================================================================================================================
1. Constructors used in different patterns 

2. Hands on example of encapsulation 

3. Hashset and treeset 

4. Multiple Inheritance in java 

5. Abstract class vs abstract method vs interface 

6. Explain with handson exp Synchronisation vs non - synchronisation. 


========================================================================================================================================================
Sample Interview Questions  

What is OOPS and give a real-life example on OOPS. What are the disadvantages of OOPS? 

What is the use of generics in collections? 

What is the algorithm of garbage collection? 

How hashmap works? How does hashmap GET and PUT methods work? 

What is Blocking Queue? 

When does catch block become unreachable? 

What is the difference between Error and Exception? Name some error class and exception class? 

What is runtime exception and what is compile-time exception? What is better, getting compile time error or runtime error? 

Explain Executor framework. (Multithreading) 

What is diamond problem in java? How do we overcome diamond problem in java? What if 1 class implements 2 interfaces and both the interfaces are having the same method (name, signature, return-type and access specifier) and will overriding the method, Which interface method will get overridden? 

What is reflection API? Give a name of application where reflection is API is used. 

How to create a custom exception? 

Difference between checked exception and unchecked exception. 

When does ClassNotFoundException occur and when does NoClassDefFoundError occur? 

What are the states of bean in spring-boot? 

What are the annotations you have used in spring-boot? 

What is @Qualifier annotation used for in spring-boot? 

What is the difference between Spring and Spring-boot? 

Can you explain the flow how spring MVC works? 

What is the use of Internal View Resolver? 

What is DevTools in spring boot? What is the use of it? 

Difference between @Service, @Repository, and @Component in spring-boot? 

In maven project if the library is present in our local system, and we need to add that library into our project, How we will do that? 

What is maven used for? 

What will happen if we run the command "mvn clean"? 

What all maven commands you have ran? 

What are the types of Dependency Injection. Explain with example. 

What is difference between HashTable and HashMap 

Iterating in  ArrayList 

What is Ellipsis in Java 

Explain SOLID principles 

Explain Association and Aggression  

How does Deque work 

Life cycle of spring bean  

What is the tool used for to check test coverage  

Difference between fetch and pull in Git 

How do you push the code after locally committed 

Streams in Java 8  

Dymond problem in java 8  

what is the need of functional interface?  

Difference bw collection and streams 

Spring MVC vs Spring Boot 

Describe Hashmap internal memory mapping 

In addition prepare on the below topics 

Java 7 to Java 8 diff 

Multithreading  

Mockito testing and Annotations 
Mockito testing and Annotations 

Bit bucket 

Gradle/Maven 

How to configure Jenkins pipeline 

Some business scenarios related to the project 

Examples like palindrome, creating linked lists 

SQL -basics 

Basic Unix commands 

Why is SonarQube used 
==========================================================================================================================================================
1)how to prevent a class from being subclass in java?
make class as final

2)Can we override static method?
What is method hiding?
Method hiding can be defined as, "if a subclass defines a static method with the same signature as a static method in the super class, in such a case, the method in the subclass hides the one in the superclass." The mechanism is known as method hiding. It happens because static methods are resolved at compile time.

3)when to use abstract class and interface

4)why we need Generics in Java
for type safe and remove classcastexception

5)Diff B/w Loose Coupling and Tight Coupling
loose coupling - reducing dependence betweeen classes and objects 
tight coupling - classes and objects are dependent eachother

What is serialization and why it is used?
Serialization is the process of converting an object into a stream of bytes to store the object or transmit it to memory, a database, or a file. Its main purpose is to save the state of an object in order to be able to recreate it when needed. The reverse process is called deserialization

6)Real time examples for java collections in the project 
1)Storing the data in the form of key value pair
2)Search the data in the collection class
3)Removing the duplicate data by using sets
4)Hold the data and transfer the data from UI to database and vice versa
5)fetch the data from the database and store each record in the suitable class.

volatile keyword important points
You can use the volatile keyword with variables. Using volatile keyword with classes and methods is illegal.
It guarantees that value of the volatile variable will always be read from the main memory, not from the local thread cache.
If you declared variable as volatile, Read and Writes are atomic
It reduces the risk of memory consistency error.
Any write to volatile variable in Java establishes a happen before the relationship with successive reads of that same variable.
The volatile variables are always visible to other threads.
The volatile variable that is an object reference may be null.
==========================================================================================================================================================
1)How hash map works internally
2)How hashset works
3)design pattrens
4)what is volitail keyword
5)trasent keyword
6)What is SOLID concept?

public class Test {
public void print(Integer i) {
System.out.println("Integer");
}
public void print(int i) {
System.out.println("int");
}
public void print(long i) {
System.out.println("long");
}
public static void main(String args[]) {
Test test = new Test();
test.print(10);
}
}

5)Remove repitative words
String s = "welcome to geeks for geeks to homeland"
Output - welcome to geeks for homeland

6)String s="ssaabbbcaaddzz"; count how many times char repeated

7) my name is chaitanya -> chaitanya is name my 
