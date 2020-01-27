# Roadmap

* [Documentation](#documentation)
* [Demonstrator](#demonstrator)
* [Converters](#converters)
* [Grid Modeling](#grid-modeling)
* [Simulators](#simulators)
* [Data management](#data-management)
* [Viewing](#viewing)
* [High level services](#high-level-services)
* [Functional tests](#functional-tests)


## Documentation
- Improve our functional documentation
- More and more user stories
- More and more tutorials
- A more logical plan for the website

## Demonstrator
We have started to create a web-based demonstrator packaged as [docker images](https://hub.docker.com/search?q=powsybl&type=image) to show the world what PowSyBl is. It will be available for everyone to experiment (the URL is coming soon !), with some great features:
- Import networks (we are working on TSOs part of the European network)
- Display networks on a map using CIM-CGMES Geographical Location (GL) profile
- Display substations
- Apply simple modifications to the network topology (tap changes, target changes, status of switches)
- Run power flows and display the calculation results
- Run security analyses and display violations on the network map and in a synthetic table

## Converters

### CIM-CGMES
&rarr; Importer
- End of basic importer (operational limits and HVDC conversions improvement and voltage remote regulations)
- Diagram layout (DL) profile management
- Geographical location (GL) profile management
- Generation and Load Shift Keys (GLSK) and Contingency list, Remedial Actions and additional Constraints (CRAC) management
- Merging through the merging view

&larr; Exporter
- Incremental export: Export back to a CIM-CGMES file, a network imported from a CIM-CGMES file.
- Full export: Export to a CIM-CGMES file, a network imported from any supported format.

### XIIDM
&rarr; Importer
- Extensions management in separate files.
- Versionning management.
- The C++ implementation is almost finished and will be in open source in Feburary 2020. Then, we have planned to work on versionning management.

&larr; Exporter
- Extensions management in separate files.
- Versionning management.
- C++ implementation is almost finished and will be in open source in Feburary 2020. Then, we have planned to work on versionning management.

### UCTE
&larr; Exporter
- Done !

### JSON
&rarr; Importer
- to be done

## Grid Modeling
The backward compatibility management has been done last year. We have now a strong basis to change the core network model:
- Three windings transformers modeling improvement: almost done.
- HVDC modeling improvement
- Operational limits modeling
- Linear and non linear shunt compensators
- Extenstions for automatic generation control, for monitoring
- DC network modeling (maybe for 2021)
- Merging view when several networks are merged.
- A listener that records events occurring on the network has been implemented. We have planned to functionally validate it.

## Simulators
- Integration of [Dynawo](https://dynawo.github.io/): work in progress.
- Improving our open load flow used for tests, experimental and collaboration purposes. For more information, please read the [README file](https://github.com/powsybl/powsybl-open-loadflow/blob/master/README.md);

## Data management
- A persistent implementation of the network core model (IIDM)
- A persistent implementation of the triple store

## Viewing
- Voltage level view: display clean, pretty and interactive drawings of voltage levels
- Substation view: display clean, pretty and interactive drawings of substations
- Improvement of the graphical charter of electro-technical components
- A geographical view of the network

## High level services
- Package and distribute computation services based on spring, as docker images

## Functional tests
We plan to validate a CIM-CGMES based workflow, focusing on the functional validation, the computation time and the memory management. The CIM-CGMES workflow consists in import networks (also called Individual Grid Model), run a power flow, merge the newtorks (topologicaly at least), run a power flow on the merged network (also called Common Grid Model), apply modifications and export the updated network(s).
