# kafka-server-installation
This is a guide to install Kafka server using docker-compose.

## Prerequisites
- Install Docker on your OS
- Install Docker-compose on your OS (if not installed with above step)
- Clone this repository
- Open terminal and navigate to the cloned repository
- Run the following command to start the Kafka server 

### on mac
```bash
docker-compose up -ds
```
### on windows
```bash
docker-compose -f dockeComposeFileName.yml up -d
```
- Run the following command to check the status of the Kafka server
```bash
docker-compose ps
```
- Run the following command to stop the Kafka server
```bash
docker-compose down
```

## Access Kafka server if you are using docker-compose
- Kafka server is running on port 9092
- Zookeeper is running on port 2181
- You can access the Kafka server using the following command
```bash
docker exec -it <kafka_container_id_or_name> bash
```
#### Note: You can get the container id or name by running the following command
```bash
docker ps
```
- Once you are inside the container, you can run the following command to create a topic
```bash
kafka-topics.sh --create --topic <topic_name> --partitions <number_of_partitions> --replication-factor <replication_factor> --bootstrap-server localhost:9092
```
- You can run the following command to list the topics
```bash
kafka-topics.sh --list --bootstrap-server localhost:9092
```
- You can run the following command to produce messages to the topic
```bash
kafka-console-producer.sh --topic <topic_name> --bootstrap-server localhost:9092
```
- You can run the following command to consume messages from the topic
```bash
kafka-console-consumer.sh --topic <topic_name> --from-beginning --bootstrap-server localhost:9092
```
- You can run the following command to describe the topic
```bash
kafka-topics.sh --describe --topic <topic_name> --bootstrap-server localhost:9092
```
- You can run the following command to delete the topic
```bash
kafka-topics.sh --delete --topic <topic_name> --bootstrap-server localhost:9092
```
- You can run the following command to check the offset of the topic
```bash
kafka-run-class.sh kafka.tools.GetOffsetShell --broker-list localhost:9092 --topic <topic_name> --time -1
``` 
- You can run the following command to check the consumer group
```bash
kafka-consumer-groups.sh --bootstrap-server localhost:9092 --list
```
- You can run the following command to check the consumer group details
```bash
kafka-consumer-groups.sh --bootstrap-server localhost:9092 --describe --group <consumer_group_name>
```
- You can run the following command to reset the offset of the consumer group
```bash
kafka-consumer-groups.sh --bootstrap-server localhost:9092 --group <consumer_group_name> --reset-offsets --to-earliest --execute --topic <topic_name>
```
- You can run the following command to check the consumer group lag
```bash
kafka-consumer-groups.sh --bootstrap-server localhost:9092 --group <consumer_group_name> --describe
```s

