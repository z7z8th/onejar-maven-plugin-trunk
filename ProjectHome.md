_(new home of the onejar-maven-plugin)_

## Lets you build an executable jar with Maven2, containing all dependencies. ##

You can do that with the assembly plugin too, but that will just unpack all dependencies together with your classes in one directory and then repack that directory into a new jar. Doing it that way means files will overwrite each other if they have the same names in the same path, which is quite common with resources such as `log4.properties` and even other more important files.

**With onejar-maven-plugin, you'll instead get a nice clean super jar with the dependency jars inside.**

Get started by following the [Usage instructions](http://onejar-maven-plugin.googlecode.com/svn/mavensite/usage.html)!


---

#### UPDATE ####
We have moved the project here to Google Code, including the project's Maven repository. If you haven't already, you MUST update your `pom.xml`'s `<pluginRepository>` declaration to get access to the latest releases.

For instructions on how to use the latest version,
please see [Usage instructions](http://onejar-maven-plugin.googlecode.com/svn/mavensite/usage.html)

---
