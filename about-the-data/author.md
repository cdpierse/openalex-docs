# 👩 Author

## The `Author` object

### `id`

_String:_ The OpenAlex ID for this author.

```json
id: "https://openalex.org/A2208157607"
```

### `orcid`

_String:_ The [ORCID](https://en.wikipedia.org/wiki/ORCID) for this author. ORCID global and unique ID for authors.

```json
orcid: "https://orcid.org/0000-0001-6187-6610"
```



### `display_name`

_String:_ The name of the author as a single string.

```json
display_name: "Jason Priem"
```



### `display_name_alternatives`

_List:_ Other ways that we've found this author's name displayed.

```json
display_name_alternatives: [
    "Jason R Priem"
]
```

### `works_count`

_Integer:_ The number of :page\_facing\_up: [Works](work.md) this this author has created.

```json
works_count: 38 
```

### `cited_by_count`

_Integer:_ The total number :page\_facing\_up: [Works](work.md) that cite a work this author has created.

```json
cited_by_count: 38 
```

``

### `ids`

_Object:_ All the [persistent identifiers (PIDs)](https://en.wikipedia.org/wiki/Persistent\_identifier) that we know about for this author, as `key`: `value` pairs, where `key` is the PID namespace, and `value` is the PID. IDs are expressed as URIs where possible. The [`openalex` ID](./#the-openalex-id) is the same one you'll find at [Author.id](author.md#id). All the IDs are strings except for `mag`, which is an integer.

```json
ids: {
    openalex: "https://openalex.org/A2208157607",
    orcid: "https://orcid.org/0000-0001-6187-6610",
    scopus: "http://www.scopus.com/inward/authorDetails.url?authorID=36455008000&partnerID=MN8TOARS",
    twitter: null,
    wikipedia: null,
    mag: 2208157607
},
```

### `last_known_institution`

_Object:_ This author's last known institutional affiliation. In this context "last known" means that we took all the [Works](work.md) where this author has an institutional affiliation, sorted them by publication date, and selected the most recent one.

This is an abridged [Institution](institution.md) object, and you can find more documentation on the [Institution](institution.md) page.

```json
last_known_institution: {
    id: "https://openalex.org/I114027177",
    ror: "https://ror.org/0130frc33",
    display_name: "University of North Carolina at Chapel Hill",
    country_code: "US",
    type: "education"
},
```

### `x_concepts`

{% hint style="danger" %}
The "x" in `x_concepts` is because it's experimental and subject to removal with very little warning. We plan to replace it with a custom link to the Concepts API endpoint.&#x20;
{% endhint %}

_List:_ The concepts most frequently applied to works created by this author. Each is represented as a dehydrated Concept object, with one additional attribute:

* `score` (_Float_): The strength of association between this author and the listed concept, from 0-100.

```json
x_concepts: [
    {
        id: "https://openalex.org/C41008148",
        wikidata: null,
        display_name: "Computer science",
        level: 0,
        score: 97.4
    },
    {
        id: "https://openalex.org/C17744445",
        wikidata: null,
        display_name: "Political science",
        level: 0,
        score: 78.9
    }
]
```

### `counts_by_year`

_List:_ [`Author.works_count`](author.md#works\_count) and [`Author.cited_by_count`](author.md#cited\_by\_count) for each of the last ten years, binned by year. To put it another way: each year, you can see how many works this author published, and how many times they got cited.&#x20;

Any works or citations older than ten years old aren't included.

```json
counts_by_year: [
    {
        year: 2022,
        works_count: 0,
        cited_by_count: 1
    },
    {
        year: 2021,
        works_count: 1,
        cited_by_count: 228
    },
    ...
    {
        year: 2012,
        works_count: 7,
        cited_by_count: 79
    }
]
```



### `works_api_url`

_String:_ An URL that will get you a list of all this author's works.

We express this as an API URL (instead of just listing the works themselves) because sometimes an author's publication list is too long to reasonably fit into a single author object.

```json
works_api_url: "https://api.openalex.org/works?filter=author.id:A2208157607",
```



### `updated_date`

_String:_ The last time anything in this author object changed, expressed as an [ISO 8601](https://en.wikipedia.org/wiki/ISO\_8601) date string. This date is updated for _any change at all_, including increases in various counts.

```json
updated_date: "2016-06-24T00:00:00"
```







## The Dehydrated`Author` object

The `DehydratedAuthor` is stripped-down [`Author`](author.md#the-author-object) object, with most of its properties removed to save weight. Its only remaining properties are:

* ``[`id`](author.md#id)``
* [`display_name`](author.md#display\_name)``
* [`orcid`](author.md#orcid)``

### ``
