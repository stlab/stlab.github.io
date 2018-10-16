---
layout: free-function
title: stlab::channel
tags: [library]
scope: stlab
pure-name: channel
brief: Creates a pair that consists of a sender and a receiver
annotation: template function
example: channel_example.cpp
defined-in-header: stlab/concurrency/channel.hpp
entities:
  - kind: overloads
    list:
      - name: channel
        pure-name: channel
        declaration: |
            template <typename T, typename E>
            std::pair<sender<T>, receiver<T>> channel(E e)
        description: This function creates a channel that consists of a sending and a receiving part of the channel.
  - kind: parameters
    list:
      - name: e
        description: Executor which is used to send the passed values from the sender down to the receiver.
  - kind: result
    description: Returns a pair of `sender` - `receiver` of type `T` that form a channel
---
