{{begin_landscape}}
# IFC 4.3 file

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

\clearpage
# Entity definitions

## Project - IfcProject

There shall be exactly one IfcProject entity in each IFC-file.
Unit assignment is mandatory and shall define units for all measure values (attribute or property) in the file.

![IfcProject]({{diagramasfigure bsf-IfcProject.pu}} "IfcProject"){{figst ifcproject}}

\clearpage
## Alignment - IfcAlignment

Every IfcAlignment entity in the file shall be aggregated directly to IfcProject, and reference exactly one IfcRoad (or IfcRailway and IfcMarineFacility.WATERWAY).
All alignments shall have horizontal and vertical layout, with optional cant definition for railways. Matching 3D geometry representation as IfcGradientCurve shall have IfcCompositeCurve for horizontal geometry with IfcCurveSegments for vertical geometry (no separate 2D horizontal shape representation).

![IfcAlignment]({{diagramasfigure bsf-IfcAlignment.pu}} "IfcAlignment"){{figst ifcalignment}}

\clearpage
### Horizontal alignment - IfcAlignmentHorizontal

Horizontal alignments with linear and circular arc segments, as well as clothoid and cubic transition segments are in scope at this stage.

![IfcAlignmentHorizontal]({{diagramasfigure bsf-IfcAlignmentHorizontal.pu}} "IfcAlignmentHorizontal"){{figst ifcalignmenthorizontal}}

\clearpage
### Vertical alignment - IfcAlignmentVertical

Vertical alignments with constant gradient as well circular and parabolic arc segments are in scope at this stage.

![IfcAlignmentVertical]({{diagramasfigure bsf-IfcAlignmentVertical.pu}} "IfcAlignmentVertical"){{figst ifcalignmentvertical}}

\clearpage
### Cant - IfcAlignmentCant

IfcAlignmentCant shall be used as defined in IFC specification (no additional rules at this stage).

## Site - IfcSite

![IfcSite]({{diagramasfigure bsf-IfcSite.pu}} "IfcSite"){{figst ifcsite}}

\clearpage
## Road - IfcRoad

![IfcRoad]({{diagramasfigure bsf-IfcRoad.pu}} "IfcRoad"){{figst ifcroad}}

#### Table:bSF_Pset_Road {#tbl:bSF_Pset_Road}
| Name | Property type | Data type | Description| Usage |
|:---|:---|:---|:---|:---|

|Status|IfcProperty&shy;Enumerated&shy;Value|PEnum_&shy;Element&shy;Status|Status (new, existing, demolish, temporary)|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|

\clearpage
## Structural model

Structural model of a route comprises subgrade and pavement (and their parts).

### Subgrade - IfcEarthworksFill

Subgrade (i.e. the structure below pavement) is efined by IfcEarthworksFill entities.

![IfcEarthworksFill]({{diagramasfigure bsf-IfcEarthworksFill.pu}} "IfcEarthworksFill"){{figst bsf-ifcearthworksfill}}

\clearpage
### Pavement - IfcPavement

IfcPavement acts as an collection of courses and kerbs.

![IfcPavement]({{diagramasfigure bsf-IfcPavement.pu}} "IfcPavement"){{figst IfcPavement}}

#### Table:Pset_PavementCommon {#tbl:Pset_PavementCommon}
| Name | Property type | Data type | Description| Usage |
|:---|:---|:---|:---|:---|

|NominalThickness|IfcSingleValue|IfcNonNegative&shy;Length&shy;Measure|Nominal thickness|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|NominalWidth|IfcSingleValue|IfcNonNegative&shy;Length&shy;Measure|Nominal width|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|


#### Table:Qto_PavementBaseQuantities {#tbl:Qto_PavementBaseQuantities}
| Name | Property type | Data type | Description| Usage |
|:---|:---|:---|:---|:---|
|Width|IfcSingleValue|IfcQuantity&shy;Length|Width|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|Depth|IfcSingleValue|IfcQuantity&shy;Length|Depth|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|NetArea|IfcSingleValue|IfcQuantity&shy;Area|Area|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|NetVolume|IfcSingleValue|IfcQuantity&shy;Volume|Volume|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|

\clearpage
### Courses - IfcCourse

Structural layers are defined by IfcCourse entities.

![IfcCourse]({{diagramasfigure bsf-IfcCourse.pu}} "IfcCourse"){{figst ifccourse}}

