# Kafka Microservices Projects

This repository contains multiple **production-inspired projects built using Apache Kafka and microservices**.
The goal of these projects is to **practice real-world event-driven architecture**, understand how distributed systems communicate using asynchronous messaging, and simulate **production-grade backend systems** used in financial platforms and high-throughput services.

Each project focuses on solving a specific architectural problem using **Kafka, Spring Boot, and containerized infrastructure**.

---

# Project 1: kafka-payment-event-processing-system

## Overview

**kafka-payment-event-processing-system** is a production-style **event-driven payment processing system** built using Apache Kafka and microservices.

The system simulates real-world payment flows where a **Payment Service publishes transaction events** that are processed asynchronously by multiple downstream services such as:

* Fraud Detection Service
* Ledger Service
* Notification Service

This architecture demonstrates how **loosely coupled microservices communicate through event streaming**, allowing the system to scale independently and process transactions reliably.

The design is inspired by real payment architectures used in large financial systems.

---

# Architecture Overview

### Core Flow

1. Payment Service generates a payment event.
2. Event is published to the Kafka topic `payment-initiated`.
3. Fraud Service consumes the event and evaluates the transaction.
4. Based on the fraud decision:

   * Fraud alert event is generated
   * OR payment is authorized
5. Ledger Service updates transaction records.
6. Payment completion event is published.
7. Notification Service sends SMS / Email / Push notifications.

This demonstrates **asynchronous processing pipelines using Kafka topics and consumer groups**.

---

# Event Flow

Payment Service → Publish Event → Kafka Topic → Fraud Service
Fraud Service → Decision → Payment Authorized / Fraud Alert
Ledger Service → Update transaction records
Notification Service → Send notifications to user

---

# Kafka Topics Used

payment-initiated
payment-authorized
payment-completed
fraud-alert

Each topic represents a **stage in the payment lifecycle**.

---

# Microservices in the System

## Payment Service

Responsible for receiving payment requests and publishing payment events to Kafka.

Responsibilities:

* Accept payment requests
* Generate transaction events
* Publish events to Kafka

---

## Fraud Detection Service

Consumes payment events and analyzes transactions for suspicious activity.

Responsibilities:

* Detect fraud patterns
* Generate fraud alerts
* Approve or reject transactions

---

## Ledger Service

Handles financial record keeping and transaction persistence.

Responsibilities:

* Update transaction records
* Maintain financial ledger
* Publish payment completion events

---

## Notification Service

Sends notifications to the user when the payment status changes.

Responsibilities:

* Send SMS notifications
* Send email alerts
* Send push notifications

---

# Technology Stack

Backend

* Java
* Spring Boot

Event Streaming

* Apache Kafka

Containerization

* Docker

Orchestration

* Kubernetes

Other tools

* REST APIs
* Microservices architecture
* Event-driven design patterns

---

# System Architecture Concepts Demonstrated

This project demonstrates several important distributed system concepts:

Event-driven architecture
Microservices communication via Kafka
Producer and consumer patterns
Kafka topics and partitions
Consumer groups and scalability
Asynchronous processing
Loose coupling between services
Fault-tolerant system design

---

# Folder Structure (Example)

kafka-payment-event-processing-system
│
├── payment-service
├── fraud-service
├── ledger-service
├── notification-service
│
├── kafka-config
├── docker
├── kubernetes
└── README.md

---

# Learning Outcomes

By implementing this project, you will gain practical experience with:

Designing event-driven microservices architectures
Building Kafka producers and consumers using Spring Boot
Designing scalable messaging systems
Handling asynchronous workflows in distributed systems
Understanding Kafka topics, partitions, and consumer groups
Implementing fault-tolerant communication between services
Containerizing applications using Docker
Deploying microservices using Kubernetes

This project helps developers understand **how real production systems process high-volume transactions using event streaming**.

---

# Future Enhancements

Potential improvements to this project include:

Adding retry mechanisms and dead-letter queues
Implementing idempotent consumers
Adding schema validation using schema registry
Introducing monitoring with metrics and dashboards
Simulating high TPS workloads for performance testing

---

# Goal of This Repository

The goal of this repository is to build **hands-on expertise in Kafka-based microservice architectures** and to simulate real-world backend systems used in financial platforms and large-scale distributed environments.

---
