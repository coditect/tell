Tell
====

**Tell** is a set of shell scripts for managing server processes (such as Apache and MySQL) that have been installed via [MacPorts](http://www.macports.org/).  It provides a unified interface that is more consistant than invoking the daemons directly and more flexible than using Launchd.


## Installation

1. Place the main `tell` script in `/opt/usr/bin`.
2. Place the `tell.d` folder in `/opt/usr/etc`.
3. Add `tell` to your `PATH` by adding the following line to `~/.profile`: `export PATH=/opt/usr/bin:$PATH`

Make sure that both the main `tell` script as well as the contents of the `tell.d` folder are executable.


## Usage

Tell commands come in the form:
```
$ tell <service> <action>
```

For example, you can start MySQL by running:
```
$ tell mysql start
```

You can list the possible actions for each service by simply omitting the action parameter:
```
$ tell mysql
Available options are:
  start    Tell MySQL to start
  stop     Tell MySQL to stop
  restart  Tell MySQL to restart
  reload   Tell MySQL to reload its permissions
  status   Tell MySQL to report its status
```

You can also get a listing of available services by omitting both parameters:
```
$ tell
Available services are: apache, couch, mongo, mysql, nginx, phpfpm, postgres
```


## Gotchas

Some of the services (MySQL and PHP-FPM) rely on the active version of their respective ports being set with `port select`.  Even if you only have one version of MySQL or PHP installed, you must set the active version for `tell` to work correctly.  For example, to activate MySQL 5.5, run:
```
$ sudo port select mysql mysql55
```
