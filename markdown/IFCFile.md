# IFC 4.3 file

{{begin_landscape}}
## File structure

![IFC File entity hierarchy]({{diagramasfigure bsf-ifc-hierarkia.pu}} "IFC file entity hierarchy"){{figst ifcfilehierarchy}}


## File headers

![IFC file header]({{diagramasfigure bsf-IfcFile.pu}} "IFC-file header"){{figst ifcfileheader}}

**TODO:Add notes to diagram or descriptive text chapter about usage of fields under "file_name"**

# Entity definitions

## Project - IfcProject

![IfcProject]({{diagramasfigure bsf-IfcProject.pu}} "IfcProject"){{figst ifcproject}}

## Alignment(s) - IfcAlignment

**TODO:Diagram missing!**

## Classification system(s) - IfcClassification

**TODO:Diagram missing!**

## Site - IfcSite

![IfcSite]({{diagramasfigure bsf-IfcSite.pu}} "IfcSite"){{figst ifcsite}}

## Road - IfcRoad

**TODO:Diagram missing!**

## Structural model - IfcCourse

Structural layers are defined by IfcCourse entities

![IfcCourse]({{diagramasfigure bsf-IfcCourse.pu}} "IfcCourse"){{figst ifccourse}}

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

## Classification reference - IfcClassificationReference

**TODO:Diagram missing!**

## Material definitions

### IfcMaterialDefinition

**TODO:Diagram missing!**

### IfcmaterialConstituentSet

**TODO:Diagram missing!**

### IfcMaterialConstituent

**TODO:Diagram missing!**

### IfcMaterial

**TODO:Diagram missing!**

## Geometry representation

![IfcGeometricRepresentationContext]({{diagramasfigure bsf-IfcGeometricRepresentationContext.pu}} "IfcGeometricRepresentationContext"){{figst IfcGeometricRepresentationContext}}

![BrepwithBreaklines]({{diagramasfigure bsf-IfcProductDefinitionShape-BrepwithBreaklines.pu}} "BrepwithBreaklines"){{figst BrepwithBreaklines}}

![Footprint]({{diagramasfigure bsf-IfcProductDefinitionShape-Footprint.pu}} "Footprint"){{figst Footprint}}

![SolidwithBreaklines]({{diagramasfigure bsf-IfcProductDefinitionShape-SolidwithBreaklines.pu}} "SolidwithBreaklines"){{figst SolidwithBreaklines}}

![TIN]({{diagramasfigure bsf-IfcProductDefinitionShape-TIN.pu}} "TIN"){{figst TIN}}

![TINwithBreaklines]({{diagramasfigure bsf-IfcProductDefinitionShape-TINwithBreaklines.pu}} "TINwithBreaklines"){{figst TINwithBreaklines}}

{{end_landscape}}

