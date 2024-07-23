# Contributing to PowSyBl

First off, thanks for taking the time to contribute! 

Before you start, we highly recommend that you read the following. IT will give you a set of guidelines for your contributions.


## Code of conduct
This project applies the [LF Energy Code of Conduct](https://wiki.lfenergy.org/display/HOME/Code+of+Conduct). By participating, you are expected to uphold this code. Please report unacceptable behavior to the project's Technical Steering Committee [powsybl-tsc@lists.lfenergy.org](mailto:powsybl-tsc@lists.lfenergy.org).


## English convention
The convention for all PowSyBl documents, is to use American English. A list of spelling differences between British and American English can be found [here](https://www.britishcouncilfoundation.id/en/english/articles/british-and-american-english).

## License
PowSyBl is an open source framework licensed under the [Mozilla Public License 2.0](https://www.mozilla.org/en-US/MPL/2.0/). By contributing to PowSyBl, you accept and agree to the terms and conditions for your present and future contributions submitted to PowSyBl.


## Reporting Bugs
If you encounter a problem with PowSyBl, the first places to ask for help are the `#issues` [Slack channel](https://app.slack.com/client/TG8ALA0TB/C02CG8Q0TS6) or the [user mailing list](https://lists.lfenergy.org/g/powsybl).

If, after having asked for help, you suspect that you have found a bug in PowSyBl, you should report it by opening an issue in the appropriate [GitHub repository](https://github.com/powsybl). Before creating a bug report, please **perform a [cursory search](https://github.com/search?q=+is%3Aissue+user%3Apowsybl)** to see if the problem has already been reported. It is preferable to add a comment to an existing issue rather than opening a new one. This avoids duplication of effort and makes it easier to triage issues.

If there is no already existing issue for your problem, feel free to create a new issue. Please provide as many details as you can on your problem filling the issue template, and don't forget to indicate which version of PowSyBl you are running and on which environment.


## Suggesting Enhancements
If you are interested in a new feature to add in the PowSyBl framework, the first place to discuss it are the `#powsybl`[Slack channel](https://app.slack.com/client/TG8ALA0TB/CGAAPNWTY) or the [developers mailing list](https://lists.lfenergy.org/g/powsybl).

You can also track your proposal by filling an issue in the appropriate [GitHub repository](https://github.com/powsybl). Before creating a feature request, please **perform a [cursory search](https://github.com/search?q=+is%3Aissue+user%3Apowsybl)** to see if someone else has already asked for it. It is preferable to add a comment to an existing issue rather than opening a new one. This avoids duplication of effort and makes it easier to triage issues.

Please provide as much detail as you can about your use cases in the issue template to help the development team meet your needs.


## Contributing to the code or the documentation
Before contributing to the project, please be sure to have read and understood the [code of conduct](https://www.lfenergy.org/about/code-of-conduct/) and the [license](#license) paragraph. 

Please also make sure that you fully understand the [DCO mechanism](#dco) and the [contributing process](#contributingprocess) described below.

### DCO

The project uses a mechanism known as a [Developer Certificate of Origin (DCO)](https://developercertificate.org/) to manage the process of ensuring that we are legally allowed to distribute all the code and assets for the project. A DCO is a legally binding statement that asserts that you are the author of your contribution, and that you wish to allow PowSyBl to use your work.

Contributors sign off on these requirements by adding a `Signed-off-by` line to commit messages. All commits from all repositories of the PowSyBl community have to be signed-off in this way:

```
This is my commit message.

Signed-off-by: John Doe <john.doe@server.com>
```

You can write it manually, but Git even has a -s command line option to automatically append it to your commit message:

```
$ git commit -s -m 'This is my commit message'
```

Please make sure to configure your .gitconfig file beforehand with your name and email address:

[user]
	name = John Doe
	email = john.doe@server.com 

Most IDEs can also be configured in order to automatically add a `Signed-off-by` line at the end of the commit message.


Note that, during continuous integration, a check is performed to see if all commits in a pull request contain a valid `Signed-off-by' line.

### Contributing process


Before you start coding, you have to agree with the [maintainers](MAINTAINERS.md) of the repository about the technical solution you will implement, to make sure it will be aligned with the project guidelines.
If you are not part of the development team, please join our [Slack](https://join.slack.com/t/powsybl/shared_invite/zt-rzvbuzjk-nxi0boim1RKPS5PjieI0rA) and ask us on the `#first-time-contributors` channel to grant you developer rights in the PowSyBl organization.
Once you do, you will receive an invitation to the PowSyBl organization. Accept it and you will be able to clone the repository, create your own branch and commit your changes! 

Once the development is done, you have to create a [pull request](https://help.github.com/en/articles/about-pull-requests):
- Fill all the relevant sections of the template to give context to the reviewer;
- Assign one or more reviewer, ideally the [maintainers](MAINTAINERS.md) of the repository;
- Add the `PR: waiting-for-review` label and all other relevant labels;
- Verify that all [status checks](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/about-status-checks) are OK, especially the Sonar analysis.

The reviewer will review your proposal and:
- Approves your changes: your contribution fits the project guidelines and will be merged;
- Comments: the reviewer suggests to make some improvements;
- Requests a change: your proposal cannot be merged as such. You need to fix it with respect to the different comments made by the reviewer.

### Continuous Integration
The Continuous Integration (CI) runs automatically when a pull request is opened, or a commit is pushed. The CI helps us maintain the quality of the project with automatic checks:
- Code style: the code style will be analyzed by `maven-checkstyle-plugin`. The [configuration](https://github.com/powsybl/powsybl-parent/blob/main/powsybl-build-tools/src/main/resources/powsybl-build-tools/checkstyle.xml) is shared between all our repositoriesk;
- Compilation: the code will be compiled using [Github Actions](https://github.com/features/actions) under Linux, Windows and MacOS, and the unit tests will be run;
- SonarCloud will report the code smells, duplications and the code coverage. You have to fix all the relevant code smells and add unit tests to reach the required barrier.






