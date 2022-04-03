# KiCad template
Template for quickly setting up a structured KiCad workspace, to organize global/local symbols and footprints, and datasheets.


## Git and KiCad
Use Git to
- Work sequentially (one person at a time) per file:
  - E.g. multiple schematic files,
  - One works on schematics, another on PCB.
- Fetch the newest versions of schematics, PCBs, libraries, footprints.
- Versioning of designs (branches, tags).
- Symbol, footprint and 3D library management.
- Datasheet management for custom parts.

Don't use Git to:
- Work in parallel on a single file.
- Resolve conflicts / merge changes from multiple designers into one file.
- Those things just won't work.

Read more [here](https://forum.kicad.info/t/pros-and-cons-of-using-a-vcs-git-etc-with-kicad/31331):


## Template file organization

```
kicad-template
|   PROJECT_README.md                     <- describes the specific project
│   TEMPLATE_README.md                    <- describes how to use this template
│   .gitignore
│   .gitmodules                           <- manages subcomponents for this template, e.g. Atomionics libraries
│
└───board
│   │   project.kicad_pcb
│   │   project.kicad_pro
│   │   project.kicad_sch
│   │
│   └───include
|       └───atomionics
|           └───digikey-kicad-library
|           └───SparkFun-KiCad-Libraries
|           └─── ....                   <- place your new symbols in a folder here, to save for future projects*
|           └───SynQor
|           └───Traco
|       └───user
|           └─── ....                   <- place your new symbols here, if only relevant for this project
│   
└───design-support
    │   supporting-documentation.pdf
    │   ....
```
\*) You must also commit and push to the submodule to save it to the Atomionics symbol repo.


## Managing paths
Paths are managed with variables. Variables are referenced at ${VARIABLE_NAME}.
- KIPRJMOD -> KiCad automatic. Directory containing the `.kicad_pro` file.
- ...
- KICAD_DATASHEET -> Location for custom datasheets.


## Library sources

### Built-in libraries
- Found in the KiCad install path, and 
- are overwritten on each version update (so no point making changes to them).

### User libraries
- By default saved somewhere on the local drive, maybe outside or maybe inside the project folder.
- If not saved in the project, this makes them hard to share in a systematic way.
- Can be included either "global" or "project-level".

### Atomionics managed libraries
- This is where we should be managing and saving relevant symbols.
- Made, modified and managed by Atomionics.
- Libraries derived from e.g. from Digi-Key, SparkFun, UltraLibrarian, etc.
- Custom libraries made for various designs.
