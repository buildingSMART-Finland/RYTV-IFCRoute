# IFC 4.3 file

{{begin_landscape}}
## File structure

![IFC File entity hierarchy]({{diagramasfigure bsf-ifc-hierarkia.pu}} "IFC file entity hierarchy"){{figst ifcfilehierarchy}}

## File headers

![IFC file header]({{diagramasfigure bsf-IfcFile.pu}} "IFC-file header"){{figst ifcfileheader}}

The Ifc file header shall be populated according to the 
[**Implementation Guideline for IFC Header Section, Version 1.0.2**](https://standards.buildingsmart.org/documents/Implementation/ImplementationGuide_IFCHeaderData_Version_1.0.2.pdf)

Specific rules applying to *description field* in *file_description* (for this version of the data exchange cases coverd in this document):
 - Mandatory keyword "ViewDefinition" fixed value "Ifc4X3NotAssigned"
 - Optional keyword "ExchangeRequirement" used with value (one or many) of "bSF-D2C | bSF-QTO | bSF-handover"


# Entity definitions

## Project - IfcProject

![IfcProject]({{diagramasfigure bsf-IfcProject.pu}} "IfcProject"){{figst ifcproject}}

## Alignment - IfcAlignment

![IfcAlignment]({{diagramasfigure bsf-IfcAlignment.pu}} "IfcAlignment"){{figst ifcalignment}}

### Horizontal alignment - IfcAlignmentHorizontal
**TODO:Diagram missing!**

Allowed parameter horizontalsegment predefined types are "Line","Circulararc","Clothoid" and "Cubic" 

### Vertical Alignment - IfcVerticalAlignment
**TODO:Diagram missing!**

Allowed parameter verticalsegment predefined types are "CONSTANTGRADIENT","CIRCULARARC" and "PARABOLICARC"

### Cant - IfcAlignmentCant
**TODO:Diagram missing!**


## Site - IfcSite

![IfcSite]({{diagramasfigure bsf-IfcSite.pu}} "IfcSite"){{figst ifcsite}}

## Road - IfcRoad

![IfcRoad]({{diagramasfigure bsf-IfcRoad.pu}} "IfcRoad"){{figst ifcroad}}
**TODO:Partial diagram!**

## Structural model
   
### Pavement - IfcPavement

IfcPavement acts as an collection of courses and kerbs.

![IfcPavement]({{diagramasfigure bsf-IfcPavement.pu}} "IfcPavement"){{figst IfcPavement}}

### Courses - IfcCourse

Structural layers are defined by IfcCourse entities

![IfcCourse]({{diagramasfigure bsf-IfcCourse.pu}} "IfcCourse"){{figst ifccourse}}


#### Table:bSF_Pset_CourseCommon {#tbl:bSF_Pset_CourseCommon}
| Name | Property type | Data type | Description| Use |
|----------|----------|----------|----------|----------|
|LoadCapacity|IcfSingleValue|IfcPlanarForceMeasure|Load capacity|[ ] Bidding<br/>[x] Design to construction<br/>[x] Digital handover|
|Granulation|IfcSingleValue|IfcLabel|Granule size, ie. 16-20mm|[ ] Bidding<br/>[x] Design to construction<br/>[x] Digital handover|
|Color|IfcSingleValue|IfcColour|Material color|[ ] Bidding<br/>[x] Design to construction<br/>[x] Digital handover|

#### Table:bSF_Pset_SurfaceCourse {#tbl:bSF_Pset_SurfaceCourse}

| Name | Property type | Data type | Description| Use |
|----------|----------|----------|----------|----------|
|ElasticModulus|IcfSingleValue|IfcModulusOfElasticityMeasure|Elastic modulus|[ ] Bidding<br/>[x] Design to construction<br/>[x] Digital handover|
|MaterialStrength|IcfSingleValue|IcfLabel|Material strength|[ ] Bidding<br/>[x] Design to construction<br/>[x] Digital handover|
|MassType|IfcSingleValue|IfcLabel|Required|Mass type, ie. AB|[ ] Bidding<br/>[x] Design to construction<br/>[x] Digital handover|
|DeformationClass|IfcSingleValue|IfcLabel|Deformation class|[ ] Bidding<br/>[x] Design to construction<br/>[x] Digital handover|
|AbrasionResistance|IfcSingleValue|IfcLabel|Abrasion resistance|[ ] Bidding<br/>[x] Design to construction<br/>[x] Digital handover|
|MixRatio|IfcSingleValue|IfcPositiveRatioMeasure|Rock/Binder ratio|[ ] Bidding<br/>[x] Design to construction<br/>[x] Digital handover|

Combinational layers (ie. highest and lowest combination of surfaces) shall be presented using IfcVirtualElement as defined on diagram below.

![IfcVirtualElement]({{diagramasfigure bsf-IfcVirtualElement.pu}} "IfcVirtualElement"){{figst IfcVirtualElement}}

## Geomodel - IfcGeomodel

![IfcGeomodel]({{diagramasfigure bsf-IfcGeomodel.pu}} "IfcGeomodel"){{figst ifcgeomodel}}

### Existing terrain

![Existing terrain]({{diagramasfigure bsf-IfcGeotechnicalStratum-Terrain.pu}} "Existing terrain"){{figst ifcgeotechnicalstratum-terrain}}

### Soil cut

![Soil cut]({{diagramasfigure bsf-IfcEarthWorksCut-Soil.pu}} "Soil cut"){{figst bsf-ifcearthworkscut-soil}}

### Rock bed

![Rock bed]({{diagramasfigure bsf-IfcGeotechnicalStratum-Rockbed.pu}} "IfcGeomodel"){{figst ifcgeotechnicalstratum-rockbed}}

### Rock cut

**TODO:Split earthworkscut-rock diagram from ifcgeotechnicalstratum-rockbed!**

# Geometry representation

![IfcGeometricRepresentationContext]({{diagramasfigure bsf-IfcGeometricRepresentationContext.pu}} "IfcGeometricRepresentationContext"){{figst IfcGeometricRepresentationContext}}

![BrepwithBreaklines]({{diagramasfigure bsf-IfcProductDefinitionShape-BrepwithBreaklines.pu}} "BrepwithBreaklines"){{figst BrepwithBreaklines}}

![Footprint]({{diagramasfigure bsf-IfcProductDefinitionShape-Footprint.pu}} "Footprint"){{figst Footprint}}

![SolidwithBreaklines]({{diagramasfigure bsf-IfcProductDefinitionShape-SolidwithBreaklines.pu}} "SolidwithBreaklines"){{figst SolidwithBreaklines}}

![TIN]({{diagramasfigure bsf-IfcProductDefinitionShape-TIN.pu}} "TIN"){{figst TIN}}

![TINwithBreaklines]({{diagramasfigure bsf-IfcProductDefinitionShape-TINwithBreaklines.pu}} "TINwithBreaklines"){{figst TINwithBreaklines}}

{{end_landscape}}

