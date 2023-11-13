# Security policy

## Warning to users

PowSyBl is a library dedicated to electrical grid modelling and simulation. As such, it includes data importers to feed the calculations. Please make sure your data comes from a safe source.

PowSyBl also provides a persistent IIDM implementation by offering the possibility to connect to an external PostgreSQL database. If you use this feature, please make sure your login and password are secure and safely stored.

## Reporting a vulnerability

Please report any **high-severity** security vulnerability, suspected or confirmed, to the Technical Steering Committee [powsybl-tsc@lists.lfenergy.org](mailto:powsybl-tsc@lists.lfenergy.org).

In your e-mail, please give basic information about who you are (name and company), detailed steps to reproduce the vulnerabilities (some Python or Java code, screenshots) and the effects.

For **moderate or low-severity** security vulnerabilities, you can use public Github issues. 

After reporting a potential vulnerability, you will be contacted by a PowSyBl team member within 7 calendar days. If the report proves to be a vulnerability, the library users will be informed and the vulnerability will be patched within 30 calendar days for high-severity vulnerability or in the next release train for moderate to low-severity security vulnerabilities.

## When to report a vulnerability

- When you think that PowSyBl has a potential security vulnerability.
- When you suspect a potential vulnerability but you are not sure if or how it would impact PowSyBl.
- When you know or suspect a vulnerability on another project that is used by PowSyBl.

## Supported versions

The available compatible releases are listed in [powsybl-dependencies](https://github.com/powsybl/powsybl-dependencies). In case of vulnerability fix, the main branches are first fixed. 
Only the most recent version will include the patch (through the usual release train or through a patch released outside the release train, depending on the severity).

## PowSyBl security requirements

### Be harmless on user environment

The PowSyBl code is executed on users environments. Using the PowSyBl code must not cause damage to the users environments.

### Be safe with user data
The PowSyBl code is executed on users data. Using the PowSyBl code must not compromise the data.

## Threat model

### Take advantage of known vulnerabilities / bugs / bad design principles

An attacker interacting with user systems powered by PowSyBl may try to use known vulnerabilities from external dependencies or take advantage of bugs or bad design principles.

### Making a malicious Pull Request

An attacker may try to push a malicious pull request, deliberatly introducing security vulnerabilities.

## Unapplicable threats

### Unapplicable: attacks on infrastructure

PowSyBl has no calculation or database servers. All calculations are run on a user environment and databases belong to users too.

## Implemented measures

In order to meet the PowSyBl security requirements and avoid possible threats, the PowSyBl team has several tools and methods listed below.

### Hunting down known security flaws

#### Regular checks on dependency vulnerabilities

Checks on known dependency vulnerabilities are automatically performed through GitHub actions. 

#### Recent Java version

We support recent Java versions so that users can benefit from the latest security improvements.

#### Controlled dependency update

We pay attention to keep our dependency versions up-to-date and also make sure the new versions are safe. This allows PowSyBl to benefit from the latest security patches, while ensuring a protection against supply-chain attacks.

#### Sonarcloud analysis

For new pull requests, we rely on Sonarcloud analysis that has [security-related rules](https://docs.sonarcloud.io/digging-deeper/security-related-rules/). The pull request cannot be merged if any vulnerability or hotspot rule is violated.

#### Open source and community

We encourage our users to report and investigate any vulnerability according to the recommendations of this document.

#### Developers best practices

We encourage contributors to use strong security practices (GPG keys, 2FA, safe and up-to-date operating systems, development tools and web browsers, etc.).

###  PowSyBl governance to control the merge of Pull Requests

All the developers allowed to merge new code are committers. They are experienced developers, known from the community. They have this right because they are competent enough. During the review process, they make sure that the pushed code is harmless to environments and data, without any malicious part, before giving their approval.
All pull requests must have at least one approval to be merged on the main branch. Some pull requests need two approvals when the impacts are significant. Thus, all the commits integrated on main branches are reviewed and approved by at least one committer. The members of the TSC are all committers. The list of TSC members is available [here](https://www.powsybl.org/pages/overview/governance). The other committers are:

- [Sophie Frasnedo](https://github.com/So-Fras)
- [Sébastien Murgey](https://github.com/orgs/powsybl/people/murgeyseb)


