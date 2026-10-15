# 🏗️ Spring Boot Three-Tier Architecture Demo

A clean demonstration of the **three-tier (MVC) architecture** using Spring Boot, Spring Data JPA, and an in-memory H2 database.

---

## 📐 Architecture

```
Browser / REST Client
        |
        ▼
ProductController   (@RestController)  ← Presentation Tier
        |
        ▼
ProductService      (@Service)         ← Business / Logic Tier
        |
        ▼
ProductRepository   (JpaRepository)    ← Data Access Tier
        |
        ▼
H2 In-Memory Database                  ← Database
```

---

## 🔧 Prerequisites

| Tool    | Version       |
|---------|---------------|
| Java    | 17 or higher  |
| Maven   | 3.6+          |

> ✅ No database installation needed — H2 runs in-memory automatically.

---

## 🚀 How to Run

### Step 1 — Clone the repository
```bash
git clone https://github.com/srraghunath/Spring-boot-three-tier-architecture-Oct7.git
cd Spring-boot-three-tier-architecture-Oct7
```

### Step 2 — Run the application
```bash
mvn spring-boot:run
```

The app will start on **http://localhost:8080**

> If port 8080 is in use, stop the conflicting process or add `--server.port=8081` to the command.

### Step 3 — Verify it's running
Open your browser or use curl:
```bash
curl http://localhost:8080/api/products
```
You should see 3 pre-loaded products (Laptop, Mouse, Keyboard).

---

## 🌐 REST API Endpoints

### GET all products
```
GET http://localhost:8080/api/products
```

### GET a single product by ID
```
GET http://localhost:8080/api/products/1
```

### POST — add a new product
```
POST http://localhost:8080/api/products
Content-Type: application/json

{
  "name": "Monitor",
  "price": 12000
}
```

---

## 🗄️ H2 In-Memory Database Console

Access the browser-based DB console at:
```
http://localhost:8080/h2-console
```

| Field     | Value                |
|-----------|----------------------|
| JDBC URL  | `jdbc:h2:mem:shopdb` |
| Username  | `sa`                 |
| Password  | *(leave blank)*      |

---

## 📦 Project Structure

```
src/main/java/com/example/threetier/
├── ThreeTierApplication.java        ← Entry point (@SpringBootApplication)
├── config/
│   └── DataLoader.java              ← Seeds 3 sample products on startup
├── controller/
│   └── ProductController.java       ← REST API (@RestController)
├── service/
│   └── ProductService.java          ← Business logic (@Service)
├── repository/
│   └── ProductRepository.java       ← Data access (JpaRepository)
└── entity/
    └── Product.java                 ← JPA Entity (@Entity)

src/main/resources/
└── application.properties           ← DB config, H2 console settings
```

---

## 🧠 Key Learning Points

| Concept | Description |
|--------|-------------|
| `@RestController` | Presentation tier — handles HTTP requests |
| `@Service` | Business tier — contains logic and validation |
| `JpaRepository` | Data access tier — CRUD without boilerplate |
| `private final` + constructor injection | Spring's recommended Dependency Injection pattern |
| `@SpringBootApplication` | Auto-configures the entire Spring context |
| H2 In-Memory DB | Zero-config database, resets on every restart |

---

## 📋 Sample Data (loaded on startup)

| ID | Name     | Price (₹) |
|----|----------|-----------|
| 1  | Laptop   | 65,000    |
| 2  | Mouse    | 800       |
| 3  | Keyboard | 1,500     |

---

## 🛠️ Tech Stack

- **Spring Boot** 3.5.6
- **Spring Data JPA** (Hibernate 6)
- **H2 In-Memory Database**
- **Java** 21 (compatible with 17+)
- **Maven**
