# Dependency Injection

 
  - **Definition**:
    Dependency injection is a programming technique in which an object or function receives other objects or functions that it depends on. 

  - **Use Case**:
    Dependency Injection is used when an object depends on another object to perform its tasks. 
    
  - **Benefits**:
    DI makes the code more maintainable, reusable, and testable. By delegating the creation of dependencies to an external framework, it allows components to be more decoupled and modular. 

  - **Extra information**:
    In Angular, dependencies are defined by providers. When a component requires a dependency, Angular uses the injector to find the appropriate provider for that service. This provider then returns a new or shared instance of the dependency.


    ---

 