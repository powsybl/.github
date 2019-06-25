# Roadmap

  * [Documentation](#documentation)
  * [Demonstrator](#demonstrator)
  * [Converters](#converters)
  * [Grid Modeling](#grid-modeling)
  * [Simulators](#simulators)
  * [Data management](#data-management)
  * [Vizualisation](#data-management)
  * [High level services](#high-level-services)


## Documentation
- Functional documentation
- User stories
- More and more tutorials
- A new web-site

## Demonstrator
- Create web-based demos packaged as docker images to show the world what is PowSyBl

## Converters

### CIM-CGMES
&rarr; Importer
- End of basic importer
- Diagram layout (DL) profile management
- Geographical location (GL) profile management
- Generation and Load Shift Keys (GLSK) and Contingency list, Remedial Actions and additional Constraints (CRAC) management
- Merging

&larr; Exporter
- Incremental export : when the exported network comes originally from an input file in CIM-CGMES format, this export is used
- Full export : otherwise this functionality is used

### XIIDM
&rarr; Importer
- Extensions management in separate files
- Partial import of datasets
- C++ implementation

&larr; Exporter
- Extensions management in separate files
- Partial export of datasets
- C++ implementation


### UCTE
&larr; Exporter
- almost done, validation in progress

### JSON
&rarr; Importer
- to be done

## Grid Modeling
- Backward compatibility management
- Three windings transformers modeling improvement : validation in progress
- HVDC modeling improvement
- DC network modeling
- Battery modeling : done !
- Merging view when several networks are merged
- A listener that records events occuring on the network

## Simulators
- Integration of [Dynawo](https://dynawo.github.io/)
- Improving our simple load-flow used for experimental purposes

## Data management
- Web services implementation in order to manage data stored in the Application File System (AFS)

## Vizualisation
- Voltage level view: display clean, pretty and interactive drawings of voltage levels
- Substation view: display clean, pretty and interactive drawings of substations
- Improvement of the graphical charter of electro-technical components

## High level services
- Package and distribute computation services based on spring, as docker images
