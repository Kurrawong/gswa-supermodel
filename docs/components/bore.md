# Bore Model

<a href="../../assets/bores-model/Concepts.svg">
<figure id="figure-bc" markdown>
  ![](../assets/bores-model/Concepts.svg)
  <figcaption>Figure BI: Bores Model intro figure</figcaption>
</figure>
</a>

This model describes physical, functional and operational aspects of Bores, sometimes known as Wells.

This Model is a formally-defined [_profile_](https://www.w3.org/TR/dx-prof/#dfn-profile) which is multi-part standard that includes a specification, schema, data validators, supporting vocabularies and a few other things. Also, this model _profiles_ other standards, that is it inherits and depends on elements of other standards. Data created conforming to this _profile_ will conform to the standards this model profiles.

The comprehensive listing of the various parts of this profile are given in the [Profile Definition](#profile-definition) section, below.

The Semantic Web model component of this profile, it's schema, is published online at a persistent web location:

* **<https://linked.data.gov.au/def/bore>**

## Model Profiling

### Is Profile Of 

This model is a specialisation of - a constraining of - several existing Standards, some of which are about bores/boreholes and some of which are about more fundamental concepts relevant to bores, such as spatiality and sampling. Specifically, this model is an interpretation of [GeoSciML](../background.md#geosciml)'s non-Semantic Web Boreholes model in Semantic Web form, with alignments to [GeoSPARQL](../background.md#geosparql) a general-purpose spatial Semantic Web standard and [SOSA](../background.md#sosa), a general Semantic Web standard for sampling features & systems. An intermediate standard is also used: the [FSDF Backbone Model](https://linked.data.gov.au/def/fsdf-backbone), which profiles GeoSPARQL and SOSA and ensures that all objects conforming to it work well with the Australian Foundational Spatial Data Framework.

The things this model is a profile of are shown graphically, in [Figure BH](#figure-bh) below.

<a href="../../assets/bores-model/Profiles Hierarchy.svg">
<figure id="figure-bh" markdown>
  ![](../assets/bores-model/Profiles Hierarchy.svg)
  <figcaption>Figure BH: Profile hierarchy of the Bores Model</figcaption>
</figure>
</a>

### Resources

This Model contains several distinct resources, all of which are contained in, or linked to from, this document. The resources and their roles are:

**Resource** | **Role**
--- | ---
Profile Definition | defines this set of resources - this table and text above
[Specification](#specification) | _[specification](https://www.w3.org/TR/dx-prof/#Role:specification)_<br />defines the profile elements in human-readable form<br /><br />[Specification](#specification) section of this document
[Schema](#schema) | _[schema](https://www.w3.org/TR/dx-prof/#Role:schema)_<br />machine-readable version of the Specification's elements<br /><br />Online at <https://linked.data.gov.au/def/bore.ttl> and in this model's repository
[Validator](#validators) | _[validation](https://www.w3.org/TR/dx-prof/#Role:validation)_<br />machine-executable rules to test data for conformance to this Profile<br /><br />Online at <https://linked.data.gov.au/def/bore/validator> and in this model's repository
[Compounded Validator](#validators) | _[validation](https://www.w3.org/TR/dx-prof/#Role:validation)_<br />this profile's validator & those of all dependencies in one<br /><br />Online at <https://linked.data.gov.au/def/bore/validator-compounded> and in this model's repository
[Vocabularies](#vocabularies) | _[vocabulary](https://www.w3.org/TR/dx-prof/#Role:vocabulary)_<br />define terms used in the Model<br /><br />[Vocabularies](#vocabularies) section of this document
[Examples](#examples) | _[example](https://www.w3.org/TR/dx-prof/#Role:schema)_<br />valid and invalid data files, building on the examples in the Specification<br /><br />In this model's repository at [rdf > components > bore > examples](https://github.com/Kurrawong/gswa-supermodel/tree/main/rdf/components/bore/examples>)
[Code Repository](#code-repository) | _[repository](https://www.w3.org/TR/dx-prof/#Role:schema)_<br />an online repository storing all of this Profile's resources<br ><br />Online at <https://github.com/Kurrawong/gswa-supermodel/>

## Specification

This Specification is the normative statement of the elements of this Model. This Specification is human-readable - this document - but does not provide either a formal model schema or data validators: those are provided for by the _schema_ and _validator_ resources listed in the [Resources Section](#resources) above.

This Specification defines data classes and predicates that can be used to describe boreholes in line with the concepts of the Figure above. The classes and predicates are defined in a following section after the total model which uses them is introduced next.

### Model

Knowledge Graph data models define data _classes_ with _predicates_ and, sometimes _axioms_ which are logical rules that are applied to class and predicates. This model, so far, only defines a few classes and predicates, no axioms.

The Figure BO below is a classes and predicates diagram (formally, an [OWL](../background.md#web-ontology-language-owl) diagram) of the major components of this profile's model. Where they match, the names of the classes in this Figure link them to the elements in the Concepts, [Figure BC](#figure-bc) above.

> The Key for the elements in this Figure is the [figure key for this Supermodel](../supermodel.md#modelling-conventions).

<a href="../../assets/bores-model/Overview.svg">
<figure id="figure-bo" markdown>
  ![](../assets/bores-model/Overview.svg)  
  <figcaption>Figure BO: Overview of the model of this Bores Model. The Bore class must be related to one or more Boreholes which, in turn, may have zero or more Borehole Intervals. Bores, Boreholes & Borehole Intervals are geospatial Features and may have Geometries recorded and Samples may be taken from them. Bores may be attributed to Agents (people and organisations) with the attribution qualified with Roles. A number of vocabulary-based classifiers are available for the Bore, such as Borehole Purpose, whose values are selected from controlled vocabularies listed within this Model. Some and datatype predicates are also available, such as depth.</figcaption>
</figure>
</a>

### Namespaces

Namespaces provide unique identity to elements within this Model - classes, predicates, validation shapes and example data. Prefixes for namespaces are used to assist with documentation readability.

Where you see a prefix used, something like `xxx:`, it is to be replaced with the namespace for complete term definition. For example, using the table below, we can understand that `bore:Bore` is equivalent to `https://linked.data.gov.au/def/borehole/Bore`.

The following prefixed namespaces are used in class and property definition tables and the code examples following:

| **Prefix** | **Namespace**                                          | **Description**                                                                 |
|------------|--------------------------------------------------------|---------------------------------------------------------------------------------|
| `ex`       | `http://example.com/`                                  | Non-resolvable namespace for examples                                           |
| `bore`     | `https://linked.data.gov.au/def/borehole/`             | The namespace fot this model                                                    |
| `bsps`     | `https://linked.data.gov.au/def/borehole-start-point/` | Borehole Start Point vocabulary, managed by the Geological Survey of Queensland |
| `dcat`     | `http://www.w3.org/ns/dcat#`                           | Data Catalogue vocabulary: cataloguing international standard                   |
| `dcterms`  | `http://purl.org/dc/terms/`                            | Dublin Core Terms: basic library catalogue-style metadata                       |
| `geo`      | `http://www.opengis.net/ont/geosparql#`                | GeoSPARQL: Semantic Web spatial international standard                          |
| `prov`     | `http://www.w3.org/ns/prov#`                           | Provenance Ontology: provenance data structures international standard          |
| `rdfs`     | `http://www.w3.org/2000/01/rdf-schema#`                | RDF Schema vocabulary: Basic structural RDF elements                            |
| `schema`   | `https://schema.org/`                                  | The general-purpose schema.org model                                            | 
| `skos`     | `http://www.w3.org/2004/02/skos/core#`                 | Simple Knowledge Organization System: a model for controlled vocabularies       |
| `xsd`      | `http://www.w3.org/2001/XMLSchema#`                    | XML Schema Definitions Datatypes. See <https://www.w3.org/TR/xmlschema11-2/>    |

These namespaces appear at the start of RDF data files and SPARQL query files in a form similar to this table, for example in the schema for this model [:octicons-link-external-16:](https://github.com/nicholascar/gswa-supermodel/blob/main/rdf/component/bores.ttl), you can see the prefix `bore`for the Bores Model namespace on the first line: 

* `PREFIX bore: <https://linked.data.gov.au/def/bore/>`

### Classes

#### Bore
<a id="Bore"></a>

**Property** | **Value**
--- | ---
IRI | `bore:Bore`
[Name](https://schema.org/name "schema:name") | Bore
[Alternate Name](https://schema.org/alternateName "schema:alternateName") | Well, Drillhole
[Description](https://schema.org/description "schema:description") | A borehole is a narrow shaft, or set of shafts, bored in the ground with a common point of origin. A borehole may be constructed for many different purposes, including the extraction of water, other liquids (such as petroleum) or gases (such as natural gas), as part of a geotechnical investigation, environmental site assessment, mineral exploration, temperature measurement, as a pilot hole for installing piers or underground utilities, for geothermal installations, or for underground storage of unwanted substances, e.g. in carbon capture and storage.
Expected Properties | [has origin position](#hasOriginPosition "bore:hasOriginPosition")<br />[has geometry](https://opengeospatial.github.io/ogc-geosparql/geosparql11/spec.html#_property_geohasgeometry "geo:hasGeometry") - used to indicate the geometry of the Bore<br />[has part](https://schema.org/hasPart "schema:hasPart") - for linking to [Borehole](#Borehole) objects)<br />[was attributed to](https://www.w3.org/TR/prov-o/#wasAttributedTo "prov:wasAttributedTo") - for linking to [Agent](https://www.w3.org/TR/prov-o/#Agent) objects, via [Attribution](https://www.w3.org/TR/prov-o/#Attribution) objects<br />classification predicates, e.g. [has purpose](#hasPurpose "bore:hasPurpose")
[History Note](https://www.w3.org/TR/skos-reference/#notes "skos:historyNote") | This definition for a Bore is derived from of GeoSciML's definition for Borehole, however it is altered to cater for multi-shaft Bores/Wells. This is achieved by making Bore a container class for one of more Borehole objects which represent the individual shafts.

[Example](https://www.w3.org/TR/skos-reference/#notes "skos:example")
```
ex:b-01
    a bore:Bore ;
    bore:hadDrillingMethod <https://linked.data.gov.au/def/borehole-drilling-method-western-australia/hydraulic-jet> ;
    bore:hasOriginPosition [
        geo:asWKT "POINT (153.083340 -27.325458)"^^geo:wktLiteral ;
    ] ;
    bore:hasOriginSetting bsps:natural-ground-surface ;
    prov:wasAttributedTo [
        prov:agent <https://orcid.org/0000-0002-8742-7730> ;
        dcat:hadRole ex:driller ;
    ] ;
    bore:hasPurpose <https://linked.data.gov.au/def/borehole-purpose/oil-shale> ;
    bore:hasStatus <https://linked.data.gov.au/def/borehole-status/operational> ;
    hasVerticalReference <https://linked.data.gov.au/def/vertical-depth-reference-systems/lat> ;
    # other predicates such as links to Bores
.
```

This example shows a borehole, `ex:bh-01`, with an origin position at longitude 153.083340 E & latitude 27.325458 S, a surface circumstance taken from a Geological Survey of Queensland vocabulary ("natural ground surface") and there's an attribution of the borehole to an Agent: Nicholas Car, identified by an IRI, with the role of driller.

#### Borehole
<a id="Borehole"></a>

**Property** | **Value**
--- | ---
IRI | `bore:Borehole`
[Name](https://schema.org/name "schema:name") | Borehole
[Alternate Name](https://schema.org/alternateName "schema:alternateName") | Wellbore
[Description](https://schema.org/description "schema:description") | A Borehole is an individual shaft drilled into the ground
[Scope Note](https://www.w3.org/TR/skos-reference/#notes "skos:scopeNote") | A Borehole is not the overall Bore or Well object but a distinct part of it. Every Borehole must be presented in relation to a Bore
Expected Properties | [has geometry](https://opengeospatial.github.io/ogc-geosparql/geosparql11/spec.html#_property_geohasgeometry "geo:hasGeometry") - used to indicate the geometry of the Borehole, perhaps as a LineString or a Polygon<br />[has part](https://schema.org/hasPart "schema:hasPart") - for linking to [Borehole Interval](#BoreholeInterval) objects)
[History Note](https://www.w3.org/TR/skos-reference/#notes "skos:historyNote") | This definition for a Bore is derived from of GeoSciML's definition for Borehole. Borehole is the class assigned to represent an individual shaft whereas Bore has been made a container class that contains one or more Borehole objects. This is to cater for multi-shaft Bores which are common in some industries, for example petroleum exploration where Bores are referred to as Wells and Boreholes as Wellbores.

[Example](https://www.w3.org/TR/skos-reference/#notes "skos:example")
```
ex:b-01
    a bore:Bore ;
    schema:hasPart 
        ex:bh-01 , 
        ex:bh-02 ;     
.

ex:bh-01
    a bore:Borehole ;
    geo:hasGeometry [
        geo:asWKT "LINESTRING (...)"^^geo:wktLiteral
    ] ;
.
```

#### Borehole Interval
<a id="BoreholeInterval"></a>

| **Property**                                                              | **Value**                                                                                                  |
|---------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
| IRI                                                                       | `bore:BoreholeInterval`                                                                                    |
| [Name](https://schema.org/name "schema:name")                             | Borehole Interval                                                                                          |
| [Alternate Name](https://schema.org/alternateName "schema:alternateName") | Wellbore Interval                                                                                          |
| [Description](https://schema.org/description "schema:description")        | A segment of a Borehole, usually started and terminated by changes in direction or of the material drilled |

[Example](https://www.w3.org/TR/skos-reference/#notes "skos:example")
```
ex:bh-01
    a bore:Borehole ;
    schema:hasPart 
        ex:bhi-01 ,
        ex:bhi-02 ,
        ex:bhi-03 ;
.

ex:bhi-01
    a bore:HoreholeIntervale ;
    geo:hasGeometry [
        geo:asWKT "LINESTRING (...)"^^geo:wktLiteral
    ] ;    
.
```

#### Number
<a id="Number"></a>

| **Property**                                                               | **Value**                                                                                                                                                                                                        |
|----------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| IRI                                                                        | `schema:Number`(https://schema.org/Number "schema:Number")                                                                                                                                                       |
| [Name](https://schema.org/name "schema:name")                              | Number                                                                                                                                                                                                           |
| [Description](https://schema.org/description "schema:description")         | A number object                                                                                                                                                                                                  |
| [Scope Note](https://www.w3.org/TR/skos-reference/#notes "skos:scopeNote") | Use this class to communicate a number with a value and a unit of measure. Use in this model requires `schema:value` and `schema:unitCode` values with the latter indicating units from [QUDT](https://qudt.org) |

[Example](https://www.w3.org/TR/skos-reference/#notes "skos:example")
```
ex:bh-01
    a bore:Borehole ;
    schema:hasPart 
        ex:bhi-01 ,
        ex:bhi-02 ,
        ex:bhi-03 ;
.

ex:bhi-01
    a bore:HoreholeIntervale ;
    geo:hasGeometry [
        geo:asWKT "LINESTRING (...)"^^geo:wktLiteral
    ] ;    
.
```

### Predicates

#### depth
<a id="depth"></a>

| **Property**                                                                 | **Value**                                                                                                                                                                                              |
|------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| IRI                                                                          | [`schema:depth`](https://schema.org/depth "schema:depth")                                                                                                                                              |
| [Name](https://schema.org/name "schema:name")                                | depth                                                                                                                                                                                                  |
| [Description](https://schema.org/description "schema:description")           | The depth of the Bore                                                                                                                                                                                  |
| [Domain Includes](https://schema.org/domainIncludes "schema:domainIncludes") | [Bore](#Bore), [Borehole](#Borehole), [BoreholeIntervale](#BoreholeIntervale)                                                                                                                          |
| [Range Includes](https://schema.org/rangeIncludes "schema:rangeIncludes")    | [double](https://www.w3.org/TR/xmlschema11-2/#double "xsd:double"), [Number](https://schema.org/Number "schema:Number")                                                                                |
| [Scope Note](https://www.w3.org/TR/skos-reference/#notes "skos:scopeNote")   | Use this to give a simple value for the depth of the Bore overall. Detailed depth calculations should be made using geometries. If a simple double value is given, it is assumed to be depth in metres |

[Example](https://www.w3.org/TR/skos-reference/#notes "skos:example")
```
ex:b-01
    a bore:Bore ;
    schema:depth 431.2 ;  # assumed to be in metres
.

ex:b-02
    a bore:Bore ;
    schema:depth [  # 2.473 kM
        schema:value 2.473 ;
        schema:unitCode <https://qudt.org/vocab/unit/KiloM> ;
    ] ;
.
```

#### had drilling method
<a id="hasDrillingMethod"></a>

| **Property**                                                          | **Value**                                                                                                                                                                                                      |
|-----------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| IRI                                                                   | `bore:hadDrillingMethod`                                                                                                                                                                                       |
| [Name](https://schema.org/name "schema:name")                         | had drilling method                                                                                                                                                                                            |
| [Description](https://schema.org/description "schema:description")    | The method used to drill the Bore                                                                                                                                                                              |
| [Domain](http://www.w3.org/2000/01/rdf-schema#domain "rdfs:domain")   | [Bore](#Bore)                                                                                                                                                                                                  |
| [Range](http://www.w3.org/2000/01/rdf-schema#range "rdfs:range")      | A [Concept](https://www.w3.org/TR/skos-reference/#concepts "skos:Concept") from the [_Borehole drilling method (of WA)_ vocabulary](https://linked.data.gov.au/def/borehole-drilling-method-western-australia) |
| [Example](https://www.w3.org/TR/skos-reference/#notes "skos:example") | See example for [Bore](#Bore)                                                                                                                                                                                  |

#### has inclination
<a id="hasInclination"></a>

| **Property**                                                               | **Value**                                                                                                                                     |
|----------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| IRI                                                                        | `bore:hasInclination`                                                                                                                         |
| [Name](https://schema.org/name "schema:name")                              | has inclination                                                                                                                               |
| [Description](https://schema.org/description "schema:description")         | The angle in the vertical plane relative to a reference vector parallel to the force of gravity, i.e. downwards                               |
| [Domain](http://www.w3.org/2000/01/rdf-schema#domain "rdfs:domain")        | [Bore](#Bore)                                                                                                                                 |
| [Range Includes](https://schema.org/rangeIncludes "schema:rangeIncludes")  | [double](https://www.w3.org/TR/xmlschema11-2/#double "xsd:double"), [Concept](https://www.w3.org/TR/skos-reference/#concepts "skos:Concept")  |
| [Scope Note](https://www.w3.org/TR/skos-reference/#notes "skos:scopeNote") | The value must be between 0 and -90 or a concept from a vocabulary, such as [Borehole Design](https://linked.data.gov.au/def/borehole-design) |

[Example](https://www.w3.org/TR/skos-reference/#notes "skos:example")
```
ex:b-01
    a bore:Bore ;
    bore:hasInclination 78 ;  # assumed to be in degrees from the vertical
.

ex:b-02
    a bore:Bore ;
    bore:hasInclination <https://linked.data.gov.au/def/borehole-design/inclineddown> ;  # from the Borehole Design vocab
.
```

#### has origin position
<a id="hasOriginPosition"></a>

| **Property**                                                               | **Value**                                                                                    |
|----------------------------------------------------------------------------|----------------------------------------------------------------------------------------------|
| IRI                                                                        | `bore:hasOriginPosition`                                                                     |
| [Name](https://schema.org/name "schema:name")                              | has origin position                                                                          |
| [Description](https://schema.org/description "schema:description")         | The position of the start of the first Borehole of the Bore on a surface                     |
| [Domain](http://www.w3.org/2000/01/rdf-schema#domain "rdfs:domain")        | [Bore](#Bore)                                                                                |
| [Range](http://www.w3.org/2000/01/rdf-schema#range "rdfs:range")           | [Geometry](https://docs.ogc.org/is/22-047r1/22-047r1.html#_class_geogeometry "geo:Geometry") |
| [Scope Note](https://www.w3.org/TR/skos-reference/#notes "skos:scopeNote") | Only use Point geometries                                                                    |
| [Example](https://www.w3.org/TR/skos-reference/#notes "skos:example")      | See example for [Bore](#Bore)                                                                |

#### has origin setting
<a id="hasOriginSetting"></a>

| **Property**                                                                   | **Value**                                                                                                                                                                                    |
|--------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| IRI                                                                            | `bore:hasOriginSetting`                                                                                                                                                                      |
| [Name](https://schema.org/name "schema:name")                                  | has origin setting                                                                                                                                                                           |
| [Description](https://schema.org/description "schema:description")             | Indicates the nature of the bore origin surroundings                                                                                                                                         |
| [Domain](http://www.w3.org/2000/01/rdf-schema#domain "rdfs:domain")            | [Bore](#Bore)                                                                                                                                                                                |
| [Range](http://www.w3.org/2000/01/rdf-schema#range "rdfs:range")               | A [Concept](https://www.w3.org/TR/skos-reference/#concepts "skos:Concept") from the [_Borehole start point setting_ vocabulary](https://linked.data.gov.au/def/borehole-start-point-setting) |
| [History Note](https://www.w3.org/TR/skos-reference/#notes "skos:historyNote") | This predicate is the equivalent of GeoSciML's `startPoint` property                                                                                                                         |
| [Example](https://www.w3.org/TR/skos-reference/#notes "skos:example")          | See example for [Bore](#Bore)                                                                                                                                                                |

#### has purpose
<a id="hasPurpose"></a>

| **Property**                                                               | **Value**                                                                                                                                                            |
|----------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| IRI                                                                        | `bore:hasPurpose`                                                                                                                                                    |
| [Name](https://schema.org/name "schema:name")                              | has purpose                                                                                                                                                          |
| [Description](https://schema.org/description "schema:description")         | A purpose of the Bore                                                                                                                                                |
| [Domain](http://www.w3.org/2000/01/rdf-schema#domain "rdfs:domain")        | [Bore](#bore)                                                                                                                                                        |
| [Range](http://www.w3.org/2000/01/rdf-schema#range "rdfs:range")           | A [Concept](https://www.w3.org/TR/skos-reference/#concepts "skos:Concept") from the [_Borehole Purpose_ vocabulary](https://linked.data.gov.au/def/borehole-purpose) |
| [Scope Note](https://www.w3.org/TR/skos-reference/#notes "skos:scopeNote") | Multiple purposes may be indicated                                                                                                                                   |
| [Example](https://www.w3.org/TR/skos-reference/#notes "skos:example")      | See example for [Bore](#bore)                                                                                                                                        |

#### has status
<a id="hasStatus"></a>

| **Property**                                                          | **Value**                                                                                                                                                          |
|-----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| IRI                                                                   | `bore:hasStatus`                                                                                                                                                   |
| [Name](https://schema.org/name "schema:name")                         | has status                                                                                                                                                         |
| [Description](https://schema.org/description "schema:description")    | The current state of a Bore within its lifecycle from proposed through operational through to abandoned                                                            |
| [Domain](http://www.w3.org/2000/01/rdf-schema#domain "rdfs:domain")   | [Bore](#bore)                                                                                                                                                      |
| [Range](http://www.w3.org/2000/01/rdf-schema#range "rdfs:range")      | A [Concept](https://www.w3.org/TR/skos-reference/#concepts "skos:Concept") from the [_Borehole Status_ vocabulary](https://linked.data.gov.au/def/borehole-status) |
| [Example](https://www.w3.org/TR/skos-reference/#notes "skos:example") | See example for [Bore](#bore)                                                                                                                                      |

#### has vertical reference
<a id="hasVerticalReference"></a>

| **Property**                                                          | **Value**                                                                                                                                                                                            |
|-----------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| IRI                                                                   | `bore:hasVerticalReference`                                                                                                                                                                          |
| [Name](https://schema.org/name "schema:name")                         | has vertical reference                                                                                                                                                                               |
| [Range](http://www.w3.org/2000/01/rdf-schema#range "rdfs:range")      | A `skos:Concept` from the [_Depth Reference_ vocabulary](#vocabularies)                                                                                                                              |
| [Description](https://schema.org/description "schema:description")    | The point or level from which heights and depths are measured and referenced to for an entity or activity                                                                                            |
| [Domain](http://www.w3.org/2000/01/rdf-schema#domain "rdfs:domain")   | [Bore](#bore)                                                                                                                                                                                        |
| [Range](http://www.w3.org/2000/01/rdf-schema#range "rdfs:range")      | A [Concept](https://www.w3.org/TR/skos-reference/#concepts "skos:Concept") from the [_Vertical/depth reference systems_ vocabulary](https://linked.data.gov.au/def/vertical-depth-reference-systems) |
| [Example](https://www.w3.org/TR/skos-reference/#notes "skos:example") | See example for [Bore](#bore)                                                                                                                                                                        |

## Schema

The machine-readable schema for this model is the OWL ontology available at the persistent web location given above, but you need to ask for RDF, e.g.

* <https://linked.data.gov.au/def/bore.ttl>

The same content is available in the `bores.ttl` file in this Supermodel's repository, `rdf > components > bores.ttl`.

## Validators

To prove that data conforms to this Model, it must be validated. Since all the expected data for this Model is RDF data, [SHACL](https://www.w3.org/TR/shacl/) validation may be used. SHACL is a constraints language providing machine-executable rul formulation for RDF.

This Model presents its own validator which only includes tests for the rules specific to this profile and not those of the things this Model is dependent on. However, a compounded validator is also given below which includes this Model’s validator and all the dependent ones.

The validator for this Model's rules is available in machine-readable form here:

* <https://linked.data.gov.au/def/borehole/validator>

The individual rules tested for by the validator are given in the next subsection.

The compounded validator that includes all the rules within this profile's validator and all those from Standards that this Model is dependent on is available in machine-readable format here:

* <https://linked.data.gov.au/def/borehole/validator-compounded>

Technical specification of the validation tool and help on how to perform automated validation are given in the [Validation Tools](#tools) subsection below.

### Rules

These are the rules checked for by this profile's validator. They are referenced by identifier in the machine-readable validator above so that validation messages are able to be linked to these rules.

### Tools

Coming...

## Vocabularies

This section lists the vocabularies that the Bores Model indicates for use. Some of these vocabularies are defined elsewhere - by other organisations and within standards - so this listing also indicates how each is managed.

| **Vocabulary**                                                                                                                                                                                                                                                                                                                                                       | **Model access point**                          | **Managing Organisation**                                                                                                       |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------|
| [Borehole drilling method (of WA)](https://linked.data.gov.au/def/borehole-drilling-method-western-australia)<br /><br />extension of [GSQ's Borehole Drilling Method](linked.data.gov.au/def/borehole-drilling-method) which extends [CGI's Borehole Drilling Method](https://resource.geosciml.org/classifierscheme/cgi/2016.01/boreholedrillingmethod) vocabulary | [has drilling method](#hasDrillingMethod)       | [Geological Survey of WA](https://linked.data.gov.au/org/gswa)                                                                  |
| [Borehole Design](https://linked.data.gov.au/def/borehole-design)                                                                                                                                                                                                                                                                                                    | [has inclination](#hasInclination)              | [Geological Survey of Queensland](https://linked.data.gov.au/org/gsq)                                                           |                                        |
| [Borehole start point setting](https://linked.data.gov.au/def/borehole-start-point-setting)                                                                                                                                                                                                                                                                          | [has origin setting](#hasOriginSetting)         | [Geological Survey of WA](https://linked.data.gov.au/org/gswa)                                                                  |
| [Borehole Purpose](https://linked.data.gov.au/def/borehole-purpose)                                                                                                                                                                                                                                                                                                  | [has purpose](#hasPurpose)                      | [Geological Survey of Queensland](https://linked.data.gov.au/org/gsq)                                                           |
| [Borehole Status](https://github.com/Kurrawong/gswa-vocabs/blob/main/vocabularies/borehole-statuses.ttl)                                                                                                                                                                                                                                                             | [has status](#hasStatus)                        | [Geological Survey of Queensland](https://linked.data.gov.au/org/gsq), on behalf of [GGIC](https://www.geoscience.gov.au/about) |
| [Vertical/depth reference systems](http://linked.data.gov.au/def/vertical-depth-reference-systems)<br /><br />related to [GSQ's Depth Rference](http://linked.data.gov.au/def/depth-reference) vocabulary                                                                                                                                                            | [has vertical reference](#hasVerticalReference) | [Geological Survey of WA](https://linked.data.gov.au/org/gswa)                                                                  |

GSWA _Borehole_ vocabularies so far not used:

* Borehole Geometry
* [Borehole configuration ](https://linked.data.gov.au/def/borehole-configuration)

## Code Repository

While a copy of all Bores Model resources are contained within the repository for the GSWA Supermodel, the home location of this profile is:

* <https://github.com/geological-survey-of-queensland/gsq-borehole-profile/>
