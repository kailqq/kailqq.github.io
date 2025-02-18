---
comments: true
---

# Fundamentals of computer design

## Introduction

### Classer of computers

- Desktop computers (or personal computers .aka. PC)
      - General-purpose,vatiety of software
      - Emphasize good performance for a single user at relatively low cost
      - Mostly execute third-party software(第三方软件)

- Server Computers
      - Emphasize great performance for a few complex applications
      - Or emphasize reliable performance for many users at once
      - Greater computing power, storage, or network capacity than personal computers

- Embedded computers
      - Largest class and most diverse
      - Hidden as components of systems
      -  Stringent power, cost, and size constraints,performance.

- Personal Mobile Devices
      - Such as smartphones, tablets/ipad, and wearables
      - generally have the same design requirements as PCs

- Supercomputer
      - Computer cluster(集群)
      - High capacity,prformance, and reliability
      - Range to building size(即大型机)


#### Class By Flynn

福林分类法

- SISD: Single Instruction Stream, Single Data Stream
- SIMD: Single Instruction Stream, Multiple Data Stream
- MISD: Multiple Instruction Stream, Single Data Stream
- MIMD: Multiple Instruction Stream, Multiple Data Stream

!!!info "definition"
    - IS: Instruction Stream
    - DS: Data Stream
    - CS: Control Stream
    - CU: Control Unit
    - PU: Processing Unit
    - MM&SM: Memory Module & Storage Module

See as follows:

<div align="center">
    <img src="../img/lec1-1.png" width="70%">
</div>