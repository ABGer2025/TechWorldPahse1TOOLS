# Build Tools Exercises Summary

## EXERCISE 1: Build jar artifact

### Official Instructions
You want to deploy the artifact to share that library with all team members. So:
- Try to build the jar file
- The Build will fail, because of a compile error in a test, so you can't build the jar.

### Steps Completed
1. Updated `build.gradle` to use Java 21 (changed from Java 17 to match installed JDK)
2. Attempted to build the project with `gradle build`
3. **Result:** Build failed as expected with compilation error in `AppTest.java` line 22
   - Error: Incompatible types - String cannot be converted to boolean
   - `boolean result = myApp.getCondition("true");`

---

## EXERCISE 2: Run tests

### Official Instructions
- Fix the test, by changing "true" string to true boolean
- Run gradle test to execute only the tests and check the fix

### Steps Completed
1. Opened `src/test/java/AppTest.java`
2. Changed line 22 from `boolean result = myApp.getCondition("true");` to `boolean result = myApp.getCondition(true);`
3. Ran `gradle test`
4. **Result:** BUILD SUCCESSFUL - All tests passed

---

## EXERCISE 3: Clean and build App

### Official Instructions
You fixed the test. Now:
- Clean the build folder with gradle clean
- Try to build jar file again

### Steps Completed
1. Executed `gradle clean` - Successfully cleaned build folder
2. Executed `gradle build` - Successfully built the project
3. **Result:** BUILD SUCCESSFUL - JAR file created at `build/libs/build-tools-exercises-1.0-SNAPSHOT.jar`

---

## EXERCISE 4: Start application

### Official Instructions
Start the jar file to test that the application runs successfully as a jar file
- Start app with `java -jar build/libs/app-1.0.jar`
- NOTE: replace "app-1.0.jar" with the name of YOUR jar file

### Steps Completed
1. Listed files in `build/libs/` directory to find the JAR name
   - Found: `build-tools-exercises-1.0-SNAPSHOT.jar`
2. Started the application with `java -jar build/libs/build-tools-exercises-1.0-SNAPSHOT.jar`
3. **Result:** Application started successfully
   - Spring Boot application running on port 8080
   - Tomcat server initialized
   - Welcome page available at `http://localhost:8080`

---

## EXERCISE 5: Start App with 2 Parameters

### Official Instructions
Now you want to add parameters to your application, so you and other users can pass different values on startup.
- Add parameter input to the Java code
- Rebuild the jar file
- Execute the jar file again with 2 params

**Code snippet provided:**
```java
Logger log = LoggerFactory.getLogger(Application.class);
try {
    String one = args[0];
    String two = args[1];
    log.info("Application will start with the parameters {} and {}", one, two);
} catch (Exception e) {
    log.info("No parameters provided");
}
```

### Steps Completed
1. Modified `src/main/java/com/example/Application.java`
   - Added the parameter handling code in the `main` method before `SpringApplication.run()`
2. Rebuilt the JAR file with `gradle build`
3. Started application with two parameters: `java -jar build/libs/build-tools-exercises-1.0-SNAPSHOT.jar param1 param2`
4. **Result:** Application started successfully with parameters
   - Log output confirmed: "Application will start with the parameters param1 and param2"
   - Application running on port 8080

---

## Summary of Changes

### Files Modified:
1. **build.gradle** - Updated Java toolchain version from 17 to 21
2. **src/test/java/AppTest.java** - Fixed test by changing String "true" to boolean true
3. **src/main/java/com/example/Application.java** - Added parameter handling in main method

### Git Commit:
- Commit message: "Complete exercises 1-5: Fix test, add parameters, update Java version to 21"
- All changes pushed to `main` branch successfully

### Key Learnings:
- How to diagnose and fix compilation errors in Gradle builds
- Running specific Gradle tasks (test, clean, build)
- Building and executing JAR artifacts
- Adding command-line parameter support to Spring Boot applications
- Managing Java toolchain versions in Gradle
