# PulseChat

# ConvoSphere  
### Secure Real-Time Chat Application (Java 21, Spring Boot, WebSockets, JWT)

ConvoSphere is a **production-ready real-time chat application** built with **Java 21 (LTS)** and **Spring Boot 3**.  
It enables secure, low-latency, one-to-one messaging using **WebSockets (STOMP)** and **JWT-based authentication**, with a clean and scalable backend architecture.

This project is designed as a **portfolio-quality system**, demonstrating modern Java, Spring ecosystem best practices, and real-world system design.

---

## 🚀 Features

- 🔐 **JWT Authentication**
  - Secure login using REST
  - JWT validation for both REST and WebSocket connections

- 💬 **Real-Time Messaging**
  - WebSocket + STOMP protocol
  - One-to-one private chat
  - Instant message delivery

- 🧵 **High Concurrency with Java 21**
  - Virtual Threads enabled
  - Efficient handling of many WebSocket connections

- 🗄️ **Message Persistence**
  - Messages stored in a relational database
  - Chat history support

- 🧱 **Clean Architecture**
  - Layered and modular package structure
  - Separation of concerns (auth, chat, websocket, security)

- 📈 **Scalable Design**
  - Ready for Redis / Kafka integration
  - Horizontal scaling friendly

---

## 🏗️ System Architecture

```sh
Client (Web / Mobile)
|
| JWT Authentication
|
WebSocket (STOMP)
|
Spring Boot Backend (Java 21, Virtual Threads)
|
Database (PostgreSQL / MySQL)
|
(Optional)
Redis / Kafka for Scaling
```

---

## 🧠 Technology Stack

### Backend
- **Java 21 (LTS)**
- **Spring Boot 3.3+**
- Spring WebSocket
- Spring Security
- Spring Data JPA
- JWT (JSON Web Tokens)

### Database
- PostgreSQL or MySQL

### Messaging
- WebSocket
- STOMP protocol

### Build Tool
- Maven

---

## 📁 Project Structure

```java
convosphere/
├── auth/
│ ├── AuthController
│ ├── JwtUtil
│ ├── JwtChannelInterceptor
├── security/
│ ├── SecurityConfig
├── websocket/
│ ├── WebSocketConfig
├── chat/
│ ├── ChatController
│ ├── ChatMessage
│ ├── ChatRepository
├── user/
│ ├── UserEntity
│ ├── UserRepository
├── ConvoSphereApplication.java
```

---

## 🔐 Authentication Flow

1. User logs in via REST endpoint `/auth/login`
2. Server validates credentials
3. JWT token is generated and returned
4. Client includes JWT in WebSocket `Authorization` header
5. JWT is validated during WebSocket connection
6. Authenticated user is associated with WebSocket session

---

## 💬 Chat Message Flow

Client A
→ SEND /app/chat.private
Server
→ /user/{receiver}/queue/messages
Client B
← Receives message instantly

```java

---

## ⚡ Java 21 Virtual Threads

This project uses **Java 21 virtual threads**, allowing the application to:
- Handle thousands of concurrent WebSocket connections
- Maintain simple blocking code
- Achieve high scalability without reactive complexity

Configuration:
```yaml
spring:
  threads:
    virtual:
      enabled: true

```
🛠️ Setup & Run
Prerequisites

Java 21

Maven

PostgreSQL / MySQL

Clone Repository

```java
git clone https://github.com/your-username/convosphere-chat.git
cd convosphere-chat
```
```
spring:
  datasource:
    url: jdbc:postgresql://localhost:5432/chatdb
    username: chat
    password: chat
```
Run Application
```java
mvn spring-boot:run
```

Server runs at:
```java
http://localhost:8080
```

WebSocket endpoint:
```java
ws://localhost:8080/ws
```
📡 WebSocket Usage (Client Side)
Connect
```java
CONNECT /ws
Authorization: Bearer <JWT_TOKEN>
```
Subscribe
```java
SUBSCRIBE /user/queue/messages
```
Send Message
```java
SEND /app/chat.private
```


# Future Enhancements

  - Group chat
  - Typing indicators
  - Online/offline presence
  - Message read receipts
  - File and media sharing
  - Redis Pub/Sub for multi-instance scaling
  - Kafka-based event streaming
  - Observability (Micrometer + Prometheus)

👨‍💻 Author
  - Getinet Amare
  - Backend Engineer | Java | Spring Boot
  - This project was built to demonstrate:
  - Modern Java (Java 21)
  - Secure real-time systems
  - Clean backend architecture
  - Production-ready design

⭐ Why This Project Matters
  - ConvoSphere showcases:
  - Real-time communication
  - Secure authentication across protocols
  - Scalable backend design
  - Modern Java concurrency (Virtual Threads)
