# Springdoc OpenAPI Externalized Documentation library

![Code Soapbox logo](readme-images/logo.png)

## Introduction

This library is an extension for *Springdoc OpenAPI* and allows for defining OpenAPI 3.0 specification outside of the
classes being documented.
 
Its main purpose is to allow documentation of domain model classes (such as value objects, enums) as part of the
OpenAPI specification, while maintaining their separation.

While it was developed with *Springdoc OpenAPI* in mind, **you can apply this solution to any
Spring Boot OpenAPI library based on Spring Core**.

## Getting Started

1. Add a dependency on `springdoc-openapi-externalized-documentation`:

```xml
<dependency>
    <groupId>com.danielfrak.code</groupId>
    <artifactId>springdoc-openapi-externalized-documentation</artifactId>
    <version>1.0.0</version>
</dependency>
```

2. Create an empty class and annotate it with `@ExternalizedSchema`:

```java
import com.danielfrak.code.springdoc.openapi.externalizeddocs.ExternalizedSchema;
import io.swagger.v3.oas.annotations.media.Schema;
import pl.nc.datapresenter.data.articles.domain.ArticleType;

@ExternalizedSchema(source = MyValueObject.class, schema = @Schema(
    implementation = String.class,
    example = "Example value",
    description = "Some description"
))
public class MyValueObjectDocs {
}
```

## @ExternalizedSchema fields

* `source` - the class to document
* `schema` - a `@io.swagger.v3.oas.annotations.media.Schema` annotation to apply to the source class