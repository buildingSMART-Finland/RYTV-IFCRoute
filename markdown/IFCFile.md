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
 - Optional keyword "ExchangeRequirement" used with value (one or many) of "bSF-QTO | bSF-D2C | bSF-DH"


# Entity definitions

## Project - IfcProject

There shall be exactly one IfcProject entity in each IFC-file.
Unit assignment is mandatory and shall define units for all measure values (attribute or property) in the file.

![IfcProject]({{diagramasfigure bsf-IfcProject.pu}} "IfcProject"){{figst ifcproject}}

## Alignment - IfcAlignment

Every IfcAlignment entity in the file shall be aggregated directly to IfcProject, and reference exactly one IfcRoad (or IfcRailway and IfcMarineFacility.WATERWAY).
All alignments shall have horizontal and vertical layout, with optional cant definition for railways. Matching 3D geometry representation as IfcGradientCurve shall have IfcCompositeCurve for horizontal geometry with IfcCurveSegments for vertical geometry (no separate 2D horizontal shape representation).

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

#### Table:bSF_Pset_Road {#tbl:bSF_Pset_Road}
| Name | Property type | Data type | Description| Usage |
|:---|:---|:---|:---|:---|
|Status|IfcPropertyEnumeratedValue|PEnum_ElementStatus|Status (new, existing, demolish, temporary)|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|

## Structural model

Structural model of a route comprises subgrade and pavement (and their parts).

### Subgrade - IfcEarthworksFill

Subgrade (i.e. the structure below pavement) is efined by IfcEarthworksFill entities.

![IfcEarthworksFill]({{diagramasfigure bsf-IfcEarthworksFill.pu}} "IfcEarthworksFill"){{figst bsf-ifcearthworksfill}}
   
### Pavement - IfcPavement

IfcPavement acts as an collection of courses and kerbs.

![IfcPavement]({{diagramasfigure bsf-IfcPavement.pu}} "IfcPavement"){{figst IfcPavement}}

#### Table:Pset_PavementCommon {#tbl:Pset_PavementCommon}
| Name | Property type | Data type | Description| Usage |
|:---|:---|:---|:---|:---|
|NominalThickness|IfcSingleValue|IfcNonNegativeLengthMeasure|Nominal thickness|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|NominalWidth|IfcSingleValue|IfcNonNegativeLengthMeasure|Nominal width|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|

#### Table:Qto_PavementBaseQuantities {#tbl:Qto_PavementBaseQuantities}
| Name | Property type | Data type | Description| Usage |
|:---|:---|:---|:---|:---|
|Width|IfcSingleValue|IfcQuantityLength|Width|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|Depth|IfcSingleValue|IfcQuantityLength|Depth|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|NetArea|IfcSingleValue|IfcQuantityArea|Area|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|NetVolume|IfcSingleValue|IfcQuantityVolume|Volume|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|

### Courses - IfcCourse

Structural layers are defined by IfcCourse entities.

![IfcCourse]({{diagramasfigure bsf-IfcCourse.pu}} "IfcCourse"){{figst ifccourse}}

#### Table:Pset_CourseCommon {#tbl:Pset_CourseCommon}
| Name | Property type | Data type | Description| Usage |
|:---|:---|:---|:---|:---|
|NominalThickness|IfcSingleValue|IfcNonNegativeLengthMeasure|Nominal thickness|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|NominalWidth|IfcSingleValue|IfcNonNegativeLengthMeasure|Nominal width|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|

#### Table:Qto_CourseBaseQuantities {#tbl:Qto_CourseBaseQuantities}
| Name | Property type | Data type | Description| Usage |
|:---|:---|:---|:---|:---|
|Length|IfcSingleValue|IfcQuantityLength|Length|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|Width|IfcSingleValue|IfcQuantityLength|Width|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|Thickness|IfcSingleValue|IfcQuantityLength|Depth|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|Volume|IfcSingleValue|IfcQuantityVolume|Volume|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|

#### Table:bSF_Pset_CourseCommon {#tbl:bSF_Pset_CourseCommon}
| Name | Property type | Data type | Description| Usage |
|:---|:---|:---|:---|:---|
|MaterialName|IfcSingleValue|IfcLabel|Material name|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|LoadCapacity|IfcSingleValue|IfcPlanarForceMeasure|Load capacity|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|Granulation|IfcSingleValue|IfcLabel|Granule size, ie. 16-20mm|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|Color|IfcSingleValue|IfcColor|Material color|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|

#### Table:bSF_Pset_SurfaceCourse {#tbl:bSF_Pset_SurfaceCourse}
| Name | Property type | Data type | Description| Usage |
|:---|:---|:---|:---|:---|
|ElasticModulus|IfcSingleValue|IfcModulusOfElasticityMeasure|Elastic modulus|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|MaterialStrength|IfcSingleValue|IfcLabel|Material strength|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|MassType|IfcSingleValue|IfcLabel|Mass type, ie. AB|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|DeformationClass|IfcSingleValue|IfcLabel|Deformation class|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|AbrasionResistance|IfcSingleValue|IfcLabel|Abrasion resistance|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|ShockResistance|IfcSingleValue|IfcLabel|Shock resistance|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|MixRatio|IfcSingleValue|IfcPositiveRatioMeasure|Rock/Binder ratio|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|

### Kerb - IfcKerb

![IfcKerb]({{diagramasfigure bsf-IfcKerb.pu}} "IfcKerb"){{figst ifckerb}}


