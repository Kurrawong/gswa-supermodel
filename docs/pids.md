# Persistent Identifiers

## Overview

This document provide a policy for the creation of Persistent Identifiers (PIDs) for the following cases:

1. **high-level definitional object**
    * models within [GSWA's Supermodel](index.md)
    * GSWA vocabularies
    * stand-alone collections of Concepts
2. **low-level definitional object**
    * Classes, Concepts, Predicates & Datatypes defined within high-level definitional objects
3. **high-level data object**
    * datasets of content created in accordance with this Supermodel's models
4. **low-level data object**
    * instances of classes within high-level data object


## IRIs

The PIDs used by the GSWA Supermodel are all [Internationalized Resource Identifiers (IRIs)](https://en.wikipedia.org/wiki/Internationalized_Resource_Identifier) which are web page URLs that:

* can be used in data to identify things without necessarily resolving to a web page
* can be managed with domain name ownership
* allow for a specified range of characters
    * e.g. non-English alphabets
* have validation rules
    * similar to web address (URL) rules
    * e.g. no spaces

The cases of object above _MUST_ be identified with IRI PIDs, so where something may have another kind of PID, perhaps an internal database ID, this must be treated as secondary. See [Alternate Identifiers](pids.md#alternate-identifiers) below.

IRIs always consist of a:

* _scheme_
    * technical system, usually "https" 
* _authority_
    * the owned Domain name, e.g. linked.data.gov.au/
* _path_
    * things after the authority, separated by '/'
    * e.g. dataset/x
* _ID_
    * individual object identifier - last part of the path
    * from above, 'x'


## Namespaces

The namespace, or basis, to be used for all cases above is the _authority_:

`https://linked.data.gov.au/`

This namespace is managed by the [Australian Government Linked Data Working Group](https://linked.data.gov.au) on behalf of all Australian governments and is intended to provide persistent identifiers for all Australian government-relevant [Linked Data](https://www.w3.org/wiki/LinkedData). GSWA has registered identifiers for the cases above and is required to keep doing so for new items. See the [Registration](pids.md#registration) section below for more details. 


## Reusing Existing IRIs

If an object that GSWA wishes to identify already has a functioning IRI, it _SHOULD_ be reused directly, wherever possible. 

Some examples:

* Concepts from existing vocabularies
    * "Jurassic" from the [International Commission on Stratigraphy](https://stratigraphy.org/)'s [RDF version of the Chart](https://stratigraphy.org/ICSchart/data/ChronostratChart2023-09.ttl): `http://resource.geosciml.org/classifier/ics/ischart/Jurassic`
        * this is used in [GSWA's local copy of the Chart](https://vocabulary.gswa.kurrawong.ai/v/vocab/ics:ischart/schrt:Jurassic)
* Objects in existing Linked Data datasets
    * [Wheat Belt - South Statistical Area 3](https://linked.data.gov.au/dataset/asgsed3/SA3/50903) from the [Australian Statistical Geography Standard Linked Data API](https://asgs.linked.fsdf.org.au/dataset/asgsed3): `https://linked.data.gov.au/dataset/asgsed3/SA3/50903`
        * GSWA could indicate that administrative areas are within this region

GSWA _SHOULD NOT_ reuse an existing IRI only when it is know that the IRI does not function.


## Alternate Identifiers

The canonical form of model content and instance data created according to this Supermodel is [RDF](https://en.wikipedia.org/wiki/Resource_Description_Framework) and RDf only uses IRIs for element identification.

If a real-world or data object has another form of identifier that should be preserved, such as a [DOI](https://en.wikipedia.org/wiki/Digital_object_identifier), [IGSN](https://en.wikipedia.org/wiki/International_Generic_Sample_Number), internal database ID, lookuptable key, chemical element symbol, mineral code etc., it _MUST_ be done so linking to IRI PID.

### Creating IRIs for things with Alternate Identifiers

IRIs for all objects, whether they have alternate identifiers or not, should be done in the same general way - in accordance with this document. This policy leaves open the logic used to generate the `ID` part of an `IRI` so it could be generated from an alternate identifier. Some made-up examples:

* Vocabulary term of "Gold" as a Critical Mineral using the commonly known chemical element symbol `Au` for the IRI ID
    * `https://linked.data.gov.au/def/critical-minerals/au`
* Instance of a Rock Sample with an internal Sample Number of S1234 in Dataset X
    * `https://linked.data.gov.au/dataset/x/sample/s1234`

### Linking the Alternate Identifier(s) to the IRI

Within RDF realisations of definitional data - models and vocabularies - and instance data - datasets containing objects, links between alternate, non-IRI, identifiers and IRIs can be linked with the `[schema:identifier](https://schema.org/identifier)` predicate and a custom datatype like this:

```turtle
<https://linked.data.gov.au/dataset/x/sample/s1234>
    a sosa:Sample ;
    schema:name "Sample 1234" ;
    # ... other predicates
    schema:identifier "S1234"^^<https://linked.data.gov.au/def/geosamples/datatype/gswa-sample-id> ;
.
```

In the example code above, a dummy sample with IRI `https://linked.data.gov.au/dataset/x/sample/s1234` is linked to its "GSWA Sample ID" with the predicate `schema:identifier` which indicates a value of "S1234" with a special (dummy) datatype of `https://linked.data.gov.au/def/geosamples/datatype/gswa-sample-id`. This datatype describes the identifier regime, perhaps like this:

```turtle
<https://linked.data.gov.au/def/geosamples/datatype/gswa-sample-id>
    a rdfs:Datatype ;
    schema:name "GSWA's Sample ID" ;
    schema:description "IDs for physical samples issued by GSWA's XYZ database and controlled by the Primary Key of the [Samples] table" ;
    sh:regex "^S(\d{4,6})$" ;
.
```

The description of the datatype above gives human-readable details about what the GSWA Sample ID is, where it comes from, how it is managed and who to contact about it. It also provides validation logic - the pattern indicated by "^S(\d{4,6})$" - which mandated such an ID start with the letter 'S' which is then followed by 4 to 6 digits, e.g. S1234 or S12345. Datatyle definitions need not contain such validation logic. 


### DOIs, IGSNs

[DOI](https://en.wikipedia.org/wiki/Digital_object_identifier)s & [IGSN](https://en.wikipedia.org/wiki/International_Generic_Sample_Number)s often act a lot like IRIs: they have web address form and resolve online when clicked. However, they do not deliver usable Linked Data information, only web pages. For this reason, they are considered non-IRIs and should be used as alternate identifiers, not IRIs to be directly reused. 

Note that while it is possible to retrieve _some_ RDF from DOIs, this is basic registry metadata and not the detailed information that a fully-functioning Linked Data IRI would deliver 

## Creating IRIs

To create an IRI, we need to consider the Case of object the IRI is for, as per the cases above in the [Overview](pids.md#overview). Knowing that, we can select the pattern from the table below.

#### Patterns per Case

| Case                                  | Pattern                                                                                                                                     | Elements                                                                                                                                                                                                                                                                  |
|---------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1. **high-level definitional object** | `https://linked.data.gov.au/def/{ID}`                                                                                                       | `{ID}` - may be anything acceptable to the [Australian Government Linked Data Working Group](https://linked.data.gov.au) which means be in accordance with their [Guidelines](https://www.linked.data.gov.au/guidelines). See [Registration](pids.md#registration) below. |
| 2. **low-level definitional object**  | `https://linked.data.gov.au/def/{ID}/{LOW-LEVEL-ID}`                                                                                        | `{ID}` - as per the requirements above <br />`{LOW-LEVEL-ID}` - distinct within scope of containing high-level object, starting upper-letter if a Class, starting lower-case letter if a Predicate                                                                        |
| 3. **high-level data object**         | `https://linked.data.gov.au/dataset/{ID}`                                                                                                   | As per Case 1                                                                                                                                                                                                                                                             |
| 4. **low-level definitional object**  | `https://linked.data.gov.au/dataset/{ID}/{LOW-LEVEL-ID}` or<br />`https://linked.data.gov.au/dataset/{ID}/{CLASS-SIGNIFIER}/{LOW-LEVEL-ID}` | As per Case 2 or use of an additional path element, `{CLASS-SIGNIFIER}`, to indicate the class of object as well as its individual ID.                                                                                                                                    |

#### Classes per Case

Specific classes of object per Case as listed above are:

| Case                                  | Classes                                                                                                                        |
|---------------------------------------|--------------------------------------------------------------------------------------------------------------------------------|
| 1. **high-level definitional object** | `owl:Ontology`<br />`skos:ConceptScheme`<br />`skos:Collection`                                                                |
| 2. **low-level definitional object**  | `owl:Class`<br />`rdfs:Property` and all forms of OWL Property<br />`skos:Concept`<br />`sh:NodeShape`<br />`sh:PropertyShape` |
| 3. **high-level data object**         | `schema:Dataset`<br />`schema:DataCatalog`                                                                                     |
| 4. **low-level definitional object**  | everything else not listed in Cases 1 - 3                                                                                      |


#### Examples

| Case                                  | Examples                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|---------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1. **high-level definitional object** | Ontology - `https://linked.data.gov.au/def/bore` - _Bore Model_<br />ConceptScheme - `https://linked.data.gov.au/def/borehole-drilling-method-western-australia` - _Borehole Drilling Method_ vocabulary                                                                                                                                                                                                                                                |
| 2. **low-level definitional object**  | Class - `https://linked.data.gov.au/def/bore/Bore` - _Bore_ class in Bore Model<br />Property - `https://linked.data.gov.au/def/bore/hadDrillingMethod` - _had drilling method_ property in Bore Model<br />Concept - `https://linked.data.gov.au/def/borehole-drilling-method-western-australia/non-rotary` - _non-rotary drilling_ concept in _Borehole Drilling Method_ vocabulary<br />NodeShape - _coming soon_<br />PropertyShape - _coming soon_ |
| 3. **high-level data object**         | Dataset - _coming soon_<br />DataCatalog - _coming soon_                                                                                                                                                                                                                                                                                                                                                                                                |
| 4. **low-level definitional object**  | _coming soon_                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| x. **Organisations**                  | `https://linked.data.gov.au/org/gswa` - GSWA within the AGLDWG Org Register                                                                                                                                                                                                                                                                                                                                                                             |

## Agents

Agents - Organisations and People - have a couple of special considerations. When they are referred to in data, they would be considered instances of a _low-level definitional object_ however two particular sources of existing IRIs for them _SHOULD_ be considered:

* Organisations
    * AGLDWG Org Register: <https://catalogue.linked.data.gov.au/organisations>
    * Australian Government organisations Linked Data IRIs 
    * reuse if exists or register if it doesn't
* People
    * ORCID: https://orcid.org/
    * personal IDs for researchers
    * reuse if the person has an ID there


## Registration

The process for registering a `linked.data.gov.au`-based PID is to request a new one from the Australian Government Linked Data Working Group via their catalogue system at <https://catalogue.linked.data.gov.au>.

The process is as follows:

1. *create* an identifier pattern in accordance with the AGLDWG [Guidelines](https://www.linked.data.gov.au/guidelines)
2. *submit* a request for the PID pattern to the AGLDWG via the [AGLDWG Catalogue](https://catalogue.linked.data.gov.au/)
    * you will need an account on that system to do this - GSWA already has members with such accounts
    * the AGLDWG will _ACCEPT_ the PID pattern if valid according to the Guidelines
    * the AGLDWG will then request a resolution target - where it is to resolve to
3. *implement* the PID in data and systems so that it may resolve to content
4. *update* the PID resolution patterns
    * either GSWA or AGLDWG staff can update the linked.data.gov.au PID patterns to resolve to resolution targets
    * if valid (resolving) the AGLDWG will mark the PID pattern _STABLE_
    * see GSWA's existing PID Patterns at the [PID Proxy Config for GSWA](https://github.com/AGLDWG/pid-proxy/blob/master/conf/linked.data.gov.au/org/gswa.conf) and the [tests for the PID Patterns](https://github.com/AGLDWG/pid-proxy/blob/master/test-suite/linked.data.gov.au/org/gswa.json)

Once _STABLE_, GSWA may allocate sub-PIDs within that registered PID however they like from the AGLDWG's point-of-view. Such allocation should follow this policy's [Sub-PIDs](#sub-pids) section.