##SciGraph Configuration
Here we provide configuration files to insert data into a Neo4J graph database using the [SciGraph](https://github.com/SciGraph/SciGraph) application.  These files also contain extensions to the default REST services that include queries specific to cancer use cases using the Cypher query language and SciGraph query expansion.

#####Note: We have created public servers for demonstration purposes.  While the servers contain basic REST API documentation, these are not intended to serve as a user interface and require knowledge of the underlying dataset.  We are the in the process of improving documentation of these pages, see the conversation [here](https://github.com/SciGraph/SciGraph/issues/93).


###Input
Identifiers are stored as URIs but we recommend searching using the [CURIE](http://www.w3.org/TR/curie/) syntax; for example, DOID:1781 is equivalent to http://purl.obolibrary.org/obo/DOID_1781.  Our Curie configuration can be found [here](https://github.com/monarch-initiative/dipper/blob/master/dipper/curie_map.yaml).

###Graph Output
Graph queries where JSON is the specified format are outputted in the BBOP Graph Format, for example (with metadata removed):

        {
          "nodes": [
            {
              "id": "DOID:10011",
              "lbl": "thyroid lymphoma",
              "meta": {}
            },
            {
              "id": "DOID:1781",
              "lbl": "thyroid cancer",
              "meta": {}
            }
          ],
          "edges": [
            {
              "sub": "DOID:10011",
              "obj": "DOID:1781",
              "pred": "subClassOf",
              "meta": {}
            }
          ]
        }

A javascript API is available in the [BBOP-JS codebase](https://github.com/berkeleybop/bbop-js/) with API Documentation [here](http://berkeleybop.github.io/bbop-js/docs/files/model-js.html#bbop.model.graph)

###Vocabulary Output
With JSON specified vocabulary queries are returned in the format (with synonyms removed for brevity):

        {
          "concepts": [
            {
              "uri": "http://purl.obolibrary.org/obo/DOID_8524",
              "labels": [
                "nodular lymphoma"
              ],
              "fragment": "DOID_8524",
              "curie": "DOID:8524",
              "categories": [],
              "synonyms": [
                "Follicular low grade B-cell lymphoma (disorder)",
                "Follicular non-Hodgkin's lymphoma (disorder)"
              ],
              "acronyms": [],
              "abbreviations": [],
              "deprecated": true,
              "definitions": []
            }
          ]
        }
