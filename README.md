# channel-sync-lib

A channel is a synchronization tool that works through message passing. Think of it as a queue or buffer with a fixed size. Threads (Senders) can send messages by adding them to the queue, and other threads with access to the channel (Receivers) can pick up those messages by removing them from the queue. A channel can have multiple senders and receivers interacting with it simultaneously.

Channels serve as the foundation for various concurrent programming techniques. They are widely used in Google's Go language and are highly effective for high-level concurrent programming. In this project, I created my version of a channel to facilitate communication between multiple clients. Each client can either write to or read from the channel. It’s important to note that multiple clients may be reading from and writing to the channel at the same time. I focused on designing a channel that functions correctly and avoids being slow or inefficient, although performance was not the main priority—functionality was. I avoided designs that waste CPU time, such as those that rely on fixed-time sleeps.

There are different types of channels, depending on whether sending/receiving is blocking or non-blocking. In blocking mode, receivers wait until there is data to retrieve, while in non-blocking mode, they simply return if there is nothing to receive. Similarly, in blocking mode, if the queue is full, senders wait until space is available, whereas in non-blocking mode, they leave without sending. In this project, I implemented both blocking and non-blocking send/receive functions.

You will find all of my code implementation in `channel.h`, `channel.c`, `linked_list.h`, and `linked_list.c`. The remaining code, including the actual buffer implementation and unit tests to ensure code efficiency, was provided by Timothy Zhu, a Computer Science professor at The Pennsylvania State University.

