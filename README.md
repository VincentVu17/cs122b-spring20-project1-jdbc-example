# CS 122B Project 1 JDBC example

This example shows how a Java program can use JDBC to connect with MySQL.

## To run this example: 

1. Make sure you have properly installed Java, Maven, Git, MySQL, and Intellij on your local machine.
2. Clone this repository using `git clone https://github.com/UCI-Chenli-teaching/cs122b-spring20-project1-jdbc-example.git`

3. Create users and sample tables on mysql by executing the following command:

 - login to mysql as a root user 
    ```
    local> mysql -u root -p
    ```

 - create a test user and grant privileges:
    ```
    mysql> CREATE USER 'mytestuser'@'localhost' IDENTIFIED BY 'mypassword';
    mysql> GRANT ALL PRIVILEGES ON * . * TO 'mytestuser'@'localhost';
    ```

 - create a testdb:
    ```
    mysql> create database testdb;
    mysql> use testdb;
    mysql> create table stars(
               id varchar(10) primary key,
               name varchar(100) not null,
               birthYear integer
           );
    ```
 - insert some records:
    ``` 
    mysql> INSERT INTO stars VALUES('755011', 'Arnold Schwarzeneggar', 1947);
    mysql> INSERT INTO stars VALUES('755017', 'Eddie Murphy', 1961);

    mysql> select * from stars;
    ```
 - exit and re-login mysql with test user, with the password you created:
    ```
    mysql> quit
    local> mysql -u mytestuser -p
    ```
 - verify you can access data:    
    ```
    mysql> use testdb;
    mysql> select * from stars;
    ```

### To import project into Intellij and run within Intellij:

1. Open Intellij -> Import Project -> Choose the project you just clone (The root path mush contain the pom.xml!) -> Choose Import project from existing sources -> choose `Maven` -> Click on Finish -> The Intellij wll load automatically
2. If the system asks you to import MAVEN modules using the tooltip, just click on `import changes`
3. If the Intellij shows `Project SDK is not defined`, that may because your Intellij doesn't have default SDK, so just click on `Setup SDK` and choose your JDK.
4. To run JDBC1.java, JDBC2.java, click Run on the right corner, then you will successfully see the results

### Alternatively, to run the Java program within command line:

1. Go to the repository folder, run `mvn clean install`.
2. Run `mvn exec:java -q -Dexec.cleanupDaemonThreads=false -Dexec.mainClass="JDBC1"`. To run JDBC2, change `mainClass="JDBC1"` to `mainClass="JDBC2"`.
