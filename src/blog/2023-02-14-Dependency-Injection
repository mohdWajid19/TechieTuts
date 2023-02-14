# A simple program demonstrating the example and use of Dependency Injection (Constructor-Dependency-Injection-Method). 
#### Note: I have used Csharp as demonstration language, the concept remains same, just the way you write changes. And the example I used uses Constructor-Dependency-Injection-Method.


## What actually is Dependency Injection, and why do we need it?
- before understanding what dependency Injection is we have to understand few concepts of Software Development and OOPs
  if you think you already know the concepts you can skip to dependency injection part.
  ### 1. Tight Coupling: 
      - We say that a group of classes are tightly coupled when "Classes in that group are Highly dependent on one another".
      
      - Dependent means one class requires the object of other class to function properly. i.e. one client-class requires 
        the service(object) of service-provider-class.
        
      - So to use an object(service) of other-class(service-provider-class) in main-class(client-class) we instantiate 
        the service-class in client-class using "new" keyword(again it depends upon programming language how you create an object).
        
      - The moment we instantiate using the new keyword we are tightly-coupling the service-class with the client-class.
      
      - This is fine till this point, but in future if you want to change the service, then you need to modify the content/code in 
        the client-class, this seems fine for a small application but for an application at enterprise level where this service is 
        used quite oftenly changing the object is highly unfeasable in all classes and also we voilate one of the rules of 
        SOLID principles (that is a class should be open for extension but closed for modification).
        
      - So tight coupling is something which we want to avoid in our application. hence we go with loose coupling.
      
      - Eg: say a class logger(service-provider-class) provides a service by logging the details in a file, we bind the main-class 
            with the logger class and It works, but when we want to now change the service to instead of logging the details in a 
            file we want it to log the details in a database then, as the requirement (the service) changed we have to change 
            the logger class which is our service-provider. Hence all the classes which depend on this service(object) for logging 
            needs to be modified. This overhead of work occured, due to tight coupling of classes.
            
  ### 2. Loose Coupling:
      - Loose Coupling is opposite to the Tight Coupling, Here all the classes are independent or less dependent on services or 
        objects of other classes or service-provider-class.
      - Hence when the dependency is said to be low we say the classes are Loosely Coupled.
      - In this Coupling, upon changing the service we donot modify the code in client-class.
      - Loose coupling also helps in achieving the single responsibility and less concern of changing services.
 
  ### 3. Interfaces:
      - used to specify the behaviour of a class
      - blueprint of a class
      - contains static constants and abstract methods
      - mechanism to achieve 100% abstraction
      - used to achieve abstraction and multiple inheritance in java
      - interfaces can have abstract methods and variables, cannot have a method body.
      
  ### Need for Dependency Injection.
   - Now we understood the types of coupling and difficulties/ problems due to Tight coupling we now want to change our tightly coupled
     classes into loosely coupled ones, ie hightly dependent classes into less dependent ( or Independent classes ), but how?
   
   - "To convert a tightly coupled class into a loosely coupled, we use Dependency Injection".
   
   - Real-Life-Example:
       - Let us say there are three People A, B, C. B & C took the loan from person A, and skipped the repayment, now 
      until B or C returns the amount A becomes dependent on B. any person B or C getting away will affect the life of A, this is what 
      happens in Tight Coupling where A is a client and B, C are service providers.             

       - To avoid such situation we bring a main-incharge(An Injector Class) of B, C who is well settled, and
      will be responsible for any service or repayment by B, C. so now A does not have to depennd on B, C. and is now 
      Independent as main-incharge(Injector Class) assures the repayment(Service) from B or C when required depending
      on the situation, this is what happens in Loose Coupling.
                            
   - As mentioned above we include the interfence of Injector class which takes care of service(object) provided by service-provider-class,
     and change our tightly coupled classes into loosely coupled ones, as the Injector class injects the dependency required by client-class
     or dependent class, the process is termed as dependency Injection.
   
   ### Dependency Injection:
      - As the name suggests, It is the process in which a class injects the dependency
        (i.e. service or object of service-provider-class) into the client-class (dependent-class) using that service(object).
      - Generally we use a static class which has static method which returns the service(object).
      - Dependency Injection can be of three types
       1> Constructor Injection        : Injector supplies the service(dependency) through the client class constructor.
       2> Setter or Property Injection : Injector supplies the service(dependency) through the public property of the client 
                                         class.
       3> Method Injection             : Injector supplies the service(dependency) through the methods. This methods could be
                                         class methods or Interface methods.
        
   - Now Again a Question arises How do we change the reference of service-provider-classes without modifying the client-class ? 
      - The answer is simple we use Interface, which is inturn implemented by these service-providers and 
        all the services(objects) are instantiated by Injector class, in its definition which is changeable overtime.
      - This newly instantiated object is returned to the requested client service. And hence any changes to the service is done 
        at the injector class level and does not need to modify the code in client-class. as the objects are provided by Injector.     
