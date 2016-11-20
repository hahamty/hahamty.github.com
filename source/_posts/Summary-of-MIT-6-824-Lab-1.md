---
title: Summary of MIT 6.824 Lab 1
tags:
  - Distributed Systems
  - Map Reduce
date: 2016-11-6 12:30:05
---

# Part I #

Implement `doMap()` and `doReduce()` to distribute the works to different computers/threads.

**Some Important Points**

In `doMap()`, the KV pairs with the same key should be put into the same file. A good way to determine whether KV pairs should be put in the same file is to calculate the hash of the key by a hash function.
In `doReduce()`, the KV pairs after reducing should be sorted before they are finally being merged into a file.

# Part III #

It is easy to have deadlock while using channel in Go. The channel in Go is blocking and the thread has to wait until the lock is released.
