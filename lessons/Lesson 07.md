# Lesson 07: Packages and Imports
## Packages
A package is a collection of related Java classes. At the top of every Java file, you will see its package declaration. In an FRC context, that is usually always something of the form `frc.robot.something;`. The folder structure simply matches your file system, so a file for a file called  `Drivetrain.Java` would be located within a package like `frc.robot.subsystems`, where the file, by definition, would be located in a folder called `subsystems`, within a folder called `robot`, within a folder called `frc`.

The convention to use for packages that are user defined (ie not part of the built in Java environment) is to reverse your website name. In FRC Worchester Polytechnic Institute designs the base code structure (this is the acronym WPI that appears everywhere in robot code and FRC programming discussions). Since WPI owns `https:/wpi.edu`, their packages use `edu.wpi` as the prefix to all of their code. This automatically guarantees any code they as WPI write and produce will be distinct from anyone else's code. In our case, we would not want to have someone else using the `org.wildcards` package namespace.

The `i2j` part is referencing the "Intro To Java" course name. It's useful to separate the projects or libraries at this level. This way, separate efforts at the same company won't conflict. If there were two libraries that both needed camera related classes, just using `org.wildcards.camera` as the package name for both would cause a conflict. So we separate them by the library/project.

Ironically, as stated before, FRC uses `frc.robot` for all package names. As far as I can tell, this package name reversal isn't actually a hard requirement for code design, but it is the industry standard and may lead to failures if not followed outside of an FRC context.

### Imports
An `import` statement is how you reference a specific class. Because people can make the same class name in multiple packages, you need to tell Java which class you meant. This is what the import statement handles for you:

```java
import package.name.Class;
```

(Note that that's not a real package name or class, it's only meant as a demonstration) We import a specific class by name by referencing the full path with its package.

You can also import all of the classes of a package:
```java
import package.name.*;
```

A real case you've seen in your assignments will be the `Scanner` class:
```java
import java.util.Scanner;
```

Some classes are in the `java.lang` package which gets imported automatically. That's why you don't have to do an import for `String` or `Math`, for example.
### Import static
One interesting thing you can do, which I find most useful when using the `Math` functions. Example:
```java
import static java.lang.Math.abs;
```

This would introduce the `abs()` method locally and you could just call it in your code directly. Instead of using `Math.abs()`, you'd just call `abs()`. You can also use an asterisk here as well instead of specifying the method directly.
### Multiple classes with the same name
Sometimes you end up in the situation where two classes have the same name in different packages, and you need to reference both. The way to handle this is to import one of them and use the "fully qualified" name for the other. That means every single place you use it, you have to specify the package with the class. e.g.:

```java
java.util.Scanner scanner;
```

This still is a variable that is of type `Scanner`, but we use the fully qualified path here instead of importing `java.util.Scanner` at the top of the file.

## Access Modifiers
Finally, I can go over the full list of access modifiers in Java. Instead of typing out everything, I'm going to reference this document: https://docs.oracle.com/javase/tutorial/java/javaOO/accesscontrol.html

Some things you might need to know:
- When they say "top level", they mean a modifier before the `class` keyword.
- When they say "member level", they mean a field or a method inside a class.

In general, if you understand `public` and `private`, you're pretty good for most Java code.