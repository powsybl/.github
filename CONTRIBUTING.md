# Contributing to PowSyBl

First off, thanks for taking the time to contribute!

The following is a set of guidelines for contributing to PowSyBl, which are hosted in the [PowSyBl Organization](https://github.com/powsybl) on GitHub. These are mostly guidelines, not rules. Use your best judgment, and feel free to propose changes to this document in a pull request.

#### Table Of Contents

[Code of Conduct](#code-of-conduct)

[License and developer Certificate of Origin](#license-and-developer-certificate-of-origin)

[How Can I Contribute?](#how-can-i-contribute)
  * [Reporting Bugs and Suggesting Enhancements](#reporting-bugs-and-suggesting-enhancements)
  * [Contributing Code](#contributing-code)
  * [Tools to contribute](#tools-to-contribute)
    * [Basic Maven Usage](#basic-maven-usage)
    * [Advanced Maven Usage](#advanced-maven-usage)
    * [IDEs](#ides)
      * [Intellij IDEA](#intellij-idea)
      * [Eclipse IDE](#eclipse-ide)

[Styleguides](#styleguides)
  * [Git Commit Messages](#git-commit-messages)
  * [Java Styleguide](#java-styleguide)

[Project Governance](#project-governance)
  * [Project Owner](#project-owner)
  * [Committers](#committers)
  * [Technical Steering Committee](#technical-steering-committee)
  * [Contributors](#contributors)

[Roadmap](#roadmap)
  * [Documentation](#documentation)
  * [Converters](#converters)
  * [Grid Modeling](#grid-modeling)
  * [Simulators](#simulators)
  * [Data management](#data-management)
  * [Vizualisation](#data-management)
  * [High level services](#high-level-services)

## Code of Conduct

This project and everyone participating in it is governed by the [PowSyBl Code of Conduct](CODE_OF_CONDUCT.md). By participating, you are expected to uphold this code. Please report unacceptable behavior to [powsybl.ddl@rte-france.com](mailto:powsybl.ddl@rte-france.com).

## License and developer Certificate of Origin

PowSyBl is an open source framework licensed under the [Mozilla Public License 2.0](https://www.mozilla.org/en-US/MPL/2.0/). By contributing to PowSyBl, you accept and agree to the terms and conditions for your present and future contributions submitted to PowSyBl.

The project also uses a mechansim known as a [Developer Certificate of Origin (DCO)](https://developercertificate.org/) to manage the process of ensuring that we are legally allowed to distribute all the code and assets for the project. A DCO is a legally binding statement that asserts that you are the creator of your contribution, and that you wish to allow PowSyBl to use your work.

Contributors sign-off that they adhere to these requirements by adding a ``Signed-off-by`` line to commit messages. All commits of all repositories of the PowSyBl community have to be signed-off like this :

````
This is my commit message.

Signed-off-by: Anne Tilloy <anne.tilloy@rte-france.com>
````
You can write it manually but Git even has a -s command line option to append this automatically to your commit message:
````
$ git commit -s -m 'This is my commit message'
````

Note that a check will be performed during the integration, indicating whether or not commits in a Pull Request do not contain a valid ````Signed-off-by```` line.

The ````Signed-off-by```` line at the end of the commit message can be written automatically. You just have to configure the ```` .gitconfig```` file with the following alias :
````
[alias]
    ci = commit -s
````
and instead of
````
$ git commit -m "This is my message"
````
you just have to write
````
$ git ci -m "This is my message"
````
Note that most of IDEs can be configured in order to add a ````Signed-off-by```` line at the end of the commit message (Intellij IDEA and Eclipse IDE for example, do not hesitate to ask us).

## How Can I Contribute?

### Reporting Bugs and Suggesting Enhancements

Bugs and enhancement suggestions are tracked as [GitHub issues](https://guides.github.com/features/issues/). Create an issue and provide the following information by filling in [the template](ISSUE_TEMPLATE.md).

Before creating bug reports or suggesting enhancement, please **perform a [cursory search](https://github.com/search?q=+is%3Aissue+user%3Apowsybl)** to see if the problem has already been reported. If it has **and the issue is still open**, add a comment to the existing issue instead of opening a new one..

You can also contact the team directly to talk about your ideas at [powsybl.ddl@rte-france.com](mailto:powsybl.ddl@rte-france.com) or chat on [Spectrum](https://spectrum.chat/powsybl).

> **Note:** If you find a **Closed** issue that seems like it is the same thing that you're experiencing, open a new issue and include a link to the original issue in the body of your new one.

### Contributing Code

Code Contribution is tracked as [GitHub Pull Requests](https://help.github.com/en/articles/about-pull-requests). Crafting a good pull request takes time and energy and we will help as much as we can, but be prepared to follow our iterative process. The iterative process has several goals:

- Maintain PowSyBl's quality
- Fix problems that are important to users
- Engage the community in working toward the best possible PowSyBl
- Enable a sustainable system for PowSyBl's maintainers to review contributions

Please follow these steps to have your contribution considered by the maintainers:

1. Follow all instructions in [the template](PULL_REQUEST_TEMPLATE.md)
2. Follow the [styleguides](#styleguides)
3. After you submit your pull request, verify that all [status checks](https://help.github.com/articles/about-status-checks/) are passing.
5. Request a GitHub review by one of the core developers (e.g. @mathbagu @geofjamg @MioRtia)
6. Follow their instructions or discuss about the requested changes. Please don't take criticism personally, it is normal to iterate on this step several times.
7. Repeat step 6 until the pull request is merged !

Continuous integration is setup to run on all branches automatically and will often report problems, so don't worry about getting everything perfect on the first try (SonarCloud Analysis is a notorious problem source). Until you add a reviewer, you can trigger as many builds as you want by amending your commits. The status checks enforce the following:

- All tests in the test suite pass.
- Checkstyle and SonarCloud report no violations.
- The code coverage is high enough (currently about 80%).

### Tools to contribute

Continuous integration is setup automatically on all contributions. However, it's faster to iterate locally to fix problems than waiting for the status checks to finish. There are many tools that can be used to do the verifications that are enforced by all status checks. The most simple and universal tool is maven, but IDE integrations can be used to get more immediate feedback. Most of the team uses IntelliJ IDEA, but others IDEs can be used, for exemple the Eclipse IDE.

#### Basic Maven Usage
The project uses maven to manage the build. The configuration of all the tools is fairly standard, so if you have already contributed to Java projects, you should feel right at home. You can safely run the full test suite, checkstyle, see code coverage information and the generated documentation with the following command:
```
$ mvn clean verify javadoc:aggregate -Pjacoco
```
You can then inspect global code coverage in `distribution-core/target/site/jacoco-aggregate/index.html` and the javadoc in `./target/site/apidocs/index.html`.

To run a full sonarqube analysis, download and launch a sonarcube server on your machine and add the `sonar:sonar` goal at the end of the maven command line. However, it is not practical to run it every time. A more efficient alternative is to run sonarlint in an IDE.

#### Advanced Maven Usage

Using maven, you can selectively run some tests and compile only some projects and avoid long package generation tasks. Here are a few examples that are useful, feel free to compose them to find a workflow that suits you. Please consult Maven's documentation for more uses of maven.
```
# Simple run of a single test class in one project. Use either a colon followed by the ArtifactId or the directory of the project.
$ mvn test -Dtest=MyTestClass -DfailIfNoTests=false -pl :artifactid -am
# Simple run of a all tests in the time-series project (use the correct package and artifactid)
$ mvn test -Dtest=com.powsybl.timeseries.** -DfailIfNoTests=false -pl :artifactid -am
# Complex selection of tests
$ mvn test -Dtest=Project1Class#method1,Project1Class#method3,com.powsybl.package2.** -DfailIfNoTests=false -pl :artifact1,directory2 -am
# Sometimes problems are masked by maven trimming stacktraces:
$ mvn test -DtrimStackTrace=false
# Running tests and compiles in parallel can speed things up:
$ mvn -T 2.0C test
```

#### IDEs
If your IDE is supported by sonarlint (both IntelliJ IDEA and the Eclipse IDE are supported), it is recommended to install it. It provides immediate feedback on most sonar issues. Running tests individually is often possible in IDEs without invoking maven. Please consult the documentation of your IDE for setting up the project through maven integration.

##### Intellij IDEA
Import the project using IDEA's maven integration in the GUI. Install SonarLint. Code !

##### Eclipse IDE
Eclipse IDE has two ways to import maven projects: the eclipse GUI component m2e that understands maven or the maven CLI component maven-eclipse-plugin.

Using maven-eclipse-plugin, it is possible to recreate all the necessary eclipse files from scratch. A practical way to use it and get deterministic results is to remove all existing eclipse files, delete all eclipse projects from the workspace, regenerate all the eclipse files and reimport everything into eclipse as "existing eclipse projects". If all your projects are checked out outside of the eclipse workspace on the file system, then deleting all the projects is even simpler because you can just delete the whole workspace. The whole cycle takes only a few seconds.
```
# Ensure that eclipse is not running
# delete the projects in the GUI, or "rm -rf" the eclipse workspace if you only have the powsybl projects
# delete all eclipse files from the file system
$ find . -name .project -o .classpath -o -name .settings -exec rm -rf '{}' \;
# regenerate eclipse files
$ mvn package eclipse:eclipse
# import as existing eclipse projects in the GUI (alternatively, use eclim's :ProjectImportDiscover directly from ViM)
```

After importing the projects with either method, install SonarLint for quicker feedback on potential sonar issues.

## Styleguides

### Git Commit Messages

As usual, please start the commit message with a short line describing the commit, then leave a blank line, then give more context and explanations. You can use GitHub's integrations, for exemple to link to existing issues. In general, pull requests with more than one commits will be squashed when merged in master.

### Java StyleGuide

- The project uses modern java, feel free to use any new APIs provided by the current java version (currently java 8).
- New API classes and methods should be documented with javadoc. Write higher level documentation for classes and lower level documentation for methods. For example, [ThreeWindingsTransformer.java](https://github.com/powsybl/powsybl-core/blob/master/iidm/iidm-api/src/main/java/com/powsybl/iidm/network/ThreeWindingsTransformer.java) has a schema and business documentation: https://javadoc.io/page/com.powsybl/powsybl-core/latest/com/powsybl/iidm/network/ThreeWindingsTransformer.html
- User-facing configuration options and general design decisions should be documented in the website maintained at https://github.com/powsybl/powsybl.github.io
- We use standard configurations of well known tools like checkstyle and sonarqube to enforce a coherent coding style, please consult those tools for justifications on these rules.

As a simple yet instructive example, consider IdentifierNetworkPredicate.java (available at https://github.com/powsybl/powsybl-core/blob/master/iidm/iidm-reducer/src/main/java/com/powsybl/iidm/reducer/IdentifierNetworkPredicate.java). It uses the modern java8 stream capabilities, it asserts that its inputs are well formed by using Objects::requireNonNull and has some javadoc (it's missing some global description on the class javadoc though).
```java
/**
 * Copyright (c) 2019, RTE (http://www.rte-france.com)
 * This Source Code Form is subject to the terms of the Mozilla Public
 * License, v. 2.0. If a copy of the MPL was not distributed with this
 * file, You can obtain one at http://mozilla.org/MPL/2.0/.
 */
package com.powsybl.iidm.reducer;

import com.powsybl.iidm.network.*;

import java.util.*;

/**
 * @author Mathieu Bague <mathieu.bague at rte-france.com>
 */
public class IdentifierNetworkPredicate implements NetworkPredicate {

    private final Set<String> ids = new HashSet<>();

    public static IdentifierNetworkPredicate of(String... ids) {
        Objects.requireNonNull(ids);
        return new IdentifierNetworkPredicate(Arrays.asList(ids));
    }

    public IdentifierNetworkPredicate(Collection<String> ids) {
        Objects.requireNonNull(ids);

        this.ids.addAll(ids);
    }

    /**
     * Keep this substation if the IDs list contains the ID of this substation or one of its voltage levels.
     * @param substation The substation to test
     * @return true if the IDs list contains the ID of this substation or one of its voltage levels, false otherwise
     */
    @Override
    public boolean test(Substation substation) {
        Objects.requireNonNull(substation);
        if (ids.contains(substation.getId())) {
            return true;
        }

        return substation.getVoltageLevelStream()
                .map(VoltageLevel::getId)
                .anyMatch(ids::contains);
    }

    /**
     * Keep this voltage level if the IDs list contains the ID of this voltage level.
     * @param voltageLevel The voltage level to test
     * @return true if the IDs list contains the ID of this voltage level, false otherwise
     */
    @Override
    public boolean test(VoltageLevel voltageLevel) {
        Objects.requireNonNull(voltageLevel);
        return ids.contains(voltageLevel.getId()) || ids.contains(voltageLevel.getSubstation().getId());
    }
}
```

## Project Governance

#### Project Owner

PowSyBl is part of the LF Energy Foundation, a project of The Linux Foundation that supports open source innovation projects within the energy and electricity sectors.

#### Committers

Committers are contributors who have made several valuable contributions to the project and are now relied upon to both write code directly to the repository and screen the contributions of others. In many cases they are programmers but it is also possible that they contribute in a different role. Typically, a committer will focus on a specific aspect of the project, and will bring a level of expertise and understanding that earns them the respect of the community and the project owner.

#### Technical Steering Committee

The Technical Steering Committee (TSC) is composed of voting members elected by the active Committers as described in the project’s Technical Charter.

PowSyBl TSC voting members are:
- Mathieu Bague (https://github.com/mathbagu)
- Jon Harper (https://github.com/jonenst)
- Geoffroy Jamgotchian (https://github.com/geofjamg)
- Sylvain Leclerc (https://github.com/sylvlecl)
- Sébastien Murgey (https://github.com/murgeyseb)
- Miora Ralambotiana (https://github.com/MioRtia)
- Anne Tilloy (https://github.com/annetill)
- Luis Zamarreno (https://github.com/zamarrenolm)

#### Contributors

Contributors include anyone in the technical community that contributes code, documentation, or other technical artifacts to the Project.

Anyone can become a contributor. There is no expectation of commitment to the project, no specific skill requirements and no selection process. To become a contributor, a community member simply has to perform one or more actions that are beneficial to the project.

## Roadmap

### Documentation
- Functional documentation;
- User stories;
- More and more tutorials.

### Converters

#### CGMES
&rarr; Importer
- End of basic importer;
- Diagram layout (DL) profile management;
- Geographical location (GL) profile management;
- Generation and Load Shit Keys (GLSK) and Contingency list, Remedial Actions and additional Constraints (CRAC) management;
- Merging.

&larr; Exporter
- Incremental export;
- Full export.

#### XIIDM
&rarr; Importer
- Extensions management in separate files;
- Incremental import of extensions;
- C++ implementation.

&larr; Exporter
- Extensions management in separate files;
- Incremental export of extensions;
- C++ implementation.


#### UCTE
&larr; Exporter
- to be done.

#### JSON
&rarr; Importer
- to be done.

### Grid Modeling
- Decreasing compatibility management;  
- HVDC modeling improvement;
- DC network modeling;
- Battery modeling.

### Simulators
- Integration of Dynawo;

### Data management
- Web services implementation in order to access to data;

### Vizualisation
- Voltage level view: necessity of having a clear and interactive image of voltage levels;
- Substation view: necessity of having a clear image of substations;
- Improvement of the graphical charter of electro-technical components.

### High level services
- Services packaging;
- Containers adding.
