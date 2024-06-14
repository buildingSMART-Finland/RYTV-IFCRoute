---
title: "RYTV 22003_2"
subtitle: "IFC route data exchange requirements"
version: "{{draft-version}}"
author: "RYTV 22003_2 working group"
#abstract: "IFC route data exchange requirements"
#abstract-title: "Abstract"
#classoption:
#- abstract
geometry: "left=2cm,right=2cm,top=2cm,bottom=2cm"
xnos-warning-level: 1
xnos-number-by-section: true
header-left: '`\includegraphics{bsf.png}`{=latex}'
titlepage: true
logo: "logo.png"
logo-width: "11cm"
---

\clearpage

{{plantumlheader ../diagrams/plantumlheader.pu}}

# First chapter!

## lorem ipsum


{{begin_landscape}}


## render uml to figure, landscape mode ... test for long text sentences ... blaablablaa blaa blaa blablaa blaa blaa blablaa


![IFC-File entity hierarchy]({{diagramasfigure bsf-ifc-hierarkia.pu}} "IFC-File entity hierarchy"){{figst ifcfilehierarchy}}

{{end_landscape}}



## embedded uml example

@startuml
entity example_thing
{
    *test1:type1
    +test2:type2
}
@enduml

{{diagram "embedded uml example" embeddeduml}}