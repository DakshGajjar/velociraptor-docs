---
title: Generic.Client.Trace
hidden: true
tags: [Client Artifact]
---

This artifact collects profiling information about the running
client. The artifact is automatically added when the GUI selects a
non zero Trace frequency.

NOTE: You can also add the artifact directly, but then you will need
to cancel the collection manually since it will continue to run
until the timeout is reached.

Minimum Version: 0.6.8


```yaml
name: Generic.Client.Trace
description: |
  This artifact collects profiling information about the running
  client. The artifact is automatically added when the GUI selects a
  non zero Trace frequency.

  NOTE: You can also add the artifact directly, but then you will need
  to cancel the collection manually since it will continue to run
  until the timeout is reached.

  Minimum Version: 0.6.8

parameters:
- name: FrequencySec
  type: int
  default: 10

sources:
- query: |
    SELECT * FROM if(condition=version(function="trace"),
    then={
       SELECT trace() AS TraceFile
       FROM clock(start=0, period=FrequencySec)
    })

```
