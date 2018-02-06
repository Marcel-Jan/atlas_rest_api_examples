# Apache Atlas REST API - working examples

I'm preparing the implementation of Apache Atlas on a data lake (Hadoop Data Platform 2.6.3) and to speed things up, I want to have Atlas REST API calls ready to run. I've tried the Atlas REST API Swagger (http://atlas.apache.org/api/v2/ui/index.html#/), but I couldn't get every API call from it working. Therefor I've tried and tried and this is a set of API calls that I managed to run on a Hortonworks Data Platform 2.6.3 Sandbox.

### Prerequisites

This has been tested on HDP 2.6.3.
Atlas and Ranger must be running.

# Adding HDFS paths to Atlas with tags

## Creating entities for HDFS paths
Unlike for example Hive databases, tables and columns HDFS paths are not automatically added to Atlas as entities. So we need to do this ourselves. HDFS paths can be directories or files. 
```
curl -u holger_gov:holger_gov  -ik -H "Content-Type: application/json" -X POST -d '{"entity": {"typeName" : "hdfs_path", "attributes" : {"name" : "electionresults", "qualifiedName" : "electionresults.electionresults@Sandbox", "path" : "/user/dmaster/electionresults/ls2014.tsv", "clusterName":"Sandbox"}}}' http://sandbox.hortonworks.com:21000/api/atlas/v2/entity
```



