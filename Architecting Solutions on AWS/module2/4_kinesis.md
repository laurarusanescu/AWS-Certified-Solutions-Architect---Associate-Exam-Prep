# Differences Between Amazon Kinesis Services — Notes

---

# Amazon Kinesis Family (EXAM CRITICAL)

The Amazon Kinesis Family is designed to:
- Collect
- Process
- Analyze

real-time streaming data.

Common data types:
- Website clickstreams
- Application logs
- Financial transactions
- IoT telemetry
- Video/audio streams

Key advantage:
- Process data **as it arrives**
- Enable real-time insights

---

# 1️⃣ Amazon Kinesis Data Streams

## What It Is
- Massively scalable real-time streaming service
- Designed for custom real-time processing
- Data available in milliseconds

---

## Key Characteristics
- Capture gigabytes per second
- Low latency (sub-second)
- Full control over consumers
- Requires consumer application (Lambda, EC2, etc.)

---

## Best For
- Real-time dashboards
- Anomaly detection
- Dynamic pricing
- Custom stream processing logic

---

## Trade-Off
- More operational responsibility than Firehose
- Must manage stream scaling and consumer logic

---

# 2️⃣ Amazon Kinesis Data Firehose (EXAM FAVORITE)

## What It Is
- Fully managed delivery service
- Automatically loads streaming data into destinations

---

## Supported Destinations
- Amazon S3
- Amazon Redshift
- Amazon OpenSearch Service
- HTTP endpoints
- SaaS tools (Datadog, Splunk, etc.)

---

## Key Features
- Fully managed
- Automatic scaling
- Built-in:
  - Batching
  - Compression
  - Encryption
  - Transformation

---

## Latency
- Higher than Data Streams
- Batch-based delivery (e.g., 60 seconds)

---

## Best For
- Loading clickstream data into S3
- Data lake ingestion
- Minimal operational overhead

---

# 3️⃣ Amazon Kinesis Data Analytics

## What It Is
- Real-time streaming analytics service
- Built on Apache Flink
- Serverless

---

## Key Characteristics
- Process streaming data in real time
- Automatic scaling
- No infrastructure to manage
- Pay per resource consumption

---

## Best For
- Stateful stream processing
- Continuous real-time analytics
- Aggregations over streaming windows

---

# 4️⃣ Amazon Kinesis Video Streams

## What It Is
- Streaming video ingestion service
- Secure video streaming to AWS

---

## Key Features
- Stores and indexes video
- Integrates with:
  - Amazon Rekognition Video
  - ML frameworks
- Supports WebRTC for real-time streaming

---

## Best For
- Video analytics
- Surveillance systems
- Live streaming
- Computer vision applications

---

# Comparing Kinesis Services (EXAM FAVORITE)

| Service | Purpose | Latency | Management | Best Use Case |
|-----------|----------|----------|-------------|----------------|
| Data Streams | Custom stream processing | Milliseconds | Managed but requires consumer logic | Real-time analytics |
| Data Firehose | Delivery to storage/analytics | Seconds (batch-based) | Fully managed | Data lake ingestion |
| Data Analytics | Real-time stream processing | Near real-time | Fully managed | Streaming transformations |
| Video Streams | Video ingestion | Real-time | Fully managed | Video ML & analytics |

---

# Clickstream Scenario Mapping (Week 2)

For clickstream ingestion:
- Use **Kinesis Data Firehose** → Deliver to S3 (simplest, managed)
- Use **Kinesis Data Streams** → If ultra-low latency required
- Use **Kinesis Data Analytics** → For real-time aggregations
- Video Streams → Not relevant for clickstream

---

# Exam Takeaway Summary

- Kinesis = real-time streaming family
- Data Streams = low-latency custom streaming
- Firehose = fully managed delivery to S3/Redshift
- Data Analytics = streaming processing (Flink)
- Video Streams = video ingestion
- Choose based on latency vs operational complexity
