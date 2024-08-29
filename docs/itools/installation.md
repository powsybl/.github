# Installation of a basic PowSyBl distribution

Follow these simple steps to get familiar with the PowSyBl environment. Below are instructions to install a basic PowSyBl distribution and to start running iTools commands.

Please note that this PowSyBl distribution is functional on Windows and Linux but is not supported for MacOS yet.

## Installation from binaries

Start by downloading the [latest version of a PowSyBl distribution](https://github.com/powsybl/powsybl-distribution).
Unzip the downloaded package. You can now add `<INSTALL_DIR>/powsybl-distribution-<LATEST_VERSION>/bin` to your environment variable `PATH`.

You can now use iTools commands in your terminal:

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
**Optional**: You can set a default configuration by copying the provided configuration file in the `.itools` repository
in your `HOME` (note that you will need to create this repository if it does not exist):
```
$ mkdir <HOME>/.itools
$ cp <INSTALL_DIR>/resources/config/config.yml <HOME>/.itools/config.yml
```
This step is not mandatory **if you already have a custom configuration file and the necessary configuration modules are filled**.
For more information, go to the [documentation page of the configuration]().

## Installation from sources


