# Yellow Belt

### Overview:

In this study case, we'll build a Communication Delivery Feature using .NET that allows sending messages via multiple channels such as WhatsApp (WA), SMS, and Email. The project will be built using .NET 6  or later, starting with the basics of .NET, and expanding to handle different delivery mechanisms. We'll also implement Dependency Injection (DI), Generic Types, Interface to ensure scalability, maintainability, and flexibility.

### Requirements:

1. Multi-Channel Message Delivery:
    - Support  for sending messages via:
        1. Whatsapp
        2. SMS
        3. Email (with multiple service providers)
            - SMTP
            - SendGrid or other 3rd party email services
            - The system must dynamically select the appropriate provider for email services based on configuration or availability.
2. Async Processing:
    - Ensure that all database and external service operations (such as sending messages) are performed asynchronously to enhance performance and scalability.
3. Error Handling & Logging
    - Any exceptions of failures should be logged.

### Tech Stack

1. .NET 6 or later
2. [ASP.Net](http://ASP.Net) Core Web API / MVC (choose one)
3. Dependency Injection
4. EF Core
5. SQL Server
6. Logging Framework: Log4Net/NLog/Serilog
7. Unit Test (xUnit/NUnit/etc)

### Implementation

1. Create a solution that contains:
    - [ASP.NET](http://ASP.NET) Core API / MVC project
    - Business Logic Layer:
    - External Service Integration (e.g. WhatsApp API, SMS Provider, Email Services)
    - Persistence (Repository Layer using EF Core)
    - Test Project
        
        E.g. Project Structure
        
        ```csharp
        CommunicationDeliveryService/
        ├── CommunicationDelivery.API                 # API layer for HTTP endpoints
        ├── CommunicationDelivery.Core                # Core business logic and models
        ├── CommunicationDelivery.Infrastructure      # External service integrations
        ├── CommunicationDelivery.Persistence         # Database operations
        └── CommunicationDelivery.Tests               # Unit testing project
        ```
        
2. Define an Interface for Message Sending Service:
    
    ```csharp
    Task<bool> SendMessageAsync(Message message);
    ```
    
3. Service Implementations for each Messaging Platform
4. Service Registration (Dependency Injection)
5. Define and Implement a Generic Repository Interface
Create a generic interface `IRepository<T>` that defines basic CRUD operations. This will allow any entity inheriting this interface to use the same methods.
6. Implement a logging framework like **Serilog** or **NLog** to log exceptions, failures, or critical events.
7. Implement Unit Testing using **xUnit** or **NUnit** to test the service logic and controller actions.
