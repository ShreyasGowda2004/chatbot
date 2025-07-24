Java Basics (Recap)
OOP Concepts: Inheritance, Encapsulation, Polymorphism, Abstraction

Data Types: int, float, double, char, String, boolean

Control Structures: if, for, while, switch

Collections:

List (e.g. ArrayList)

Set (e.g. HashSet)

Map (e.g. HashMap)

Streams & Lambdas: Used for functional-style operations on collections.

🧩 Spring Boot Essentials
@SpringBootApplication: Entry point of any Spring Boot app

@RestController: Used to define RESTful web services

@RequestMapping, @PostMapping, @GetMapping: Map HTTP routes

@Autowired: Inject dependencies

application.properties: External configuration (e.g. keys, URLs)

pom.xml: Manages dependencies (e.g. Spring Boot, Gson, Apache HttpClient)

📁 Common Spring Project Structure
bash
Copy
Edit
src/
├── main/
│   ├── java/
│   │   └── com/example/chatbot/
│   │       ├── config/         # API keys, constants
│   │       ├── controller/     # REST API endpoints
│   │       ├── model/          # POJOs for request/response
│   │       ├── service/        # Business logic (Gemini, GitHub)
│   │       └── AIGitChatbotApplication.java
│   └── resources/
│       └── application.properties
📦 Maven Dependency Example
Add to your pom.xml:

xml
Copy
Edit
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-web</artifactId>
</dependency>
<dependency>
  <groupId>com.google.code.gson</groupId>
  <artifactId>gson</artifactId>
  <version>2.10</version>
</dependency>
<dependency>
  <groupId>org.apache.httpcomponents.client5</groupId>
  <artifactId>httpclient5</artifactId>
  <version>5.2.1</version>
</dependency>
🤖 Gemini API (Java Usage)
You’ll use:

HttpClient or RestTemplate to send POST requests

Create JSON payload (e.g. file content → prompt → LLM)

Parse response using Gson

📦 Useful Java Libraries for AI Projects
Gson / Jackson: JSON parsing

Apache HttpClient: HTTP requests to Gemini or GitHub

JGit: Clone/read GitHub repositories programmatically

jsoup: HTML parsing if needed

