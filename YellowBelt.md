# Yellow Belt

### Overview:

In this study case, we'll build a Communication Delivery Feature using .NET that allows sending messages via multiple channels such as WhatsApp (WA), SMS, and Email. The project will be built using .NET 6  or later, starting with the basics of .NET, and expanding to handle different delivery mechanisms. We'll also implement Dependency Injection (DI), Generic Types, and Interfaces to ensure scalability, maintainability, and flexibility.

### Requirements:

1. Multi-Channel Message Delivery:
    - Mock the 3rd party Service Call, assuming it supports sending messages via:
        1. Whatsapp 
        2. SMS
        3. Email (with multiple service providers)
            - SMTP
            - SendGrid or other 3rd party email services
            - The system must dynamically select the appropriate provider for email services based on configuration (App.config).
2. Async Processing:
    - Ensure that all database and external service operations (such as sending messages) are performed asynchronously to enhance performance and scalability.
3. Error Handling & Logging
    - Any exceptions or failures should be logged.

### Tech Stack

1. .NET 6 or later
2. [ASP.Net](http://ASP.Net) Core Web API / MVC (choose one)
3. Dependency Injection
4. EF Core
5. SQL Server
6. Logging Framework: Log4Net/NLog/Serilog

### Implementation

1. Create a solution that contains:
    - ASP.NET Core Web API / MVC project
    - Business Logic Layer:
    - External Service Integration (e.g., WhatsApp API, SMS Provider, Email Services)
    - Persistence (Repository Layer using EF Core)
        
        E.g., Project Structure
        
        ```csharp
        CommunicationDeliveryService/
        ├── CommunicationDelivery.API                 # API layer for HTTP endpoints
        │   ├── Controllers/
        │   ├── Services/
        │   ├── DTOs/
        │   └── Startup.cs
        ├── CommunicationDelivery.Core                # Core business logic and models
        │   ├── Interfaces/
        │   ├── Models/
        │   └── Services/
        ├── CommunicationDelivery.Infrastructure      # External service integrations
        │   ├── WhatsAppService/
        │   ├── SMSService/
        │   ├── EmailService/
        │   ├── PushNotificationService/
        │   └── Persistence/
        ├── CommunicationDelivery.Persistence         # Database operations
        ```
        
2. Define an Interface for Message Sending Service:
    
    ```csharp
    Task<bool> SendMessageAsync(Message message);
    ```
    
3. Service Implementations for each Messaging Platform
4. Service Registration (Dependency Injection)
5. Create a Controller with the following methods:
    1. SendMessage: to send a message based on the MessageType (WA, SMS, or Email)
    2. SendToAllChannels: to send the message using all channels (WA, SMS, and Email)
6. Define and Implement a Generic Repository Interface
Create a generic interface `IRepository<T>` that defines basic CRUD operations. This will allow any entity inheriting this interface to use the same methods.
7. Create a Repository and Service to Log all messaging activity.
8. Implement a logging framework like **Serilog** or **NLog** to log exceptions, failures, or critical events globally.