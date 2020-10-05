# Roadmap

* [Documentation](#documentation)
* [Demonstrator](#demonstrator)
* [Converters](#converters)
* [Grid modeling](#grid-modeling)
* [Simulators](#simulators)
* [Data management](#data-management)
* [Viewing](#viewing)
* [High level services](#high-level-services)
* [Functional tests](#functional-tests)


## Documentation
- [Expected contributions](https://github.com/powsybl/powsybl.github.io/blob/master/pages/todo/expected-contributions.md) for next months
- Improve our functional documentation
- More and more user stories
- More and more tutorials

## Demonstator Grid Suite
We have started to create a web-based demonstrator packaged as [docker images](https://hub.docker.com/search?q=powsybl&type=image) to show the world what PowSyBl is: https://demo.powsybl.org/study-app/. It is available for everyone to experiment, with some great features:
- Import networks (we are working on TSOs part of the European network)
- Display networks on a map using CIM-CGMES Geographical Location (GL) profile
- Display substations (single line diagram) using CIM-CGMES Diagram Layout (DL) profile
- Apply simple modifications to the network topology (tap changes, setpoints changes, status of switches)
- Run power flows and display the calculation results
- Run security analyses and display violations on the network map and in a synthetic table

The demonstrator will be available at the end of 2020.

## Converters

### CIM-CGMES
&rarr; Importer
- End of basic importer of static information (operational limits to be completed): end of 2020.
- Generation and Load Shift Keys (GLSK) and Contingency list, Remedial Actions and additional Constraints (CRAC) management: 2021.
- Merging through the read-only merging view of the network: available as beta feature.
- Improvement of HVDC modelling: the ENTSO-E WG implementation guide for DC part is not available, will start just after.

Pending subjects: short circuit (waiting for an engine) and operation stereotypes, dynamics profile. 

&larr; Exporter
- Incremental export: export back to a CIM-CGMES file, a network that has been imported from a CIM-CGMES file. 
    - The export of the SV (only bus/branch) and the SSH profiles are available as beta features. The SV export of node/breaker topology will be available at the end of 2020.
    - TP and EQ exports: 2021.
- Full export: export to a CIM-CGMES file, a network imported from any supported format: 2021.

### XIIDM
&rarr; Importer
- Current IIDM version for the Java implementation: 1.3
- Current IIDM version for the C++ implementation: 1.2

&larr; Exporter
- Current IIDM version for the Java implementation: 1.3
- Current IIDM version for the C++ implementation: 1.2

### UCTE
&larr; Exporter
- Done !

### JSON
&rarr; Importer
- to be done

&larr; Exporter
- to be done

## Grid modeling
The backward compatibility management is robust. We have now a strong basis to change the core network model:
- HVDC modeling improvement: 2021.
- Operational limits modeling: work in progress, expected end of 2020.
- Extenstions for monitoring: work in progress.
- DC network modeling (maybe for 2021).
- Merging view when several networks are merged: we need to improve the boundary modelling in order to support hybrid merging.

## Simulators
- Integration of [Dynawo](https://dynawo.github.io): feature available on a IEEE14 network.
    - Support more and more dynawo models.
    - Support modifications on the network by the simulator.
    - Support of curves. 
- Improving our open load flow used for tests, experimental and collaboration purposes. For more information, please read the [README file](https://github.com/powsybl/powsybl-open-loadflow/blob/master/README.md).
    - A performant security analysis: work in progress. Support of remedial actions in discussion.
    - Increase support of transformer regulations: end of 2020, shunt regulations for 2021.
    - Sensitivity computations: 2021.
   
## Py-powsybl
A solution for Python users to call Powsybl, based on JPype. We have planned to build a prototype before the end of 2020.
    
## Data management
- A persistent implementation of the network core model (IIDM) based on [Apache Cassandra](http://cassandra.apache.org)
- A Persistent implementation of the extensions
- A permissions and quotas management in the AFS
- A log collector in the AFS

## Viewing
- Voltage level view: display clean, pretty and interactive drawings of voltage levels
- Substation view: display clean, pretty and interactive drawings of substations
- Improvement of the graphical charter of electro-technical components
- A geographical web view of the network: done

## Grid Study Environment
Archived.

## High level services
- Package and distribute computation services based on spring, as docker images

## Functional tests
We plan to validate a CIM-CGMES based workflow, focusing on the functional validation, the computation time and the memory consumption. The CIM-CGMES workflow consists in importing networks (also called Individual Grid Model), running a power flow, merging the networks (topologically at least), running a power flow on the merged network (also called Common Grid Model), applying modifications and exporting the updated network(s).
