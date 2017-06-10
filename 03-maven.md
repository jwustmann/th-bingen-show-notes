# Maven and Travis

## YouTube Videos

* [Part I: Git](https://youtu.be/zLxuCqzwxdw)
* [Part II: Maven](https://youtu.be/cOpbWdK9j0U)
* [Part III: Travis](https://youtu.be/b3C31lQU4zE)
* [Part IV: Homework](https://youtu.be/yM1dIL5p5KM)

## Show Notes

* how to get the latest project version with Git
* how projects are developed, built, and executed
* how Maven can help
* how Travis can help

### How can Git share code?

As part of the last homework, you contributed to the _Energy Model_ project on GitHub, which changed the original repository.
Now you need to update your fork and your local clone.
To do that you need to "connect" your local clone to the original version, which is usually called _upstream_:

```bash
git remote -v
# very likely you will only see "origin" (twice);
# if so, execute the following command:
git remote add upstream https://github.com/nicolaiparlog/energy-model.git
git remote -v
# now you can see "origin" and "upstream"
```

You are now ready to...

* pull the latest changes from _upstream_ into your local copy
* push them from there to your fork

All Git operations that interact with remotes (particularly push and pull) default to _origin_.
If you want to interact with _upstream_, you need to mention it in the right places:

```bash
# switch to the master branch
git checkout master
# pull the changes from "upstream" into your local clone
git pull upstream master
# now your local version is updated;
# time to push the changes to your fork
git push
```

* if anything fails, post in the forum
* if you want, you can delete local branches with `git branch -d <branch-name>`
* if you also want to delete the branches you pushed to your fork (list them with `git branch -a`), you can do that with `git push --delete origin <branch-name>`.

### How are projects built?

We have been using IntelliJ to write our code as well as to execute it when trying it out.
Sooner or later we want to make our project usable to people who do not want to install an IDE - what has to be done for that?

* the source code we write is not executable as is - instead it needs to be [compiled](https://en.wikipedia.org/wiki/Compiler) into _byte code_
* each source code file is compiled into at least one byte code file, which can result in quite a lot of files - to make dealing with them easier they are packaged into an _artifact_ that is called a _JAR_ (essentially a ZIP-file with a different file extension)
* projects often not only consist of their own code but also use libraries or frameworks that offer functionality the project needs; these _dependencies_, in the form of JAR files, need to be present during compilation
* managing dependencies is actually a pain; these are just regular files but they need to be downloaded (as well as _their_ dependencies), organized and put into all the right places
* ideally projects should contain _tests_, which need to be executed to verify the code is working as expected
* there can be other files that need to be part of the artifact, like JavaScript, HTML, or CSS files for web applications or configuration
* complex projects have many more details that need to be sorted out...

IntelliJ (and other IDEs for that matter) usually only compile the source code to byte code and then execute it (or the tests if you want).
This makes them valuable during development but they do not suffice to build a full project.

### How can Maven help?

This is where build tools come in.
They make all of the above steps configurable in one file and execute them in a sensible order, giving ample feedback about what worked (and what didn't).

Maven is the most prominent build tool for Java, to which Kotlin is strongly related, so it makes a good tool for Kotlin as well.
Some central concepts:

* Maven is a program much like Git that you install locally and invoke in your project
* unlike Git, Maven needs a project-specific configuration to work; this is a file `pom.xml` in the project's root directory
* Maven operates with "convention over configuration", meaning many details do not have to be configured if they follow the convention; some examples:
	* source files are located in `src/main/java` (which we need to change to `src/main/kotlin`)
	* _test_ source files are located in `src/test/java` (which we will eventually change to `src/test/kotlin`)
	* all output is generated in the `target` folder
* Maven goes through a series of phases to build your project from source code all the way to a self-contained artifact
* the end result is a file like `energy-model-1.0-SNAPSHOT.jar` in the `target` folder

But Maven not only executes the build, it also manages dependencies:

* dependencies are specified with a _group ID_, an _artifact ID_, and a _version_; for example:
	* group ID: `com.univocity`
	* artifact ID: `univocity-parsers`
	* version: `2.4.1`
* the block that goes into the `pom.xml` looks as follows:

	```xml
	<dependency>
		<groupId>com.univocity</groupId>
		<artifactId>univocity-parsers</artifactId>
		<version>2.4.1</version>
	</dependency>
	```
* Maven downloads dependencies, stores them on disk, and makes sure they end up where they are needed, e.g. during compilation

### How can Travis help?

Build tools like Maven are great but you have to run them to make use of them.
Want to make sure your changes compile?
Run Maven!
Want to make sure the pull request makes sense?
Run Maven!
Want to create a testable version of your project?
Run Maven!
Want to release a new version of your project?
Run Maven!

This is particularly problematic in a big team, where projects are rapidly changed but need to be constantly verified.
This is where a _continuous integration_ (CI) server comes in.
A CI server is usually configured to execute the project's build tool on every commit and show the results in places that are easy to see.

Travis is one such CI server and can easily be configured to work together with GitHub.
Once activated for a project, Travis will build every pull request and display feedback below the conversation with a link back to more details.
This helps everybody involved in the project to see whether a PR should even be considered to be merged.

## Homework

Most of the Maven documentation, tutorials, and other resources focus in Java.
You can assume that all of it applies to Kotlin as well unless I point out differences.

### Install Maven

There are many ways to install Maven but I recently discovered Jenv, a great tool to manage all kinds of Java-based applications (like Maven).
Head over to [jenv.io](http://www.jenv.io/) and install the tool, then run `jenv selfupdate` to update all information to the current version.

You are now set up to install maven with `jenv install maven 3.5.0`.
When asked whether that version should become the default, say `Y`(es).
Make sure everything works as planned with `mvn --version`.

### Study XML

Spend 10 minutes to learn XML basics:

* [Introduction to XML](http://www.xmlfiles.com/xml/xml_intro.asp) and [XML Syntax](http://www.xmlfiles.com/xml/xml_syntax.asp) by Jan Egil Refsnes
* [XML introduction](https://developer.mozilla.org/en-US/docs/XML_Introduction) on MDN

### Study Maven

Watch the following videos (parts of a very thorough introduction; in total a little over an hour):

* [Maven Tutorial 01 Part 1- Introduction and Setting up](https://www.youtube.com/watch?v=al7bRZzz4oU&list=PL92E89440B7BFD0F6) (you can skip the install guide from 3:22 to 5:12)
* [Maven Tutorial 01 Part 2- Introduction and Setting up](https://www.youtube.com/watch?v=KlIM897RGwc&list=PL92E89440B7BFD0F6&index=2)
* [Maven Tutorial 02- Understanding Archetypes and pom.xml](https://www.youtube.com/watch?v=AI8Kjag1vGk&list=PL92E89440B7BFD0F6&index=3)
* [Maven Tutorial 03- Maven Build Phases](https://www.youtube.com/watch?v=IYRYbPR5Gek&index=4&list=PL92E89440B7BFD0F6)
* [Maven Tutorial 04 - Adding a Dependency](https://www.youtube.com/watch?v=IRKu8_l5YiQ&list=PL92E89440B7BFD0F6&index=5)
* [Maven Tutorial 06 - Introduction to Plugins with the Maven Compiler Plugin](https://www.youtube.com/watch?v=OQLBcd8QrWk&index=7&list=PL92E89440B7BFD0F6)

Work through these tutorials on your own machine:

* [Your First Maven Project](http://tutorials.jenkov.com/maven/your-first-maven-project.html)
* [Maven in 5 Minutes](https://maven.apache.org/guides/getting-started/maven-in-five-minutes.html)

Now it gets a little bit more complicated.
So far you've used Maven with Java, which works out of the box - interacting with Kotlin requires more work.
But in the end Kotlin is compiled to the same byte code files (recognizable by their `.class` file extension), which means we can use Java to execute them.
To prepare yourself [read the documentation on Kotlin and Maven](https://kotlinlang.org/docs/reference/using-maven.html).
Don't follow along yet and don't worry if you don't get all the details - we'll do it in small steps.

### Hand In

Our goal is to get Maven to build the project with `mvn clean install` and then execute it with `java -jar <resulting-artifact>`.
Follow the steps below carefully!

Some notes:

* There should only be one of the following tags: `<properties>`, `<dependencies>`, `<build>/<plugins>` - if you have several properties, dependencies, or plugins, you can enumerate all of them inside those tags.
* When you want to look at a simple example, check out [the `pom.xml` from the Travis demo project](https://github.com/nicolaiparlog/travis-demo/blob/master/pom.xml).

Before starting, create a new branch (e.g. `maven`) and make sure to commit completed steps on the way to eventual success.
If you want, you can push the branch immediately (without any new commits) and create a pull request right away - because Travis is activated, you will get feedback on the PR telling you how you're doing.

If you have _any_ questions, it is best to push what you have (whether it works or not), open a PR, and then ask the question there - this way I can see your exact problem.

#### New pom.xml

Create a new `pom.xml` and define our project's name with group ID `org.codefx.demo.bingen`, artifact ID `energy-model`, and version `1.0-SNAPSHOT`.
Note that `mvn clean install` works but the _compile_ goal does nothing:

```
[INFO] --- maven-compiler-plugin:3.1:compile (default-compile) @ energy-model ---
[INFO] No sources to compile
```

The reason is that the compiler plugin looks for Java sources in `src/main/java`, which doesn't exist, so nothing is compiled.
Before we come to that we want to get rid of that warning about the encoding - have a look at [the Maven docs](https://maven.apache.org/plugins/maven-resources-plugin/examples/encoding.html) for how to do that.
After that, there should be no more warnings.

#### Compile Kotlin sources

To remedy the empty compilation, follow the documentation for [defining the plugin and versions](https://kotlinlang.org/docs/reference/using-maven.html#plugin-and-versions) (use `1.1.2` instead of `1.1.2-2`) and [compiling Kotlin only source code](https://kotlinlang.org/docs/reference/using-maven.html#compiling-kotlin-only-source-code).
Note that we don't have tests, so you can leave out the tags for `<testSourceDirectory>` and the `<execution>` tag that contains `<id>test-compile</id>`.

When executing `mvn clean install`, you should now see the Kotlin compiler going to work:

```
[INFO] --- kotlin-maven-plugin:1.1.2:compile (compile) @ energy-model ---
[INFO] Kotlin Compiler version 1.1.2
[INFO] Compiling Kotlin sources from [/home/nipa/code/th-bingen-energy-model/src/main/kotlin]
```

It then fails because we use types from the Kotlin standard library but the compiler does not know where to find them.
The [section on dependencies](https://kotlinlang.org/docs/reference/using-maven.html#dependencies) explains how to fix that.
After that `mvn clean install` should be successful.

Have a look into `target` now.
You will find the compiled `MainKt.class` (from `Main.kt`) in `target/classes/org/codefx/demo/bingen/energy_model` and a JAR `energy-model-1.0-SNAPSHOT.jar` in `target` - it contains that byte code file and some meta information.

#### Execute the created JAR

The resulting JAR can be executed on the command line as follows:

```
java -jar target/energy-model-1.0-SNAPSHOT.jar
```

If you do that, you will see that Java complains about some missing manifest attribute - until we fix that, you will have to do the following:

```
java -cp target/energy-model-1.0-SNAPSHOT.jar org.codefx.demo.bingen.energy_model.MainKt
```

While this actually executes the JAR we created it fails due to some missing Kotlin stuff.
Like during compilation the reason is that the standard library is missing.
This is an **important lesson**:
The compiler **does not include dependencies**!
It compiles source code _against_ them but to run the byte code you also need them.

#### Build self-contained JAR file

For applications (like our potential energy model), it is not unusual to create an artifact that contains the project's code as well as all dependencies, so that the JAR can be executed without further ado - this is called a _self-contained JAR_.

To create one have a look at [the corresponding section in the docs](https://kotlinlang.org/docs/reference/using-maven.html#self-contained-jar-file).
Note that the proposed configuration references the property `main.class` which you can define under `<properties>` with `<main.class>org.codefx.demo.bingen.energy_model.MainKt</main.class>`.
This tells Maven to create the the manifest attribute that was missing earlier.

After running `mvn clean install` you should see a new file in `target`: `energy-model-1.0-SNAPSHOT-jar-with-dependencies.jar`.
Run that with the `java -jar` command and you should see the desired output `Hello, World!` - **congratulations**!

If you didn't do that earlier, create a pull request with your changes.

## Further Sources:

* [Maven for building Java applications - Tutorial (Vogella)](http://www.vogella.com/tutorials/ApacheMaven/article.html)
* [Maven Tutorial (Jenkov)](http://tutorials.jenkov.com/maven/maven-tutorial.html)
