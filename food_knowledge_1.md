# [fanfic] Decentralised Recipe Indexing

## or: *"let 10,000 recipe blogs bloom"*

I've been accumulating notes on different kinds of food knowledge for a while, but made the mistake of trying to write everything into a single piece that was becoming far too involved to publish. I've decided to break things down into shorter posts, articulating different shapes + opinions of ways to represent knowledge about food, as a proxy for articulating a kind of \~vibe\~ for what a 'decentralised knowledge'.

(as previously discussed) food knowledge has a lot of qualities that would make a compelling underlay demo:
* highly subjective and contextual (+ broadly accepted as such)
* entities related to one another across multiple dimensions -> a general notion of 'food-space'
* inherently decentralised context (everybody's 'food space' is different)
* provenance of assertions is complex and meaningful
* attempts to index and centralise food knowledge can be essentialising and extractive when they lose information or are taken out of context
* our ability to query food information online is currently funneled through mediators like Google/Apple, which add a layer of corporate monetisation and opacity to this

For now, I'm thinking primarily about the last 2 points, in the context of tools for recipe-indexing, and creating improved tools for recipe search. I won't go into recipe/ingredient deconstruction here: in this instance, a recipe is a little blob of food knowledge, written by an author, that exists at the end of a URL and has a bunch of different metadata associated with it. I'll follow on later with some different ideas about recipes/dishes/ingredients/information.

## navigating the internet of recipes

How do we currently encounter recipes online?

* recipe blogs, typically maintained by 1 or 2 people, that span a gradient of size, structure and context
	* at one end you have mega-blogs like [Maangchi](https://www.maangchi.com/) and [The Woks of Life](https://thewoksoflife.com/), which are highly structured
	* at the other, small websites written in HTML, maybe not even using a CMS
* recipe websites stewarded by larger single entities
	* newspaper recipe archives like The New York Times, Guardian, BBC
	* web-oriented 'food media' sites like The Spruce Eats and BonAppetit
	* multi-contributor sites like [Archana's Kitchen](https://www.archanaskitchen.com/index.php?option=com_akrecipes&lang=en&limit=24&limitstart=24&view=frontpage), which sit somewhere between blogs and larger platforms (having grown from the former into the latter)
* hi-res, unstructured data mediated by social media, e.g. youtube/tiktok (to find these recipes you're normally searching *within* the platform, and more often than not navigating from existing recommendations made by the platform itself))
* large crowdsourced websites like Cookpad (which is federated by region) are both googlable, but are also internally searched
* there are large aggregator sites and associated apps (Yummly, Paprika), which scrape recipes from smaller sites and monetise them by rendering them in a standard format + adding organisation

At present, most searches for recipes using a search engine like Google will prioritise recipes from more centralised, indexed sources as a proxy for trust in the quality of the recipe -- and there's little to no transparency as to *why* a particular recipe was prioritised in search results. This can result in larger, more centralised sites becoming a de facto authority on all food, despite doing a fairly [poor job](http://www.intersectionalanalyst.com/intersectional-analyst/2017/1/7/who-gets-to-be-an-authority-on-ethnic-cuisines) of representation. I think this is a good case where the answer isn't just 'make one big search engine that's better' (in the sense that a centralised onotology will always be exclusionary and limited), but instead, allow people to make their own structures for recipe representation.

## alternative search engines

What would alternative search engines for recipes look like? Sam Lavigne's project [Other Orders](https://lav.io/projects/other-orders/) does a version of this for Twitter -- using the API to rewrite recommendation algorithms, allowing users to see their twitter feed ordered according to options such as 'alphabetical', 'crudely understood marxism', 'gothness', etc. In the context of food, perhaps one could define recipe searches by their form or their context, or the other websites they link out to, similarity to other recipes.

One thing that's really key to designing these kinds of tools is that they should integrate with the systems that are already to hand when people share recipes. At present, one main form of online recipe-indexing is managed through Schema.org's [Recipe](https://schema.org/Recipe) type, which has the properties of being a creative work, and a set of instructions, can have a list of string [Ingredients](https://schema.org/recipeIngredient), and can belong to a category, or a particular cuisine. A large number of recipe blogs from the past 7 years or so that use Wordpress (currently a pretty dominant form, especially for the larger blogs), use a plugin called [WP Recipe Maker](https://wordpress.org/plugins/wp-recipe-maker/), which automatically renders the JSON-LD required to fit into this format.

One of the real joys of reading older recipe blogs is that the form is quite undefined -- people have their own idea of what a recipe structure should be, what a recipe should look like. One could imagine making a Wordpress extension that posts to a Collector API, where you decide what schema for 'recipe' you'd like to use (or can even build your own?). 