# Monitoring Plugin: Elasticsearch cluster

### Description
Monitor the status of your elasticsearch cluster. This script does monitor the value "status" from "ES_API/_cluster/health" if not specified anything else.
If -a is set to a specific attribute you can monitor a number against the specified threshold (-w and -c). Possible attributes can be taken from
ES_API/_cluster/health (curl localhost:9200/_cluster/health?pretty), they are not documented here since they are different between the different versions of elasticsearch.

### Usage
    -h Shows this message
    -H [Default: localhost] Elasticsearch cluster node
    -p [Default: 9200] Port
    -s [Default: <notset>] SSL
    -a [Default: status] Check attribute
    -w [Default: <notset>] Warning (Only required if -a is different than the default "status")
    -c [Default: <notset>] Critical (Only required if -a is different than the default "status")

### Examples
./check_elasticsearch_cluster -H localhost\
elasticsearch cluster status is green

./check_elasticsearch_cluster -H localhost -a active_primary_shards -w200 -c300\
elasticsearch cluster health active_primary_shards=181 is 

./check_elasticsearch_cluster -H localhost -a unassigned_shards -w10 -c20\
elasticsearch cluster health unassigned_shards=0 is O

### Install 
Copy check_elasticsearch_cluster to your plugin folder and create a service/exec in your monitoring engine. 
