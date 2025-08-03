# Bank-App-Layered
🏦 Banking System Console Application
A simple command-line banking application built with Spring Boot, demonstrating a layered architecture (Controller, Service, Repository) with Spring IoC and DI. The application uses Spring Data JPA to interact with a MySQL database.

🚀 Features
This application provides the following features through a console interface:

Create Account: Create a new bank account with an initial balance.

Deposit: Deposit funds into an existing account.

Withdraw: Withdraw funds from an account, with balance checks.

View Account: Look up and display the details of a specific account by ID.

List All Accounts: Display a list of all existing accounts.

Exit: Close the application.

⚙️ Technologies Used
Java 11+: The core programming language.

Spring Boot: Provides the foundation for building a production-ready, stand-alone Spring application.

Spring Data JPA: Simplifies data access by automatically generating repository implementations for your entities.

Hibernate: The JPA provider used by Spring Data JPA for Object-Relational Mapping (ORM).

MySQL: The relational database used to store account information.

Maven: The build automation tool for managing dependencies and project lifecycle.

📂 Project Structure
banking-app/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/
│   │   │       └── example/
│   │   │           └── bankingapp/
│   │   │               ├── config/
│   │   │               │   └── AppConfig.java
│   │   │               ├── controller/
│   │   │               │   └── AccountController.java
│   │   │               ├── model/
│   │   │               │   └── Account.java
│   │   │               ├── repository/
│   │   │               │   └── AccountRepository.java
│   │   │               ├── service/
│   │   │               │   └── AccountService.java
│   │   │               └── BankingApplication.java
│   │   └── resources/
│   │       └── application.properties
└── pom.xml
🛠️ Prerequisites
Before you begin, ensure you have the following installed:

Java Development Kit (JDK) 11 or higher

Apache Maven

MySQL Server running on your local machine

A MySQL user with the username root and password root

⚙️ Setup Instructions
1. Database Setup (MySQL)
This project is configured to automatically create the database and table on startup.

Ensure your MySQL server is running.

The application will attempt to connect to a database named banking_db on localhost:3306. If it doesn't exist, Spring will automatically create it for you thanks to the spring.datasource.url property in application.properties.

The Account entity will be mapped to a table named account in the banking_db database, and its schema will be automatically updated by Hibernate (spring.jpa.hibernate.ddl-auto=update).

2. Configure application.properties
The src/main/resources/application.properties file contains the database connection details. Make sure these settings match your local MySQL configuration.

Properties

# MySQL DataSource configuration
spring.datasource.url=jdbc:mysql://localhost:3306/banking_db?createDatabaseIfNotExist=true
spring.datasource.username=root
spring.datasource.password=root
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

# JPA/Hibernate configuration
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL5Dialect
Note: If your MySQL username or password is not root, please update these values accordingly.

3. Build and Run the Application
Navigate to the root directory of the project in your terminal and execute the following Maven command:

Bash

mvn spring-boot:run
This command will download all dependencies, compile the code, and start the Spring Boot application. The console menu will appear in your terminal.

🎮 How to Use
Once the application is running, you will see a menu of options in your terminal. Enter the number corresponding to the action you wish to perform and press Enter.

--- Banking System Menu ---
1. Create Account
2. Deposit
3. Withdraw
4. View Account
5. List All Accounts
6. Exit
Enter your choice:
Example Usage:
Create an Account:

Enter 1

Enter a name (e.g., John Doe)

Enter an initial balance (e.g., 1000.00)

The application will display a success message with the new account's details, including its ID.

View an Account:

Enter 4

Enter the account ID you wish to view.

Deposit:

Enter 2

Enter the account ID to deposit into.

Enter the amount to deposit.

Withdraw:

Enter 3

Enter the account ID to withdraw from.

Enter the amount to withdraw. The application will prevent withdrawals that exceed the current balance.

List All Accounts:

Enter 5 to see a list of all accounts currently in the database.

Exit:

Enter 6 to gracefully shut down the application.

Verifying Database Changes
You can verify that the data is being saved and updated in real-time by using a MySQL client (like the command-line client or MySQL Workbench). Simply connect to the banking_db database and run the following SQL query:

SQL

SELECT * FROM account;
You will see the records change live as you interact with the console application.
