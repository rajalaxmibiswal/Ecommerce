# 🛒 SimpleEcommerce — Spring Boot E-Commerce Application

<div align="center">

![Java](https://img.shields.io/badge/Java-17%2B-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.x-6DB33F?style=for-the-badge&logo=springboot&logoColor=white)
![Thymeleaf](https://img.shields.io/badge/Thymeleaf-Template%20Engine-005F0F?style=for-the-badge&logo=thymeleaf&logoColor=white)
![Maven](https://img.shields.io/badge/Maven-Build%20Tool-C71A36?style=for-the-badge&logo=apachemaven&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)

A full-stack e-commerce web application built with **Spring Boot**, featuring role-based access control for Admins and Users, product management, order processing, and a contact system.

[Features](#-features) · [Tech Stack](#-tech-stack) · [Project Structure](#-project-structure) · [Getting Started](#-getting-started) · [Installation & Setup](#-installation-&-setup).

</div>

---

## ✨ Features

### 👤 User
- Register / Login securely
- Browse and search products
- Purchase products (Buy Now)
- View and manage personal profile
- Contact support via the Contact Us page

### 🛠️ Admin
- Secure Admin Dashboard
- Full **CRUD** for Products (Add, Update, Delete)
- Manage and view all Users
- View and process Orders
- Handle customer contact messages

---

## 🧰 Tech Stack

| Layer | Technology |
|---|---|
| Backend | Java, Spring Boot |
| Frontend | Thymeleaf, HTML5, CSS3 |
| ORM | Spring Data JPA / Hibernate |
| Database | MySQL / H2 (configurable) |
| Build Tool | Maven (Maven Wrapper) |
| Template Engine | Thymeleaf |
| Static Assets | Served via `/static` |

---

## 📁 Project Structure

```
simpleecommerceapp/
├── src/
│   ├── main/
│   │   ├── java/com/example/simpleecommerceapp/
│   │   │   ├── controller/
│   │   │   │   ├── AdminController.java       # Admin dashboard & management
│   │   │   │   ├── ContactController.java     # Contact form handling
│   │   │   │   ├── HomeController.java        # Landing & home routes
│   │   │   │   ├── OrderController.java       # Order processing
│   │   │   │   ├── ProductController.java     # Product listing & details
│   │   │   │   └── UserController.java        # User auth & profile
│   │   │   ├── entity/
│   │   │   │   ├── Admin.java                 # Admin entity model
│   │   │   │   ├── Message.java               # Contact message entity
│   │   │   │   ├── Order.java                 # Order entity model
│   │   │   │   ├── Product.java               # Product entity model
│   │   │   │   └── User.java                  # User entity model
│   │   │   ├── repo/
│   │   │   │   ├── AdminRepo.java             # Admin JPA repository
│   │   │   │   ├── ContactRepo.java           # Contact JPA repository
│   │   │   │   ├── OrderRepo.java             # Order JPA repository
│   │   │   │   ├── ProductRepo.java           # Product JPA repository
│   │   │   │   └── UserRepo.java              # User JPA repository
│   │   │   ├── service/
│   │   │   │   ├── AdminService.java          # Admin business logic
│   │   │   │   ├── ContactService.java        # Contact business logic
│   │   │   │   ├── OrderService.java          # Order business logic
│   │   │   │   ├── ProductService.java        # Product business logic
│   │   │   │   └── UserService.java           # User business logic
│   │   │   └── SimpleecommerceappApplication.java  # Main entry point
│   │   └── resources/
│   │       ├── static/
│   │       │   └── videos/                    # Static media assets
│   │       ├── templates/
│   │       │   ├── AboutUs.html               # About page
│   │       │   ├── AdminHomePage.html         # Admin dashboard
│   │       │   ├── BuyProductPage.html        # Product purchase page
│   │       │   ├── ContactUs.html             # Contact form
│   │       │   ├── HomePage.html              # Landing page
│   │       │   ├── LoginPage.html             # Login / Register page
│   │       │   ├── Products.html              # Product listing
│   │       │   ├── UpdateAdmin.html           # Admin profile update
│   │       │   ├── UpdateProduct.html         # Product edit form
│   │       │   └── UpdateUser.html            # User profile update
│   │       └── application.properties         # App configuration
│   └── test/
│       └── java/com/example/simpleecommerceapp/
│           └── SimpleecommerceappApplicationTests.java
├── .gitattributes
├── .gitignore
├── mvnw                                       # Maven wrapper (Unix)
├── mvnw.cmd                                   # Maven wrapper (Windows)
└── pom.xml                                    # Maven dependencies
```

---

## 🚀 Getting Started

### Prerequisites

Ensure the following are installed on your machine:

- [Java 17+]([https://adoptium.net/](https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html))
- [Maven](https://maven.apache.org/) _(or use the included Maven Wrapper)_
- [MySQL](https://www.mysql.com/downloads/) _(or configure H2 for in-memory testing)_
- [Git](https://git-scm.com/)

---

### 🔧 Installation & Setup

**1. Clone the repository**

```bash
git clone https://github.com/your-username/simpleecommerceapp.git
cd simpleecommerceapp
```

**2. Configure the database**

Open `src/main/resources/application.properties` and update:

```properties
# Database Configuration
spring.datasource.url=jdbc:mysql://localhost:3306/ecommerce_db
spring.datasource.username=your_mysql_username
spring.datasource.password=your_mysql_password

# JPA / Hibernate
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQLDialect
```

**3. Create the MySQL database**

```sql
CREATE DATABASE ecommerce_db;
```

**4. Build and run the application**

```bash
# Using Maven Wrapper (recommended)
./mvnw spring-boot:run        # Linux / macOS
mvnw.cmd spring-boot:run      # Windows

# Or using Maven directly
mvn spring-boot:run
```

**5. Open the app in your browser**

```
http://localhost:8080
```

---

## 🗄️ Database Schema Overview

| Entity | Description |
|---|---|
| `User` | Registered customers |
| `Admin` | Admin accounts with elevated access |
| `Product` | Items available for purchase |
| `Order` | Customer orders linked to users & products |
| `Message` | Contact form submissions |

---

## 🌐 Application Routes

| URL | Description | Access |
|---|---|---|
| `/` | Home Page | Public |
| `/login` | Login / Register | Public |
| `/products` | All Products | User |
| `/buy/{id}` | Buy a Product | User |
| `/contact` | Contact Us | User |
| `/about` | About Page | Public |
| `/admin` | Admin Dashboard | Admin |
| `/admin/update` | Update Admin Profile | Admin |
| `/product/update/{id}` | Update Product | Admin |
| `/user/update/{id}` | Update User | Admin |

---

## ⚙️ Configuration

Key properties in `application.properties`:

```properties
# Server port (default: 8080)
server.port=8080

# App name
spring.application.name=simpleecommerceapp

# Thymeleaf cache (disable in dev)
spring.thymeleaf.cache=false
```

🎥 [Watch Demo Video](https://www.youtube.com/watch?v=o1_CZqkDJi8)

---

## 🧪 Running Tests

```bash
./mvnw test
```

---

## 📦 Building for Production

```bash
./mvnw clean package
java -jar target/simpleecommerceapp-0.0.1-SNAPSHOT.jar
```

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

## 👨‍💻 Author

**Rajalaxmi Biswal**  
📧 rajalaxmibiswal2005@gmail.com  
🔗 [GitHub](https://github.com/rajalaxmibiswal) ·

---

<div align="center">
  <sub>Built with ❤️ using Spring Boot</sub>
</div>
