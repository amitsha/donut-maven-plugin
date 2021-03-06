![](http://magentys.github.io/donut/img/Donut-05.png)

[![Build Status](https://travis-ci.org/MagenTys/donut-maven-plugin.svg?branch=master)](https://travis-ci.org/MagenTys/donut-maven-plugin) [![Maven Central](https://maven-badges.herokuapp.com/maven-central/io.magentys/donut-maven-plugin/badge.svg)](https://maven-badges.herokuapp.com/maven-central/io.magentys/donut-maven-plugin)

## donut-maven-plugin

This is a maven plugin for donut. More about donut [here](http://github.com/MagenTys/donut).

## usage

in your `pom.xml` add the plugin with the following configuration: 

```
<plugin>
    <groupId>io.magentys</groupId>
    <artifactId>donut-maven-plugin</artifactId>
    <version>0.0.3</version>
    <executions>
        <execution>
            <id>execution</id>
            <phase>post-integration-test</phase>
            <goals>
                <goal>generate</goal>
            </goals>
            <configuration>
                <sourceDirectory>${project.build.directory}/cucumber-reports</sourceDirectory>
                <outputDirectory>${project.build.directory}/donut</outputDirectory>
                <timestamp>${maven.build.timestamp}</timestamp>
                <template>default</template>
            </configuration>
        </execution>
    </executions>
</plugin>
```

#### all configuration parameters

```
<sourceDirectory>
<outputDirectory>
<prefix>
<timestamp>
<template>
<countSkippedAsFailure>
<countPendingAsFailure>
<countUndefinedAsFailure>
<countMissingAsFailure>
<projectName>
<projectVersion>
```

default values:
* **sourceDirectory** : is mandatory is mandatory and it should be the directory that hold the generated JSON files to be visualised.
* **outputDirectory** : by default a `donut` folder will be generated
* **prefix** : the generated file is `donut-report.html`, however you can specify prefix i.e. `myproject-`
* **timestamp** : refers to the start time of your execution. If not specified by the user reports will use `now`
* **template** : donut supports 2 themes, `default` and `light`. `default` is the default value.
* **countSkippedAsFailure**, **countPendingAsFailure**, **countUndefinedAsFailure**, **countMissingAsFailure**: are boolean values, and by default they are set to `false`. 
* **projectName** : is a string value
* **projectVersion** : is a string value

#### report timestamp

As it may take a while to execute your tests, Donut expects that you pass the start timestamp, otherwise will default it to `now` at the time of the report execution. The format should be `yyyy-MM-dd-HHmm`

Example: 

```
<properties>
   <maven.build.timestamp.format>yyyy-MM-dd-HHmm</maven.build.timestamp.format>
</properties>
```

### License

This project is under an MIT license

Powered by: [MagenTys](http://magentys.io)
