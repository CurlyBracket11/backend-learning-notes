Maven kya hai?

Maan lo tum ek Java project bana rahi ho jisme:

\- Spring Boot

\- MySQL

\- Spring Data JPA

\- Spring Security

\- Lombok

use karna hai.



In sabki libraries manually download karna, correct versions maintain karna aur project mein add karna tedious hoga.



**Maven ek build automation aur dependency management tool hai.**

Iska kaam:

1\. Dependencies download aur manage karna.

2\. Java code compile karna.

3\. Tests execute karna.

4\. Application package karna.

5\. Build process automate karna.



**Dependency kya hoti hai?**

Dependency ek external library hoti hai jiski functionality tum apne project mein use karti ho.

Example: MySQL Driver.

Tumhe MySQL se connect karna hai, toh MySQL JDBC driver dependency chahiye.



**pom.xml kya hai?**

Maven project ki main configuration file.

POM ka full form hai Project Object Model.



**Maven Wrapper kya hai?**

Humare project mein do important files hain:

\- mvnw

\- mvnw.cmd



Ye Maven Wrapper hain.

Normally Maven use karne ke liye system mein Maven install hona chahiye.

Wrapper project ke required Maven version ko manage karke Maven commands run karne mein help karta hai.



**Important Maven commands**

Command	Purpose

.\\mvnw.cmd clean	        Previous build output clean karta hai.

.\\mvnw.cmd compile	        Main source code compile karta hai.

.\\mvnw.cmd test	                Tests run karta hai.

.\\mvnw.cmd package	        Application package karta hai.

.\\mvnw.cmd clean install	Clean, compile, test, package aur local Maven repository mein install tak lifecycle execute karta hai.

.\\mvnw.cmd spring-boot:run	Spring Boot application run karta hai.





**Maven: Build aur dependency management tool.**

**Spring Boot: Java backend application develop karne ka framework.**

**Tomcat: HTTP requests receive aur handle karne wala web server.**





