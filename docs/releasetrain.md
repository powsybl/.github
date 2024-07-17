# Release train 🚂

The release train consists of six repositories: 

- [powsybl-core](https://github.com/powsybl/powsybl-core)
- [powsybl-diagram](https://github.com/powsybl/powsybl-diagram)
- [powsybl-open-loadflow](https://github.com/powsybl/powsybl-open-loadflow)
- [powsybl-dynawo](https://github.com/powsybl/powsybl-dynawo)
- [powsybl-entsoe](https://github.com/powsybl/powsybl-entsoe)
- [powsysbl-open-rao](https://github.com/powsybl/powsybl-open-rao)

## Release Candidate

The powsybl-core repository is the repository on which every other repository of the release train depends. For this reason, a release candidate is released about two weeks before the release train starts so that maintainers of the five other repositories can run tests before the "real" version is out.

Release candidates versions follow this pattern: v[X].[Y].[Z]-RC[A] with X.Y.Z the version number to come and A the number of the release candidate (there may be several release candidates if bugs are found during testing).

## Release train course

After the testing period, the release train starts with powsybl-core followed by the five other repositories in an order that takes into account the internal dependencies.

Those dependencies are pictured in the diagram below.

![release-train](/_static/img/releaseTrainDependencies.svg)

## The powsybl-dependencies artifact

After the six repositories have been released, a new version of [powsybl-dependencies](https://github.com/powsybl/powsybl-dependencies) is created.
The powsybl-dependencies artifact helps projects with dependency management by gathering a set of compatible versions for the release train repositories.

## The powsybl-starter and powsybl-distribution artifacts

Following [powsybl-dependencies](https://github.com/powsybl/powsybl-dependencies), [powsybl-starter](https://github.com/powsybl/powsybl-starter) is released. This artifact is meant for beginners. By including this sole dependency in their pom.xml, new users get access to the main features of the library. They can start exploring very quickly without bothering about specific dependencies.

The [powsybl-distribution](https://github.com/powsybl/powsybl-distribution) artifact is then released. It allows users to download a [.zip file](https://github.com/powsybl/powsybl-distribution/releases) that allows them to use PowSyBl from the command line.
