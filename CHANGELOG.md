# CHANGELOG

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
