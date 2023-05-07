# Kafka-Benthos-Elasticsearch Pipeline

This is a docker-compose configuration for a pipeline that reads data from a Kafka topic, processes it with Benthos, and stores it in Elasticsearch.

## Prerequisites

You will need to have [Docker](https://www.docker.com/) and [Docker Compose](https://docs.docker.com/compose/) installed in your system.

## Configuration

The pipeline consists of the following services:

- `zookeeper`: Apache ZooKeeper instance used by Kafka for coordination.
- `kafka`: Apache Kafka instance used as the data source and sink for the pipeline.
- `elasticsearch`: Elasticsearch instance used as the storage backend for the pipeline.
- `kibana`: Kibana instance used as a web-based UI to visualize Elasticsearch data.
- `benthos`: Benthos instance used as the processing engine for the pipeline.

The configuration of the pipeline is defined in the `docker-compose.yml` file. By default, the pipeline reads data from a Kafka topic named `kbe-topic`, applies a Benthos pipeline that simply logs the messages to the console, and stores the messages in Elasticsearch under an index named `kbe-index`.

If you need to modify the pipeline configuration, you can do so by editing the `docker-compose.yml` file directly or by providing an alternative configuration file using the `-f` option of `docker-compose`.

## Running the pipeline

To run the pipeline, execute the following command in the same directory as the `docker-compose.yml` file:

```
docker-compose up
```

This will start all the required services and display their logs in the console. If you want to run the pipeline in detached mode, you can use the `-d` option:

```
docker-compose up -d
```

To stop the pipeline and remove the containers, use the following command:

```
docker-compose down
```

## Accessing the data

You can access the Kibana UI by opening a web browser and navigating to `http://localhost:5601`. From there, you can create visualizations and dashboards based on the data stored in Elasticsearch.

To access Elasticsearch directly, you can use the following URL: `http://localhost:9200`. You can use tools like [curl](https://curl.se/) or [Postman](https://www.postman.com/) to send queries to Elasticsearch or inspect the stored data.

## Disclaimer

This configuration is intended for demonstration and testing purposes only. It may not be suitable for production environments and should be used at your own risk.