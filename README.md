# REST API Basics and Interview Questions

### What is an API and how does it work

An API (Application Programming Interface) is a software intermediary that allows two distinct applications to interact and share data with one another.

**How it works:** It follows a Client-Server architecture. A client sends an explicit request (payload/parameters) over a network protocol (like HTTP) to a specific endpoint. The server processes the request, communicates with a database if necessary, and returns an HTTP response containing a status code and data.

### What is the difference between an API and a Web Service

Primary difference is that all web services are APIs, but not all APIs are web services. A Web Service is a specific type of API that strictly requires a network connection and relies on web protocols (like HTTP or SOAP) to exchange data or to communicate between machines. An API (Application Programming Interface) is a broader umbrella term representing any interface that allows two software components to talk to each other, whether they are on the same local device or spread across the internet.

**Protocol Support:** API (Any protocol e.g., HTTP, gRPC, WebSockets, local OS system calls, file inputs), Web Service (Strictly web protocols e.g., HTTP/HTTPS, SOAP).

**Data Format:** API (Highly flexible. Supports JSON, XML, YAML, binary streams, or plain text), Web Service (Relies heavily on XML (especially for SOAP) or JSON for RESTful variations).

### What do you understand by RESTful Web Services

RESTful Web Services are a way of designing and developing web services that use REST (Representational State Transfer) principles. They enable applications to communicate over the web using standard HTTP methods, such as GET, POST, PUT and DELETE. REST is lightweight, stateless and widely used in modern web and mobile applications. 

REST (Representational State Transfer) is an architectural style used to design distributed systems using the HTTP protocol. To be truly RESTful, an API must adhere to key constraints:

**How RESTful Web Services Work:** 

**Define Messaging in terms of RESTful web services:** Here, messaging refers to the exchange of data between a client and a server via standard HTTP protocols. Because REST is stateless, every communication transaction is fully self-contained within two types of messages: the HTTP Request (sent by the client) and the HTTP Response (returned by the server).

These messages consist of two primary parts: Metadata (information about the data or the connection) and Message Data/Payload (the actual content being transferred).

### What are the main HTTP methods used in REST APIs

HTTP request methods (also known as HTTP verbs) define the primary action a client wants to perform on a server-side resource. They map closely to typical CRUD (Create, Read, Update, Delete) database operations.

The core HTTP methods are categorized based on their technical behaviors, specifically whether they are Safe (do not modify server state) or Idempotent (making multiple identical requests yields the same server state).

**GET**: Retrieves the current representation of a resource without altering data. Data parameters are passed directly via the URL. (Safe, Idempotent and Cacheable). Returns status codes like `200 OK` or `404 Not Found`.

**POST**: Submits new data enclosed within the request body to create a new resource or trigger server-side processing. (Neither safe nor idempotent, Cacheable is conditional). Often returns `201 Created` or `200 OK`.

**PUT:** Replaces the entire target resource with the new request payload. If the resource doesn't exist, it creates it. (Not safe, Idempotent and Not cacheable). Often returns `200 OK` or `204 No Content`.

**DELETE:**  Removes the specified resource entirely from the target server. (Not safe, Idempotent and Not cacheable). Often returns `200 OK`, `202 Accepted`, or `204 No Content`.

**PATCH:** Applies partial modifications to a resource, so we need to send the fields we wish to change. (Neither safe nor idempotent, Cacheable is conditional). Often returns `200 OK` or `204 No Content`.

OPTIONS: This fetches the list of supported options of resources present on the server.

### What is the Difference Between PUT, POST, and PATCH in RESTful API

### What are basic HTTP status codes

200

OK

Successful GET, PUT, PATCH

201

Created

Successful POST (include Location header)

204

No Content

Successful DELETE

400

Bad Request

Malformed syntax

404

Not Found

Resource does not exist

500

Internal Server Error

Server-side failure

### What is an API Endpoint and what are Parameters

