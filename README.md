csshi2
======

Very simple cluster ssh implementation for iTerm2 on MacOS.
At the moment the current release version of iTerm2 (2.0.0.x) is support as well as the development version (>=2.9).

# Installation

## Manually

Just copy the `csshi2` file to one of your bin-directories (like /usr/local/bin/csshi2) and give it the executable flag.
The files beneath `bash` may be used so support bash completion. Respectively the files beneath `zsh` for zsh completion.

## Using Homebrew

I created a homebrew tap for my projects.
```
brew tap untoldwind/extras
brew install csshi2
```
If you are using homebrews's bash-completion you may want to use
```
brew install csshi2 --with-bash-completion
```
resp. for zsh-completions
```
brew install csshi2 --with-zsh-completions
```

# Usage

## Basic

Just write a list of ssh connections to the commandline
```
csshi2 user1@host1 user2@host2 user3@host3 ...
```

## With cluster configuration

You may also create a `.cluster.yaml` file in your home directory with like this:
```
production:
  web:
    user: root
    hosts:
      - webserver1.prod.somewhere.com
      - webserver2.prod.somewhere.com
      - webserver3.prod.somewhere.com
  db:
    user: root
    hosts:
      - db1.prod.somewhere.com
      - db2.prod.somewhere.com
stage:
  web:
    user: root
    hosts:
      - webserver1.stage.somewhere.com
      - webserver2.stage.somewhere.com
  db:
    user: root
    hosts:
      - db1.stage.somewhere.com
somethingelse:
  user: root
  hosts:
    - some1.host.com
    - some2.host.com
```

I.e. the `.cluster.yaml` defined hierachical sets for ssh connections.
In this scenario you can use:

```
csshi2 production/web
```
to open ssh connections to the webservers in production or
```
csshi2 production
```
tp open ssh connections to all production servers (db and web).

# License

This software is licensed under the MIT license: http://opensource.org/licenses/MIT
