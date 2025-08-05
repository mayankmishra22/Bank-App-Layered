# 💳 Banking System Console Application

A simple **command-line banking application** built with **Spring Boot**, demonstrating a layered architecture using Spring IoC and DI principles. The application leverages **Spring Data JPA** to interact with a **MySQL** database.

---

## 🚀 Features

This console-based application provides the following functionalities:

- 🏦 **Create Account**: Register a new account with an initial balance.
- 💰 **Deposit**: Add funds to an existing account.
- 💸 **Withdraw**: Withdraw funds, with balance validation.
- 🔍 **View Account**: Display details of a specific account.
- 📋 **List All Accounts**: Show all registered accounts.
- ❌ **Exit**: Gracefully close the application.

---

## ⚙️ Technologies Used

| Technology     | Purpose                                       |
|----------------|-----------------------------------------------|
| Java 11+       | Core programming language                     |
| Spring Boot    | Framework for building and managing the app   |
| Spring Data JPA| Simplified database interaction               |
| Hibernate      | ORM provider for JPA                          |
| MySQL          | Relational database                           |
| Maven          | Dependency and build lifecycle management     |

---

## 📂 Project Structure

```
banking-app/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/example/bankingapp/
│   │   │       ├── config/               # Spring configuration
│   │   │       │   └── AppConfig.java
│   │   │       ├── controller/           # Console input/output logic
│   │   │       │   └── AccountController.java
│   │   │       ├── model/                # JPA entity classes
│   │   │       │   └── Account.java
│   │   │       ├── repository/           # JPA repository interfaces
│   │   │       │   └── AccountRepository.java
│   │   │       ├── service/              # Business logic layer
│   │   │       │   └── AccountService.java
│   │   │       └── BankingApplication.java  # Main application class
│   └── resources/
│       └── application.properties        # Configuration file
├── pom.xml                              # Maven project descriptor
```

---

## 🛠️ Prerequisites

Make sure the following are installed on your system:

- Java JDK 11 or higher
- Apache Maven
- MySQL Server (local instance)
- MySQL user: `root` | Password: `root` (or update accordingly)

---

## ⚙️ Setup Instructions

### 1️⃣ Database Configuration

The app connects to a MySQL DB named `banking_db` (auto-created if it doesn’t exist):

```properties
# MySQL DataSource configuration
spring.datasource.url=jdbc:mysql://localhost:3306/banking_db?createDatabaseIfNotExist=true
spring.datasource.username=root
spring.datasource.password=root
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

# JPA/Hibernate configuration
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL5Dialect
```

> 🔧 If your MySQL credentials differ, update the above accordingly in `src/main/resources/application.properties`.

---

### 2️⃣ Build & Run the Application

Open a terminal in the root project directory and run:

```bash
mvn spring-boot:run
```

This will:
- Download dependencies
- Compile the project
- Start the Spring Boot application

---

## 🎮 How to Use

Once launched, the following menu will appear:

```
--- Banking System Menu ---
1. Create Account
2. Deposit
3. Withdraw
4. View Account
5. List All Accounts
6. Exit
Enter your choice:
```

### 📌 Sample Workflow

#### ✅ Create an Account
```
Enter: 1
Name: John Doe
Initial Balance: 1000.00
```

#### 🔍 View an Account
```
Enter: 4
Account ID: 1
```

#### 💰 Deposit Funds
```
Enter: 2
Account ID: 1
Amount: 500
```

#### 💸 Withdraw Funds
```
Enter: 3
Account ID: 1
Amount: 200
```

#### 📋 List All Accounts
```
Enter: 5
```

#### ❌ Exit Application
```
Enter: 6
```

---

## 🧪 Verifying Database Changes

Connect to MySQL and run the following:

```sql
USE banking_db;
SELECT * FROM account;
```

You will see real-time updates based on your interactions.

---