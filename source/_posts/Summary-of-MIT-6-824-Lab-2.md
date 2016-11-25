---
title: Summary of MIT 6.824 Lab 2
tags:
  - Distributed Systems
  - Raft protocol
date: 2016-11-25 13:46:16
---


# Task 1 #

Implement leader election (`RequestVote()`) and heartbeats (empty `AppendEntries()`).

**Some Important Points**

- A candidate only votes for itself.
- Any server that finds a larger term will become follower state.
- A constant loop for each server should be implemented to determine whether its timer is fired.
- The timeout of the follower state and the candidate state is better to be the same, since a candidate may be not up to date and be rejected in `RequestVote()`.
- All the modification to the variables in a server should be in critical session to make the operation atomic. However, we should be careful about the locking step, since it is easy to deadlock and to ask for a lock twice (the thread will be blocked by itself).

# Task 2 #

Implement full `AppendEntries()` RPC after `Start()` being called.

**Some Important Points**

- In `RequestVote()`, we only need the last term and the last index of the server to determine whether a candidate is up to date.
- In `AppendEntries()`, we only need to delete the incompatible log entries.

# Task 3 #

Implement persisting in Raft.

**Some Important Points**

- The variables needed to be stored are `currentTerm`, `voteFor`, and `logs`, while the other variables are used to record volatile states, so their value can be calculated during runtime.

# Other notes #

- It is imperative to determine the state of server, such as `raftState` and `currentTerm`, before doing any operation.
- The leader only commit the logs of its current term to avoid overwrite previous logs incorrectly.
- Same update can be committed for several times in Lab 2, since in Lab 3 we will check whether the committed update is duplicated.
- `NextIndex` should be added into `AppendEntriesReply` to facilitate the synchronization between leader and follower. Otherwise, the last few tests will be failed.

# Reference #
[In Search of an Understandable Consensus Algorithm](https://pdos.csail.mit.edu/6.824/papers/raft-extended.pdf)
