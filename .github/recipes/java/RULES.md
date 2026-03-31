# Java Ecosystem Rules

When BootstrApp is scaffolding or injecting dependencies into a Java project, adhere to the following rules:

## 1. Framework & Scope Selection
- **Do not assume Spring Boot immediately**. If the user asks for a "Java project," explicitly ask:
  - "Do you want to scaffold a Spring Boot application or a standard barebones Maven/Gradle project?"
- Only proceed with `spring-boot.json` or `maven-barebones.json` once confirmed.
- Maven allows different packaging (jar, war) and versions. Prompt the user for these details if they want a barebones project.

## 1. Environment & Planning Pre-Flight
- NEVER assume Java 21 or Java 17. ALWAYS run `java -version` first to detect the environment, and format your API request to Spring Initializr accordingly (e.g. `javaVersion=17`).
- Ask the user about their intent: "What are you planning to build? Do you need specific features like Web, Security, or Database integrations?"
- Since Java dependencies are hard to add manually later, it's best to gather this information upfront so you can ask Spring Initializr for the right `dependencies=` payload.

## 3. Build Tool Generation
- The user must explicitly choose **Maven** or **Gradle**.
- For Maven, request `type=maven-project` from Spring Initializr. Use `.\mvnw.cmd` for validation.
- For Gradle, request `type=gradle-project` from Spring Initializr. Use `.\gradlew.bat` for validation.
- **NEVER** mix build tools in the same directory.

## 4. Dependency Injection
- Unlike Node or Python, there are no CLI commands to simply inject a library. 
- You MUST use your file editing tools to manually update the `pom.xml` (Maven) or `build.gradle` (Gradle) files.
- ALWAYS run `.\mvnw.cmd clean compile` or `.\gradlew.bat classes` after a manual edit to ensure you didn't break the XML/Groovy syntax.