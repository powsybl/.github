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

The PowSyBl code is executed on users own environment. The code has to do what it says it does and nothing more. For example, we do not want to introduce a bitcoin mining piece of software into a user server.

### Be safe with user data

PowSyBl is a library. No piece of software that allows data exfiltration from a user environement should be allowed.

## Threat model

### Making profit of known vulnerabilities / bad design principles

An ill-intentionned developer may try to use known vulnerabilities from external dependencies used by PowSyBl or take advantage of bad design principles.

### Making a malicious Pull Request

An ill-intentionned developer may try to push a pull request implementing a gateway to get hold of confidential data or even, as previously stated, implementing a bitcoin miner inside a user server.

### Attacking PowSyBl servers

An ill-intentionned developer may try to attack or access PowSyBl servers.

## Implemented measures

In order to meet the PowSyBl security requirements and avoid possible threats, the PowSyBl team has several tools and methods listed below.

### Hunting down known security flaws

#### Regular checks on dependency vulnerabilities

Checks on known dependency vulnerabilities are automatically performed through GitHub actions. We pay attention to keep our dependency versions up-to-date, especially when releasing a new PowSyBl version, to benefit from the latest security patches.

#### Up to date Java version

We use a recent Java version so that users can benefit from the latest security improvements.

#### Sonarcloud analysis

For new pull requests, we rely on Sonarcloud analysis that has [security-related rules](https://docs.sonarcloud.io/digging-deeper/security-related-rules/). The pull request cannot be merged if any vulnerability or hotspot rule is violated.

###  PowSyBl governance to control the merge of Pull Requests

All the developers allowed to merge new code are committers. They are experienced developers, known from the community. They have this right because they are competent enough. During the review process, they make sure that the pushed code is harmless to environments and data, without any malicious part, before giving their approval.
All pull requests must have at least one approval to be merged on the main branch. Some pull requests need two approvals when the impacts are significant. Thus, all the commits integrated on main branches are reviewed and approved by at least one committer. The members of the TSC are all committers. The list of TSC members is available [here](https://www.powsybl.org/pages/overview/governance). The other committers are:

- [Sophie Frasnedo](https://github.com/So-Fras)
- [Sébastien Murgey](https://github.com/orgs/powsybl/people/murgeyseb)

### No PowSyBl infrastructure

PowSyBl has no calculation or database servers for users. All calculations are run on a user environment and databases belong to users too. Thus, no attacks on PowSyBl servers could harm users.
