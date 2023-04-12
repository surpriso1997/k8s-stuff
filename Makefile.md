#### Makefile basics

Example:
```Makefile

build: package.json index.js main.cpp
    npm build

```
Here:
 - **build** is the name of command
 - **package.json inde.js and main.cpp** are - dependencies for that build
 - There should be the make sections for package.json and others for build



If a command starts with `-`, Make ignore its return status. Examplee:
```
clean:
    - rm -rf *
```

echo:

Its like print command in Make.
```
install:
   @echo You must be root to install
```

include:

include is use to read one or more makefiles in the current one. Used for overrides and for modularizing makefile

Justfile is better than Makefile