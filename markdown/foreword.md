# Foreword

This document specifies the Finnish data exchange requirements of a route.
Examples of route include road, street, walkway railway and waterway.
This documents excludes domain specific content of rail- and waterways (such as km-posting). 
Also the content of this specification is limited to define:

- Geometry of a route
- Structural model of a route
- Existing terrain and rock bed
- Earthworks cuts and fills

Following data exchange use cases are covered by this specification:

- Earthworks and excavation bidding
- Design to construction
- Digital handover

LandXML based Inframodel format is widely used in Finland for the data excange use cases mentioned above.
However, it is based on aging LandXML which is setting some limititations for the design file content. 
For this reason, many different types of documents (ie. drawings, spreadsheets, pdf) are typically used together with Inframodel.
On the other hand, IFC 4.3 provides too diverse set of features to be properly machine processed, unless further rules are applied.
This document defines an minimal subset of IFC4.3 functionality which cover the defined data exchange use cases. 
Transition to IFC-based data exchange would allow machine readable feature rich communication.

## Data exchange use cases

In all three use cases the exchange of information is limited to covering superstructures, surface structures, structural layers and geometry lines of the route.

### Earthwork and excavation bidding

This use case describes the exchange of quantity information required for cost calculation. The specification includes the quantity information required in both design and construction phases, as well as a description of the required geometric representation.

### Design to construction

This use case describes the exchange of information between construction plan phase and the construction phase. The specification includes attributes, properties and geometric representation that allow surveying and installing the structure on the site.

### Digital handover
This use case describes the road as-built information exchange to the customer's systems. The specification includes the necessary attributes, properties and geometric presentation that enable the information required by the subscriber to be transferred to the customer's systems, such as registers or asset management systems. 

## Presentation format

Wide range of technologies and tools are available to specify the content of an IFC file (mvd, ids and bsdd, etc.).
This specification is using diagrams for good human readability, machine readable format will follow later.
The diagrams are drawn applying "crow's foot notation" as explained below.

### Defining entities

IFC Entity types explicitly included in all the use cases mentioned above are shown in the diagrams in this document. They are either used "as-is" (i.e. with no use case specific rules), or with additional rules specified in this document. 
Entity types used "as-is" appear as white boxes, or as relationship names in case of short-hand notation for IfcRel-entities.
Entity types with additional rules appear as green boxes, if defined in the current diagram, or as blue boxes, if referenced from another diagram.
Addinonal rules may apply only in a paricular usage, in which case the IFC entity name is appeded with a qualifier (e.g. IfcProductDefinitionShape-Alignment or IfcProductDefinitionShape-TIN). Otherwise, the rules on the Entity type apply globally.
These rules may 
 - change OPTIONAL attribute to MANDATORY
 - prohibit the use of OPTIONAL attribute (marked as $)
 - limit cardinality (usually allowing only one item in a list or a set)
 - applying value restrictions on attributes:
  -- Fixed value or list of allowable values (enumerated or range)  
  -- Enumeration datatype having some of the enumeration items excluded
  -- Entity datatypes excluded from allowable subtypes or select items
Attributes with no use case specific rules are omitted (and are to be used per standard IFC specification).

@startuml
entity ExampleEntity <<DefinedInThisDiagram>>
{
  *Attribute-1 : text
  *Attribute-2 : boolean = TRUE
  +Attribute-3 : text = red | amber | green
  +Attribute-4 = $
  Relationship-1
}

note top of ExampleEntity
    Fully defined entity. 
    Generic and unused attributes and relationships omitted.
end note

note left of ExampleEntity::Attribute-1
    Mandatory attribute with data type
end note
note left of ExampleEntity::Attribute-2
    Mandatory attribute with fixed value
end note
note left of ExampleEntity::Attribute-3
    Optional attribute with data type
end note
note left of ExampleEntity::Attribute-4
    Optional attribute with fixed value
end note
note left of ExampleEntity::Relationship-1
    Cardinality shown on the link\n to another entity type 
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
protocol "IfcPropertySet-Course" <<DefinedInThisDiagram>>
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
    bSF/IM properties for entity/type
    Contents defined in another diagram.
end note

protocol "IfcElementQuantity-Course" <<UndefinedEntity>>
{
    *Qto_CourseBaseQuantities
}

note top of "IfcElementQuantity-Course"
    Standard Ifc quantities for entity/type
    Contents defined in IFC documentation
end note

@enduml

{{diagram "Legend, property/property set definitions" propertylegend}}

## Taxonomy/classification system(s)

**TODO:Add some text, describe infrabim/rak two level hierarchy(surface/category+feature code)!**

