# AMQ-9359-wwwjames ReadMe

This is WIP of my unoffical attempt at moving the current `main` ActiveMQ branch to Jetty 12.0.x per AMQ-9359[1] since
this has appered to stall per a pr[2] to resolve some high and critical CVEs with pre-12 versions which will not be
addressed since they are now EOL[3].

There have been sigificant changes made to Jetty 12.x, and while they have provided migration guides, they are 
incomplete in many places[4], thus requiring alot of back and forth with examples as suggested.

** NOTE: ** This ReadMe will be removed.

## Setup

Using manually installed and aliased maven 3.9.x since its required for ActiveMQ and Java 17 to compile.
Maven 3.9.x is manually installed since its not included with apt.

Also using `jenv` to manage JDKs.

```
$ jenv shell 17
$ mvn-39 -DskipTests clean install
```

**NOTE:** See ~/.profile for details, had to modify for jenv shell to work with new logins
due to open `jenv` issue.

## Status

Following the Jetty 11 to 12 migration guide, using Jetty 12.0.36 and ee8, altered the project's pom to minimze the 
number of moudles to work on in the temporary `wwwjames-AMQ-9359` maven profile enabled by default.
                      
Use the following for the initial build before importing into IntelliJ:

```
$ mvn-39 clean install
```


## Documentation

- [Jetty 11 to 12 migration guide](https://jetty.org/docs/jetty/12/programming-guide/migration/11-to-12.html)
- [Jetty WebSocket Server and Serlvet migration guide](https://jetty.org/docs/jetty/12/programming-guide/server/websocket.html#jetty)

## Repositories

- [Jetty 12.0.x examples](https://github.com/jetty/jetty-examples/blob/12.0.x/pom.xml)

## References

- [1](https://issues.apache.org/jira/browse/AMQ-9359)
- [2](https://github.com/apache/activemq/pull/1344)
- [3](https://webtide.com/end-of-life-changes-to-eclipse-jetty-and-cometd)
- [4](https://github.com/jetty/jetty.project/issues/11461)
