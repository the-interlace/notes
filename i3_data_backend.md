# Choosing a database backend for the I3 index

goals:
* human-readable (either immediately, or through a simple transformation + not requiring download / external interface)
* persistent
* versioned
* amenable to user-friendly workflows (e.g. not requiring people to enter redundant information that can be retrieved from a URL; making it easiest to submit high-quality data)
* open-source / not proprietary
* play well w/ common formats
* ability to accept input from a variety of sources
* performant, concurrent + readily machine readable
* if multiple representations, they stay up to date w/ one another
* collaborative (+ moderatable if needed)
* annotatable

## List of possibilities considered

### GitHub Pull Requests (YAML) + automation

(based on [this project](https://github.com/awslabs/open-data-registry/)) Nice and simple, but not a format that optimises for good sharing of structured data + gets sticky as soon as you start trying to include external tools. Has the advantage of every edit being immediately annotatable + easy managing of collaboration/curation/editing. Persistent, versioned etc.

However, those features come at the cost of usability when you're getting people to submit information, as you get into annoying feedback loops mediated by pull requests, or require a lot of redundancy in the submission. Building an interface to it solves some of these issues but hard to maintain concurrency.

### simple DB + versioned copy in Github Flat Data (current choice)

This is the current version; I think it's the least 'smart' solution but SQLite + versioning with Github Flat Data.

Key drawback is that it's not a format that's readily very collaborative, other than in the instance where anyone can submit information (which should be the initial default, but adding any layer of collab. curation on top of that could be suddenly quite annoying to manage)

That said, it's probably a good place to start as SQLite very adaptible -> always possible to export to a different format further down the line.

### Terminus DB

TerminusDB is a collaborative, versioned graph database, which might be pretty ideal for this application. [TerminusHub](https://terminusdb.com/hub/) used to collaborate on projects.

I'm going to test this out as a potential basis this week -- the tests for whether this is useful or not will probably look something like:

* what is the support for annotation on a by-record basis?
* how easy is it to spin up an API endpoint around?
* would this still require an external repo for e.g. persistence?
* what's the workflow for someone directly contributing a record not mediated through an interface/API call?
* How well does this play with others' existing workflows

If the answers to these are satisfactory then this might be a great platform to use and would remove the need for a separate GH repo (though it might still be good to have one for the sake of longevity/discoverability).


