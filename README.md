# Confluent Cloud Kafka Producer and Consumer Examples
These Python scripts demonstrate how to create a basic Kafka producer and consumer for use with Confluent Cloud. The code is adapted from the Confluent Developer getting started guide for Python, specifically focusing on producers and consumers for Confluent Cloud.
## Contents:
1. producer.py - A sample Kafka producer
2. consumer.py - A sample Kafka consumer
3. requirements.txt - A file listing required Python packages
## Prerequisites:
* Python 3.x
* Confluent Cloud account and credentials
* A topic named `purchases` with 1 partition and no schema
## Setup:
1. Install the required library by using the provided requirements.txt file:
```
pip install -r requirements.txt
```
2. Set up your Confluent Cloud environment variables:
CONFLUENT_CLOUD_BOOTSTRAP_SERVERS
CONFLUENT_CLOUD_API_KEY
CONFLUENT_CLOUD_SECRET
## Usage:
1. Run the producer:
```
python producer.py
```
2. Run the consumer
```
python consumer.py
```
The producer will generate 10 random purchase events and send them to the "purchases" topic. The consumer will continuously poll for messages from the same topic and print them to the console.
## Notes:
The producer uses a delivery callback to confirm successful message delivery.
The consumer will continue running until interrupted (Ctrl+C).
Both scripts use environment variables for configuration. Ensure these are set correctly before running.
The consumer group ID is set to 'kafka-python-getting-started'. Modify this if needed.
The consumer's auto.offset.reset is set to 'earliest', meaning it will read all available messages in the topic.
For more detailed information and advanced usage, refer to the Confluent Developer documentation:
https://developer.confluent.io/get-started/python/
Troubleshooting:
If you encounter connection issues, verify your Confluent Cloud credentials and network settings.
Ensure your Confluent Cloud cluster is running and the "purchases" topic exists.
This example is intended for educational purposes and may need modifications for production use.
