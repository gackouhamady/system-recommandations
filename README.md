# Real-Time Recommendation System with Apache Kafka and Hadoop

[![Kafka](https://img.shields.io/badge/Apache%20Kafka-3.7.2-blue.svg)](https://kafka.apache.org/)
[![Hadoop](https://img.shields.io/badge/Hadoop-3.x-yellow.svg)](https://hadoop.apache.org/)
[![PySpark](https://img.shields.io/badge/PySpark-compatible-orange.svg)](https://spark.apache.org/docs/latest/api/python/)
[![Google Colab](https://img.shields.io/badge/Google%20Colab-supported-success.svg)](https://colab.research.google.com/)
[![License: Open](https://img.shields.io/badge/license-Open-lightgrey.svg)](#license)
[![Build Status](https://img.shields.io/badge/build-passing-brightgreen.svg)](#)
[![HDFS Integration](https://img.shields.io/badge/HDFS-integrated-blueviolet.svg)](https://hadoop.apache.org/docs/stable/hadoop-project-dist/hadoop-hdfs/)
[![GitHub Repo](https://img.shields.io/badge/source-GitHub-black.svg)](https://github.com/gackouhamady/system-recommandations)

- [Description](#description)
- [Project Structure](#project-structure)
- [Installation & Configuration](#installation--configuration)
  - [Installation of Kafka](#installation-of-kafka)
  - [Start Zookeeper and Kafka](#start-zookeeper-and-kafka)
  - [Creating a Kafka Topic](#creating-a-kafka-topic)
  - [Checking Kafka Topics](#checking-kafka-topics)
  - [Producing and Consuming Messages](#producing-and-consuming-messages)
- [Integration with Hadoop](#integration-with-hadoop)
- [Project Goals](#project-goals)
- [Technologies Used](#technologies-used)
- [Authors](#authors)
- [License](#license)


## Description
This project implements a real-time recommendation system for a streaming platform, using **Apache Kafka** for real-time event processing and **Hadoop** for data storage.


## ## Project Structure
```
├── kafka-3.7.2-src/ # Kafka source code (to be compiled)
├── kafka_2.13-3.7.2/ # Kafka binary distribution (after compilation)
├── hadoop/ # Hadoop configuration folder
├── scripts/ # Automation scripts
├── data/ # Data used for testing
└── README.md # Project documentation
```

## Installation & Configuration

### Installation of Kafka
```sh
# Clone the project
git clone https://github.com/gackouhamady/system-recommandations.git

# Build Kafka (if not pre-compiled)
cd kafka-3.7.2-src
./gradlew clean releaseTarGz -PscalaVersion=2.13.12

# Extract the binary distribution
cd ..
tar -xzf kafka-3.7.2-src/core/build/distributions/kafka_2.13-3.7.2.tgz

```

### Start Zookeeper and Kafka
```sh
# Start Zookeeper
./kafka_2.13-3.7.2/bin/zookeeper-server-start.sh -daemon kafka_2.13-3.7.2/config/zookeeper.properties

# Start Kafka
./kafka_2.13-3.7.2/bin/kafka-server-start.sh -daemon kafka_2.13-3.7.2/config/server.properties
```

### Creating a Kafka Topic
```sh
./kafka_2.13-3.7.2/bin/kafka-topics.sh --create --topic user-events --bootstrap-server localhost:9092 --partitions 1 --replication-factor 1

```
### Checking Kafka Topics
```sh
./kafka_2.13-3.7.2/bin/kafka-topics.sh --list --bootstrap-server localhost:9092
```
### Producing and Consuming Messages

#### Send Messages
```sh
./kafka_2.13-3.7.2/bin/kafka-console-producer.sh --broker-list localhost:9092 --topic user-events
./kafka_2.13-3.7.2/bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic user-events --from-beginning
```
## Integration with Hadoop
This project stores Kafka events in **HDFS** using the **Kafka Connect HDFS Sink**.

1. Configure Hadoop and HDFS.
2. Use a Kafka Connect HDFS connector.
3. Consume the stored data for analysis and recommendations.

## Project Goals
- Implement a real-time recommendation system based on user events.
- Integrate Kafka with Hadoop for log persistence.
- Analyze user events to generate optimized recommendations.

##  Technologies Used
- **Apache Kafka 3.7.2**  
- **Hadoop**  
- **PySpark**  
- **Google Colab**

## Authors
- [Hamady GACKOU](https://github.com/gackouhamady)

## License
This project is open-source. However, I am not responsible for any use in production environments.
