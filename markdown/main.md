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

# First chapter!
## lorem ipsum
### render uml to figure

![IFC-File entity hierarchy]({{diagramasfigure bsf-ifc-hierarkia.pu}} "IFC-File entity hierarchy"){{figst entityhierarchy}}

### embedded uml example

@startuml
entity example_thing
{
    *test1:type1
    +test2:type2
}
@enduml

{{diagram "embedded uml example" embeddeduml}}