# CogSci Researcher Atlas

A searchable directory of cognitive science researchers, filterable by topic, institute and country. It has four views: a list of researchers, a topic index, a network (researchers ↔ topics, or co-authorship) and a world map.



## Edit the data

Every researcher is one object in `data/researchers.json`:

```json
{
 "name": "Wim De Neys",
 "affiliation": "CNRS / LaPsyDÉ, Université Paris Cité, Paris",
 "country": "France",
 "city": "Paris",
 "lat": 48.857, "lng": 2.352,
 "topics": ["reasoning", "dual-process", "judgment & heuristics", "moral cognition"],
 "bio": "One sentence on what they work on.",
 "known_for": "A well-known work (year)",
 "website": "https://…",
 "scholar": "https://scholar.google.com/citations?user=XXXXXXXXXXXX",
 "deceased": false,
 "source": "verified",
 "institute": "LaPsyDÉ (Université Paris Cité)",
 "keywords": ["dual-process", "logical intuitions"],
 "coauthors": ["Bence Bago", "Gordon Pennycook"]
}
```

- `topics` must come from the fixed list in `index.html` (the `FAMILIES` constant). A topic that isn't on that list is ignored. To add a topic, add it to a family there.
- `coauthors` lists names exactly as they appear in other entries. Listing a link on one side is enough; the page adds the reverse link itself.
- `lat`/`lng` place the city dot on the world map. Researchers who share a city should use the same coordinates.
- `source` is `"verified"` once the website and Scholar links have been checked. It is `"coauthor"` for entries added through co-authorship whose links are still pending; those show "pending" instead of "No website".
- `website` and `scholar` can be `null`.
- `institute` feeds the Institute filter. Use the same spelling for everyone in a lab.
- `keywords` are free-form and searchable; clicking one on a profile searches for it.
- `via` is optional. `"parisneuro"` marks entries drawn from the [ParisNeuro](https://parisneuro.fr/) directory and shows a credit on the profile.
- `check` is optional. It holds a short caveat shown in the profile panel.

Commit the edited file and GitHub Pages republishes within a minute or two.


## License and credits

**Code.** `index.html` is released under the [GNU General Public License v3.0](LICENSE) (GPL-3.0-or-later), Copyright (C) 2026 Nicolas Beauvais. If you share a modified version, you must release it under the same license.

**Data.** `data/researchers.json` is released under [Creative Commons Attribution 4.0 (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/). You may reuse and adapt it if you credit "CogSci Researcher Atlas, Nicolas Beauvais". One exception: the keywords of entries marked `"via": "parisneuro"` come from the [ParisNeuro](https://parisneuro.fr/) directory ([source repository](https://github.com/jmourabarbosa/compneuroparis)). They are reused here with credit and are not covered by this license.

**Facts about researchers.** Names, affiliations and public profile links describe people's public academic activity. If you are listed and want something corrected or removed, use "Suggest a correction" on your profile or open an issue.

**Third-party components.**
- World map geography: `data/countries-110m.json` from [world-atlas](https://github.com/topojson/world-atlas) (ISC License), derived from [Natural Earth](https://www.naturalearthdata.com/) (public domain).
- [D3](https://d3js.org/) (ISC License) and [TopoJSON](https://github.com/topojson/topojson) (ISC License) are loaded from cdnjs and not redistributed here.
- Fonts: Bricolage Grotesque, IBM Plex Sans and IBM Plex Mono via Google Fonts (SIL Open Font License).
