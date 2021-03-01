# kafka-evenodd

In this application i have taken maximum number as 50, minimum number as 10 and range as "max - min + 1".
Created random number: "rand = (int)(Math.random() * range) + min".

This app will let us know wether the randomly generated integer is even or odd.


## Prerequisities

* OpenJDK 
* Install Apache Zookeeper
* Install Apache Kafka
* Vs code

## Open powershell as an administrator in the kafka installed folder and run following commands

## Start Zookeeper Service

```
.\bin\windows\zookeeper-server-start.bat .\config\zookeeper.properties
```

## Start Kafka Service

```
.\bin\windows\kafka-server-start.bat .\config\server.properties
```

## Create the Topic

```
.\bin\windows\kafka-topics.bat --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --create --topic vineetha-kafka-app
```

## Open powershell as an administrator in the root project folder and run following commands.

## Compile and Build the Fat Jar File

```
mvn clean compile assembly:single
```

## Start Consumer

```
java -cp target/kafka-api-1.0-SNAPSHOT-jar-with-dependencies.jar com.spnotes.kafka.simple.Consumer vineetha-kafka-app group1
```

## Start Producer

```
java -cp target/kafka-api-1.0-SNAPSHOT-jar-with-dependencies.jar com.spnotes.kafka.simple.ProducerOddEvenNumber test
```

## Input values:
Randomly generated 10 values from the given range.

## Output values:
Gives wether generated value is even or odd.
