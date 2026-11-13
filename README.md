# GoldenCompass

GoldenCompass is a **command-line application for managing internship applications**, optimised for fast typists who prefer a keyboard-driven workflow. It helps you track internships, schedule interviews, and stay on top of deadlines, all from your terminal. Given below are instructions on how to set up, build, and test the project.

## Setting up in Intellij

Prerequisites: JDK 17 (use the exact version), update Intellij to the most recent version.

1. **Ensure Intellij JDK 17 is defined as an SDK**, as described [here](https://www.jetbrains.com/help/idea/sdk.html#set-up-jdk) -- this step is not needed if you have used JDK 17 in a previous Intellij project.
1. **Import the project _as a Gradle project_**, as described [here](https://se-education.org/guides/tutorials/intellijImportGradleProject.html).
1. **Verify the setup**: After the importing is complete, locate the `src/main/java/seedu/goldencompass/GoldenCompass.java` file, right-click it, and choose `Run GoldenCompass.main()`. If the setup is correct, you should see something like the below:
   ```
   > Task :compileJava
   > Task :processResources NO-SOURCE
   > Task :classes

   > Task :GoldenCompass.main()
   Hello, I'm your Golden Compass!
   ```
   Type a command (e.g., `list`) and press enter to try it out, or type `bye` to exit. Refer to the [User Guide](docs/UserGuide.md) for the full list of commands.

**Warning:** Keep the `src\main\java` folder as the root folder for Java files (i.e., don't rename those folders or move Java files to another folder outside of this folder path), as this is the default location some tools (e.g., Gradle) expect to find Java files.

## Build automation using Gradle

* This project uses Gradle for build automation and dependency management, configured in the `build.gradle` file.
* Commonly used tasks (use `gradlew` instead of `./gradlew` on Windows):
  * `./gradlew run` -- runs the application.
  * `./gradlew shadowJar` -- builds the executable JAR file `build/libs/goldencompass.jar`.
  * `./gradlew check` -- runs the Checkstyle checks and the JUnit tests.
* If you are new to Gradle, refer to the [Gradle Tutorial at se-education.org/guides](https://se-education.org/guides/tutorials/gradle.html).

## Testing

### I/O redirection tests

* To run _I/O redirection_ tests (aka _Text UI tests_), navigate to the `text-ui-test` folder and run the `runtest(.bat/.sh)` script.
* The script builds the JAR file, feeds `input.txt` to the application, and compares the actual output against `EXPECTED.TXT`.

### JUnit tests

* JUnit tests are located in `src/test/java/seedu/goldencompass`, covering the commands, the parser, and the storage.
* To run them, use `./gradlew test`, or right-click the `src/test/java` folder in Intellij and choose `Run 'All Tests'`.
* If you are new to JUnit, refer to the [JUnit Tutorial at se-education.org/guides](https://se-education.org/guides/tutorials/junit.html).

## Checkstyle

* The CheckStyle rule configuration of this project is in the `config/checkstyle` folder.
* To check the code against the rules, run `./gradlew checkstyleMain checkstyleTest`.
* If you are new to Checkstyle, refer to the [Checkstyle Tutorial at se-education.org/guides](https://se-education.org/guides/tutorials/checkstyle.html).

## CI using GitHub Actions

The project uses [GitHub actions](https://github.com/features/actions) for CI. When you push a commit to this repo or PR against it, GitHub actions will run automatically to build and verify the code as updated by the commit/PR. The workflow runs the Gradle checks and the I/O redirection tests on Ubuntu, macOS, and Windows.

## Documentation

`/docs` folder contains the project documentation:

* [User Guide](docs/UserGuide.md) -- how to install and use GoldenCompass.
* [Developer Guide](docs/DeveloperGuide.md) -- the design and implementation of GoldenCompass.
* [About Us](docs/AboutUs.md) -- the team behind GoldenCompass.

The documentation is published to the public via GitHub Pages, with the `source` set as `master branch /docs folder` in the `settings` tab of the team repo on GitHub.
