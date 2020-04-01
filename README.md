## CS 122B Project 1 JDBC example

This example shows how a Java program can use JDBC to connect with MySQL.

### To run this example: 

1. Make sure you have properly installed Java, Maven, Git, MySQL, and Eclipse on your local machine.
2. Clone this repository using `https://github.com/UCI-Chenli-teaching/cs122b-spring20-project1-jdbc-example.git`

3. Create users and sample tables on mysql by executing the following command:
```
mysql -u root -p

CREATE USER 'mytestuser'@'localhost' IDENTIFIED BY 'mypassword';
GRANT ALL PRIVILEGES ON * . * TO 'mytestuser'@'localhost';

create database testdb;
use testdb;
create table stars(
    id varchar(10) primary key,
    name varchar(100) not null,
    birthYear integer
);

INSERT INTO stars VALUES('755011', 'Arnold Schwarzeneggar', 1947);
INSERT INTO stars VALUES('755017', 'Eddie Murphy', 1961);

select * from stars;
exit

mysql -u mytestuser -p

use testdb;
select * from stars;
```

To import project into Eclipse and run within Eclipse:

4. Open Eclipse -> File -> import -> under "Maven" -> "Existing Maven Projects" -> Click "Next".
5. For "Root Directory", click "Browse" and select this repository's folder. Click "Finish".
6. To run JDBC1.java, JDBC2.java, click Run -> Run as -> Java Application.

Altenatively, to run the Java program within command line:

4. Go to the repository folder, run `mvn install`.
5. Run `mvn exec:java -q -Dexec.cleanupDaemonThreads=false -Dexec.mainClass="JDBC1"`. To run JDBC2, change `mainClass="JDBC1"` to `mainClass="JDBC2"`.
