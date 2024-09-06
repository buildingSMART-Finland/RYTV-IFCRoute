# BsF IfcRoute documentation in markdown format 

In addition to markdown syntax, the document generation toolchain allows use of specific "moustache syntax commands" to extend the functionality of markdown.

Command syntax:

{{command [args]}}

Supported commands:

{{refto ID}} - insert a reference to a annex

{{refsec section-id}} - insert a reference to a (sub)section

{{include FILE}} - recursively include a file (or, if FILE=="annexes", all the annexes in letter order)

{{figure IMAGE}} - path to IMAGE, where IMAGE is a path relative to ./figures

{{diagramasfigure DIAGRAM}} path to plantuml DIAGRAM, where DIAGRAM is a path relative to ./diagrams

{{figst ID}} - apply default figure styles and set optional id (alphanum-_)+ for figure number referencing

{{figref ID}} - insert a reference to a figure

{{diagram DESCRIPTION ID}} - insert an embedded plantuml diagram as figure

**main.md file uses {{include}} command to include all main sections as separate markdown files.** 
