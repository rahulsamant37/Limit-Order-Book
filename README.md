# High-Performance Limit Order Book (LOB) & Matching Engine

A high-performance Limit Order Book (LOB) and matching engine implementation in C++ focused on low-latency order processing, efficient memory management, and realistic exchange-style price-time priority matching.

## Overview

This project demonstrates the core architecture used in modern electronic trading systems:

- Price-Time Priority Matching
- Limit Orders
- Market Orders
- Order Cancellation
- Object Pooling
- O(1) Order Lookup
- Benchmarking Framework
- Low-Latency Memory Management

The implementation includes a synthetic benchmark that executes 1,000,000 order operations and reports latency and throughput statistics.

---

## Features

### Matching Engine

- Buy and Sell order books
- Price-Time (FIFO) execution priority
- Limit order support
- Market order support
- Partial fills
- Full fills
- Order cancellation

### Performance Optimizations

#### Object Pooling

Orders and price levels are pre-allocated to avoid heap allocations on the critical execution path.

#### Cache-Friendly Design

```cpp
struct alignas(64) Order
