# Security policy

## Reporting a vulnerability

Please report any **critical** or **important** security vulnerability, suspected or confirmed, **privately** to this subgroup of PowSyBl maintainers:
- [Anne Tilloy](anne.tilloy@rte-france.com)
- [Florian Dupuy](florian.dupuy@rte-france.com)
- [Olivier Perrin](olivier.perrin@rte-france.com)
- [Sophie Frasnedo](sophie.frasnedo@rte-france.com)
- [Jon Schuhmacher](jon.harper@rte-france.com)

In your e-mail, please give basic information about who you are (name and company), detailed steps to reproduce the vulnerabilities (some Python or Java code, screenshots) and the effects.

For **moderate** or **low-severity** security vulnerabilities, you can use public Github issues. 

In order to help you assess the severity of the potential vulnerability, you can use the [Apache severity rating](https://security.apache.org/blog/severityrating/).

If you are not sure whether the issue should be reported privately or publicly, please make a private report.

After reporting a potential vulnerability, you will be contacted by a PowSyBl team member within 7 calendar days. If the report proves to be a vulnerability, the library users will be informed and the vulnerability will be patched within 30 calendar days for critical or important vulnerabilities or in the next release train for moderate to low-severity vulnerabilities.
For security patch releases (outside the release train), the **repositories concerned by the vulnerability** and the **powsybl-dependencies repository** will be released. The powsybl-starter and powsybl-distribution repositories will be released upon request only.

## When to report a vulnerability

- When you think that PowSyBl has a potential security vulnerability.
- When you suspect a potential vulnerability but you are not sure if or how it would impact PowSyBl.
- When you know or suspect a vulnerability on a dependency used by PowSyBl.

## Supported versions

The available compatible releases are listed in [powsybl-dependencies](https://github.com/powsybl/powsybl-dependencies). In case of vulnerability fix, the main branches are first fixed. 
Only the most recent version will include the patch (through the usual release train or through a patch released outside the release train, depending on the severity).

## PowSyBl security requirements

### Be harmless on user environment

The PowSyBl code is executed on users environments. Using the PowSyBl code must not cause damage to the users environments.

### Be safe with user data

The PowSyBl code is executed on users data. Using the PowSyBl code must not compromise the users data.

## Threat model

### Take advantage of known vulnerabilities / bugs / bad design principles

An attacker interacting with user systems powered by PowSyBl may try to use known vulnerabilities from external dependencies or take advantage of bugs or bad design principles.

### Making a malicious Pull Request

An attacker may try to push a malicious pull request, deliberatly introducing security vulnerabilities in PowSyBl source code.

## Non-relevant threats

### Unapplicable: infrastructure

PowSyBl has no user-dedicated calculation or database servers. All calculations are run on a user environment and databases belong to users too.

### Out of scope: user environment

The user is responsible for the security of the surrounding system. When using pypowsybl or itools.sh, do not execute untrusted commands or scripts. When using powsybl in servers, apply security best practices for all associated servers.

PowSyBl includes data importers to feed the calculations. Even though we enforce strong security principles and use Sonar as a safeguard, making sure your data comes from a safe source is an additional protection.

Furthermore, if you use external Groovy scripts as data postprocessors or configuration DSLs, make sure they are not compromised.

## Implemented measures

In order to meet the PowSyBl security requirements and avoid possible threats, the PowSyBl team has several tools and methods listed below.

### Hunting down known security flaws

#### Regular checks on dependency vulnerabilities

Checks on known dependency vulnerabilities are automatically performed through GitHub actions. 

#### Recent Java, Python and Groovy versions

We support recent Java, Python and Groovy versions so that users can benefit from the latest security improvements.

#### Controlled dependency update

We pay attention to keep our dependency versions up-to-date and also make sure the new versions are safe. This allows PowSyBl to benefit from the latest security patches, while ensuring a protection against supply-chain attacks.

#### Sonarcloud analysis

For new pull requests, we rely on Sonarcloud analysis that has [security-related rules](https://docs.sonarcloud.io/digging-deeper/security-related-rules/). The pull request cannot be merged if any vulnerability or hotspot rule is violated.

#### Open source and community

We encourage our users to report and investigate any vulnerability according to the recommendations of this document.

#### Developers best practices

We encourage contributors to use strong security practices (GPG keys, safe and up-to-date operating systems, development tools and web browsers, etc.).

###  PowSyBl governance to control the merge of Pull Requests and the release process

All the developers allowed to merge new code are maintainers. They are experienced developers, known from the community. They have this right because they are competent enough. During the review process, they make sure that the pushed code is harmless to environments and data, without any malicious part, before giving their approval.
All pull requests must have at least one approval to be merged on the main branch. Some pull requests need two approvals when the impacts are significant. Thus, all the commits integrated on main branches are reviewed and approved by at least one maintainer. 

The same goes for releases: only a maintainer of a repository can release this repository.

The members of the TSC are all maintainers. The list of TSC members is available [here](https://www.powsybl.org/pages/overview/governance). The other maintainers are:

- [Sophie Frasnedo](https://github.com/So-Fras)
- [Sébastien Murgey](https://github.com/murgeyseb)
- [Olivier Perrin](https://github.com/olperr1)




