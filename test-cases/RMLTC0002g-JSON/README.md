## RMLTC0002g-JSON

**Title**: "Two columns mapping, invalid JSONPath"

**Description**: "Test the presence of an invalid JSONPath"

**Error expected?** Yes

**Input**
```
{
  "students": [{
    "ID": 10,
    "Name":"Venus"
  }]
}

```

**Mapping**
```
@prefix ex: <http://example.com/> .
@prefix rml: <http://w3id.org/rml/> .

<http://example.com/base/TriplesMap1> a rml:TriplesMap;
  rml:logicalSource [ a rml:LogicalSource;
      rml:iterator "$.students[*]]";
      rml:referenceFormulation rml:JSONPath;
      rml:source [ a rml:RelativePathSource;
          rml:root rml:MappingDirectory;
          rml:path "student2.json"
        ]
    ];
  rml:predicateObjectMap [
      rml:objectMap [
          rml:reference "$.IDs"
        ];
      rml:predicate ex:id
    ];
  rml:subjectMap [
      rml:template "http://example.com/{$.ID}/{$.Name}"
    ] .

```

