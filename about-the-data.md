# About the data

## License

All OpenAlex data is made available under the [CC0 license](https://creativecommons.org/publicdomain/zero/1.0/). That means it's in the public domain, and free to use in any way you like. We appreciate attribution where it's convenient, but it's not at all necessary.

## Sources

OpenAlex is not doing this alone! Rather, we're aggregating and standardizing data from a whole bunch of other great projects, like a river fed by many tributaries. Our two most important data sources are [MAG](https://aka.ms/msracad) and [Crossref.](https://www.crossref.org) Other key sources include:

* [ORCID](https://orcid.org)
* [ROR](https://ror.org)
* [DOAJ](https://doaj.org)
* [Unpaywall](https://unpaywall.org)
* [Pubmed](https://pubmed.ncbi.nlm.nih.gov)
* [Pubmed Central](https://www.ncbi.nlm.nih.gov/pmc/)
* [The ISSN International Centre](https://www.issn.org)
* Web crawls
* Subject-area and institutional repositories from [arXiv](https://arxiv.org) to [Zenodo](https://zenodo.org) and everywhere in between

## Known issues

### Some strings not yet matched to entities.

We've got a lot of strings floating around for venues and institutions that haven't actually been linked to a [`Venue`](about-the-data/venue.md) or [`Institution`](about-the-data/institution.md) entity in the database. These show up as objects missing an `id` property, in these fields:

* [HostVenue](https://docs.openalex.org/entity-objects/work#the-hostvenue-object) objects (found in the [`Work.host_venue`](https://docs.openalex.org/entity-objects/work#host\_venue) and [`Work.alternate_host_venues`](https://docs.openalex.org/entity-objects/work#alternate\_host\_venues) properties).
* [`Dehydrated Institution`](https://docs.openalex.org/entity-objects/institution#the-dehydratedinstitution-object) `` objects found as part of the [`Authorships`](https://docs.openalex.org/entity-objects/work#the-authorship-object) objects in the [`Work.authorships property`](https://docs.openalex.org/entity-objects/work#authorships).

These ID-less objects are tricky because they can't do most of the things a regular entity can. They're just a suitcase for a name, right now.  They are inherited from MAG, and we plan to fix them. Over the next month or so, we'll be processing all these stub entities, clustering them together, and minting tens of millions of new entities from them.

### Standard format snapshot missing some strings.&#x20;

The Standard format is currently missing some strings that aren't associated with Venues or Institutions -- these stub entities described in the issue "Some strings not yet matched to entities" above are displayed in the API but are missing from the current snapshot. The snapshot will be updated in the next week to fix this inconsistency (and then, as described above, these sub entities will be expanded in the next month or so).

### Standard format snapshot doesn't include the inverted abstract indices.&#x20;

Sorry about that!  They got missed on the initial release.  We'll be adding them in in the next few weeks.

### Misspelled associated\_insitutions

We misspelled associated\_institutions key in the Institutions entity as associated\_insitutions. It is currently fixed in some places but not others.  Sorry about that! Will fix everywhere soon.

### MAG format snapshot has a few duplicate rows and escaping issues.

We're continuing to improve our processes to make sure the data in the MAG format is clean and easy to pull in to a relational database. This current release still has a few issues, but we'll try to fix these by the next release.

## Reporting bugs

OpenAlex is still very new, and so you'll probably encounter some bugs as you look through the data. Please report these by emailing us at **team@ourresearch.org.**
