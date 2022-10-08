# Spring Integration Knowledge

## Core
+ Provide a simple model for integration solutions.
+ Provide asynchronous, message-driven behavior in a Spring application.
+ Supports integration with external systems via declarative adapters.
+ Spring Integration typically implements a "pipes-and-filters" approach where the "filters" are components that produce or consume messages and the "pipes" transport messages.

![](images/overview.png)

### Messaging Channels

<details>
  <summary>What is Messaging Channels?</summary>
  <br/>
  
  The `MessageChannel` decouples message producers from messgae consumers.

  ```
  public interface MessageChannel {

      boolean send(Message message);

      boolean send(Message message, long timeout);
  }
  ```
  _`MessageChannel` interface_
</details>
<details>
  <br/>
  <summary>Messaging Channels</summary>
  
  + Messaging Channels in EIP
  
  ![](images/Messaging_Channels.jpeg)
  
  + Messaging Channels in Spring Integration
    + QueueChannel
    + PublishSubscribeChannel
    + PriorityChannel
    + DirectChannel
    + ...
</details>
<details>
  <br/>
  <summary>Messaging Channel API in Spring Integration</summary>
  
   These two sub-interfaces that define the buffering (pollable) and non-buffering (subscribable) channel behavior.
   
   ```
   public interface PollableChannel extends MessageChannel {

      Message<?> receive();

      Message<?> receive(long timeout);

   }
   ```
   **_PollableChannel_**
   ```
   public interface SubscribableChannel extends MessageChannel {

      boolean subscribe(MessageHandler handler);

      boolean unsubscribe(MessageHandler handler);

   }
   ```
   **_SubscribableChannel_**
</details>

<details>
  <br/>
  <summary>Channel Interceptor</summary>
  
   
</details>

### Messages
The Spring Integration `Message` is a generic container for data.
```
public interface Message<T> {

    T getPayload();

    MessageHeaders getHeaders();

}
```
### Message Endpoint
<details>
  <br/>
  <summary>What is Message Endpoint?</summary>
  
  A Message Endpoint represents the “filter” of a _pipes-and-filters_ architecture. One of the primary goals is to simplify the development of enterprise integration solutions.
  
  In other words, you should **not** implement the consumer or producer directly. Instead, you can **focus on** your business implementation. 
  
  Just as a controller handles HTTP requests, the message endpoint handles messages. Just as controllers are mapped to URL patterns, message endpoints are mapped to message channels.
  
</details>
<details>
  <summary>Messgae endpoints</summary>
  <br/>
  
  + Messgae endpoints in EIP
  
  ![](images/message_endpoint.jpeg)
  
  + Messgae endpoints in Spring Integration
    + Channel Adapter
    + Service Activator
    + Messaging Gateways
</details>

### Message Routing
<details>
  <br/>
  <summary>What is Message Routing?</summary>
  
</details>
<details>
  <br/>
  <summary>Message routings are supported by Spring Integration</summary>
  
</details>

### Message Transformation
<details>
  <br/>
  <summary>What is Message Transformation?</summary>
  
</details>
<details>
  <br/>
  <summary>Message transformation support by Spring Integration</summary>
  
</details>

## HTTP
## JMS
