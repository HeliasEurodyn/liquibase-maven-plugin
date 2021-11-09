# Liquibase Maven Plugin

This project provides an easy way to generate Liquibase ChangeLogs from Databases.
<br>The chapter <b>Generate Changelog File from Database</b> explains how to generate a Changelog from a database. 
<br>While the chapter <b>Generate Diff Changelog File from 2 Databases differences</b> explains how to generate a Changelog from 2 database differences.

### Generate Changelog File from Database  
Navigate to the below file to setup the database & changelog properties
```sh
/src/main/resources/db/liquibase.properties
```
On lines 1 to 4 define your Database's path and credentials.
```sh
url=jdbc:mysql://localhost:3306/sofia4
username=root
password=
driver=com.mysql.cj.jdbc.Driver
```

On line 6 define the path & the name that your generated changelog file will save.
```sh
outputChangeLogFile=src/main/resources/db/changelog/db.changelog-1.4.0.xml
```

Save everything, open a command line and execute the command.
```sh
mvn liquibase:generateChangeLog
```

The Changelog file will be generated.

### Generate Diff Changelog File from 2 Databases differences  
Navigate to the below file to setup the database & changelog properties
```sh
/src/main/resources/db/liquibase.properties
```
On lines 1 to 4 define your Database's path and credentials.
```sh
url=jdbc:mysql://localhost:3306/sofia4
username=root
password=
driver=com.mysql.cj.jdbc.Driver
```

On lines 8 to 11 define your updated Database's path and credentials.
```sh
url=jdbc:mysql://localhost:3306/sofia5
username=root
password=
driver=com.mysql.cj.jdbc.Driver
```

Navigate to pom.xml and on line 67 define the path & the name that your generated changelog file will save.
```sh
<diffChangeLogFile>src/main/resources/db/changelog/db.changelog-diff.xml</diffChangeLogFile>
```

Save everything.
Open a command line and execute the command below just to view the differences of the 2 databases.
```sh
mvn liquibase:diff
```

Open a command line and execute the command below to generate the Changelog file.
```sh
mvn liquibase:diff -Dliquibase.diffChangeLogFile
```

For more mvn liquibase commands please advise the Liquibase Maven Goals docs <a href="https://docs.liquibase.com/tools-integrations/maven/commands/home.html" target="_blank">here </a>.