#### Table:Pset_KerbStone {#tbl:Pset_KerbStone}
| Name | Property type | Data type | Description| Usage |
|:---|:---|:---|:---|:---|
|NominalLength|IfcSingleValue|IfcNonNegativeLengthMeasure|Nominal length|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|NominalHeight|IfcSingleValue|IfcNonNegativeLengthMeasure|Nominal height|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|NominalWidth|IfcSingleValue|IfcNonNegativeLengthMeasure|Nominal width|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|

#### Table:Pset_OnSiteCastKerb {#tbl:Pset_OnSiteCastKerb}
| Name | Property type | Data type | Description| Usage |
|:---|:---|:---|:---|:---|
|NominalHeight|IfcSingleValue|IfcNonNegativeLengthMeasure|Nominal height|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|NominalWidth|IfcSingleValue|IfcNonNegativeLengthMeasure|Nominal width|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|


#### Table:Pset_PrecastKerbStone {#tbl:Pset_PrecastKerbStone}
| Name | Property type | Data type | Description| Usage |
|:---|:---|:---|:---|:---|
|Type|IfcSingleValue|IfcLabel|Type designation|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|


#### Table:bSF_Pset_KerbCommon {#tbl:bSF_Pset_KerbCommon}
| Name | Property type | Data type | Description| Usage |
|:---|:---|:---|:---|:---|
|MaterialName|IfcSingleValue|IfcLabel|Material name|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|Color|IfcSingleValue|IfcColor|Material color|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|InstallationMethod|IfcLabel|Installation method|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|


#### Table:Qto_KerbBaseQuantities {#tbl:Qto_KerbBaseQuantities}
| Name | Property type | Data type | Description| Usage |
|:---|:---|:---|:---|:---|
|Length|IfcSingleValue|IfcQuantityLength|Length|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|Height|IfcSingleValue|IfcQuantityLength|Height|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|Width|IfcSingleValue|IfcQuantityLength|Width|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|Volume|IfcSingleValue|IfcQuantityVolume|Volume|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|


## Geomodel - IfcGeomodel

![IfcGeomodel]({{diagramasfigure bsf-IfcGeomodel.pu}} "IfcGeomodel"){{figst ifcgeomodel}}

### Existing terrain

![Existing terrain]({{diagramasfigure bsf-IfcGeotechnicalStratum-Terrain.pu}} "Existing terrain"){{figst ifcgeotechnicalstratum-terrain}}

### Soil cut

![Soil cut]({{diagramasfigure bsf-IfcEarthWorksCut-Soil.pu}} "Soil cut"){{figst bsf-ifcearthworkscut-soil}}

#### Table:Qto_EarthworksCutBaseQuantities {#tbl:Qto_EarthworksCutBaseQuantities}
| Name | Property type | Data type | Description| Usage |
|:---|:---|:---|:---|:---|
|Length|IfcSingleValue|IfcQuantityLength|Length|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|Height|IfcSingleValue|IfcQuantityLength|Height|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|Width|IfcSingleValue|IfcQuantityLength|Width|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|UndisturbedVolume|IfcSingleValue|IfcQuantityVolume|Undisturbed volume|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|LooseVolume|IfcSingleValue|IfcQuantityVolume|Loose Volume|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|Weight|IfcSingleValue|IfcQuantityWeight|Estimated weight|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|

### Rock bed

![Rock bed]({{diagramasfigure bsf-IfcGeotechnicalStratum-Rockbed.pu}} "IfcGeomodel"){{figst ifcgeotechnicalstratum-rockbed}}

### Rock cut

![Rock cut]({{diagramasfigure bsf-IfcEarthWorksCut-Rock.pu}} "Rock cut"){{figst bsf-ifcearthworkscut-rock}}

# Geometry representation

There shall be exactly one 3D geometric representation context (hich may have subcontexts for different types of shape representation in 3D space). 

![IfcGeometricRepresentationContext-3D]({{diagramasfigure bsf-IfcGeometricRepresentationContext-3D.pu}} "IfcGeometricRepresentationContext-3D"){{figst IfcGeometricRepresentationContext-3D}}

![AlignmentCurve]({{diagramasfigure bsf-IfcProductDefinitionShape-Alignment.pu}} "AlignmentCurve"){{figst AlignmentCurve}}

![Annotation]({{diagramasfigure bsf-IfcProductDefinitionShape-Annotation.pu}} "Annotation"){{figst Annotation}}

![BrepwithBreaklines]({{diagramasfigure bsf-IfcProductDefinitionShape-BrepwithBreaklines.pu}} "BrepwithBreaklines"){{figst BrepwithBreaklines}}

![Footprint]({{diagramasfigure bsf-IfcProductDefinitionShape-Footprint.pu}} "Footprint"){{figst Footprint}}

![SolidwithBreaklines]({{diagramasfigure bsf-IfcProductDefinitionShape-SolidwithBreaklines.pu}} "SolidwithBreaklines"){{figst SolidwithBreaklines}}

![TIN]({{diagramasfigure bsf-IfcProductDefinitionShape-TIN.pu}} "TIN"){{figst TIN}}

![TINwithBreaklines]({{diagramasfigure bsf-IfcProductDefinitionShape-TINwithBreaklines.pu}} "TINwithBreaklines"){{figst TINwithBreaklines}}

{{end_landscape}}

