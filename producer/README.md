# Kafka Producer

Supports [ClickHouse documentation on Kafka]().

This is a simple Kafka producer written in Python for ndjson data. It ensures a schema is set for the JSON - either generating a schema or using a specified one.

Schemas are required for tools such as the Kafka JDBC sink.

## Requirements

- Python 3.8.10+
- Kafka instance v7+. Easiest solution is to create a Kafka cluster in Confluent Cloud - which offers an adequate free tier.
- Ndjson file. A sample github json file can be found [here]() with accompanying config for the script [here]()

## Setup

`pip install -r requirements.txt`

## Usage

1. Prepare a configuration. See [github.config]() for examples. Any target topic will be automatically created if it doesn't exist.
2. (Optional) Prepare a [JSON schema file](https://json-schema.org/) for your ndjson and specify this in the config from (1) via `input.schema`. To infer a schema automatically do not set this parameter. This will cause the schema to be inferred from the first 100 lines. This is best effort only (but works for the gitub dataset)!
3. Run it!

`python producer.py -c <config_file>`

## Not in scope

Whilst all producer configuration parameters supported by the [Kafka python client](https://kafka-python.readthedocs.io/en/master/apidoc/KafkaProducer.html) can be used - replace `_` with `.` in the configuration, no work has been done regards testing these settings for optimal performance.