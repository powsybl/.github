# With Itools

## Itools overview
Itools provides a command line interface to run Powsybl commands through a Windows or Linux terminal. For more information please refer to this [itools documentation](https://powsybl.readthedocs.io/projects/powsybl-core/en/stable/user/itools/index.html).

## Getting a basic PowSyBl distribution
Follow these steps to install a basic PowSyBl distribution and to start running iTools commands.

### From the binaries

It is possible to directly use the executable tool from the `powsybl-distribution` repository. For this follow these steps:
- Download the zip folder from the [powSyBl-distribution latest version release](https://github.com/powsybl/powsybl-distribution/releases)
- Unzip the downloaded package
- You can then add `<INSTALL_DIR>/powsybl-distribution-<LATEST_VERSION>/bin` to your environment variable `PATH`.

### From the sources

It is possible to generate the tool from the sources. For this follow these steps:
- Download the [powsybl-distribution](https://github.com/powsybl/powsybl-distribution) sources
- You can checkout on the latest stable version thanks to the tag
- Generate the executable with the maven command

```
$ git clone https://github.com/powsybl/powsybl-distribution.git
$ cd powsybl-distribution
$ git checkout tags/<LATEST_RELEASE_TAG> -b latest-release
$ mvn clean package
```

The distribution is generated in the `target` folder.  
You can then add `<PROJECT_ROOT_PATH>/target/powsybl-distribution-<VERSION>/bin` to your environment variable `PATH`.

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

You can set a default configuration `config.yml` by copying the provided configuration file in your `<HOME>/.itools` repository (note that you will need to create this repository if it does not exist):

```
$ mkdir <HOME>/.itools
$ cp <INSTALL_DIR>/resources/config/config.yml <HOME>/.itools/config.yml
```

This step is not mandatory **if you already have a custom configuration file and the necessary configuration modules are filled**.

For more information on configuration, go to the [related documentation](https://powsybl.readthedocs.io/projects/powsybl-core/en/stable/user/configuration/index.html).

## Usages

See the documentation [here](https://powsybl.readthedocs.io/projects/powsybl-core/en/stable/user/itools/index.html) about he itools available commands.
