Solr Web 
=============
This project is a skeleton to create Solr 4.10.3 web applications.
Requires 2 parameters in order to replace those values in files: logging.properties and web.xml.
  -warName: name of the web application
  -solr.home: path to the solr home directory.
  
For example:
mvn clean war:war -DwarName=registry-solr -Dsolr.home=/var/local/large/solr/registry-solr/ -DlogDir=/var/log/tomcat/
creates a file registry-solr.war

The logging.properties file will be transformed from:

```java.util.logging.FileHandler.pattern = ${logDir}${warName}.log```

 to:
 
```java.util.logging.FileHandler.pattern = /var/log/tomcat/registry-solr.log```

The file web.xml contains the path to the solr home directory:
```
<env-entry>
    <env-entry-name>solr/home</env-entry-name>
    <env-entry-value>${solr.home}</env-entry-value> 
```
This value will be replaced by "/var/local/large/solr/registry-solr/" for the example command above.
    
### Pending tasks:
1. An deployment plugin (like Cargo) can be used to deploy the result war file in running container.

