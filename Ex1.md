= Building the Northwind Ontology =

The Northwind dataset is a classical exemplar, widely used in relational database tutorials and courses.
It contains the transactions, operational records and organization
information for a trading company (that order products from suppliers and then, well, sell them to customers).

Your task is to turn the relational DB schema into an ontology.

== Why? ==

This is how a general-purpose knowledge graph is aggregated bit-by-bit: starting from a particular domain, and try to link the domain to other domains. For example, "employee", "region" and such can all find their corresponding entities in Freebase, DBPedia, ConceptNet etc.

== Technical details ==

Here is the schema of the database:
![northwind_schema](https://cdn.rawgit.com/yatli/KnowledgeGraphTutorial/df4d564f/Northwind_Schema.png)

A more detailed description of the dataset can be found here:
https://theaccessbuddy.wordpress.com/2011/07/03/northwind-database-explained/

There are a dozen of tables involved here. Notably, due to the Entity-Relationship methodology used in relational databases, sometimes it requires multiple tables to represent one entity. When you want to gather the information, you join tables.

== Tips ==

- The OWL reference documentation is your good friend: http://www.w3.org/TR/2012/REC-owl2-primer-20121211/
- Don't worry about the detailed syntax, datatypes, XSD, etc. Write what you think that best captures your ideas.
- You don't have to mechanically convert the whole schema (that's boring and time-consuming), but instead, proceed as necessary, until you feel comfortable with the OWL concepts.
- During the process, observe how the tables can be converted to knowledge graph entity classes, how to model relationships
- Going further, do you have any ideas about how to link this dataset to a "master graph", say, Freebase?
- Anything on your mind, that leverages the knowledge within the "master graph" to exploit interesting facts in this domain? For example, one day one of the employees Linda, is on sick leave. She is the only one in charge of a region. Find a backup for her that can effectively communicate with the clients. Here we assume that we can get People.Person.SpeaksLanguage from the master graph (Freebase does have this).
- Try to write some constraints with OWL assertions. For example, if we assume that the shippers should be shipping from the same geographical region as the supplier of an order (obviously the shipper does not want to drive a truck across the country, get the cargo loaded and head towards the customer). Note: this is possible in OWL, though a bit subtle. Hint: count them.
- After trying the previous example, do you feel the limitation of OWL? You may take a look here: https://en.wikipedia.org/wiki/Description_logic
