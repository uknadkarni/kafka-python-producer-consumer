<<<<<<< HEAD
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
`CONFLUENT_CLOUD_BOOTSTRAP_SERVERS`, `CONFLUENT_CLOUD_API_KEY`, `CONFLUENT_CLOUD_SECRET`

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
=======
# Kafka Python Producer and Consumer Demo

This project demonstrates a simple Kafka producer-consumer pattern using Python and the Confluent Kafka client library. It simulates an e-commerce purchase tracking system where a producer generates random purchase events and a consumer processes them in real-time.

## What This Project Does

This project implements a basic event streaming architecture with two main components:

1. **Producer (`producer.py`)** - Generates and publishes simulated purchase events to a Kafka topic
   - Creates 10 random purchase events with user IDs and product names
   - Uses delivery callbacks to confirm successful message delivery
   - Publishes messages to the "purchases" topic with user ID as the key and product as the value

2. **Consumer (`consumer.py`)** - Subscribes to and processes purchase events from the Kafka topic
   - Continuously polls for new messages from the "purchases" topic
   - Prints consumed events showing user purchases in real-time
   - Handles graceful shutdown on interruption (Ctrl+C)

## Project Structure

```
├── producer.py          # Kafka producer that generates purchase events
├── consumer.py          # Kafka consumer that processes purchase events
├── requirements.txt     # Python dependencies (confluent-kafka==2.6.0)
└── README.md           # This file
```

## Prerequisites

- Python 3.x
- Confluent Cloud account with API credentials
- A Kafka topic named `purchases` (will be created automatically if it doesn't exist)

## Setup

1. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

2. **Configure Confluent Cloud credentials:**
   Set the following environment variables with your Confluent Cloud credentials:
   ```bash
   export CONFLUENT_CLOUD_BOOTSTRAP_SERVERS="your-bootstrap-servers"
   export CONFLUENT_CLOUD_API_KEY="your-api-key"
   export CONFLUENT_CLOUD_SECRET="your-api-secret"
   ```

## Usage

1. **Start the consumer** (in one terminal):
   ```bash
   python consumer.py
   ```
   The consumer will start polling and wait for messages.

2. **Run the producer** (in another terminal):
   ```bash
   python producer.py
   ```
   The producer will generate 10 purchase events and send them to Kafka.

## Sample Output

**Producer output:**
```
Produced event to topic purchases: key = eabara       value = book
Produced event to topic purchases: key = jsmith      value = alarm clock
Produced event to topic purchases: key = sgarcia     value = t-shirts
...
```

**Consumer output:**
```
Consumed event from topic purchases: key = eabara       value = book
Consumed event from topic purchases: key = jsmith      value = alarm clock
Consumed event from topic purchases: key = sgarcia     value = t-shirts
...
```

## Configuration Details

- **Security**: Uses SASL_SSL with PLAIN authentication for secure connection to Confluent Cloud
- **Producer**: Configured with `acks=all` for maximum durability
- **Consumer**:
  - Consumer group: `kafka-python-getting-started`
  - Auto offset reset: `earliest` (reads all available messages)
  - Graceful shutdown handling

## Troubleshooting

- **Connection issues**: Verify your Confluent Cloud credentials and network connectivity
- **Topic not found**: Ensure the "purchases" topic exists in your Confluent Cloud cluster
- **Authentication errors**: Double-check your API key and secret environment variables
- **Network timeouts**: Verify your bootstrap servers URL is correct

## Educational Purpose

This example is designed for learning Kafka concepts and may require modifications for production use, including:
- Error handling and retry logic
- Monitoring and logging
- Schema management
- Partitioning strategies
- Consumer group management

## References

- [Confluent Developer Documentation](https://developer.confluent.io/get-started/python/)
- [Confluent Kafka Python Client](https://docs.confluent.io/kafka-clients/python/current/overview.html)
>>>>>>> e00fa9c (Initial commit: Kafka Python producer-consumer demo)
