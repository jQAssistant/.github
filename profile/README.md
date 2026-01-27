![](https://raw.githubusercontent.com/jQAssistant/.github/main/profile/jqa.jpg)

- [Overview](#overview)
- [The jQAssistant lifecycle](#the-jqassistant-lifecycle)
- [About the organization](#about-the-organization)
- [Quick Start](#quick-start)
- [Contributions](#contributions)
- [News](#news)
- [Further inforamation](#further-information)

# Overview

jQAssistant is an Open-Source-Tool that helps you to analyze and control the quality of your software systems. It is centered around three main use cases:
* Easily carry out [Software Analytics](https://en.wikipedia.org/wiki/Software_analytics) to gain insights into your software systems
* Continuously verify the correct implementation of targeted design and architecture using provided or user-defined rules to reach defined quality goals
* Automatically enable [Living Documentation](https://medium.com/geekculture/living-documentation-brief-history-and-evolution-of-the-concept-4492fafb5d7) by generating documentation from the code and validating documentation against the implementation to avoid the documentation-code-gap and confusion
 
Out-of-the-box, it brings first class support for **Java** based applications including a bunch of default scanners for most used formats like **XML**, **JSON** or **YAML** and default rules for **jUnit**.  With its plugin-based architecture, it can support a multitude of technologies, frameworks and architectural concepts. And if the out-of-the-box plug-ins are not enough, then there's a [collection of plugins](https://github.com/jqassistant-plugin) available, e.g. for **TypeScript**, **Dart**, **Spring**, **C4**, etc.
Or you can easily create your own plugin where needed.  

Typical technologies that are supported by jQAssistant as of now are shown in the visualization below. Note that the technology support may be provided by additional plug-ins from the GitHub organizations listed in section [About the organization](#about-the-organization).

![](https://raw.githubusercontent.com/jQAssistant/.github/main/profile/jqa_universe.jpg)

# The jQAssistant lifecycle

The main aspect for working with jQAssistant is to understand how it is working internally. While this is described in detail in several How-Tos and the official manual (as linked in [Further Information](#further-information)), the high-level overview is shown in below visualization. Mainly, the jQAssistant lifecycle is split into three phases:

* **Scan** - jQAssistant scans the configured resources such as source/byte code, XML configuration files, Maven build- and dependency-information or documentation artifacts into a Neo4j graph database which is delivered as part of the jQAssistant distribution.
* **Analyze** - jQAssistant analyses the structures in the database by executing so called concepts (enrich the graph with additional information) and constraints (validate structures in the graph). These are either defined project-specific by the user or are distributed via plugins. Reports are created containing the constraint violations (returned rows of constraints) and concept results (e.g. enriched/updated data or graphical representations).
* **Server** - jQAssistant starts the Neo4j graph database and makes its UI available at http://localhost:7474. This allows the user to develop concepts and constraints or carry out software analytics.

![](https://raw.githubusercontent.com/jQAssistant/.github/main/profile/jqa_process.jpg)

# About the organization

This GitHub organization is the main entry point for jQAssistant. 

However, we created a universe around it with the following two GitHub organizations to make your life easier:

1. [jQAssistant Plugin](https://github.com/jqassistant-plugin) provides a collection of useful extensions to jQAssistant such as scanners for additional formats, rule sets for frameworks and technologies, and means to report results as e.g. AsciiDoc or rendered PlantUML diagrams.
2. [jQAssistant Tutorials](https://github.com/jqassistant-tutorials) gives an overview of potential use cases including description on how to set them up in your environment. We recommend that every (new) user takes a look at it and be inspired.
3. [jQAssistant Tooling](https://github.com/jqassistant-tooling) offers integrations for jQAssistant into other tools such as AsciidoctorJ or SonarQube.
4. [jQAssistant Archive](https://github.com/jqassistant-archive) contains the history of plugins that were either deprecated and discontinued from ongoing development or plugins that were moved in the context of the jQAssistant 2.0 migration. For the latter case, the old development stat (<2.0.0) can be found in the archive, the newer state in the Plugin organization.

# Quick Start

## Command Line Distribution

- The latest command line distributions is available on Maven Central for [Java 11](https://central.sonatype.com/artifact/com.buschmais.jqassistant.cli/jqassistant-commandline-neo4jv4/versions) and [Java 17 or later](https://central.sonatype.com/artifact/com.buschmais.jqassistant.cli/jqassistant-commandline-neo4jv5/versions). Just click `Browse`, select the desired version and download the `*-distribution.zip`.
- Download and unpack the distribution, a directory `jqassistant-commandline-distribution-_version_` will be created.
- Run a scan using ```bin\jqassistant.cmd scan -f lib``` (Windows) or ```bin/jqassistant.sh scan -f lib``` (Linux)
- Start the embedded server using ```bin\jqassistant.cmd server``` (Windows) or ```bin/jqassistant.sh server``` (Linux) and open the URL ```https://localhost:7474``` in your browser
- Start exploring using the Neo4j browser!
- Read the [jQAssistant Tutorials](https://github.com/jqassistant-tutorials) and the [User Manual](https://jqassistant.github.io/jqassistant/) for further information

## Maven

- Add the jQAssistant Maven plugin to your ```pom.xml```:
```
<project>
    <build>
        <plugins>
            <plugin>
                <groupId>com.buschmais.jqassistant</groupId>
                <artifactId>jqassistant-maven-plugin</artifactId>
                <version>2.x.x</version>
                <executions>
                    <execution>
                        <goals>
                            <goal>scan</goal>
                            <goal>analyze</goal>
                        </goals>
                    </execution>
                </executions>
            </plugin>
        </plugins>
    </build>
</project>
```
- Run ```mvn verify```
- Start the embedded server using ```mvn jqassistant:server``` and open the URL ```https://localhost:7474``` in your browser 
- Start exploring using the Neo4j browser!
- Read the [jQAssistant Tutorials](https://github.com/jqassistant-tutorials) and the [User Manual](https://jqassistant.github.io/jqassistant/) for further information

# Contributions

We're happy about every contribution. To make this as efficient as possible, take a look at the following guidance:

* Issues should have a meaningful description, best with an example for reproduction. If possible to identify, put the issue into the repository of the part (e.g. core, a plugin, an example) where the issue occurred. This saves us a lot of time.
  * We're happy to accept pull requests that solve the issue. 
* Feature Requests should have a meaningful description, best with an example. If possible to identify, put the feature request into the repository of the part (e.g. core, a plugin, an example) where you expect the feature to be. This saves us a lot of time.
    * We're happy to accept pull requests that implement the request.

We also provide an Idea Hub for all your great ideas and to host discussions about jQAssistant at [Idea-Hub](https://github.com/jQAssistant/Idea-Hub).

For any other topics, feel free to [Contact Us](mailto:info@jqassistant.org)


# News

- **2026-01-26**
  - [jQAssistant C4 Plugin](https://github.com/jqassistant-plugin/jqassistant-c4-plugin) 2.2.0 released
- **2026-01-25**
  - [jQAssistant Codecharta Plugin](https://github.com/jqassistant-plugin/jqassistant-codecharta-plugin) 1.0.0 released
- **2026-01-20**
  - jQAssistant 2.9.0-RC1 released
    - [Overriding of rules](https://jqassistant.github.io/jqassistant/snapshot/#_overriding_rules)
    - [Key columns for concepts and constraints](https://jqassistant.github.io/jqassistant/snapshot/#_key_columns)
    - [Mark concepts as abstract](https://jqassistant.github.io/jqassistant/snapshot/#_rule_dependencies)
    - [Separated of Java annotations into separate dependency](https://jqassistant.github.io/jqassistant/snapshot/#_annotations)
    - Searchable HTML report in a reword look & feel
    - Create HTML report during `analyze` goal/task
    - Re-use already loaded configurations in Maven multi-module reactors (performance improvement in slow build environments)
    - Fixed compatibility with Java 11 and Maven 3.9.12
    - Fixed concept `java:VirtualInvokes` to correctly consider siblings in inheritance hierarchies

# Further Information

* [User Manual](https://jqassistant.github.io/jqassistant/) 
* [Introduction to jQAssistant in the JavaMagazin (german only)](https://www.buschmais.de/download/JavaMagazin_Artikelserie_jQAssistant.pdf)
* [jQAssistant Tutorials](https://github.com/jqassistant-tutorials)
* [jQAssistant Plugins](https://github.com/jqassistant-plugin)
* [Kontext E Plugins for jQAssistant](https://github.com/orgs/kontext-e/repositories)
