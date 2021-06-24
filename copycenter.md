# Background
Most works that are in the public domain are not 100% confirmed to be so -- due to ambiguities in (c) law
before copyright started to be extended, effectively indefinitely.

Most published works that are not in the public domain are orphaned or out of print: there is no active mechanism for getting a copy,
or for having reuse approved by the rightsholder.

One step towards fixing this is publishing a catalog of the best publicly-known estimate of current (c) terms, and clusters of related works,
and providing a way for any curator or organization to update that catalog.  

## Distributed solutions

We need a dweb approach to cataloging existence, theoretical accessibility, and actual accessibility, for published works. 
This would provide a single referent for citations that can be shared across the web, 
and that record can highlight all of the ways to access the underlying source. 

Important bits of such a catalog:
* Estimates of (c) expiry, estimates of fair use options, an index of known digital copies (whether or not they are world-readable).
* A published resource listing the above, that can be referenced when adding a single data point to Wikidata. 
* * (in contrast: see NYPL's public db of OCR'ed and partially-cleaned records : it is a monolithic repo, hard to reference)
* Processes that generate reasonable estimates of accessibility, between "complex, we don't know" and "we spent 10 hrs on (c) analysis".  
* Provenance (something like [fatcat](https://fatcat.wiki/release/rkaga44egrb4fdtbgajpzcfx5q) w/ confidence scores)
* A framework for anyone who wants to speed up the work to claim a chunk and do so, or see what chunks are in progress. 

# See also
*  case.law does a good job at a centrally managed, definitive record.    


# Layers and components
* Copyright status + expiry database: For each work, when is it out of (c), what alternate versions are out of (c) soonest, what types of fair use are available, who to contact for reuse?
* Archival status + digitization: How has a work been digitized, how redundantly is this archived, how to contact the archives, how to mirror this?
* Derivation, bulk analysis, metadata: How can scripts be run over copies of the work, what associated data exists?
* Annotation: What annotation exists, how can new notes be added?

I'm looking for sources.  Currently
 - NYPL has a small grant to digitize books records at $8/pg (no idea if/how they plan to extend to all others; but it's clear how parallelizing could happen). 
 - JMO's work on serials has a wikidata fellow (no idea how well this is parallelizable)
