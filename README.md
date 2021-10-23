
Enter the docker container to run commands there:

`docker exec -it taskd_kafka-1_1 /bin/sh`
`docker exec -it taskd_kafka-2_1 /bin/sh`
`docker exec -it taskd_kafka-3_1 /bin/sh`

In all of the docker container run 
`cd ../../`  -> go to root dir

Create topic named example
`./usr/bin/kafka-topics  --create --topic example --partitions 3 --replication-factor 3 --if-not-exists --zookeeper localhost:32181`

Describe topic example
`./usr/bin/kafka-topics  --describe --topic example  --zookeeper localhost:32181`

In a host: (Producer)
`./usr/bin/kafka-console-producer --broker-list localhost:29092 --topic example`

In another host: (Consumer)
`./usr/bin/kafka-console-consumer --bootstrap-server localhost:29092 --topic example --from-beginning`

Can try consuming/producing from different hosts

Kill a docker container

And try producing and consuming from the topic again