# Today I learned: SPARQL 

Today I learned is going to be a series about new technologies I discover and getting started with. I explain basic concepts and show some example usage of the technology.

In this first article we are looking at *SPARQL*. The name itself is an abbreviation for *S*PARQL *P*rotocol *A*nd *R*DF *Q*uery *L*anguage. It is a graph-based query language to operate on *RDF*. RDF, the *R*esource *D*escription *F*ramework is a description language to build semantic web knowledge bases, but this will be part of another TIL article.

The thing to keep in mind for this article is, you would use SPARQL to run queries on an RDF knowledge base. Those knowledge bases are referred to as *ontologies*. In my case, I was given an extract of the publicly availiably *dbpedia* ontology. The extract is centered around Art: Artists, Museums, Paintings, Scultptures and things in relation to them. My goal is to extract information from this ontology using SPARQL.


On the surface, SPARQL looks like an SQL dialect. A sample SPARQL-query may look like this:
```
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>

SELECT ?subject ?object
	WHERE { ?subject rdfs:subClassOf ?object }
```

The `SELECT` and the `WHERE` very much remind us of standard SQL. But keep in mind - and RDF ontology is not a relational database. There are no tables to join and data can be:
 - very loosely structured
 - ambiguos
 - missing from an entry
 
 It depends a bit on the quality of the RDF, the thing is, we are not looking in a structured schema, we rather search for possible endpoint in a loosly coupled graph.
 
 RDF statements are formulated as triples of subject, predicate, object like this:
 ```
 dbpedia:Michelangelo dbpedia-owl:birthDate "1475-03-06+02:00"^^xsd:date .
 ```
 
 In this case *dbpedia:Michelangelo* would be our subject, a resource in dbpedia. The predicate is *dbpedia-owl:birthDate*, another resource and *"1475-03-06+02:00"^^xsd:date* the object. The dot terminates the statement. You could probably best compare that to the sentence `Michelangelo was born on 06.03.1475` to get what is going on here.
 
 Now with SPARQL the queries are formulated with this subject, predicate, object system in mind. Query-Variables are preceded by a questionmark, so `?subject` and `?object` from the sample SPARQL query above are both query variables. That means the above query would be looking for all subjects that a subclasses of an object.
 
  
  

[//]: # ![_config.yml]({{ site.baseurl }}/images/config.png)

[//]: #  The easiest way to make your first post is to edit this one. Go into /_posts/ and update the Hello World markdown file. For more instructions head over to the [Jekyll Now repository](https://github.com/barryclark/jekyll-now) on GitHub.
