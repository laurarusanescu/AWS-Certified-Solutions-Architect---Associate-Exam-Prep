# Event-Driven Architectures on AWS — Notes

---

## Why Move to Event-Driven Architecture? (EXAM CRITICAL)

Current problem:
- Synchronous web application
- Tight coupling between services
- Cascading failures
- Poor scalability during spikes

Solution:
- **Event-driven architecture**
- Decoupled services
- Independent scaling
- Increased resilience

---

## What Is an Event-Driven Architecture?

An **event-driven architecture (EDA)**:
- Uses events to trigger communication between services
- Services are loosely coupled
- Common in microservices-based applications

---

## What Is an Event?

An event is:
- A **change in state**
- An update in the system

Examples:
- Order placed
- Item added to cart
- Order shipped

---

## Types of Events

### 1. State-Carrying Events
- Include full data payload
- Example:
  - Order details
  - Price
  - Delivery address

### 2. Identifier-Based Events
- Contain a reference
- Consumers fetch full data separately

---

## Core Components of Event-Driven Architecture (EXAM FAVORITE)

1. **Event Producers**
   - Publish events

2. **Event Routers**
   - Route events to appropriate targets

3. **Event Consumers**
   - React to events

➡️ Producers and consumers are **decoupled**

---

## Benefits of Event-Driven Architecture

- Independent scaling
- Independent deployment
- Improved resilience
- Better fault isolation
- Reduced cascading failures
- Handles peak demand efficiently

---

# Amazon EventBridge vs Amazon SNS (EXAM FAVORITE)

Both support event-driven systems but serve different needs.

---

## Amazon EventBridge

### Best For:
- Events from AWS services
- SaaS integrations
- Structured JSON events
- Rule-based routing

### Key Characteristics:
- Serverless event bus
- Rule-based filtering
- Event pattern matching
- Integrates with 90+ AWS services
- ~0.5 second typical latency
- Moderate throughput (can request increase)

### Targets Include:
- AWS Lambda
- Amazon SQS
- Amazon SNS
- Kinesis Streams
- API destinations
- Other event buses

---

## Amazon SNS

### Best For:
- High throughput
- Low latency
- Simple pub/sub messaging
- High fan-out

### Key Characteristics:
- Near-unlimited throughput
- < 30 ms typical latency
- Supports multiple endpoints:
  - Lambda
  - SQS
  - HTTP/S
  - Email
  - SMS
  - Mobile push
- Unstructured message support

### Why SNS Was Chosen
- Simple messaging between application components
- Straightforward pub/sub model

---

# Amazon DynamoDB Streams (EXAM FAVORITE)

## What Is DynamoDB Streams?
- Captures item-level changes in a DynamoDB table
- Stores changes for **24 hours**
- Near real-time

---

## Key Guarantees:
- Each record appears exactly once
- Preserves order of modifications
- No impact on table performance

---

## Common Use Case:
- Trigger Lambda when:
  - New order inserted
  - Order updated
- Build reactive workflows

---

## Comparing EventBridge vs SNS

| Feature | EventBridge | SNS |
|----------|------------|-----|
| Best For | AWS/SaaS events | App-to-app messaging |
| Latency | ~500ms | <30ms |
| Throughput | Moderate | Nearly unlimited |
| Message Format | Structured JSON | Any format |
| Routing | Rule-based filtering | Topic-based fan-out |

---

## Why Event-Driven Fits This Customer

Customer needs:
- Decoupling downstream services
- Handling spiky demand
- Preventing cascading failures
- Reliable asynchronous processing

Event-driven architecture enables:
- Independent processing
- Better resilience
- Automatic scaling
- Loose coupling

---

## Exam Takeaway Summary

- Event-driven = decoupled microservices
- Producers → Router → Consumers
- SNS = high throughput, low latency pub/sub
- EventBridge = structured routing & SaaS integration
- DynamoDB Streams = change data capture
- EDA improves resilience and scalability
