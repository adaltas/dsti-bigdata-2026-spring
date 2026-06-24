# Lab: Data Streaming with Kafka

- Build a real-time data streaming process using Kafka producer and consumer.

## Tasks

1. Launch a Kafka producer to produce data from source, and consume the message. (Medium)

## Set up the environment

## Lab resources

- Use Docker compose to launch Kafka and data producer container.
- Download the dataset from [NYC Taxi Fare Dataset in Kaggle](https://www.kaggle.com/datasets/diishasiing/revenue-for-cab-drivers?resource=download), and place the CSV file into `./lab-resources/producer/`

## Launch the Docker containers

```bash
cd lab-resources
docker compose up -d
```

## Produce real-time data

1. Examine the `kafka_producer.py` to see how to implement Kafka package with Python.

2. Run `kafka_producer.py` python script inside a container to simulate real-time data, and continuously produce to a Kafka topic.

   ```bash
   docker exec -it lab-kafka-data-producer /bin/sh
   # Inside the container:
   python kafka_producer.py \
       --brokers lab-kafka01:19092,lab-kafka02:19092,lab-kafka03:19092 \
       --topic demo-nyc-taxi-fare \
       --csv data.csv \
       --delay 1
   ```

## Consume Kafka messages

Launch a container to consume the topic `demo-nyc-taxi-fare` to see the consuming process.

1. Refer to this [documentation](https://docs.confluent.io/kafka/operations-tools/kafka-tools.html#) to find the suitable tool to consume.

   ```bash
   docker run --rm -it --network lab-kafka-net apache/kafka:4.1.1 \
     /opt/kafka/bin/<TODO>
   ```
