# p419dcatservices

## Axioms

1. publishing schema.org should be easy (Guha et al)
2. the difficult work of should be the job of the harvester (Guha et al)
3. primary audience for schema.org markup is harvesters
4. the common denominator across search interfaces of most harvesters is a single text box (for harvester-specific DSL queries)
5. a typical schema.org harvester should not be expected to understand other vocabularies outside of schema.org

## Analysis of Axioms

1. schema.org for Data Services should help harvesters find and understand how to present these services _as a search result_
2. for deeper integrations from harvesters, schema.org for Data Services should help harvesters _pass along single text box query_ to the service
3. to support pass thru service calls for [schema.org] class-specific searches (such as the Dataset class), the schema.org markup describing services must express:
    1. _the result set is specific to the schema.org class_ being searched (i.e. Dataset objects are being returned as search results from executing a service call)
    2. the response is formatted as _parseable schema.org_ (JSON-LD or HTML response, to support RDFa, microformats, etc.)

## Issues

| Issue |
| ----- |
| [What is the schema.org model for offering Data Services and Continuous Feeds?](https://github.com/earthcubearchitecture-project418/p419dcatservices/issues/3) |
| [Can we use Wikidata for canonical data service types?](https://github.com/earthcubearchitecture-project418/p419dcatservices/issues/2) |

## References

* [DCAT Version 2](https://w3c.github.io/dxwg/dcat/) (https://w3c.github.io/dxwg/dcat/)
* [Machine Readable Web APIs with Schema.org Action Annotations](https://doi.org/10.1016/j.procs.2018.09.025) (https://doi.org/10.1016/j.procs.2018.09.025)
