# Entrez Direct (EDirect)
These materials are a guide on using EDirect to query NCBI databases from the command line.

## What is EDirect?
From the NCBI EDirect tutorial pages:

> Entrez Direct (EDirect) provides access to the NCBI's suite of interconnected databases (publication, sequence, structure, gene, variation, expression, etc.)
> from a Unix terminal window. Search terms are entered as command-line arguments.
> Individual operations are connected with Unix pipes to allow construction of multi-step queries. Selected records can then be retrieved in a variety of formats.

## Why use EDirect?
Sometimes, you might want to see all the related records from an entry in an NCBI database, then find related records in yet another database. This requires multiple clicks in the web versions of the databases, and you cannot specify the terms you want to use for "relatedness", or specify all the fields you might want to filter on when finding related records. You can do that with EDirect. It retrieves results in plain text format that you can then analyze with text packages, or place into tabular format, or use for analysis software packages (such as sequence alignment). Query results run quickly, because EDirect uses indexing to target the fields you define in your queries.

## Deciding what to search manually and what to search with EDirect
Not all NCBI database searches will be made easier with EDirect. 

For example, to retrieve PubMed records associated with GEO Datasets, it's more efficient to do a keyword search in GEO, then export the GEO record numbers to a file, then use those record numbers to search for associated PubMed records, using EDirect. 

As you use EDirect, you will learn what types of queries are best-suited for it.

