# Introduction #

As a developer in this project, you need certain things to make deployment easy.


# Details #

## mvn site:deploy ##

To automatically set correct mime-types on anything you `svn add`, put this in your `~/.subversion/config`:

```
enable-auto-props = yes
[auto-props]
*.txt = svn:mime-type=text/plain
*.html = svn:mime-type=text/html
*.css = svn:mime-type=text/css
*.png = svn:mime-type=image/png
*.jpg = svn:mime-type=image/jpeg
*.jpeg = svn:mime-type=image/jpeg
*.gif = svn:mime-type=image/gif
```


Make sure you have checked out the entire svn repo, and not just the trunk.

```
svn co https://onejar-maven-plugin.googlecode.com/svn onejar-maven-plugin-root
```

Build the site from trunk:

```
cd onejar-maven-plugin-root/trunk
mvn site site:deploy
```

That should deploy the site into `../mavensite/`. Check if there is anything you need to `svn add`:

```
cd ../
svn st
```

...and possibly add whatever is not added yet, for example:

```
svn add mavensite/*
```

...or to automatically add all non-added files:

```
svn st | grep '^\?' | sed -r 's/^\? +//' | xargs svn add
```

Go ahead and commit.

```
svn ci -m 'Generated mavensite.'
```

Mime-types should hopefully be correct. Check at http://onejar-maven-plugin.googlecode.com/svn/mavensite/index.html



## mvn deploy ##

As above, make sure you have the entire svn repo checked out, and not just the trunk.

Build a snapshot from the trunk:

```
cd trunk
mvn clean && mvn install source:jar javadoc:jar deploy
```

That should deploy the artifacts into `../mavenrepo-snapshot/`. Check if there is anything you need to `svn add`:

```
cd ../
svn st
```

...and possibly add whatever is not added yet, for example:

```
svn add mavenrepo-snapshot/*
```

Go ahead and commit.

```
svn ci -m 'Deployed 1.2.3-SNAPSHOT.'
```


## mvn release ##

If you have set up your working directory like above, `mvn release:prepare` and `mvn release:perform` should work too.

(TODO: we'll see how well it works when we release version 1.2.3!)