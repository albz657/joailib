# About #
Joailib tries to be an easy to use java library for OAI metadata harvesting.
it follows the OAI-PMH v2 spec, that you can find [here](http://www.openarchives.org/OAI/openarchivesprotocol.html)

## Features ##
  * Support for OAI-PMH v2.
  * Automatic resumptionToken processing.
  * Harvest downloading.
  * Recovery from **503 Service Unavailable** in a non abusive way.


---

## Examples ##
#### Setting up an OAI repository ####
```
  Harvester harvester = new Harvester("http://catarina.udlap.mx/u_dl_a/tales/oai/requestETD.jsp");
```

#### Identifying ####
```
   Identify identify = harvester.identify();
   System.out.println(identify.getRepositoryName());
   System.out.println(identify.getProtocolVersion());

```
#### Listing metadata supported formats ####
```
   List<MetadataFormat> metadataformats = harverster.listMetadataFormats();
   for(MetadataFormat metaformat : metadataformats) {
      System.out.println(metaformat.getSchema());
   }
```
#### Listing sets ####
```
   List<Set> sets = harverster.listSets();
   for(Set set : sets) {
      System.out.println(set.getSetName())
   }
```
#### Listing identifiers ####
```
   List<Header> identifiers = harverster.listIdentifiers();
   for(Header identifier:identifiers) {
      System.out.println(identifier.getIdentifier());
   }			
```
#### Getting a record giving an identifier ####
```
   Record record = harvester.getRecord("oai:ciria.udlap.mx:u-dl-a/tesis/1011010008981");
   System.out.println(record.getMetadata().getTitleList().get(0));
```
#### Getting all the records ####
```
   // This can take a few minutes.
   RecordIterator it =  harvester.listRecords();
   while(it.hasNext()) {
      Record record = it.next();	
      // process record here.			      
   }
```

For more documentation on other useful classes download the joailib-bin zip, and check out the javadoc.