# CHANGELOG

## Release v4.0.0

### [Improve Performance of Client-Server Communication](https://gitlab.switch.ch/hslu/edu/bachelor-computer-science/vsk/24fs01/g08/g08-documentation/-/issues/35)

- Replace the standard Java serialization framework (`Serializable`), with the more performant and
  efficient [kryo](https://github.com/EsotericSoftware/kryo) library
- Reduces an average log message round about 3/4 in size, when in a serialized form

Contributors: @jan.rueger1

### [String-Persistor Performance Improvements](https://gitlab.switch.ch/hslu/edu/bachelor-computer-science/vsk/24fs01/g08/g08-documentation/-/issues/34)

StringPersistor

- Replace the slower `java.io.*` with `java.nio.Files.*` apis for fs-operatiobs, since they are generally more
  performant and optimized for the underlying OS filesystem
- Remove costly Regexp construction for replacing linebreaks to spaces

Contributors: @eldar.omerovic1, @jan.rueger1

### [4.14 Vorbereitung für Abschlusswettbewerb](https://gitlab.switch.ch/hslu/edu/bachelor-computer-science/vsk/24fs01/g08/g08-documentation/-/issues/30)

LoggerServer

- If the environment variables LOG_FILE or LISTEN_PORT are set, use those values as config instead of the values in the
  configfile.

Contributors: @laurin.scholtysik1

### [4.13a LoggerViewer](https://gitlab.switch.ch/hslu/edu/bachelor-computer-science/vsk/24fs01/g08/g08-documentation/-/issues/29)

- Added a new module LoggerViewer
- LoggerViewer is a simple Java GUI that displays the logs from the LoggerServer
- The loggerServer communicates with the LoggerViewer via a socket connection and push notifications
- The LoggerViewer also displays the Status of the LoggerServer

Contributors: @enya.senn1

### [Implement log file format for competition](https://gitlab.switch.ch/hslu/edu/bachelor-computer-science/vsk/24fs01/g08/g08-documentation/-/issues/33)

LoggerServer

- Add log formatting strategy for competition

Contributors: @eldar.omerovic1

### [Simplify LoggerServer architecture & add integration tests](https://gitlab.switch.ch/hslu/edu/bachelor-computer-science/vsk/24fs01/g08/g08-documentation/-/issues/31)

LoggerServer

- Removed the consumer-producer setup which was previously decoupled by a priority queue, thus simplifying the overall
  architecture while maintaining the same functionality
- Set up Testcontainers and added multiple integration tests to check the behaviour of the logger-server under different
  circumstances

Contributors: @jan.rueger1

### [Introduce dedicated Logging Library for Logger Server](https://gitlab.switch.ch/hslu/edu/bachelor-computer-science/vsk/24fs01/g08/g08-documentation/-/issues/32)

LoggerServer

- Added & configured _logback_ as defautl logger via sfl4j
- Replaced all direct logs to `System.out` with their according sfl4j alternatives

Contributors: @jan.rueger1

## Release v3.0.0

### [3.10 Anbindung von StringPersistor mittels Adapter-Pattern](https://gitlab.switch.ch/hslu/edu/bachelor-computer-science/vsk/24fs01/g08/g08-documentation/-/issues/25)

LoggerServer

- Added adapter to handle the communication with the StringPersistor interface in the LoggerServer
- Added Tests for adapter
- Added Exception Handling in safeLogMessage method

Contributors: @enya.senn1

### [3.9 Paralleles und ortsunabhängiges Loggen auf LoggerServer](https://gitlab.switch.ch/hslu/edu/bachelor-computer-science/vsk/24fs01/g08/g08-documentation/-/issues/24)

LoggerServer

- Use dedicated virtual threads for accepting incoming socket connections and handling all messages sent across by the
  client during their lifetime
- Split the accepting and persisting of logs into a multiple publishers and a consumer (single thread). Between is a
  priority queue which is responsible for enforcing the correct chronolgical of how the logs are persisted.

Contributors: @jan.rueger1

### [3.8 Zuverlässige Behandlung von Verbindungsunterbrüchen](https://gitlab.switch.ch/hslu/edu/bachelor-computer-science/vsk/24fs01/g08/g08-documentation/-/issues/23)

LoggerComponent

- Cache logs if logger client cannot connect at startup or connection breaks
- Resend cached logs on startup or once connection is resumed

Demo App

- Send every type of loglevel upon cli user input (loop)

StringPersistor

- Strings to be saved now escape newline characters
- If get is called but nothing has been saved before, an empty list is returned

Contributors: @laurin.scholtysik1

### [3.11 Austauschbare Speicherformate](https://gitlab.switch.ch/hslu/edu/bachelor-computer-science/vsk/24fs01/g08/g08-documentation/-/issues/26)

- Add interface for log stratgies
- Implement CSV and default TEXT strategy

Contributors: @eldar.omerovic1

## Release v2.0.0

### [2.6 Auslieferbarkeit von LoggerServer als Image für einen Docker-Container](https://gitlab.switch.ch/hslu/edu/bachelor-computer-science/vsk/24fs01/g08/g08-documentation/-/issues/13)

- A dockerfile was added that packs the logger-server inside a dockerimage
- Plugin was added to deliver the jar as an uberjar
- A docker-compose file was also added that runs the dockerimage as a container.

Contributors: @enya.senn1

### [2.4 Logger-Schnittstelle: Austauschbarkeit](https://gitlab.switch.ch/hslu/edu/bachelor-computer-science/vsk/24fs01/g08/g08-documentation/-/issues/10)

- Logger component publishes the concrete `LoggerSetupBuilder` implementation as Java SPI provider
- DemoApp consumes the builder instance via Java SPI (as described above)

Contributors: @jan.rueger1

### [2.5 Logger-Schnittstelle: Log-Level](https://gitlab.switch.ch/hslu/edu/bachelor-computer-science/vsk/24fs01/g08/g08-documentation/-/issues/11)

- Logger component implements interfaces now
- Logger component sends loglevel to server
- Logger server receives loglevel from clients and writes them down

Contributors: @eldar.omerovic1

### [Add and use config file to logger component and server](https://gitlab.switch.ch/hslu/edu/bachelor-computer-science/vsk/24fs01/g08/g08-documentation/-/issues/14)

- LoggerServer can now be configured through the LoggerServer.properties file.

Contributors: @laurin.scholtysik1

### [Use StringPersistor to save log messages](https://gitlab.switch.ch/hslu/edu/bachelor-computer-science/vsk/24fs01/g08/g08-documentation/-/issues/12)

- LoggerServer now uses Stringpersistor instead of logging received messages to cli.

Contributors: @laurin.scholtysik1

### [String persistor does not create path if it does not exist](https://gitlab.switch.ch/hslu/edu/bachelor-computer-science/vsk/24fs01/g08/g08-documentation/-/issues/20)

- FileStringPersistor now creates the directory of the specified logfile if it does not exist yet.

Contributors: @laurin.scholtysik1

## Release v1.0.0

### [Fix socket connection closing after first message](https://gitlab.switch.ch/hslu/edu/bachelor-computer-science/vsk/24fs01/g08/g08-documentation/-/issues/9)

- Fix logger server only being able to handle one message per socket connection.

Contributors: @eldar.omerovic1

### [1.3 Erweiterte Informationen in Log-Messages hinzufügen](https://gitlab.switch.ch/hslu/edu/bachelor-computer-science/vsk/24fs01/g08/g08-documentation/-/issues/4)

- Add dataobject in order to additionaly send the log's source and timestamp from component to the server.

Contributors: @jan.rueger1

### [1.2 Speichern von Log-Messages](https://gitlab.switch.ch/hslu/edu/bachelor-computer-science/vsk/24fs01/g08/g08-documentation/-/issues/3)

- Add implementation according to the StringPersistor interface.
- Add unit tests.

Contributors: @laurin.scholtysik1

### [1.1 Grundkommunikation](https://gitlab.switch.ch/hslu/edu/bachelor-computer-science/vsk/24fs01/g08/g08-documentation/-/issues/1)

- Establish basic communication between logger component and server.
- Use this new communication in DemoApp.

Contributors: @enya.senn1, @eldar.omerovic1

---
