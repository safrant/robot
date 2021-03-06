# Duplicate Exact Synonym

Problem: Two entities share an exact synonym. This causes ambiguity.

Solution: Avoid ambiguity by assigning unique exact synonyms or changing the exact synonym to a different annotation (e.g. broad synonym).

```sparql
PREFIX obo: <http://purl.obolibrary.org/obo/>
PREFIX oboInOwl: <http://www.geneontology.org/formats/oboInOwl#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT DISTINCT ?entity ?property ?value
WHERE {
 VALUES ?property {
   obo:IAO_0000118
   oboInOwl:hasExactSynonym
 }
 ?entity ?property ?value .
 ?entity2 ?property ?value .
 FILTER (?entity != ?entity2)
}
```
