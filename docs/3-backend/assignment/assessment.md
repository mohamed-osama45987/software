# Module 3 Assessment

> **Submit your work on Skills Union →** <https://skillsu.com/member/assessment>

**Mandatory** • 20 questions • Covers concepts for the Backend lessons.

Try each question closed-book first. Click **Show hint** if you get stuck — hints point you at the relevant lesson section and how to think about it, without naming the answer.

---

**Q1.** Which of the following is NOT a Java primitive data type?

- int
- boolean
- String
- double

<details>
<summary>Show hint</summary>

- **Where:** [Java fundamentals](../java-fundamentals/variables-datatypes.md) — primitive vs reference types.
- **Think:** `String` is a class type, while the others are built-in primitive values.

</details>

**Q2.** What is the default value of an uninitialized `int` variable in a class?

- 1
- 0
- null
- undefined

<details>
<summary>Show hint</summary>

- **Where:** [Java fundamentals](../java-fundamentals/variables-datatypes.md) — default values for fields.
- **Think:** For numeric primitives, Java gives them a zero value when they are not explicitly assigned.

</details>

**Q3.** Which keyword is used to create an object in Java?

- create
- construct
- new
- make

<details>
<summary>Show hint</summary>

- **Where:** [Constructors and objects](../java-oop-01/constructors.md) — object creation.
- **Think:** This keyword is used to allocate a new instance of a class.

</details>

**Q4.** Which access modifier allows visibility within the same package only?

- default (no modifier)
- protected
- public
- private

<details>
<summary>Show hint</summary>

- **Where:** [Java packages](../corejava02/java-package.md) — package-level visibility.
- **Think:** If you do not write a modifier, Java allows access only inside the same package.

</details>

**Q5.** What does the `static` keyword mean when applied to a variable?

- Variable value cannot change
- Variable belongs to the class, not objects
- Variable is temporary
- Variable is private

<details>
<summary>Show hint</summary>

- **Where:** [Static keyword and POJOs](../java-oop-01/static-keyword-pojo.md) — class members.
- **Think:** The key idea is that the member is shared by the class itself, not by each instance.

</details>

**Q6.** What is the output of `System.out.println(10 / 4);`?

- 2
- 2.5
- 2.0
- Compilation error

<details>
<summary>Show hint</summary>

- **Where:** [Java operators](../corejava01/operators.md) — arithmetic division.
- **Think:** Both values are integers, so Java performs integer division here.

</details>

**Q7.** Which method is the entry point of a Java program?

- public static void main(String[] args)
- public static main(String args[])
- public void main()
- static public void main()

<details>
<summary>Show hint</summary>

- **Where:** [Class and main method](../java-fundamentals/class-main-method.md) — program entry point.
- **Think:** This exact signature is what Java looks for to start the program.

</details>

**Q8.** What does “inheritance” in Java mean?

- Using methods of another package
- Deriving new classes from existing ones
- Copying data from another class
- Overriding constructors

<details>
<summary>Show hint</summary>

- **Where:** [Inheritance](../java-oop-02/inheritance.md) — class relationships.
- **Think:** One class can build on another class and reuse its behavior.

</details>

**Q9.** Which collection class allows duplicate elements and maintains insertion order?

- ArrayList
- HashSet
- TreeSet
- LinkedHashMap

<details>
<summary>Show hint</summary>

- **Where:** [ArrayLists](../corejava02/arraylists.md) — list behavior.
- **Think:** This collection keeps items in the order you add them and allows repeats.

</details>

**Q10.** What is the purpose of the `this` keyword?

- Refers to the current class instance
- Refers to superclass object
- Refers to static members
- Refers to another package

<details>
<summary>Show hint</summary>

- **Where:** [Constructors and objects](../java-oop-01/constructors.md) — object references.
- **Think:** The keyword points to the current object you are working inside.

</details>

**Q11.** Spring Boot is mainly used to?

- Replace the Java compiler
- Simplify Spring application setup and configuration
- Replace JDBC
- Manage operating system services

<details>
<summary>Show hint</summary>

- **Where:** [Getting started with Spring Boot](../springboot-basics/springboot-intro.md) — what Spring Boot is for.
- **Think:** It helps you start Spring apps with much less manual setup.

</details>

**Q12.** The `@SpringBootApplication` annotation is a combination of which three annotations?

- @Configuration, @EnableAutoConfiguration, @ComponentScan
- @Service, @Repository, @Controller
- @RestController, @Component, @Bean
- @Autowired, @Value, @Bean

<details>
<summary>Show hint</summary>

- **Where:** [Spring Boot intro](../springboot-basics/springboot-intro.md) — application setup.
- **Think:** This annotation is the main entry-point setup for a Spring Boot app.

</details>

**Q13.** What is the default embedded server used by Spring Boot?

- Tomcat
- Jetty
- Undertow
- Netty

<details>
<summary>Show hint</summary>

- **Where:** [Spring Boot intro](../springboot-basics/springboot-intro.md) — built-in server behavior.
- **Think:** Spring Boot commonly runs web apps on this server by default.

</details>

**Q14.** Which file is used for application configuration in Spring Boot?

- application.properties or application.yml
- config.xml
- pom.xml
- settings.gradle

<details>
<summary>Show hint</summary>

- **Where:** [Spring Boot intro](../springboot-basics/springboot-intro.md) — configuration files.
- **Think:** These files store settings such as ports, database URLs, and secrets.

</details>

**Q15.** What does the `@RestController` annotation do?

- Marks a class as a service component
- Combines @Controller and @ResponseBody for REST APIs
- Marks configuration classes
- Enables auto-configuration

<details>
<summary>Show hint</summary>

- **Where:** [Basic routing](../springboot-basics/basicrouting.md) — controllers and responses.
- **Think:** This annotation is used when a controller should return data directly for API requests.

</details>

**Q16.** What does the `@Autowired` annotation do?

- Performs dependency injection automatically
- Creates a new bean manually
- Configures a database
- Registers routes

<details>
<summary>Show hint</summary>

- **Where:** [IoC and DI](../service-repository-pattern/iocanddi.md) — dependency injection.
- **Think:** Spring uses this to provide dependencies for you instead of creating them manually.

</details>

**Q17.** What is the default port Spring Boot runs on?

- 8081
- 8080
- 3000
- 5000

<details>
<summary>Show hint</summary>

- **Where:** [Spring Boot intro](../springboot-basics/springboot-intro.md) — default startup settings.
- **Think:** The usual default web port for Spring Boot apps is this number.

</details>

**Q18.** Which annotation is used to define a JPA entity class?

- @Table
- @Entity
- @Column
- @Repository

<details>
<summary>Show hint</summary>

- **Where:** [JPA and Hibernate](../spring-data-jpa-postgresql/jpa-hibernate.md) — entity mapping.
- **Think:** The annotation marks a Java class as a database entity.

</details>

**Q19.** Which annotation is used in Spring Data JPA to define a method as a CRUD operation?

- @Repository
- @Service
- @Controller
- @Bean

<details>
<summary>Show hint</summary>

- **Where:** [Repositories](../service-repository-pattern/repository.md) — data access layer.
- **Think:** This layer is where Spring Data JPA manages CRUD-style operations.

</details>

**Q20.** Which database is often used by Spring Boot for relational data storage?

- MongoDB
- MySQL
- PostgreSQL
- SQLite

<details>
<summary>Show hint</summary>

- **Where:** [PostgreSQL setup](../spring-data-jpa-postgresql/install-postgressql-dbeaver.md) — relational databases.
- **Think:** This is a common relational database choice for Spring Boot apps.

</details>
