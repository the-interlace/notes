# I3 index workflows: data sources and metadata extraction

The overarching goal of the workflow is to minimise as much redundant effort as possible, instead either focussing attention on important annotation tasks (such as linking datasets together), innovation-specific metadata (e.g. timeframes), or to enable bulk submission of useful information linked to URLs, with little to no oversight.

This process depends on metadata extraction from the location of external datasets. The goal is to balance the tradeoff of generality, while extracting the most information about a source to prevent redundancy. This system should be easily extensible, with the lowest-hanging fruit (e.g. sources with easily accessible and standard-format metadata) comprising the first modules.

To evaluate the sources to optimise for, I made a count of dataset sources currently in the I3 dataset index (some entries omitted as duplicates/subsets of a single source, e.g. multiple lens sub-sets):

* dataverse 8
* zenodo 5
* BigQuery 3
* personal/dedicated website 9
* university library 4
* dedicated platform (e.g. Lens, PatentsView) 8

<img width="574" alt="Screenshot 2021-06-28 at 13 30 05" src="https://user-images.githubusercontent.com/16444898/123645236-12258780-d81e-11eb-9b35-add5e4537cd1.png">

### Standardised Citation Metadata

Out of these sources, Dataverse and Zenodo, and almost all university libraries, mint a DOI and associated citation metadata which is available through the URL -- either via the APIs, or through citation-extraction tools such as Zotero's [translation server](https://github.com/zotero/translation-server).

### Metadata APIs

Separately, Dataverse and Zenodo also run their own APIs. The structures of the responses are more specific to each platform, though they contain rich information worth extracting, such as details of dataset schemas and filetypes. Without an immediate space constraint, it might be best to simply extract all of this available information into a table, rather than seeking to change the source structure too much, with the potential for adding to the schema later on.

BigQuery datasets are not legible to Zotero's translation server (a query just cites 'Google Cloud Platform' as a webpage), but the platform has a fairly rich [metadata API](https://cloud.google.com/bigquery/docs/dataset-metadata) which can be used to extract most of the information required.

### Platforms + Personal websites

Dedicated platforms are a bit trickier, as they tend not to behave like single resource, requiring manual information entry in most cases. While these comprise a large proportion of the resources in the sheet, however, I believe this might not be representative of the wider landscape: due to their size common usage, they're more likely to be reported in a sheet like this.

Personal websites present the biggest issue, with services like the translation server extracting potentially misleading, and with multiple resources hosted on the same URL. These datasets also dominate the list. This problem won't be solved overnight, but it's a good idea to flag often-used datasets that get accessed in this way -- potential to find a better place for them. Potential future solutions could also involve some generic web scraping to get basic information. Zotero also lists some [scraping tools](https://www.zotero.org/support/dev/translators/framework) alongside the translation server that would be a good starting point.

## Workflow Description

The current plan is to cascade metadata retrieval in a series of requests, prioritising the information with the most predictable structure (to determine which calls to apply), to avoid e.g. reliance on URL strings to determine provenance (e.g. `relianceonscience.org` *looks* like a personal website address, but it's actually a Zenodo record that can also be reached via a URI). Zenodo's translation server returns both the PID (if one found), and the catalog storing the record, standardising the result. I'd like to try and make this as modular as possible -- especially thinking in the context of 'pipeline' blocks for collector, thinking about schema inputs/outputs at each stage.





