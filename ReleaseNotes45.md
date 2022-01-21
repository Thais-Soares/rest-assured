# Release Notes for REST Assured 4.5.0 #

## Contents
1. [Highlights](#highlights)
1. [Minor Changes](#minor-changes)

## Highlights
* JAXB is now an optional dependency for XmlPath and is now longer required. Depend on `jakarta.xml.bind:jakarta.xml.bind-api:2.3.3` and `com.sun.xml.bind:jaxb-impl:2.3.3` to re-introduce support for JAXB if you're using Java 11+ [issue 1510](https://github.com/rest-
assured/rest-assured/issues/1510).
* Implemented support for serializing and deserializing XML with Jakarta EE 8 and 9. To use it you need to have Jakarta EE on the classpath, for example by depending on `jakarta.xml.bind:jakarta.xml.bind-api:3.0.1` and `org.glassfish.jaxb:jaxb-runtime:3.0.2`.
* Add on fail message builder for response specification. This means that you can no do:

  ```java
  when().
        get().
  then().
        onFailMessage("Some specific message").
        statusCode(200);
   ```
  The "onFailMessage" will be shown in the error. This is good if you want to e.g. more easily distinguish between tests if they fail. (thanks to Victor Borovlev for pull request) (issue [1502](https://github.com/rest-
assured/rest-assured/issues/1502)
* Introduced a rest-assured bom project for maven. Depend on 'io.rest-assured:rest-assured-bom:4.5.0' to use it. The bom contains configuration details for the rest-assured project that imports the correct dependencies (and versions) and to build your project. (thanks to George Gastaldi for pull request)


## Minor changes ##

See [change log](https://github.com/rest-assured/rest-assured/raw/master/changelog.txt) for more details.