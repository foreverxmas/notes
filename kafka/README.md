## Producer
- Create a topic
>`kafka-topics.sh --zookeeper zk001:2181,zk002:2181,zk003:2181/kafkaData --topic topic1 --partitions 1 --replication-factor 2 --create`
- Check a leader and followers
>`kafka-topics.sh --zookeeper zk001:2181,zk002:2181,zk003:2181/kafkaData --topic topic1 --describe`
- Open console and type messages
>`kafka-console-producer.sh --broker-list kafka001:9092,kafka002:9092,kafka003:9092 --topic topic1`
- Add ack option to the command above if needed `--request-required-acks 1` 
- Check messages
>`kafka-console-consumer.sh --bootstrap-server kafka001:9092,kafka002:9092,kafka003:9092 --topic topic1 --from-beginning`
## Consumer
- Check consumer group
>`kafka-consumer-groups.sh --bootstrap-server kafka001:9092,kafka002:9092,kafka003:9092 --list`
- Set consumer group name
>`kafka-console-consumer.sh --bootstrap-server kafka001:9092,kafka002:9092,kafka003:9092 --topic topic1 --group consumer-group1 --from-beginning`
## Kafka configuration change
- Change topic period to 1 hour
>`kafka-config.sh --zookeeper zk001:2181,zk002:2181,zk003:2181/kafkaData --alter --entity-type topics --entity-name topic1 --add-config retention.ms=3600000`
- Change partitions
>`kafka-reassign-partitions.sh --zookeeper zk001:2181,zk002:2181,zk003:2181/kafkaData --reassignment-json-file /usr/local/kafka/partition.json --execute`
> partition.json
```
{"version":0.1,
 "partitions":[
    {"topic":"topic1","partition":0,"replicas":[1,2]},
    {"topic":"topic1","partition":1,"replicas":[2,3]}
 ]  
}
```