API Endpoint is a specific digital location or URL path where an API receives requests from a client to interact with a server, constructed by combining a Base URL (the server's root address) with a Path (the specific resource). API Parameters are the custom options or variables passed to that endpoint to give the server specific instructions on what exact data to process or return - three primary types of parameters.

**Path Parameters:** Variables embedded directly within the URL path to isolate a distinct resource (e.g., `/users/101` targets user ID 101).

**Query Parameters:** Key-value pairs appended at the end of the URL following a ? symbol, primarily utilized to filter, sort, search, or paginate results (e.g., `/users?status=active&sort=price`).

**Body / Payload Parameters:** Hidden inside the "body" of the request (often as raw text or JSON).Submits complex data or files, typically used when creating or updating something.Sent alongside a POST request to create a product

### Difference between SOAP and REST API

REST (Representational State Transfer) and SOAP (Simple Object Access Protocol) are the two most common methods for client-server communication. REST is an architectural style with flexible design guidelines, while SOAP is a official protocol with strict rules, often used in complex enterprise systems.

**Data Format:** SOAP is XML only, data must be packaged in a rigid XML structure. REST is flexible, supports JSON, XML, HTML, and plain text.

**Design Focus:** SOAP is Function-driven, exposes operations or actions (e.g., CreateEmployee). REST is Resource-driven:, Exposes data resources via URLs (e.g., `/employees`).

**Operations:** SOAP uses an interface contract defined by a WSDL file and requests typically use POST. REST uses standard HTTP methods directly (GET, POST, PUT, DELETE).

**State:** Stateful or Stateless: Can store and track client interactions between requests.Stateless: Every request is entirely independent and self-contained.CachingNot supported natively: Responses cannot be cached easily.Built-in: Supports HTTP caching, significantly improving speed and efficiency.SecurityBuilt-in enterprise security standards like WS-Security (encryption and digital signatures).Relies on transport layer security (HTTPS) and token authorization (OAuth, JWT).TransactionsBuilt-in compliance for ACID transactions (highly reliable for multi-step bank transfers).Limited transactional support; managing state-heavy steps requires client-side software.PerformanceHeavier and slower: Large XML envelopes consume more bandwidth and CPU to process.Lightweight and faster: Minimal payload overhead (especially with JSON).

When to Use SOAPSOAP is highly structured and ideal for legacy enterprise environments. Choose SOAP for:Financial and Banking Services: Where ACID compliance is necessary to ensure transactions never fail silently or partially.High-Security Systems: Applications requiring bank-grade, end-to-end encryption and token validation via WS-Security.Stateful Operations: Systems that need to track consecutive, multi-step actions across a distributed network.🌐 When to Use RESTREST dominates the modern web because it is easy to build, scale, and consume. Choose REST for:Public Web APIs & Mobile Apps: Lightweight JSON payloads save bandwidth and process quickly on mobile devices.Microservices: Ideal for building decoupled, independent, and stateless cloud applications.Scalable Web Performance: Direct integration with HTTP allows data to be cached at the browser or CDN level, reducing server loads.

https://www.google.com/search?q=Difference+between+SOAP+and+REST+API&rlz=1C5FPAB_enIN1189IN1189&gs_lcrp=EgZjaHJvbWUyBggAEEUYOdIBCDE3MTFqMGo3qAIAsAIA&sourceid=chrome&ie=UTF-8&fbs=ABfTbFVyMZGZf1hfvX9uKjN_-G8c4u0nXx4bEIpwm1lnNH832cSpkWkfSwsmpNIrD_OQ-UfVcuk_CN5lZ7ooDDWHK2MvRnkJCfpKMCXqclK-P4WAh82d25jqGtbeY99CshApuFApJdhBniVRKv_-rylb_ASjcXJYoQ2hox6HVTmY1M1uLkVuRADjuugOu2Tw38WgSDDphzX2mMJEqRuZd6SsW6lkNPUO2A&aep=10&ntc=1&sxsrf=APpeQnvEXWuFxJb6PqKUc7sX1XXCOj8ylg%3A1790477912302&mstk=AUtExfBtuVtYlvqI05_B5ggjDJBzYdFDFa3xTgfqap0xnoVjsqAAPyn9ZCZJEt6xkkb4csbAHY4HQuz8KrK_GpITYIIR8AGm9G2XoIYCnPoWRDCAm9XicHIuMHyVuhM4Xk-bJIot8usSQ2TN9RysvhO75z2vq_m-CNR2cZ5nIA_TB80aTYdfAcW4zly_YRCVkpVEr8ClCnVkjRsTsnj8oP49FDBNdj7cKQC5mr0tw_RW6ks9WhlGhJzrrs-dLGBFSFiCSk9iys3etRahQw&aioh=3&csuir=1&cs=0&mtid=P5O4aqevL4SUhvcP6NLxsQ4&udm=50







2.What is API Authentication and Authorization
----------------------------------------------
Authentication is the process of verifying the identity of a user or client making a request to a Web API, while authorization is the process of determining 
whether the authenticated user has the necessary permissions to access a particular resource or perform a specific action.

REST APIs are stateless, i.e. server does not store client's session information. Each request is treated as an independent unit. So, every request from the
client to the server must contain all the necessary information for the server to understand and process that request. Makes it easier to scale applications
horizontally, as any server can handle any request without needing to maintain specific client state. Simplifies server-side design. Promotes cacheability,
as responses can be cached without concerns about stale session data. Stateful authentication requires the server to maintain session state for each
authenticated user, using cookies or session tokens.

API is requested by a client or an application to fetch resources. The request must include authentication credentials as an access token, API key, 
JWT, or OAuth-2.0 auth token. API server validates the credentials by ascertaining whether they are active, valid, and authorized. If OAuth 2.0 or OpenID 
Connect (OIDC) is being used, the request is forwarded to the authentication server for validation. After successful verification, the server creates an 
access token (JWT or OAuth token). The token contains user permission and expiration details to enable future API calls without further authentication.

Authorization header in an HTTP request transmits credentials from a client to a server for authentication and authorization. follows a specific format:
Authorization: <scheme> <credentials>

<scheme> -> indicates the authentication method being used. Basic -> For basic authentication, where credentials (username and password) are Base64 encoded.
(credentials are a Base64 encoded string of "username:password"). Considered secure with other security mechanisms such as HTTPS/SSL. Legacy systems.
Bearer -> For token-based authentication, commonly used with OAuth 2.0/JWT, where a bearer token is provided. This access token provided by an 
authentication server.
API key -> token that a client provides when invoking API calls, it a secret that only the client and server know. token can be sent in the request header 
or as query parameter. Like Basic authentication, API key-based authentication is only considered secure when used with other security mechanisms such as 
HTTPS/SSL. Authorization: Bearer <API_KEY>.


3.Access control authentication and authorization in a REST API
---------------------------------------------------------------
Access Control is a method of limiting access to a system or resources. Access control systems perform identification, authentication, and authorization of
users and entities by evaluating the login credentials. After a user is authenticated, access control policies define the specific actions and resources 
that the authenticated user is allowed to access. Types of access control:

Role-Based Access Control (RBAC) -> Assigning roles to users and defining permissions based on those roles. Users are authorized based on their assigned 
roles. Attribute-Based Access Control (ABAC) -> Defining policies that determine access based on attributes of the user, resource, and environment. It 
provides more granular control over permissions.


4.JSON Web Token (JWT)
----------------------
JWT consists of header, payload, and signature, encoded into a single string, allows a server to verify the client's identity by using a digital signature. 

- Authentication -> A user signs in with their credentials.
- Token Generation -> The server creates and digitally signs a JWT containing user information, known as claims, such as user ID and role.
- Token Transmission -> The server sends this encoded JWT back to the client.
- Authorization -> For subsequent requests, the client sends the JWT to the server.
- Verification -> The server verifies the JWT's signature to confirm it hasn't been tampered with and that the claims are valid, thereby authenticating 
and authorizing the user. 

Structure of a JWT:

- Header: Contains information about the token, such as the signing algorithm (HMAC SHA256 or RSA) and token type (JWT or JWE).
- Payload: Holds the claims, or data, about the user (e.g., user ID, roles, expiration time).
- Signature: Created by combining the Base64 encoded header and payload, a secret key, and the algorithm used to sign the token.


5.Explain the concept of idempotence in Web API requests
--------------------------------------------------------
Idempotence is the property of an operation that produces the same result regardless of how many times it is executed with the same input parameters. 
In the context of Web API requests, idempotent operations can be safely retried or repeated without causing unintended side effects or altering the 
system state. PUT is an idempotent method, while POST isn’t. For instance, calling the PUT method multiple times will either create or update the same 
resource, whereas, multiple POST requests will lead to the creation of the same resource multiple times.


6.What are the best practices for securing a RESTful API
--------------------------------------------------------
Broken Access Control -> occurs when an application fails to properly restrict what authenticated users are allowed to do, allowing attackers to access
unauthorized functionality and data. Includes sophisticated attacks on microservices authentication, JWT token abuse, and API endpoint exploitation.

SQL/NoSQL Injection -> Malicious code injected into database queries. Should use prepared statements, parameterized queries, or stored procedures instead
of dynamic SQL.

Cross-Site Scripting (XSS) -> Malicious scripts are injected into web pages that execute in users' browsers. Two types of XSS attacks: In Reflected or
Nonpersistent XSS, untrusted user data is submitted to a web application, which is immediately returned in the response, adding untrustworthy content to
the page. The web browser assumes the code came from the web server and executes it. This might allow a hacker to send you a link that, when followed,
causes your browser to retrieve your private data from a site you use and then make your browser forward it to the hacker’s server. In Stored or Persistent
XSS, the attacker’s input is stored by the webserver. Subsequently, any future visitors may execute that malicious code. Validate and sanitize user inputs,
use output encoding where special symbols like < and > are converted to HTML entity equivalents (https://www.baeldung.com/spring-prevent-xss).

Security Misconfiguration -> occurs when security settings are not properly defined, implemented, maintained, or monitored. Common misconfigurations include
exposed cloud storage buckets, default credentials in production, overly permissive Cross-Origin Resource Sharing (CORS) policies. Implement proper CORS
configuration for API endpoints.

Server-Side Request Forgery (SSRF) -> attacks trick applications into making unintended requests to internal systems, potentially exposing sensitive data
or enabling further attacks against internal infrastructure. Validate and sanitize all URLs and user inputs that could trigger server-side requests, 
Implement allowlists for external requests and restrict internal network access, Apply the principle of least privilege to server-side request capabilities.

- Regularly update all software to fix known vulnerabilities and prevent exploits by hackers.
- Prevent attackers from injecting malicious queries into your database by using parameterized queries and input validation.
- Prevent Cross-Site Scripting (XSS) by sanitizing user input to block scripts that could run in users' browsers and steal sensitive data.
- Validate User Input by performing input validation on both client and server sides to block malformed or malicious data.
- Use Strong Passwords: Enforce complex password policies to protect against brute-force attacks—include uppercase, lowercase, numbers, and symbols.
- Implement HTTPS, which secures the webapp with HTTPS to encrypt data during transmission and prevent interception.
- Enable Two-Factor Authentication (2FA) which adds an extra layer of security by requiring a second form of verification beyond a password.
- Access Control: Restrict access based on user roles and use the principle of least privilege to minimize risk.
- Monitor and Log Activity: Keep logs of access and actions on your site to detect suspicious behavior and audit breaches.


https://www.stackhawk.com/blog/10-web-application-security-threats-and-how-to-mitigate-them/ (Check here for mitigation strategies)
https://www.geeksforgeeks.org/ethical-hacking/web-security-considerations/



Types of Webservers
-------------------
https://www.geeksforgeeks.org/node-js/web-server-and-its-type/



How do you implement web caching in RESTful web services
--------------------------------------------------------


How do you implement contract testing in RESTful web services
-------------------------------------------------------------


How do you perform performance and load testing for a RESTful API
-----------------------------------------------------------------
https://www.geeksforgeeks.org/software-testing/how-to-use-jmeter-for-performance-and-load-testing/
Performance testing tools: BlazeMeter, Apache JMeter


What is the role of API gateways in Web API architecture
--------------------------------------------------------
An API gateway is a server that acts as an entry point for requests to a RESTful web service. It provides a centralized point of control and helps manage 
the complexity of microservices architectures. In this setup, the API gateway serves as a mediator between clients and services, handling authentication,
authorization, traffic management, and other cross-cutting concerns. It allows clients to make requests to different services through a single endpoint,
simplifying the client's access to various functionalities. The API gateway also enforces security measures by, for example, validating API keys or 
implementing rate limiting. It can transform requests and responses, aggregate data from multiple services, and cache results to improve performance. 
Overall, the API gateway enhances the scalability, reliability, and security of RESTful web services.


What is gRPC, and how does it differ from traditional RESTful APIs
------------------------------------------------------------------
gRPC is a high-performance, open-source RPC (Remote Procedure Call) framework developed by Google that uses Protocol Buffers (protobuf) for serialization 
and HTTP/2 for transport. Unlike RESTful APIs, which use JSON over HTTP, gRPC offers strong typing, bi-directional streaming, and automatic code 
generation, making it ideal for building efficient and scalable microservices architectures.


Can you explain the concept of load balancing in RESTful web services
---------------------------------------------------------------------
Load balancing is a technique used in RESTful web services to distribute incoming network traffic across multiple servers. The purpose is to optimize 
resource utilization, improve scalability, and enhance the overall performance of the system. In load balancing, a load balancer acts as a mediator between
the client and the servers. It receives the incoming requests and distributes them among the available servers based on various algorithms, such as
round-robin or least connections. This ensures that no single server gets overwhelmed with excessive traffic, leading to increased reliability and
responsiveness of the RESTful web service.


What is service discovery and how is it used in RESTful web services
--------------------------------------------------------------------
Service discovery is a mechanism used in RESTful web services to allow services to find and communicate with each other without manual configuration. It 
involves a central registry or service registry where services can register themselves and provide information about their location, endpoints, and 
capabilities.
When a service needs to communicate with another service, it can query the service registry to obtain the necessary information. This eliminates the need 
for hardcoding or manual configuration of endpoints, making the system more dynamic and flexible. Service discovery enables automatic load balancing, 
failover, and scaling in distributed systems, as services can easily discover and connect to available instances of other services.








How do you implement asynchronous communication in RESTful web services
-----------------------------------------------------------------------
Asynchronous communication in REST APIs refers to a pattern where client does not wait for an immediate response from the server after sending a request.
Instead, the server processes the request in the background and notifies the client about the outcome at a later time. It is different from synchronous 
communication, where the client blocks and waits for a response before proceeding. Several approaches to implement:

HTTP polling involves the client sending a request to the server which returns a response indicating that the request has been received but not yet
processed. The client then periodically sends the same request to check if the server is done processing the request. When done, the server sends a
response with the requested data.

Use of message queues. Here, the client sends a request to the web service, which then places a message onto a message queue (e.g., RabbitMQ, Apache Kafka,
AWS SQS). Consumer process listens to the queue, retrieves the message, and performs the long-running task. Once the server processes it, it sends a 
response back to the client. This decouples the service from the processing logic.


Can you explain the concept of message brokers and how they are used in RESTful web services
--------------------------------------------------------------------------------------------
A message broker is a middleware service that acts as a communication bridge between two or more applications. They are used with RESTful services, 
particularly in microservices architectures, to handle tasks like decoupling services, ensuring reliable message delivery during failures, and 
managing asynchronous workflows.

A message broker acts as a central hub/intermediary that decouples message producers (senders) from message consumers (receivers). Applications don't need 
to be available at the same time. producer sends a message to the broker, and the consumer retrieves it when it's ready. Brokers use queues to store 
messages. The producer puts messages into the queue, and the consumer takes them out, ensuring messages aren't lost even if a consumer is temporarily 
offline. Message brokers provide durability and reliability ensuring messages are not lost in case of a consumer failure. Helps in decoupling the services, 
making them modular and easier to maintain. Improves scalability as the web services can handle a large volume of requests and scale up and down as 
required.

For example, consider an e-commerce website that has to handle a large number of orders. Instead of processing all orders directly, the site can
use a message broker to receive the order requests and then forward them to the order processing service. This way, the website can handle multiple
orders simultaneously, and the processing service can work independently, without the need for direct communication with the website.


Can you explain the concept of containerization and how it is used in RESTful web services
------------------------------------------------------------------------------------------
Containerization is a method used to package software applications, along with their dependencies and configurations, into lightweight and portable 
containers. Provides a consistent environment across different systems, making it easier to deploy and manage applications. Allows for the isolation of 
different components of a system, such as web server, application server, and database. Each component is packaged into its own container, with its own 
resources and configuration settings. This approach provides flexibility, scalability, and improved resource utilization. e.g. Docker.


Can you explain the concept of webhooks and how they are used in RESTful web services
-------------------------------------------------------------------------------------
Webhooks are a mechanism in RESTful web services that allow for real-time communication between two applications. In simple terms, webhooks act as a 
type of notification system. When a certain event occurs on one application, it sends data to another application about that occurrence through a webhook. 
The receiving application then processes that data and takes necessary actions based on it. This allows for a more seamless and immediate transfer of 
information between applications.

Webhooks are commonly used in scenarios such as triggering actions based on user input or sending real-time updates to mobile applications. Overall, 
webhooks serve as an efficient tool for integrating different applications and improving the user experience.






Explain the concept of OAuth and how is it used in RESTful web services
------------------------------------------------------------------------
User initiates the process: When a user wants to connect their account on a service (known as the "resource server") to a third-party application (known as 
the "client"), they initiate the OAuth process by clicking on a "Connect with [client]" button.

Authorization Request: The client redirects the user to the resource server's authorization endpoint along with information about the requested access and 
a redirect URL where the user will be sent after authorization.

User gives consent: The user is presented with a consent screen by the resource server, which explains the requested access and asks for their permission 
to grant the client access to their resources.

Authorization Grant: If the user consents, the resource server generates an authorization grant (e.g., an access token) and redirects the user back to 
the redirect URL provided by the client.

Access Token Request: The client exchanges the authorization grant for an access token by making a request to the resource server's token endpoint, 
providing the grant, client credentials (e.g., client ID and client secret), and the redirect URL used in the authorization request.

Access Token Issued: If the token request is valid, the resource server verifies the grant and returns an access token to the client.

Accessing Protected Resources: The client can now use the access token to make requests to the resource server's API, including the user's protected 
resources. The resource server verifies the access token for every request, ensuring that the client has been authorized to access those resources.
