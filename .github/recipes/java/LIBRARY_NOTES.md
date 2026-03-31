# Java Library Integration Notes

Consult these notes when a user requests specific libraries to avoid common configuration pitfalls and outdated practices.

## Spring Boot
- **JPA / Hibernate**: If adding `spring-boot-starter-data-jpa`, ALWAYS ensure a database driver (e.g., `postgresql` or `h2`) is also added to the `pom.xml` or `build.gradle` to prevent runtime crashes on startup.
- **Lombok**: If scaffolding with Lombok, remind the user to configure their IDE plugin for annotation processing.
