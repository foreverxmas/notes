# Groovy notes
## Run Groovy From Java
- Run java util by groovy
> groovy -e 'println InetAddress.localHost'`
- Create class `groovyc hello_world.groovy`
- Java compile info `javap hello_world`
- Add the Groovy JAR file into the class path as a dependency to run from Java
> java -cp $GROOVY_HOME/lib/groovy-2.5.6.jar:. hello_world