#### Table:Pset_CourseCommon {#tbl:Pset_CourseCommon}
| Name | Property type | Data type | Description| Usage |
|:---|:---|:---|:---|:---|
|NominalThickness|IfcSingleValue|IfcNonNegative&shy;Length&shy;Measure|Nominal thickness|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|NominalWidth|IfcSingleValue|IfcNonNegative&shy;Length&shy;Measure|Nominal width|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|



#### Table:Qto_CourseBaseQuantities {#tbl:Qto_CourseBaseQuantities}
| Name | Property type | Data type | Description| Usage |
|:---|:---|:---|:---|:---|
|Length|IfcSingleValue|IfcQuantity&shy;Length|Length|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|Width|IfcSingleValue|IfcQuantity&shy;Length|Width|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|Thickness|IfcSingleValue|IfcQuantity&shy;Length|Depth|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|Volume|IfcSingleValue|IfcQuantity&shy;Volume|Volume|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|


#### Table:bSF_Pset_CourseCommon {#tbl:bSF_Pset_CourseCommon}
| Name | Property type | Data type | Description| Usage |
|:---|:---|:---|:---|:---|
|MaterialName|IfcSingleValue|IfcLabel|Material name|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|LoadCapacity|IfcSingleValue|IfcPlanar&shy;Force&shy;Measure|Load capacity|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|Granulation|IfcSingleValue|IfcLabel|Granule size, ie. 16-20mm|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|Color|IfcSingleValue|IfcColor|Material color|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|

#### Table:bSF_Pset_SurfaceCourse {#tbl:bSF_Pset_SurfaceCourse}
| Name | Property type | Data type | Description| Usage |
|:---|:---|:---|:---|:---|
|ElasticModulus|IfcSingleValue|IfcModulus&shy;Of&shy;Elasticity&shy;Measure|Elastic modulus|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|MaterialStrength|IfcSingleValue|IfcLabel|Material strength|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|MassType|IfcSingleValue|IfcLabel|Mass type, ie. AB|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|DeformationClass|IfcSingleValue|IfcLabel|Deformation class|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|AbrasionResistance|IfcSingleValue|IfcLabel|Abrasion resistance|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|ShockResistance|IfcSingleValue|IfcLabel|Shock resistance|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|MixRatio|IfcSingleValue|IfcPositive&shy;Ratio&shy;Measure|Rock/Binder ratio|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|

\clearpage
### Kerb - IfcKerb

![IfcKerb]({{diagramasfigure bsf-IfcKerb.pu}} "IfcKerb"){{figst ifckerb}}


#### Table:Pset_KerbStone {#tbl:Pset_KerbStone}
| Name | Property type | Data type | Description| Usage |
|:---|:---|:---|:---|:---|
|NominalLength|IfcSingleValue|IfcNonNegative&shy;Length&shy;Measure|Nominal length|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|NominalHeight|IfcSingleValue|IfcNonNegative&shy;Length&shy;Measure|Nominal height|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|NominalWidth|IfcSingleValue|IfcNonNegative&shy;Length&shy;Measure|Nominal width|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|


#### Table:Pset_OnSiteCastKerb {#tbl:Pset_OnSiteCastKerb}
| Name | Property type | Data type | Description| Usage |
|:---|:---|:---|:---|:---|
|NominalHeight|IfcSingleValue|IfcNonNegative&shy;Length&shy;Measure|Nominal height|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|NominalWidth|IfcSingleValue|IfcNonNegative&shy;Length&shy;Measure|Nominal width|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|



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
|Length|IfcSingleValue|IfcQuantity&shy;Length|Length|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|Height|IfcSingleValue|IfcQuantity&shy;Length|Height|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|Width|IfcSingleValue|IfcQuantity&shy;Length|Width|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|Volume|IfcSingleValue|IfcQuantity&shy;Volume|Volume|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|

\clearpage
## Geomodel - IfcGeomodel

Geomodel represents the existing ground (one or more strata). IfcGeomodel may have geometric representation as the top surface of the ground (terrain). Material and other properties are assigned to each individual stratum.

![IfcGeomodel]({{diagramasfigure bsf-IfcGeomodel.pu}} "IfcGeomodel"){{figst ifcgeomodel}}

\clearpage
### Existing ground layers

![Existing ground]({{diagramasfigure bsf-IfcGeotechnicalStratum.pu}} "Existing ground layers"){{figst ifcgeotechnicalstratum}}

