# BuildR - Build Tools

## Description
BuildR - Build Tools is collection of scripts and configurations that used in all BuildR Framework component.
These scripts are includes the following components:

 - .gitignore file
 - Scrutinizer CI Configuration
 - Travis-CI Configuration
 - Phing Build Script
 - 2 Separate PHPUnit Configuration

## Phing

This project and all of its component use **Phing** as primary Build System. Provided
phing configuration contains several pre-defined targets. These targets has many
dependencies, there is a list:

```
 phing/phing
 phpunit/phpunit
 phploc/phploc
 sebastian/phpcpd
 pdepend/pdepend
 apigen/apigen
 squizlabs/php_codesniffer
```

The dependencies easily installed via `composer` or you can install all package locally.
By default the phing build script assumes that all this tools is installed via composer,
when you install this tools locally you need to edit the build script.

```xml
...

<!-- <property name="toolsdir" value="" /> -->

<property name="toolsdir" value="${project.basedir}/vendor/bin/" />

...
```

When you set up this correctly you can able to run on of the following targets.

```
 Target Groups:
   - default
   - travis
   - build

 Single Targets:
   - artifact        Archive Build Artifacts
   - changelog       Generate changelogs (Short and long format)
   - clean           Cleanup build workspace
   - composer        Install or update dependencies (And install composer if needed)
   - documentation   Create documentation from the 'src' folder
   - lint            Lint PHP files using PHP linter
   - pdepend         Calculaty software metrics reports and graphs
   - phpcpd          Checks for duplicated code
   - phpcs           Validate coding standard
   - phploc          Messaure project size
   - phpunit         Run unit tests
   - prepare         Creates initialial folders for build outputs
```

## Separate PHPUnit configuration

This tools is contains 2 separate configuration file for PHPUnit. The only difference in the logging section.
`phpunit.xml` only contains text logging. And the `phpunit-ci.xml` contains multiple logging configuration.

#### phpunit-ci.xml Logging

This configuration generates three types of log:

 - CRAP report
 - CloverXML coverage report
 - HTML Coverage report

## Additional Configuration

#### Project name

By default this set of configurations use `PROJECT_NAME` as project name. These defined in three place.

- build.xml
- phpunit.xml
- phpunit-ci.xml

#### Project version

In `build.xml` you can change the project actual version. This is used only in the created artifacts file name.
Changing this is easy, just change this configuration value:

```xml
...

<property name="version" value="0.0.1" />

...
```

