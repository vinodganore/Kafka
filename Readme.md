change the configurations in below files 
server.properties

log.dirs=E:/Kafka/kafka-logs


zookeeper.properties

dataDir=E:/Kafka/zookeeper-data



Open cmd prompt and following operations in below sequential order
1) To start zookeeper server

	E:\Kafka>.\bin\windows\zookeeper-server-start.bat .\config\zookeeper.properties
	
	server starts on 2181 port
		[2020-02-02 01:48:13,327] INFO clientPortAddress is 0.0.0.0/0.0.0.0:2181

2) To start Kafka server

	E:\Kafka>.\bin\windows\kafka-server-start.bat .\config\server.properties
	
	server starts on 9092 port
	
3) Create a sample Topic

	E:\Kafka>.\bin\windows\kafka-topics.bat --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic TestTopic
	
4) List all topics 

	E:\Kafka>.\bin\windows\kafka-topics.bat --list --zookeeper localhost:2181
	
5) Start producer to define/write messages

	E:\Kafka>.\bin\windows\kafka-console-producer.bat --broker-list localhost:9092 --topic TestTopic
	
	>This is my first message
	>This is my second message
	>Final message

6) Start consumer to read messages

	E:\Kafka>.\bin\windows\kafka-console-consumer.bat --bootstrap-server localhost:9092 --topic TestTopic --from-beginning
	
	This is my first message
	This is my second message
	Final message
