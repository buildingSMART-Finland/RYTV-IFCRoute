# Foreword

This document specifies the Finnish data exchange requirements of an route.
Examples of route include road, street, walkway railway and waterway.
This documents excludes domain specific content of rail- and waterways (ie. km-posting). 
Also the content of this specification is limited to define:

- Geometry of an route
- Structural model of an route
- Existing terrain and rock bed
- Earthwork cuts and fills

Following data exchange scenarios are covered by this specification:

- Earthwork and excavation bidding
- Design to construction
- Digital handover

LandXML based Inframodel format is widely used in Finland for use data excange scenarios mentioned above.
However, it's based on aging LandXML which is setting some limititations for the design file content. 
For this reason, lot's of different types of documents (ie. drawings, spreadsheets, pdf) are typically used together with Inframodel.
On the other hand, IFC 4.3 provides too diverse set of features to be properly machine processed.
This document defines an minimal subset of IFC4.3 functionality which cover the defined data exchange scenarios. 
Transition to IFC-based data exchange would allow machine readable feature rich communication.

## Data exchange scenarios

In all three scenarios the exchange of information is limited to covering superstructures, surface structures, structural layers and geometry lines of the road.

### Earthwork and excavation bidding

This scenario describes the exchange of quantity information required for cost accounting. The specification includes the quantity information required in both design and construction phases, as well as a description of the required geometric presentation.

### Design to construction

This scenario describes the exchange of information between construction plan phase and the construction phase. The specification includes attributes and a geometric representation that allows surveying and installing the structure on the site.

### Digital handover
This scenario describes the road as-built information exchange to the customer's systems.. The specification includes the necessary attributes and geometric presentation that enables the information required by the subscriber to be transferred to the customer's systems, such as registers or asset management systems. 

## Presentation format

Wide range of technologies and tools are available to specify the content of an IFC file (ie. mvd, ids and bsdd).
This specification is using diagrams for good human readability, machine readable format will follow later.

### Defining entities

@startuml
entity ExampleEntity <<DefinedInThisDiagram>>
{
  *MandatoryAttribute : string
  *MandatoryFixedAttribute : bool = TRUE
  +OptionalAttribute : string
  +OptionalFixedAttribute : bool = TRUE
  ..External relations..
  *MandatoryInverseAttribute
  +OptionalInverseAttribute
}

note top of ExampleEntity
    Fully defined entity. 
    Generic and unused attributes are excluded.
end note

note left of ExampleEntity::MandatoryAttribute
    Mandatory attribute with data type
end note
note left of ExampleEntity::MandatoryFixedAttribute
    Mandatory attribute with fixed value
end note
note left of ExampleEntity::OptionalAttribute
    Optional attribute with data type
end note
note left of ExampleEntity::OptionalFixedAttribute
    Optional attribute with fixed value
end note
note left of ExampleEntity::MandatoryInverseAttribute
    Referenced from another entity
end note
note left of ExampleEntity::OptionalInverseAttribute
    Optional relation from another entity
end note

entity ExampleEntity2 <<DefinedInAnotherDiagram>>
{
}

note top of ExampleEntity2
    Entity defined in another diagram
end note

entity ExampleEntity3 <<UndefinedEntity>>
{

}

note top of ExampleEntity3 
    Entity as it is defined by IFC documentation
end note
@enduml

{{diagram "Legend, entity definitions" entitylegend}}

### Defining properties and property sets

@startuml
protocol "IfcPropertySet-PsetCourse" <<DefinedInThisDiagram>>
{
    *Pset_CourseCommon
    *Pset_BoundedCourseCommon
    *Pset_CourseApplicationConditions
}
note top of "IfcPropertySet-PsetCourse"
    Standard Ifc properties for entity/type.
    Usage defined here.
end note


protocol "IfcPropertySet-bSFCourse" <<DefinedInAnotherDiagram>>
{
}

note top of "IfcPropertySet-bSFCourse"
    bSF/IM properties  for entity/type
    Contents defined in another diagram.
end note

protocol "IfcQuantitySet-Course" <<UndefinedEntity>>
{
}

note top of "IfcQuantitySet-Course"
    Standard Ifc quantities for entity/type
    Contents defined in IFC documentation
end note

@enduml

{{diagram "Legend, property/property set definitions" propertylegend}}

## Taxonomy/classification system(s)

**TODO:Add some text, describe infrabim/rak two level hierarchy(surface/category+feature code)!**

