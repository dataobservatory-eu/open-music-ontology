# OMO: Open Music Ontology

**Repository:** https://github.com/dataobservatory-eu/open-muisc-ontology  
**Namespace (prefix):** `omo:` → `https://dataobservatory.eu/ontology/omo#`  
**Status:** Proof of Concept (v0.1.0)

## Purpose

The **Open Music Ontology (OMO)** provides a **minimal, non-authoritative bridge vocabulary** that connects open cultural heritage and research metadata with common **industry identifiers and release categories** (e.g., ISRC, ISWC, album/single concepts).

It does **not** re-publish ISRC, ISWC, or DDEX standards; it simply offers neutral terms and links (`rdfs:seeAlso`) for interoperability in knowledge graphs such as the Slovak Comprehensive Music Database (SKCMDb), Open Music Europe, and related Data Spaces.

## Included Concepts (v0.1.0)

| Type | Term | Description |
|------|------|-------------|
| Class | `omo:Recording` | A sound recording entity (bridge for ISRC use). |
| Class | `omo:MusicalWork` | Abstract musical work (bridge for ISWC use). |
| Class | `omo:ContributorRole` | Role performed by a person or organisation. |
| Subclass | `omo:FeaturedPerformer` | Prominently credited performer role. |
| Property | `omo:hasISRC` | Associates a Recording with an ISRC code. |
| Property | `omo:hasISWC` | Associates a MusicalWork with an ISWC code. |
| Property | `omo:hasContributorRole` | Links an entity to its contributor role. |
| Property | `omo:agent` | Connects a role node to the performing agent. |
| Class | `omo:Release` | A curated bundle of recordings (album, single). |
| Class | `omo:ReleaseCategory` | Category describing a Release type. |
| Subclass | `omo:Album` | A release consisting of multiple recordings. |
| Subclass | `omo:Single` | A release with one main track. |
| Property | `omo:hasReleaseCategory` | Links a Release to its category. |

---

## Example

```turtle
@prefix omo: <https://dataobservatory.eu/ontology/omo#> .
@prefix ex:  <https://example.org/> .
@prefix foaf: <http://xmlns.com/foaf/0.1/> .

ex:rec001 a omo:Recording ;
  omo:hasISRC "SK0012345678" ;
  omo:hasContributorRole ex:role1 .

ex:work001 a omo:MusicalWork ;
  omo:hasISWC "T-123.456.789-Z" .

ex:role1 a omo:FeaturedPerformer ;
  omo:agent ex:johnDoe .

ex:johnDoe a foaf:Person ; foaf:name "John Doe" .

ex:release001 a omo:Release ;
  omo:hasReleaseCategory omo:Album ;
  omo:hasContributorRole ex:role1 .
```

⚠️ Disclaimer

This ontology is not affiliated with IFPI (ISRC), CISAC (ISWC), DDEX, or any other rights holder.
It simply provides neutral helper terms for research and cultural data interoperability.

For authoritative specifications, visit:

- ISRC: <https://isrc.ifpi.org>
- ISWC: <https://www.cisac.org/what-we-do/cis-net/iswc>
- DDEX: <https://kb.ddex.net>

## License & Citation

© 2025 contributors — Released under [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/deed.en) (CC-BY 4.0).

Daniel Antal (2025). Open Music Ontology (OMO) – proof of concept (v0.1.0).
<https://github.com/dataobservatory-eu/open-muisc-ontology>
.