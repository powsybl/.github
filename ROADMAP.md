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

## Demonstrator

## Converters

### CGMES
&rarr; Importer
- End of basic importer
- Diagram layout (DL) profile management
- Geographical location (GL) profile management
- Generation and Load Shit Keys (GLSK) and Contingency list, Remedial Actions and additional Constraints (CRAC) management
- Merging

&larr; Exporter
- Incremental export
- Full export

### XIIDM
&rarr; Importer
- Extensions management in separate files
- Incremental import of extensions
- C++ implementation

&larr; Exporter
- Extensions management in separate files
- Incremental export of extensions
- C++ implementation


### UCTE
&larr; Exporter
- to be done

### JSON
&rarr; Importer
- to be done

## Grid Modeling
- Decreasing compatibility management
- Three windings transformers modeling improvement
- HVDC modeling improvement
- DC network modeling
- Battery modeling

## Simulators
- Integration of Dynawo

## Data management
- Web services implementation in order to access to data

## Vizualisation
- Voltage level view: display clean, pretty and interactive drawings of voltage levels
- Substation view: display clean, pretty and interactive drawings of substations
- Improvement of the graphical charter of electro-technical components

## High level services
- Package and distribute computation services based on spring, as docker images
