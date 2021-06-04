# writeup: data collaboratives in practice

On March 4th, we held a session at CSV conference to convene data practitioners, and discuss experiences and challenges of cultivating open data collaboratives. The session was structured around 4 questions, discussed by participants in groups arranged by specialism. In all, 2 main groups were represented: toolmakers, and data sharers + maintainers, without sufficient attendees to fill either of the other 2 categories: catalogers and analysts.

We introduced the session within the context of the I3, and social science data sharing, with attendees coming from a range of different data-contexts, predominantly urban data and governance, and life sciences research.

The collaboratively edited slides from this session are available [here](https://docs.google.com/presentation/d/1TY54_OWHvVYef746uDlwJICPKWyYCS87DxlkeDi_keY/edit#slide=id.gd7273c5a65_0_16), and attendees list is [here](https://docs.google.com/document/d/1p8lANjxfnSJfnarEZSZbqY30vVw5N4OB0_Z3S-_K-io/edit#). Below is a summary of the responses to different questions, with dominant concerns highlighted.

## 1. Why is collaborative data design important to you? Where is it essential to the landscape of your research or field?

* non-collaborative data design reinforces existing disparities -- important to think about not just inter-institutional levels but also international collaboration
* creating datasets is labour intensive, and it's important to pool resources
* challenging for smaller institutions and researchers to use and/or steward large datasets
* in many fields there is simply *too much data* to manage repositories on an individual basis
* some contexts (e.g. government data) place a focus on using existing infrastructure

## 2. What tools do you use for coordinating, curating, and mapping data?

* information standards very important for co-ordination. e.g. [Biodiversity information standards](https://www.tdwg.org/)
* GitHub is a great tool, both for convening communities, working openly, and managing issues ([ESS-DIVE](https://github.com/ess-dive-community) has a nice example of this)
* collaborative tools like Zoom and google docs -- lo-fi but very useful and accessible across different disciplines
* [wikidata](https://query.wikidata.org/) allows for shared property namespaces, while the [entity schema](https://www.wikidata.org/wiki/Wikidata:WikiProject_Schemas) namespace is underused
* domain-specific tools like [NY Open Data Portal](https://data.ny.gov/) and [Synapse](https://www.synapse.org/) can be really useful in particular contexts

## 3. What tools do you long for? What features do you want curation & publishing tools to prioritize?

* general challenge of browsing/downloading small parts of large datasets
* schema alignment and dataset-linking tools
* tools for managing data distributed across multiple locations
* metadata and dataset annotation
* feature request mechanisms that don't require GitHub literacy
* tools for context and understanding the history of a dataset

## 4. What data-context do you wish others shared? Where have you had success in changing data-sharing practices?

* maintenance, and funding for maintenance
* having a detailed context and audit history for records is important but rately complete (e.g. accurate labelling for ML data)
* API limitations can be a big barrier to projects over a certain size
* licensing and privacy are major barriers to both code and data sharing. this is a particular problem for government departments
* there is no legal framework for making data collaboratives, outside of data privacy agreements
* no dedicated neutral space for incomplete / 'almost-public' projects that would otherwise never make it out of an institution

## 5. How do you find and share scripts that you’re using? Do you use a shared repository?

* In some contexts, it could be more helpful to focus on developing high-quality 'products' rather than just scripts
* There's a lot of pressure on whoever gets tasked with coordinating the sharing of code
* It takes time to develop Github management and policies

## 6. How do you track pipelines? Do you name/share  transformations that you apply?

* Again, GitHub is a good tool for this
* Keeping things simple and consistent is important
* Looking at [Dagster](https://www.dagster.io/) for pipeline observability

## conclusions

Open data collaboratives benefit everyone, even larger institutions that have the resources to steward big datasets, by raising the standards of data across the board and allowing for cumulative and incremental work. However, while high-quality free, open and accessible tooling exists to collaborate on code, text and flatfile data, the same infrastructure does not exist for larger datasets, and data-processing pipelines.

In creating infrastructure to make data more accessible, there's a place for high-quality domain specific tools (some of which, like Synapse, are already widely used), as well as more general tools that enable pooling, merging and transformation of generic datasets. The GitHub model is extremely popular and flexible throughout the community, in part due to being a tool that is always intended to be used collaboratively.

The need for fast data-accessibility is also reflected in GitHub's latest [write-up](https://octo.github.com/projects/flat-data) on 'Flat Data', which focusses on bringing 'working data' into repositories directly, and is based on features of Simon Willison's [Datasette](https://simonwillison.net/2020/Oct/9/git-scraping/) project. In both cases, they emphasise the importantce of having small, usable and lightweight datasets that can be pulled quickly into a project without needing a separate server.

Other standout points were the amount of administrative work (and stress!) that goes into agreeing on sharing standards and practices, at any scale, and for both data and code. Like a lot of maintenance work, it's underfunded, and goes unnoticed *especially* when it is done well. Hiring was a common issue, with small teams struggling to maintain documentation + open data alongside their other work.

