# Beacon schema v2

Current version is Draft 4. Note that Beacon v2 is still [under development](https://github.com/ga4gh-beacon/beacon-v2-Models) and needs to be approved by the [GA4GH](https://www.ga4gh.org/).

# Documentation

The core documentation can be found in this [Read The Docs](https://beacon-schema-2.readthedocs.io/en/latest).

The documentation in this README is developed for contents creators of the beacon v2 model. 

# Scope and Purpose

With growing interest from the community in the implementation of the Beacon protocol into resources and workflows, the next major release 2.0 will introduce new features which were considered important by the community: Queries by type: The Beacon will define different sets of attributes for requests and responses depending on the type of query; e.g. a specific request and response to return variants within a region in a chromosome (wildcard/region queries) or to get a list of samples related to a phenotype, provided the required authentication or authorization.

Filters: The next major version of Beacon will include a feature to filter the matched variants by additional conditions on e.g. sample specific or technical information (e.g., associated phenotypes, assay type). Here the utilization of ontologies will be encouraged, with alternative use of custom vocabularies for local applications. Schema versions: Given that new query types will return differing responses (e.g., variant annotations, pointers to data delivery protocols), a mechanism will be implemented to reference internal or external data schemas that describe the content of the Beacon response (e.g., returning variant information using "GA4GH Variant Representation v1"). Access levels: Beacon administrators will be able to specify the level of access (public, registered or controlled) for each field in the Beacon response and even refine this definition by dataset, if these diverge from the default values. This is applicable also to the query types supported (genomic variants, sample lists, etc...).


# Usage

The Beacon v2 Model is defined using [JSON](http://json-schema.org) schemas.

The latest JSON schemas can be found [here](https://github.com/ga4gh-beacon/beacon-v2-Models).

Every time that this repository is updated, all the contents from [docs/](https://github.com/mrueda/beacon-schema-2/tree/main/docs) are also automatically updated in the [Read The Docs](https://beacon-schema-2.readthedocs.io/en/latest) documentation. This addresses the issue of having multiples copies of the same document (e.g. Word, Latex, YAML) spread around the web.

The [Read The Docs](https://beacon-schema-2.readthedocs.io/en/latest) documentation is created with [MkDocs](https://www.mkdocs.org/) that works with Markdown format. Thus, we enforce creators to modify directly the Markdown files. Note that there exist tools such as [Pandoc](https://pandoc.org/) that allow transforming standard text formats to Markdown. Pandoc, however, does not transform YAML/JSON to Markdown.

# Updating Beacon v2 Models JSON-schemas

We created a tool that enables transforming Beacon v2 Model schemas (JSON) to Markdown tables.

See instructions [here](https://github.com/mrueda/beacon-schema-2/tree/main/bin).

# Versioning

This repository uses semantic versioning. See <https://semver.org> for
details.
