# AMQ-9359-wwwjames ReadMe

This is WIP of my unoffical attempt at moving the current `main` ActiveMQ branch to Jetty 12.0.x per AMQ-9359[1] since
this has appered to stall per a pr[2] to resolve some high and critical CVEs with pre-12 versions which will not be
addressed since they are now EOL[3].

There have been sigificant changes made to Jetty 12.x, and while they have provided migration guides, they are 
incomplete in many places[4], thus requiring alot of back and forth with examples as suggested.

**NOTES:** 

- This ReadMe will be removed.
- Found a fork and AMQ-9359 branch from Matt Pavlovitch[5], who is the ActiveMQ PMC & Comitter. 

## Setup

Using manually installed maven 3.9.x since its required for ActiveMQ and Java 17 to compile.
Also using `jenv` to manage JDKs.

```
$ jenv shell 17
$ mvn -DskipTests clean install
```

**NOTE:** See ~/.profile for details, had to modify for jenv shell to work with new logins
due to open `jenv` issue.

### IntelliJ import/setup

May have to explicitly check the `allow-securitymanager`, `jdk9+`, and `wwwjames-AMQ-9359` profiles then run 
clean and install in the IntelliJ Maven tool window.

May also have to manually set the JDK to 17 and remove modules in the IDE.

See [Introduction to profiles](https://maven.apache.org/guides/introduction/introduction-to-profiles.html) for more
information.

## Status

Following the Jetty 11 to 12 migration guide, using Jetty 12.0.36 and ee8, altered the project's pom to minimze the 
number of moudles to work on in the temporary `wwwjames-AMQ-9359` maven profile enabled by default.
                      
Use the following for the initial build before importing into IntelliJ:

```
$ mvn clean install
```
        
**TODO:** Currently porting `activemq-http` module, finish porting and deprecating classes from `org.apache.activemq.transport.ws.jetty11`
to `org.apache.activemq.transport.ws.jetty12`.

## Documentation

- [Jetty 11 to 12 migration guide](https://jetty.org/docs/jetty/12/programming-guide/migration/11-to-12.html)
- [Jetty WebSocket Server and Serlvet migration guide](https://jetty.org/docs/jetty/12/programming-guide/server/websocket.html#jetty)
- [jetty-ee9-websocke-jetty-server module source](https://github.com/jetty/jetty.project/tree/jetty-12.1.x/jetty-ee9/jetty-ee9-websocket/jetty-ee9-websocket-jetty-server)

## Repositories

- [Jetty 12.0.x examples](https://github.com/jetty/jetty-examples/blob/12.0.x/pom.xml)
- [Matt Pavolvic's AMQ-9359 fork](https://github.com/mattrpav/activemq/tree/AMQ-9359)

## References

- [1](https://issues.apache.org/jira/browse/AMQ-9359)
- [2](https://github.com/apache/activemq/pull/1344)
- [3](https://webtide.com/end-of-life-changes-to-eclipse-jetty-and-cometd)
- [4](https://github.com/jetty/jetty.project/issues/11461)
- [5](https://github.com/mattrpav)
