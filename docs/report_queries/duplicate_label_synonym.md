# Duplicate Label-Synonym

Problem: An entity shares a label with an exact synonym. This causes ambiguity.

Solution: Avoid ambiguity by changing the exact synonym or label.

```sparql
PREFIX obo: <http://purl.obolibrary.org/obo/>
PREFIX oboInOwl: <http://www.geneontology.org/formats/oboInOwl#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT DISTINCT ?entity ?property ?value
WHERE {
 VALUES ?property {
   obo:IAO_0000118
   oboInOwl:hasExactSynonym
   oboInOwl:hasRelatedSynonym
   oboInOwl:hasNarrowSynonym
   oboInOwl:hasBroadSynonym
 }
 ?entity rdfs:label ?value .
 ?entity ?property ?value
}
```
