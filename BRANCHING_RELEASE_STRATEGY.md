# Branching and Release strategy

The following page exposes our branching and release strategy.

## Protected branches

Some branches are protected in our repositories.

Points below detail the policy that determines in our repositories which branches are protected.

### Main branch

The default branch is named `main` and is protected. Commits can be merged only via pull requests passing different checks:
- Compiling through Ubuntu OS, MacOS and Windows OS without failing
- Having a testing coverage greater than 90% for powsybl-open-loadflow and powsybl-diagram, 80% for the other repositories
- Succeeding in Sonarcloud checks without blocking failures (rules available [here](https://sonarcloud.io/organizations/powsybl-ci-github/rules)
- At least one reviewer, different from the pull request's author, must have approved the pull request
- Each commits must be signed correctly
- WIP status must be cleared

### Release branches

Release branches, which pattern is  `release-v*..*`, are created from the corresponding tag `v*.*` each time a corrective release is needed.
Only [maintainers](MAINTAINERS.md) can create or force-push into these branches.
Other members must create a pull request to do push into these branches and pass the same checks as the `main` branch.
These branches are always up to the most recent patch of the release.

### Integration branches

There are two different types of integration branches:
- Branches that are created to support a specific major feature or to adapt to a major breaking change present in a SNAPSHOT release of another PowSyBl repository; their pattern is `integration/<other_repository_name>-<SNAPSHOT_release>` or `integration/<major_feature_name>`
- Branches preparing a new XIIDM version, which means updating of several files that can be awkward to review. Their pattern can be `evolution_xiidm/<xiidm_version>` or `xiidm_version_<xiidm_version>`

Only [maintainers](MAINTAINERS.md) can create or force-push into these branches.
Other members must create a pull request to do push into these branches and pass the same checks as the `main` branch.

## Release cycle

A new release train of the framework occurs roughly every two months.

In case of structural issues, corrective releases can also be published for some repositories.
These corrective releases are motivated by users' demand so don't hesitate to [contact us](https://www.powsybl.org/pages/community/).

There is also always a possibility to release a module outside this agenda if necessary,
please [contact us](https://www.powsybl.org/pages/community/) for further discussion.

A few weeks before the release train, one or two release candidates of [powsybl-core](https://github.com/powsybl/powsybl-core) are
usually published and available for testing and migration of dependent repositories.
A release candidate should be up for at least one week before the release is published.
On average, it is up for two weeks.

Our release train consists in the release of:
- [powsybl-core and its sub-modules](https://github.com/powsybl/powsybl-core)
- [powsybl-open-loadflow](https://github.com/powsybl/powsybl-open-loadflow)
- [powsybl-diagram and its sub-modules](https://github.com/powsybl/powsybl-diagram)
- [powsybl-dynawo and its sub-modules](https://github.com/powsybl/powsybl-dynawo)
- [pypowsybl](https://github.com/powsybl/pypowsybl)
- [powsybl-entsoe and its sub-modules](https://github.com/powsybl/powsybl-entsoe)

For each released repository:
- a release note is written by one of the repository's committer
- in case of breaking changes, a migration guide is written by one or several of the repository's developers
- its latest version is updated on the [repositories' pages](https://www.powsybl.org/pages/documentation/developer/repositories/)
- its latest version is updated in [powsybl-dependencies](https://github.com/powsybl/powsybl-dependencies)

Once all the repositories have been released
- [powsybl-dependencies](https://github.com/powsybl/powsybl-dependencies) is released
- its latest version is updated in [powsybl-starter](https://github.com/powsybl/powsybl-starter)
- its latest version is updated in [powsybl-distribution](https://github.com/powsybl/powsybl-distribution)
- its latest version is updated in [powsybl-integration-test](https://github.com/powsybl/powsybl-integration-test)

Then, a communication on the LFE mailing list [powsybl-announce](https://lists.lfenergy.org/g/powsybl-announce/)
is done by one of PowSyBl's committers to announce the new release train.

If at some point, you are interested in the release of one of our other repositories,
don't hesitate to [contact us](https://www.powsybl.org/pages/community/) to discuss it. We ensure the release of our most
used components but this check list can evolve as users' demand does.

You can also participate in our [TSC meetings](https://lists.lfenergy.org/g/powsybl-tsc/) for your voice to be heard.

After a release train is published, a new date for the next release train is fixed.

## Releasing a repository: a guide

### Prerequisites

In order to release a PowSyBl repository, you must first:
- be a maintainer of the repository you wish to release
- have a Sonatype JIRA account, that can be created [here](https://issues.sonatype.org/secure/Signup!default.jspa)
- have rights to upload artefacts with the group ID `com.powsybl`; this must be achieved by having a current maintainer to create an issue on [Sonatype JIRA Dashboard](https://issues.sonatype.org/secure/Dashboard.jspa) asking to grant you these rights
- have a PGP/GPG key to sign your release; the complete documentation is available [here](https://central.sonatype.org/pages/working-with-pgp-signatures.html)
- configure the server in your maven settings (by default in your `~/.m2/settings.xml` file):
```xml
<servers>
         ...
         <server>
             <id>ossrh</id>
             <username>SONARTYPE_LOGIN</username>
             <password>SONARTYPE_PASSWORD</password>
         </server>
</servers>
- ```

### Generating a release tag

For the sake of the demonstration, the repository to be released will be called `powsybl-repo` below.

Start by being up-to-date to your `main` branch:
```shell
$ cd powsybl-repo
$ git checkout main
$ git pull
```

Create your temporary branch preparing to the release X.Y.0 and add commits bumping to your release version then your next snapshot version.
You can then push this branch.
```shell
$ git checkout -b tmp_prepare_release
$ mvn versions:set -DnewVersion=X.Y.0
$ git commit -s -m "Bump to vX.Y.0"
$ mvn versions:set -DnewVersion=X.Y+1.0-SNAPSHOT
$ git commit -s -m "Bump to vX.Y+1.0-SNAPSHOT"
$ git push -u origin tmp_prepare_release
```

Create a pull request from your temporary branch into the `main` branch and tag another maintainer as a reviewer so they can approve it.
Once it is approved, merge it with the option `Rebase and merge`.

You can then create a Release note and tag via the GitHub UI, using the hash of the corresponding commit (bumping to vX.Y.0). The tag must respect the pattern `vX.Y.0`
Please make sure that your release note is comprehensive to all new features and bug fixes of the release and that the migration guide has been updated if necessary.

### Publishing a release

**Before creating your local release, please make sure that your local repository state is clean.**

On your repository, checkout to the release tag. You can then package and deploy your release:
```shell
$ git checkout tags/vX.Y.0
$ mvn dependency:purge-local-repository
$ mvn clean package -Prelease
$ mvn deploy -Prelease
```

Your release will then be deployed in Sonatype. The complete documentation to release from your staging repository in Sonatype is detailed [here](https://central.sonatype.org/publish/release/#locate-and-examine-your-staging-repository).

Once all the steps are completed, your release is published in maven central and might need a few more minutes to be available.

If an issue occurs at any time during the releasing process, do not hesitate to check [Maven status](https://status.maven.org/) or to leave an issue on [Sonatype JIRA Dashboard](https://issues.sonatype.org/secure/Dashboard.jspa).

### Differences for a corrective release

Please note that there are some differences in the process when you're publishing a corrective release or a patch, which version respects the pattern `vX.Y.Z' with Z different from 0.

First checkout to the previous `vX.Y.*` release or if a patch has already been released, on the `release-vX.Y` branch instead of the `main` branch.
```shell
$ git checkout tags/vX.Y.0
$ git checkout -b release-vX.Y.0
```
or
```shell
$ git checkout release-vX.Y.0
```

You can then cherry-pick the commits of your patch:
```shell
$ git cherry-pick <commit1_hash>
$ git cherry-pick <commit2_hash>
...
```
And bump to the patched version:
```shell
$ mvn versions:set -DnewVersion=X.Y.Z
$ git commit -s -m "Bump to X.Y.Z"
$ git push -u origin release-vX.Y0 --force-with-lease
```

You can then create a Release note and tag via the GitHub UI, using directly the release branch. The tag must respect the pattern `vX.Y.Z`
Please make sure that your release note is comprehensive to all bug fixes of the corrective release.

You shall then follow the steps described above in [Publishing a relelease](#publishing-a-release).

