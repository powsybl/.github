# PowSyBl  

```{toctree}
---
caption: Contents of this website
maxdepth: 2
hidden: true
---

releasetrain.md
start/gettingstarted.md

```

Powsybl is a framework for power system modeling, simulations and visualization. It supports a wide range of power system models and simulation methods. Its codebase is organized into multiple repositories to promote modularity, flexibility, and maintainability.

**Upgrades**: the 🚂 repositories are released every two to three months through a [release train](releasetrain.md).

## Overview

Below is an overview of the functional structure.

![overview](/_static/img/overview.svg)

The main repository is [powsybl-core](https://github.com/powsybl/powsybl-core).
This repository mainly allows to:
- Through importers, import network data from public or private formats that are converted to the internal IIDM format,
- Through exporters, export the IIDM networks to external public or private formats,
- Manipulate the IIDM network itself through modification features,
- Define interfaces to run simulations.

Thanks to the internal IIDM format from core it is then also possible to use other Powsybl repositories for more specific features, such as visualization (with the [powsybl-diagram](https://github.com/powsybl/powsybl-diagram) repository) or run simulations (with the [powsybl-open-loadflow](https://github.com/powsybl/powsybl-open-loadflow) or [powsybl-dynawo](https://github.com/powsybl/powsybl-dynawo) repositories).

## 🫀 Core features

The core repository allows to manipulate the network.

![overview](/_static/img/modifications.svg)

| Documentation                                                           | Github                                                   | Description                                    |
|-------------------------------------------------------------------------|----------------------------------------------------------|------------------------------------------------|
| [Documentation](https://powsybl.readthedocs.io/projects/powsybl-core)   | [powsybl-core](https://github.com/powsybl/powsybl-core)  | Grid model, exchange formats, simulation APIs  |

## 👩‍💻 Core simulations APIs

The core repository defines APIs for simulations that are then implemented within other repositories ([powsybl-open-loadflow](https://github.com/powsybl/powsybl-open-loadflow), [powsybl-dynawo](https://github.com/powsybl/powsybl-dynawo)):

![overview](/_static/img/simulations.svg)

| Documentation                                                                    | Github                                                                    | Description                                                                                                                                                                                                                                                                                     |
|----------------------------------------------------------------------------------|---------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Documentation](https://powsybl.readthedocs.io/projects/powsybl-open-loadflow)   | [powsybl-open-loadflow](https://github.com/powsybl/powsybl-open-loadflow) | Loadflow, security analysis and sensitivity analysis                                                                                                                                                                                                                                            |
| [Documentation](https://powsybl.readthedocs.io/projects/powsybl-dynawo)          | [powsybl-dynawo](https://github.com/powsybl/powsybl-dynawo)               | Integration module for [DynaFlow](https://dynawo.github.io/about/dynaflow) ([load flow simulations](inv:powsyblcore:std:doc#simulation/loadflow/index)) and [DynaWaltz](https://dynawo.github.io/about/dynawaltz) ([time domain simulations](inv:powsyblcore:std:doc#simulation/dynamic/index)) |
| [Documentation](https://powsybl.readthedocs.io/projects/powsybl-metrix)          | [powsybl-metrix](https://github.com/powsybl/powsybl-metrix)               | Multi-variant network simulation                                                                                                                                                                                                                                                                |
| [Documentation](https://powsybl.readthedocs.io/projects/powsybl-optimizer)       | [powsybl-optimizer](https://github.com/powsybl/powsybl-optimizer)         | Production-ready optimal powerflow optimizers                                                                                                                                                                                                                                                   |


## 👀 Visualization

A visualization repository is available, using the IIDM network modelisation of powsybl-core. It mainly generates SVG for single-line diagrams and network-area diagrams:
![overview](/_static/img/visualization.svg)

| Documentation                                                             | Github                                                         | Description                                  |
|---------------------------------------------------------------------------|----------------------------------------------------------------|----------------------------------------------|
| [Documentation](https://powsybl.readthedocs.io/projects/powsybl-diagram)  | [powsybl-diagram](https://github.com/powsybl/powsybl-diagram)  | network-area diagrams, single-line diagrams  |


## 🤝 European coordination

| Documentation                                                     | Github                                                                    | Description                                         |
|-------------------------------------------------------------------|---------------------------------------------------------------------------|-----------------------------------------------------|
| [Documentation](https://powsybl.readthedocs.io/projects/entsoe)   | [powsybl-entsoe](https://github.com/powsybl/powsybl-entsoe)     | Components specific to ENTSO-E-orientated processes |
| [Documentation](https://powsybl.readthedocs.io/projects/openrao)  | [powsybl-open-rao](https://github.com/powsybl/powsybl-open-rao) | Modular engine for remedial actions optimization    |

## 🐍 Python

| Documentation                                                             | Github                                                         | Description                                                  |
|---------------------------------------------------------------------------|----------------------------------------------------------------|--------------------------------------------------------------|
|[Documentation](https://powsybl.readthedocs.io/projects/pypowsybl)             | [pypowsybl](https://github.com/powsybl/pypowsybl)                         | The PowSyBl Python binding                                   |
|[Documentation](https://powsybl.readthedocs.io/projects/pypowsybl-jupyter)     | [pypowsybl-jupyter](https://github.com/powsybl/pypowsybl-jupyter)         | (Visualization) Integration of diagrams in Jupyter notebooks |

## 🧐 Advanced features

| Documentation                                                         | Github                                                 | Description                                                  |
|-----------------------------------------------------------------------|--------------------------------------------------------|--------------------------------------------------------------|
| [Documentation](https://powsybl.readthedocs.io/projects/powsybl-afs)  | [powsybl-afs](https://github.com/powsybl/powsybl-afs)  | Application File System to organize and store business data  |
| [Documentation](https://powsybl.readthedocs.io/projects/powsybl-hpc)  | [powsybl-hpc](https://github.com/powsybl/powsybl-hpc)  | High Performance Computing modules                           |

## Tutorials and demo

| Documentation                                                              | Github                                                                | Description                                               |
|----------------------------------------------------------------------------|-----------------------------------------------------------------------|-----------------------------------------------------------|
| [Documentation](https://powsybl.readthedocs.io/projects/powsybl-tutorials) | [powsybl-tutorials](https://github.com/powsybl/powsybl-tutorials)     | Java based project for Powsybl getting started purpose    |
|                                                                            | [pypowsybl-notebooks](https://github.com/powsybl/pypowsybl-notebooks) | Python based project for Powsybl getting started purpose  |