#### Table:bSF_Pset_StratumCommon {#tbl:bSF_Pset_StratumCommon}
| Name | Property type | Data type | Description| Usage |
|:---|:---|:---|:---|:---|
|soiltypeGEO|IfcSingleValue|IfcLabel|Soil type classification according to Geotekninen maaluokitus (VTT 1974)|bSF_QTO[ ] bSF_D2C[ ] bSF_DH[x]|
|soiltypeISO|IfcSingleValue|IfcLabel|Soil type classification according to SFS-EN ISO 14688-1 or SFS-EN ISO 14688-2|bSF_QTO[ ] bSF_D2C[ ] bSF_DH[x]|
|qualificationClass|IfcSingleValue|IfcLabel|Soil type qualification according to table 10 in TIEH 2100029-04|bSF_QTO[ ] bSF_D2C[ ] bSF_DH[x]|
|frostSwellingFactorWet|IfcSingleValue|IfcLabel|Soil type frost swelling factor in wet conditions|bSF_QTO[ ] bSF_D2C[ ] bSF_DH[x]|
|frostSwellingFactorDry|IfcSingleValue|IfcLabel|Soil type frost swelling factor in dry conditions|bSF_QTO[ ] bSF_D2C[ ] bSF_DH[x]|
|elasticModulusWet|IfcSingleValue|IfcLabel|Soil modulus of elasticity in wet conditions|bSF_QTO[ ] bSF_D2C[ ] bSF_DH[x]|
|elasticModulusDry|IfcSingleValue|IfcLabel|Soil modulus of elasticity in dry conditions|bSF_QTO[ ] bSF_D2C[ ] bSF_DH[x]|

\clearpage
### Soil and rock cut

![Soil and rock cut]({{diagramasfigure bsf-IfcEarthWorksCut.pu}} "Soil and rock cut"){{figst bsf-ifcearthworkscut}}

#### Table:Qto_EarthworksCutBaseQuantities {#tbl:Qto_EarthworksCutBaseQuantities}
| Name | Property type | Data type | Description| Usage |
|:---|:---|:---|:---|:---|
|Length|IfcSingleValue|IfcQuantity&shy;Length|Length|bSF_QTO[ ] bSF_D2C[ ] bSF_DH[x]|
|Height|IfcSingleValue|IfcQuantity&shy;Length|Height|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|Width|IfcSingleValue|IfcQuantity&shy;Length|Width|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|UndisturbedVolume|IfcSingleValue|IfcQuantity&shy;Volume|Undisturbed volume|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|LooseVolume|IfcSingleValue|IfcQuantity&shy;Volume|Loose Volume|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|
|Weight|IfcSingleValue|IfcQuantity&shy;Weight|Estimated weight|bSF_QTO[ ] bSF_D2C[x] bSF_DH[x]|

\clearpage
# Geometric representation

There shall be exactly one 3D geometric representation context (hich may have subcontexts for different types of shape representation in 3D space). 

![IfcGeometricRepresentationContext-3D]({{diagramasfigure bsf-IfcGeometricRepresentationContext-3D.pu}} "IfcGeometricRepresentationContext-3D"){{figst IfcGeometricRepresentationContext-3D}}

\clearpage
## Alignment

![AlignmentCurve]({{diagramasfigure bsf-IfcProductDefinitionShape-Alignment.pu}} "AlignmentCurve"){{figst AlignmentCurve}}

\clearpage
## Annotation

![Annotation]({{diagramasfigure bsf-IfcProductDefinitionShape-Annotation.pu}} "Annotation"){{figst Annotation}}

\clearpage
## BrepwithBreaklines

![BrepwithBreaklines]({{diagramasfigure bsf-IfcProductDefinitionShape-BrepwithBreaklines.pu}} "BrepwithBreaklines"){{figst BrepwithBreaklines}}

\clearpage
## Footprint

![Footprint]({{diagramasfigure bsf-IfcProductDefinitionShape-Footprint.pu}} "Footprint"){{figst Footprint}}

\clearpage
## SolidwithBreaklines

![SolidwithBreaklines]({{diagramasfigure bsf-IfcProductDefinitionShape-SolidwithBreaklines.pu}} "SolidwithBreaklines"){{figst SolidwithBreaklines}}

\clearpage
## TIN

![TIN]({{diagramasfigure bsf-IfcProductDefinitionShape-TIN.pu}} "TIN"){{figst TIN}}

\clearpage
## TINwithBreaklines

![TINwithBreaklines]({{diagramasfigure bsf-IfcProductDefinitionShape-TINwithBreaklines.pu}} "TINwithBreaklines"){{figst TINwithBreaklines}}

{{end_landscape}}

