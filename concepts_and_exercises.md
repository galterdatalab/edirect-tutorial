## Concept 1: Discovering the fields used in NCBI database records
Each NCBI database uses specific fields to index records. These fields can be used to search or filter queries. Field names and abbreviations may be the same from one database to another, but the entity in that field is not necessarily the same. For example, "unique ID" [UID] refers to the record identifier for that record, but the UID for a PubMed entry is different from that of an NCBI Gene entry.

### Example 1
Let's start by seeing what fields are in your NCBI database of choice. The "einfo" command will show you the fields for records in a given NCBI database.

```
einfo -db gene -fields
```
![EDirect_GeneFields](https://user-images.githubusercontent.com/13007103/129612872-078743bc-0bde-4bbd-9e03-7a9fd29af3ae.png)



### Exercise 1
Now write a query to find the field abbreviations in records for the Medical Genetics database. Database name in EDirect is medgen. What is the field abbreviation for clinical features?


## Concept 2: Querying NCBI databases using field "tags"

### Example 2
Now let's query the NCBI Gene database for amyloid precursor protein using the gene symbol APP. We will do this by adding [GENE] after APP to specify that we want to search the gene name field for APP. Your search query terms must be enclosed in quotation marks. This will give you a count of records that contain your query.
```
esearch -db gene -query "APP [GENE]"
```
That's a lot of results! Let's get just the human APP gene. You can do this by specifying the organism by using the [ORGN] field tag
```
esearch -db gene -query "APP [GENE] AND human [ORGN]"
```
Much better. Just one result.


### Exercise 2
Now write a query yourself to find all records in MedGen with the query term "paralysis" in the "clinical features" field (HINT: [CLIN]). How many records do you get?


## Concept 3: Combining queries

### Example 3
You can combine multiple queries on a line, sending the results from one query right to the next query using a pipe "|". Let's re-run the gene query and get related protein records for our gene. We can do that with the command elink.
```
esearch -db gene -query "APP [GENE] AND human [ORGN]" | elink -target protein
```
This gives a count of around 70+ records. Let's filter these records so that we only get annotated RefSeq records. Let's add one more pipe to this query, and use efilter to filter by the source refseq.
```
esearch -db gene -query "APP [GENE] AND human [ORGN]" |elink -target protein | efilter -source refseq
```
