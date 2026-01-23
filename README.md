# Spring MVC + Hibernate CRUD Application

This is a classic Spring MVC (non-Spring Boot) CRUD application.
The application allows you to view, add, update and delete employees using a web interface (JSP).
All changes are persisted in a MySQL database.

🛠 Requirements

Java 8+

Maven

MySQL 8.x

Apache Tomcat 9.x

IntelliJ IDEA (recommended)

## How to Run

1️⃣ Install MySQL

Make sure MySQL is installed and running on your computer.

MySQL version: 8.x

Default port: 3306

You can check MySQL installation by running:

mysql --version

Or by opening MySQL Workbench.

2️⃣ Create a local database

Open MySQL Workbench (or terminal) and execute the following SQL commands:

CREATE DATABASE my_db;
USE my_db;

Create table
CREATE TABLE employees (
  id INT NOT NULL AUTO_INCREMENT,
  name VARCHAR(15),
  surname VARCHAR(25),
  department VARCHAR(20),
  salary INT,
  PRIMARY KEY (id)
);

(Optional) Add test data
INSERT INTO employees (name, surname, department, salary) VALUES
('Lucas', 'Neumann', 'IT', 1200),
('Sophie', 'Keller', 'HR', 900),
('Maria', 'Klein', 'Sales', 950);


✅ Database is ready.

3️⃣ Configure database credentials

Open the file:

src/main/resources/applicationContext.xml


Find this section:

<bean id="dataSource"
      class="com.mchange.v2.c3p0.ComboPooledDataSource"
      destroy-method="close">

    <property name="driverClass" value="com.mysql.cj.jdbc.Driver"/>
    <property name="jdbcUrl"
              value="jdbc:mysql://localhost:3306/my_db?useSSL=false"/>
    <property name="user" value="root"/>
    <property name="password" value="root"/>

</bean>

What you can change if needed

jdbcUrl → database name (my_db)

user → MySQL username

password → MySQL password

Example (default setup):

<property name="user" value="root"/>
<property name="password" value="root"/>


If your credentials are different, simply update these values.

4️⃣ Run the application

This project is a classic Spring MVC application, so it must be deployed to Apache Tomcat.

Steps

Download Apache Tomcat 9.x
Example: apache-tomcat-9.0.113

Open the project in IntelliJ IDEA

Go to:

Run → Edit Configurations


Click +

Select:

Application Server → Tomcat Server → Local


Configure Tomcat:

Click Application Server → Configure

Choose the folder where Apache Tomcat is installed

Click Fix → Select artifact to deploy

Choose: spring_course_mvc:war exploded

Start the server (Run)

Open browser:

http://localhost:8080/


🎉 You should see the employee table in the browser.

ℹ️ Important notes

The database is not included in the repository (this is normal)

Each developer creates the database locally

All changes in the UI are persisted in MySQL

No additional MySQL users or connections are required

🧰 Technologies used

- Java
- Spring MVC
- Hibernate
- Spring AOP
- MySQL
- JSP
- Maven
