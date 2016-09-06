MongoDB
=============
This example runs MongoDB through a petset.

## Starting

    kubectl create -f init-mongo-cluster.configmap.yaml
    kubectl create -f mongodb.yaml

## Checking cluster status

    kubectl exec mongodb-0 -- mongo --eval 'rs.status();'

Should see 3 nodes in the set

    MongoDB shell version: 3.2.9
    connecting to: test
    {
    "set" : "my_replica_set",
    "date" : ISODate("2016-09-06T01:12:00.964Z"),
    "myState" : 2,
    "term" : NumberLong(1),
    "syncingTo" : "mongodb-2.mongodb.default.svc.cluster.local:27017",
    "heartbeatIntervalMillis" : NumberLong(2000),
    "members" : [
    {
      "_id" : 0,
      "name" : "mongodb-2.mongodb.default.svc.cluster.local:27017",
      "health" : 1,
      "state" : 1,
      "stateStr" : "PRIMARY",
      "uptime" : 120,
      "optime" : {
        "ts" : Timestamp(1473124201, 1),
        "t" : NumberLong(1)
      },
      "optimeDate" : ISODate("2016-09-06T01:10:01Z"),
      "lastHeartbeat" : ISODate("2016-09-06T01:12:00.197Z"),
      "lastHeartbeatRecv" : ISODate("2016-09-06T01:12:00.228Z"),
      "pingMs" : NumberLong(1),
      "electionTime" : Timestamp(1473124200, 2),
      "electionDate" : ISODate("2016-09-06T01:10:00Z"),
      "configVersion" : 3
    },
    {
      "_id" : 1,
      "name" : "mongodb-0.mongodb.default.svc.cluster.local:27017",
      "health" : 1,
      "state" : 2,
      "stateStr" : "SECONDARY",
      "uptime" : 189,
      "optime" : {
        "ts" : Timestamp(1473124201, 1),
        "t" : NumberLong(1)
      },
      "optimeDate" : ISODate("2016-09-06T01:10:01Z"),
      "syncingTo" : "mongodb-2.mongodb.default.svc.cluster.local:27017",
      "configVersion" : 3,
      "self" : true
    },
    {
      "_id" : 2,
      "name" : "mongodb-1.mongodb.default.svc.cluster.local:27017",
      "health" : 1,
      "state" : 2,
      "stateStr" : "SECONDARY",
      "uptime" : 120,
      "optime" : {
        "ts" : Timestamp(1473124201, 1),
        "t" : NumberLong(1)
      },
      "optimeDate" : ISODate("2016-09-06T01:10:01Z"),
      "lastHeartbeat" : ISODate("2016-09-06T01:12:00.257Z"),
      "lastHeartbeatRecv" : ISODate("2016-09-06T01:12:00.338Z"),
      "pingMs" : NumberLong(2),
      "syncingTo" : "mongodb-2.mongodb.default.svc.cluster.local:27017",
      "configVersion" : 3
    }
    ],
    "ok" : 1
    }

## Failover

TODO: Add details

##  Scaling

TODO: Add details

## Image Upgrade

TODO: Add details

## Limitations
* Creates a replica set of 3.  This can be increased but the petset file will have to be changed.
