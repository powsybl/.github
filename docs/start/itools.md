# Run PowSyBl commands with Itools

## Itools overview
<span style="color: red">TODO: add more information here</span>

## Installation of a basic PowSyBl distribution
Follow these steps to install a basic PowSyBl distribution and to start running iTools commands.

### Installation from binaries

Start by downloading the [latest version of a PowSyBl distribution](https://github.com/powsybl/powsybl-distribution).
Unzip the downloaded package. You can now add `<INSTALL_DIR>/powsybl-distribution-<LATEST_VERSION>/bin` to your environment variable `PATH`.

### Installation from sources

It is also possible to install the PowSyBl distribution from the sources.

First download the sources of the [`powsybl-distribution` repository](https://github.com/powsybl/powsybl-distribution):

```
$ git clone https://github.com/powsybl/powsybl-distribution.git
```

If you want to work on a stable version, go to [the latest release tag](https://github.com/powsybl/powsybl-distribution/releases/latest):

```
$ git checkout tags/<LATEST_RELEASE_TAG> -b latest-release
```

Generate a basic PowSyBl distribution by launching from the root repository:

```
$ cd <PROJECT_ROOT_PATH>
$ mvn clean package
```

The distribution is generated in `<PROJECT_ROOT_PATH>/target`. You can then add `<PROJECT_ROOT_PATH>/target/powsybl-distribution-<powsybldistribution.version>/bin` to your environment variable `PATH`.

## Test your installation

Launch the `itools --help` command in your terminal to check that everything went smoothly.

```
$> itools --help
usage: itools [OPTIONS] COMMAND [ARGS]

Available options are:
    --config-name <CONFIG_NAME>   Override configuration file name

Available commands are:

Computation:
    compare-security-analysis-results        Compare security analysis results
    loadflow                                 Run loadflow
    loadflow-validation                      Validate load-flow results of a network
    security-analysis                        Run security analysis

Data conversion:
    convert-network                          convert a network from one format to another

Misc:
    plugins-info                             List the available plugins

Script:
    run-script                               run script (only groovy is supported)

```

## Set a default configuration

You can set a default configuration by copying the provided configuration file in the `.itools` repository
in your `HOME` (note that you will need to create this repository if it does not exist):

```
$ mkdir <HOME>/.itools
$ cp <INSTALL_DIR>/resources/config/config.yml <HOME>/.itools/config.yml
```

This step is not mandatory **if you already have a custom configuration file and the necessary configuration modules are filled**.
For more information on configuration, go to the [related documentation](https://powsybl.readthedocs.io/projects/powsybl-core/en/stable/user/configuration/index.html).

## Examples

<span style="color: red">TODO: add examples of Itools use cases here</span>
