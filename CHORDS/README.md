# NCAR EarthCube CHORDS #

URL: http://portal.chordsrt.com/

| URL | Schema.org | Notes |
| --- | ---------- | ----- |
|  http://portal.chordsrt.com/ | [ResearchProject](https://github.com/earthcubearchitecture-project418/p419dcatservices/blob/master/CHORDS/ResearchProject.jsonld) |  |
| http://portal.chordsrt.com/about/data_urls | [WebAPI](https://github.com/earthcubearchitecture-project418/p419dcatservices/blob/master/CHORDS/WebAPI.jsonld) |  |
| http://portal.chordsrt.com/instruments | [DataCatalog](https://github.com/earthcubearchitecture-project418/p419dcatservices/blob/master/CHORDS/DataCatalog.jsonld) |  |
| http://portal.chordsrt.com/sites/2 | [Place](https://github.com/earthcubearchitecture-project418/p419dcatservices/blob/master/CHORDS/Place.jsonld) | Repeatable for each site page |
| http://portal.chordsrt.com/sites |  | Could define a schema.org/Place with an array of [containsPlace](https://schema.org/containsPlace) for each Site, but not necessary (This overall Place could be the bounding box of all sites for this project and be how the `areaServed` field of teh ResearchProject is defined) |
| http://portal.chordsrt.com/instruments/1 | [DataFeed](https://github.com/earthcubearchitecture-project418/p419dcatservices/blob/master/CHORDS/DataFeed.jsonld) | Repeatable for each insturment |

## Flow ##

### Homepage - ResearchProject ###

* defines a bounding box that encapsulates all sites being served by the project
* says the project 'knows about' Streaming Data (as defined at WikiData)
* says it's sponsor is NCAR w. parent Org of UCAR
* defines its funder as EarthCube via NSF
* defines an Offer Catalog of:

1. Data Catalog of Instruments (Data Feeds)
2. Web API

### CHORDS Data URLs - WebAPI ###

* defines all non-instrument specific API endpoints (NOTE: individual instruments will add instrument-specific API endpoints as offerings of the Research Project)

### Instruments - DataCatalog ###

* defines every Instrument (DataFeed) which defines its contentLocation as the corresponding Site (Place)

### Site - Place ###

* defines the GeoCoordines of the instrument
* defines the Site Type as an additionalProperty of the Site using a DefinedTerm to contextualize what 'Atmosphere' as a Site Type means (using Wikidata for now unless there is a another, better controlled vocabulary term)
* specifies that the Site is the `subjectOf` the Instrument (DataFeed)

### Instrument - DataFeed ###

* defines the provider as the ResearchProject from the Homepage (NOTE: this is how the instrument adds new WebAPI offerings onto the ResearchProject)
* specifies this instrument is included in the DataCatalog at the Instruments listing page
* defines the `temporalCoverage` as an open-ended duration starting from the first measurement date timestamp
* defines the `spatialCoverage` as the corresponding Site
* specifies that it is `about` a Thing (Instrument) with an additionalType of `https://www.w3.org/TR/vocab-ssn/#SensingDevice` (To link in the SensorML document we specify that this Instrument is the subject of a DigitalDcoument (aka the SensorML file which has an `additionalType` for the Wikidata URI for `SensorML`)
* defines the `measurementTechnique` as the name of the instrument (Note: measurmentTechnique should propobably be fixed or extended at geoschemas.org to reference an `Instrument` type.
* defines all the `variablesMeasured` with units (code and text) and an identifier to the SensorML URI for that variable
* defines 2 data download URLs (GeoJSON and CSV) 
* defines 2 potential Actions:

1. The REST endpoint for retrieving the measurments since the last timestamp
2. The REST endpoint for retrieving all measurements within a specified start/end date timestamp. 

## NOTES ##

### Keywords & Topics of a Research Project ###

There isn't a great way yet to talk about keywords or categories that are related to something. For example, it'd be nice to specify some controlled vocabulary terms that would help search engines figure out what the research project is about. Here, we use the term `knowsAbout` to point to a controlled vocabulary term for `Streaming Data` over at WikiData. Current work being proposed here at the [schema.org Github Issue queue](https://github.com/schemaorg/schemaorg/issues/2257)

### Instrument ###

There isn't a great way to define an Instrument yet in schema.org, but some work is being done on that w/r/t IoT. Created GitHub [Issue #4](https://github.com/earthcubearchitecture-project418/p419dcatservices/issues/4)

### Using `identifier` to link a `variableMeasured` to an external ontology ###

Of all the fields on [PropertyValue](https://schema.org/PropertyValue), there isn't an obvious way to richly express a link to an external ontology class that classifies the type of variable. I use [identifier](https://schema.org/identifier) to link to another `PropertyValue`. *Question:* Should we discuss an extension property to specify this?

