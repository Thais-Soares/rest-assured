# Release Notes for REST Assured 4.5.0 #

## Contents
1. [Highlights](#highlights)
1. [Minor Changes](#minor-changes)

## Highlights
* Added `io.restassured.mapper.TypeRef` class that allows one to deserialize a response to a container with generic type. For example:

  ```java
  List<Map<String, Object>> products = get("/products").as(new TypeRef<List<Map<String, Object>>>() {});
  ```
  
  Note that currently this only works for JSON :(
* Added a artifact called `rest-assured-all` that can be used if you run into issues with split packages in Java 9+. If so exclude the `rest-assured` dependency from you build script and instead add (maven example):

   ```xml
   <dependency>
      <groupId>io.rest-assured</groupId>
      <artifactId>rest-assured-all</artifactId>
      <version>3.3.0</version>
      <scope>test</scope>
   </dependency>
   ```
  Thanks to Tomasz Gaweda for pull request.
* Introduces custom listeners on test validation failures. This makes it possible to hook into Rest Assured and get a callback when the test fails with full access to the request/response specification
  as well as the response. You can do this by implementing the [ResponseValidationFailureListener](http://static.javadoc.io/io.rest-assured/rest-assured/3.3.0/io/restassured/listener/ResponseValidationFailureListener.html) and add it to the new [FailureConfig](http://static.javadoc.io/io.rest-assured/rest-assured/3.3.0/io/restassured/config/FailureConfig.html). For example:

  ```
  given().config(RestAssured.config().failureConfig(failureConfig().with().failureListeners((requestSpec, responseSpec, response) -> log.info("Rest Assured validation failed!")).when(). ..
  ```
  (issue [1093](https://github.com/rest-assured/rest-assured/issues/1093)) (thanks to Daniel Dyląg for pull request).

## Minor changes ##

See [change log](http://github.com/jayway/rest-assured/raw/master/changelog.txt) for more details.