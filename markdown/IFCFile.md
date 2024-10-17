# IFC 4.3 file

{{begin_landscape}}
## File structure

The structure of IFC exchange file (i.e. STEP file) in all three use cases mentioned above shall follow the hierarchy shown here. 
The structrure defined here allows exchange of all the content in scope in one file, or partial ecxhanges (such as route alignemnt and terrain separately).
NOTE: Even though only IfcRoad is shown in the diagram (for brevity), the same rules apply to railways and waterways (IfcRailway and IfcMarineFacility.WATERWAY).

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

There shall be exactly one IfcProject entity in each IFC-file.

![IfcProject]({{diagramasfigure bsf-IfcProject.pu}} "IfcProject"){{figst ifcproject}}

## Alignment - IfcAlignment

Every IfcAlignment entity in the file shall be aggregated directly to IfcProject, and reference exactly one IfcRoad (or IfcRailway and IfcMarineFacility.WATERWAY).
All alignments shall have horizontal and vertical layout, with optional cant definition for railways. Matching 3D geometry representation as IfcGradientCurve shall have IfcCompositeCurve for horizontal geometry with IfcCurveSegments for vertical geometry (no separate 2D horizontal geometry).

![IfcAlignment]({{diagramasfigure bsf-IfcAlignment.pu}} "IfcAlignment"){{figst ifcalignment}}

### Horizontal alignment - IfcAlignmentHorizontal

Horizontal alignments with linear and circular arc segments, as well as clothoid and cubic transition segments are in scope at this stage.

![IfcAlignmentHorizontal]({{diagramasfigure bsf-IfcAlignmentHorizontal.pu}} "IfcAlignmentHorizontal"){{figst ifcalignmenthorizontal}}

### Vertical alignment - IfcAlignmentVertical

Vertical alignments with constant gradient as well circular and parabolic arc segments are in scope at this stage.

![IfcAlignmentVertical]({{diagramasfigure bsf-IfcAlignmentVertical.pu}} "IfcAlignmentVertical"){{figst ifcalignmentvertical}}

### Cant - IfcAlignmentCant

IfcAlignmentCant shall be used as defined in IFC specification (no additional rules at this stage).

## Site - IfcSite

![IfcSite]({{diagramasfigure bsf-IfcSite.pu}} "IfcSite"){{figst ifcsite}}

## Road - IfcRoad

![IfcRoad]({{diagramasfigure bsf-IfcRoad.pu}} "IfcRoad"){{figst ifcroad}}

## Structural model

Structural model of a route comprises subgrade and pavement (and their parts).

### Subgrade - IfcEarthworksFill

Subgrade (i.e. the structure below pavement) is efined by IfcEarthworksFill entities.

![Subgrade]({{diagramasfigure bsf-IfcEarthWorksFill.pu}} "Subgrade"){{figst bsf-ifcearthworksfill}}
   
### Pavement - IfcPavement

IfcPavement acts as an collection of courses and kerbs.

![IfcPavement]({{diagramasfigure bsf-IfcPavement.pu}} "IfcPavement"){{figst IfcPavement}}

### Courses - IfcCourse

Structural layers are defined by IfcCourse entities.

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

### Kerb - IfcKerb

![IfcKerb]({{diagramasfigure bsf-IfcKerb.pu}} "IfcKerb"){{figst ifckerb}}

### Combinational surfaces - IfcVirtualElement

Combinational surfaces (ie. highest and lowest combination of surfaces) shall be represented using IfcVirtualElement as defined on diagram below.

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

![Rock cut]({{diagramasfigure bsf-IfcEarthWorksCut-Rock.pu}} "Rock cut"){{figst bsf-ifcearthworkscut-rock}}

# Geometry representation

There shall be exactly one 3D geometric representation context (with subcontexts for different types of representation in 3D space); no 2D context should be used. 

![IfcGeometricRepresentationContext]({{diagramasfigure bsf-IfcGeometricRepresentationContext.pu}} "IfcGeometricRepresentationContext"){{figst IfcGeometricRepresentationContext}}

![SubContext-Curves]({{diagramasfigure bsf-IfcGeometricRepresentationSubContext-Curves.pu}} "SubContext-Curves"){{figst SubContext-Curves}}

![SubContext-TIN]({{diagramasfigure bsf-IfcGeometricRepresentationSubContext-TIN.pu}} "SubContext-TIN"){{figst SubContext-TIN}}

![SubContext-Volumes]({{diagramasfigure bsf-IfcGeometricRepresentationSubContext-Volumes.pu}} "SubContext-Volumes"){{figst SubContext-Columes}}

![AlignmentCurve]({{diagramasfigure bsf-IfcProductDefinitionShape-Alignment.pu}} "AlignmentCurve"){{figst AlignmentCurve}}

![BrepwithBreaklines]({{diagramasfigure bsf-IfcProductDefinitionShape-BrepwithBreaklines.pu}} "BrepwithBreaklines"){{figst BrepwithBreaklines}}

![Footprint]({{diagramasfigure bsf-IfcProductDefinitionShape-Footprint.pu}} "Footprint"){{figst Footprint}}

![SolidwithBreaklines]({{diagramasfigure bsf-IfcProductDefinitionShape-SolidwithBreaklines.pu}} "SolidwithBreaklines"){{figst SolidwithBreaklines}}

![TIN]({{diagramasfigure bsf-IfcProductDefinitionShape-TIN.pu}} "TIN"){{figst TIN}}

![TINwithBreaklines]({{diagramasfigure bsf-IfcProductDefinitionShape-TINwithBreaklines.pu}} "TINwithBreaklines"){{figst TINwithBreaklines}}

{{end_landscape}}

