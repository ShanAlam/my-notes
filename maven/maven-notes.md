# Maven

## What is Maven?

Maven is a build automation and project management tool for Java projects.  

You can think of it as the Java equivalent of Python’s `pip` or `setuptools`.

---

## Key Features

- Simplifies downloading and managing project dependencies.  
- Provides a standardized project structure based on conventions.  
- Supports plugins to run quality checks, build tasks, or deploy applications.

---

## How to Identify a Maven Project

A Maven project typically contains:

- A `pom.xml` file  
- A `src/` directory  

The `pom.xml` defines the project and its configuration. Typical sections include:  

- **`<properties>`** – general project information like Java version or encoding.  
- **`<dependencies>`** – lists all external libraries the project needs.  
- **`<build>`** – configuration for build tasks, including plugins for compiling, testing, or packaging.  

**Example project structure:**

my-app/
│
├── pom.xml
└── src/
    ├── main/
    │   ├── java/
    │   └── resources/
    └── test/
        ├── java/
        └── resources/

---

## How to Install Maven

**On macOS:** Use Homebrew  
```bash
brew install maven
```

**On Windows:** Use Chocolatey  
```bash
choco install maven
```

**Using Maven Wrapper**

If you want to create a Maven project in a way where the person who clones your code doesn’t need to worry about installing Maven, you can include a Maven Wrapper in your project.  

You do this by running the command:  
```bash
mvn wrapper:wrapper  
```

This will add a `mvnw` file to your project. When someone clones the project, they can use `./mvnw` (Linux/macOS) or `mvnw` (Windows) instead of the `mvn` command.  

To verify that the project is successfully recognized as a Maven project, run:  
```bash
./mvnw validate
```

---

## Running a Maven Project

When you build a Maven project, the **`target/`** folder is created. This folder stores all build outputs, such as compiled `.class` files and packaged `.jar` files.  

Common Maven commands using the wrapper:

- **Clean build outputs:**  
```bash
./mvnw clean  
```

- **Compile main source code (`src/main/java`):**  
```bash
./mvnw compile  
```

- **Compile and run tests (`src/test/java`):**  
```bash      
./mvnw test
```  
Or combine compile and test:  
```bash
./mvnw compile test  
```

- **Package compiled code into a JAR file:**  
```bash
./mvnw package
```  
Or combine compile, test, and package:  
```bash      
./mvnw compile test package  
```

- **Install the packaged JAR into your local Maven repository:**  
```bash
./mvnw install
```  
Or combine compile, test, package, and install:  
```bash
./mvnw compile test package install
```

---

## Multi-Module Maven Projects

Maven supports **multi-module projects**, which allow you to organize a large application into multiple smaller sub-projects (modules) that are built together.  

- A multi-module project has a **parent POM** at the root.  
- Each module has its own `pom.xml` file and typically a `src/` directory.  
- Modules can depend on each other, but you only need to build the parent project to build all modules.  

**Example multi-module structure:**

my-multi-app/
│
├── pom.xml        # parent POM
├── module-a/
│   ├── pom.xml
│   └── src/
└── module-b/
    ├── pom.xml
    └── src/

**Building multi-module projects:**  
Run Maven commands at the parent level:  
```bash
./mvnw clean install  
```

This will build **all modules** in the correct order according to dependencies defined in their POMs.
