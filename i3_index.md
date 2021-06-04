# I3 Data Index Outline and Plan

A Github repository for the project is available [here](https://github.com/Innovation-Information-Initiative/i3-data-submission-wizard). Ongoing design documentation is located [here](https://www.figma.com/file/eOsZ0x1InqozLaCuKtxOXj/I3-Innovation-Data-Portal?node-id=0%3A1)

## Components

* Data submission wizard tool
	* hosted web interface (React Typescript)
	* command line interface (?node?)
* Server that hosts and serves index data (+ potentially an API) (SQLite + NodeJS)
* GitHub 'Flat Data' versioned index that reads regularly from the above server, and hosts annotations, issues and community discussion (Github Actions)
* Front end(s), that allow the index to be searched and queried (TBD, GH Flat Data provides an inspectable version for now)
* External servers (Dataverse, Zenodo) that host datasets

## Submitting Dataset URLs

Datasets are submitted through a structured form. Any submission should be acceptable, but it should be made *as convenient as possible to submit high-quality data*. Where possible, it's key to minimise requiring someone to replicate information already available at the source -> e.g. for Dataverse or Zenodo URLs, most citation information can be requested and the form pre-populated, with the option to edit or refine information before submitting.

### Conflicts and Edits

The data structure should take into account the possibility for multiple conflicting assertions about a dataset. When submitting a unique URL that matches an existing entry in the database, the contents of that entry should be displayed, with the option to add to, or edit, the information, or submit an entirely new record (accounting for the possibility of multiple datasets housed on a single webpage). Entries made in this way will be timestamped + tagged with the provenance of the data (e.g. human- or machine-generated).

### Entity Reconciliation

One important feature is the ability to reconcile columns of the dataset to named entities. In an ideal world, for the I3, this means both naming the entities themselves, and the format of the data -- something crucial for, for example, being able to immediately determine transformations required between different patent ids. OpenRefine's Entity Reconciliation API allows some support for [type reconciliation](https://github.com/OpenRefine/OpenRefine/issues/1547), though this is still under development.

As a first pass, matching named entities to e.g. the WIPO Patents Namespace, or a community-generated glossary (for key data where conventions are different) would inform the development of a reconciliation endpoint. A google sheet containing the namespaces of various projects from both within and outside of the community may be found [here](https://docs.google.com/spreadsheets/d/1pQZKYfUBCLUsJSysTlQaEi5GMzIRjaRYmmRdNVrTOac/edit#gid=1191797199).

### Annotation

One easy answer for handling annotation is to use the versioned git file (which will also include issues etc) to annotate changes to the repository. Given that the 'front end' initially will be the repository itself, this gives the most immediate way to develop a rich forum around the dataset. How this information gets represented (or not) in an eventual index is an open question, but in theory it should be possible to use the GitHub API to do this fairly easily.

## Development Plan

1. First-pass wizard tool that scrapes metadata from submitted Dataverse and Zenodo URLs
2. queriable SQLite endpoint + corresponding git flat data repository
3. CLI / bulk submission tools to populate repository
4. Development of entity reconciliation API (could prioritise this over bulk submission, depending)
5. Integrating more complex submission patterns (entity reconciliation, schema diagrams) as an optional step
6. Development of metrics (data-citations + linkages) based on index
7. Development of front end browser/search based on metrics (these 2 could happen in parallel)

## Loose Ends

### Submitting Datasets using a Submission Wizard

This is a little more tricky, as currently Dataverse does not support OAuth (+ as far as I can tell from the docs, neither does Zenodo), requiring a data submitter to locate their own API key in order to post a dataset as themselves, or to have a dedicated I3 account that people may use to submit data on their behalf (e.g. through a wizard tool).

This might be confusing, and having authentication to a single account might also cause issues later on with maintenance/updating datasets. I think this is a feature to shelve for now, but perhaps feature requesting OAuth to allow people to make external wizard tools.

