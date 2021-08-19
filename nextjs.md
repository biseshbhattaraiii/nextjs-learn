# Next.js 

## Basic overview

    1. Compatible with both typescript and pure javascript . 
    2 . (main.ts) To create a Nest application instance , we use the core NestFactory class . The ```create()``` method returns an application object , which fulfills the ```INestApplication``` interface . 
    3 . HTTP platforms supported out-of-the-box are express and fastify 

#### Controllers 
        1. used for handling incoming requests and returning responses to the client 
        ![](https://docs.nestjs.com/assets/Controllers_1.png)
        2. each controller has more than one route , and different routes can perform different actions .  
            - Routing 
                -> ```@Controller()``` is required to define a basic controller . Optional route prefix can also be given . 
            
            - Request object 
                -> Handlers often need access to the client request details . Nest provides access to the request object of the underlying platform . 
            
            - Resources 
                -> ```@Get()```, ```@Post()``` , ```@Put()``` , ```@Delete()```, ```@Patch()```, ```@Options()```, ```@Head()``` , ```@All()```
            
            -Route wildcards 
                -> pattern based routes are supported as well . For instance , the asterisk is used as a wildcard , and will match any combination of characters . 
                -> The 'ab*cd' route path will match abcd , ab_cd , abecd and so on . 
            
            -Asynchronicity
                -> Event async function has to return a Promise . This means that you can return a deferred value that Nest will be able to resolve by itself . 
                ->The above code is fully valid. Furthermore, Nest route handlers are even more powerful by being able to return RxJS observable streams (TODO)

#### Providers 
            1. main idea of provider is that is can be injected as dependency which means objects can create various relationships with each other. 
            2. Controllers should handle HTTP requests and delegate more complex tasks to providers . 
            3. The ```@Injectable()``` decorator attachers metadata , which declares that <Service_Name> is a class that can be managed by the Nest IoC container. 
            4. The <Service_Name> is injected through the class constructor . 
                ```
                    export class controllername{
                        constructor(private servicename:servicename)
                    }
                ```
            5. Dependency Injection 
                -> Dependencies are services or objects that a class needs to perform its function. Dependency injection, or DI, is a design pattern in which a class requests dependencies from external sources rather than creating them . 
                -> dependency injection is a technique in which an object receives other objects that it depends on, called dependencies. Typically, the receiving object is called a client and the passed-in ('injected') object is called a service
            6. Provider registration 
                -> Now once we have defined a provider , and we have a consumer of that service , we need to register the service with Nest so that it can perform the injection . 
        
#### Modules 
            1. is a class annotated with a ```@Module()``` decorator , provides metadata that Nest makes use of to organize the application structure . 
            2. Each application has atleast one root module . 
            3. The ```@Module()``` decorator takes a single object whose properties describe the module . 
                . providers 
                . controllers 
                . imports 
                . exports 
            4. Feature module 
                If controller and service belong to the same application domain , it makes sense to move them into a feature module . 
            5. Shared modules 
                In Nest , modules are singletons by default , and thus you can share the same instance of any provider between multiple modules effortlessly . 
                ![](https://docs.nestjs.com/assets/Shared_Module_1.png)
            6. Module re-exporting 
                Modules can export their internal providers . In addition , they can re-export modules that they import .  
            7. Dependency Injection 
                 A module class can inject providers as well , however modules classes themselves cannot be injected as providers due to circular dependencies . 

                 - Circular dependencies 
                    -> A circular dependency occurs when two classes depend on each other. For example class A needs class B , and class B also needs class A . Circular dependencies can arise in Nest between modules and between providers . 
            8. Global modules 
                As Nest encapsulates providers inside the module scope . You aren't able to use a module's providers elsewhere without first importing the encapsulating module . To make module global make the use of ```@Global()``` decorator . 
            9. Dynamic modules 
                Dynamic modules is a powerful feature in Nest . This feature enables you to easily create customizable modules that can register and configure providers dynamically . 