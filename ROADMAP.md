# Roadmap

* [Documentation](#documentation)
* [Converters](#converters)
* [Grid modelling](#grid-modelling)
* [Simulators](#simulators)
* [Data management](#data-management)
* [Viewing](#viewing)
* [High level services](#high-level-services)
* [Tutorials](#tutorials)


## Documentation
- [Expected contributions](https://github.com/powsybl/powsybl.github.io/blob/master/pages/todo/expected-contributions.md) for next months
- Improve our functional documentation
- More and more user stories
- More and more tutorials

## Converters

### CIM-CGMES
&rarr; Importer
- End of basic importer of static information, only improvements remain: improve the support of transformers at boundary, support of conversion of remote reactive power control, refactoring of `TieLine` in order to access directly to the underlying `DanglingLines`.
- CIM-CGMES 3.0: test configurations for CGMES 3.0 support expected mid 2021.
- EQ profile only: work in progress [here](https://github.com/powsybl/powsybl-core/pull/1680).
- Improvement of HVDC modelling: the ENTSO-E WG implementation guide for DC part is available, but we are waiting for test or real cases to start. If you have some, please let us know or join the community to contribute.
- Merging through the read-only merging view of the network: a complete implementation will be available end of 2021.
- Generation and Load Shift Keys (GLSK) and Contingency list, Remedial Actions and additional Constraints (CRAC) management: end of 2021.

Pending subjects: short circuit (waiting for an engine) and operation stereotypes, dynamics profile. 

&larr; Exporter
- Incremental export: export back to a CIM-CGMES file, a network that has been imported from a CIM-CGMES file. 
    - The export of the SV (bus/branch and node/breaker) and the SSH profiles are available.
    - TP export: 2022.
- Full export: export to a CIM-CGMES file, a network imported from any supported format. The EQ profile export will be available mid 2021.

### XIIDM
&rarr; Importer
- Current IIDM version for the Java implementation: 1.5
- Current IIDM version for the C++ implementation: 1.5

&larr; Exporter
- Current IIDM version for the Java implementation: 1.5
- Current IIDM version for the C++ implementation: 1.5

### UCTE
&larr; Exporter
- Functional logs: work in progress in order to be compatible with a micro-services architecture. Expected end of 2021.

### JSON
&rarr; Importer
- to be done

&larr; Exporter
- to be done

## Grid modelling
The backward compatibility management is robust. We have now a strong basis to change the core network model:
- DC line modelling improvement and DC network modelling: 2022.
- Extensions for monitoring: work in progress.
- Merging view when several networks are merged: refactoring of `TieLine` expected end of 2021.

## Simulators

### Dynawo
The integration of [Dynawo](https://dynawo.github.io) is working: feature available on a IEEE14 network. We aim to work on:  
- Support of more dynamics models.
- Support of automatons and events: the difficulty is that they have no place in the static grid modelling and they can involved several equipments of the network.
- Support modifications on the network by the simulator.
- Groovy: improve the user experience.
- DynaFlow: support of security analysis implementation.

### OpenLoadFlow
Improving our open load flow used for tests, experimental and collaboration purposes. For more information, please read the [README file](https://github.com/powsybl/powsybl-open-loadflow/blob/master/README.md). We are still working on:
- A faster security analysis: work in progress and expected before the end of 2021.
- Support of DC security analysis based on the DC sensitivity analysis implementation: work in progress. 
- Voltage control: 
    - Transformer voltage control will be improved before the end of 2021
    - Shunt local control is already available in a [branch](https://github.com/powsybl/powsybl-open-loadflow/pull/191) 
    - Support of the static var compensator slope is already available as a beta-feature in a [branch](https://github.com/powsybl/powsybl-open-loadflow/pull/304)
- Remote reactive power control: work in progress in this [branch](https://github.com/powsybl/powsybl-open-loadflow/pull/266).
- Support of Ward Injection reduction: expected before the end of 2021.
- Sensitivity analysis: support for users. Do not hesitate to ask us for more features!
   
## Pypowsybl
The PyPowSyBl project gives access PowSyBl Java framework to Python developers. This Python integration relies on GraalVM to compile Java code to a native library.

## Balances adjustment 
Support of a constant power factor on loads during scaling, required for the European Merging Function: mid 2021.

## Enstoe
We have created a repository dedicated to components specific to ENTSO-E-orientated processes. We support here CIM-CGMES oriented control areas through `CgmesVoltageLevelsArea` object and `CgmesBoundariesArea` object useful for partial merging.

We are also working on:
- A CNE export of security analysis results ;
- A PEVF and CGMA importer: already available. Tests are performed through our involvement in interoperability tests. 
    
## Data management

### Network store
- A persistent implementation of the network grid model (IIDM) based on [Apache Cassandra](http://cassandra.apache.org)
- A Persistent implementation of the extensions

### AFS
- A permissions and quotas management in the AFS
- A log collector in the AFS

### Time series

## Viewing
- Voltage level view: display clean, pretty and interactive drawings of voltage levels
- Substation view: display clean, pretty and interactive drawings of substations
- Improvement of the graphical charter of electro-technical components
- A geographical web view of the network: done
- A zonal view of the network to ease operations

## High level services
- Package and distribute computation services based on spring, as docker images

## Tutorials
We plan to create a CIM-CGMES based tutorial that implements the European Merging Function. The CIM-CGMES workflow consists in importing networks (also called Individual Grid Model), running a power flow, merging the networks (topologically at least), running a power flow on the merged network (also called Common Grid Model), computing a balances adjustment based on PEVF and CGMA files containing the AC and DC positions, applying modifications and exporting the updated network(s). This tutorial will be used during interoperability tests.

## Grid Study Environment
Archived.

