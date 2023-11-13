# Security policy

## Warning to users

PowSyBl is a library dedicated to electrical grid modelling and simulation. As such, it includes data importers to feed the calculations. Please make sure your data come from a safe source.
PowSyBl also provides a persistent IIDM implementation by offering the possibility to connect to an external PostgreSQL database. If you use this feature, please make sure your login and password are secure and safely stored.

## Supported versions

The available compatible releases are listed in [powsybl-dependencies](https://github.com/powsybl/powsybl-dependencies). In case of vulnerability fix, the main branches are first fixed. The fix will be available for the next release train. In case of vulnerability of high or critical severity, the most recent version is patched.

## Reporting a vulnerability

Please report any security vulnerability, suspected or confirmed, to the Technical Steering Committee [powsybl-tsc@lists.lfenergy.org](mailto:powsybl-tsc@lists.lfenergy.org). You can also report totally privately to the Chair of TSC [Anne Tilloy](anne.tilloy@rte-france.com) for high severity vulnerabilities. If the issue is confirmed, we will inform the library users and release a patch as soon as possible depending on the complexity.

In your e-mail, please give basic information about who you are (name and company), detailed steps to reproduce the vulnerabilities (some Python or Java code, screenshots) and the effects.

For moderate or low severity security vulnerabilities, you can use public Github issues. 

Github automatically reports vulnerabilities in opening pull requests. The fixes are usually available for the next version, but could lead to a patch depending on the severity.

## When to report a vulnerability

- When you think that PowSyBl has a potential security vulnerability.
- When you suspect a potential vulnerability but you are not sure if or how it would impact PowSyBl.
- When you know or suspect a vulnerability on another project that is used by PowSyBl.

## Security on new code

### Sonarcloud analysis

For new pull requests, we rely on Sonarcloud analysis that has [security-related rules](https://docs.sonarcloud.io/digging-deeper/security-related-rules/). The pull request cannot be merged if any vulnerability or hotspot rule is violated.

###  PowSyBl governance

All the developers allowed to merge new code are committers. They are experienced developers, known from the community. They have this right because they are competent enough. All pull requests must have at least one approval to be merged on the main branch. Some pull requests need two approvals when the impacts are significant. Thus, all the commits integrated on main branches are reviewed and approved by at least one committer. The members of the TSC are all committers. The list of TSC members is available [here](https://www.powsybl.org/pages/overview/governance). The other committers are:

- [Sophie Frasnedo](https://github.com/So-Fras)
- [Sébastien Murgey](https://github.com/orgs/powsybl/people/murgeyseb)
