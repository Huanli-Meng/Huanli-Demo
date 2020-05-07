## Producer operations

The following table lists methods available for the Pulsar Node.js producer.

| Method | Description | Return type |
| :----- | :---------- | :---------- |
| `send(Object)` | Publishes a [message](#messages) to the producer's topic. When the message is successfully acknowledged by the Pulsar broker, or an error will be thrown, the Promise object run executor function. | `Promise<null>` |
| `flush()` | Sends message from send queue to Pulser broker. When the message is successfully acknowledged by the Pulsar broker, or an error will be thrown, the Promise object run executor function. | `Promise<null>` |
| `close()` | Closes the producer and releases all resources allocated to it. If `close()` is called then no more messages will be accepted from the publisher. This method will return Promise object, and when all pending publish requests have been persisted by Pulsar then run executor function. If an error is thrown, no pending writes will be retried. | `Promise<null>` |

## Consumer operations

The following table lists methods available for the Node.js consumer.

| Method | Description | Return type |
| :----- | :---------- | :---------- |
| `receive()` | Receive a single message from the topic. When the message is available, the Promise object runs executor function and gets the message object. | `Promise<Object>` |
| `receive(Number)` | Receive a single message from the topic with specific timeout in milliseconds. | `Promise<Object>` |
| `acknowledge(Object)` | Acknowledge a message to the Pulsar broker by message object. | `void` |
| `acknowledgeId(Object)` | Acknowledge a message to the Pulsar broker by message ID object. | `void` |
| `acknowledgeCumulative(Object)` | Acknowledge *all* the messages in the stream, up to and including the specified message. The `acknowledgeCumulative` method will return void, and send the ack to the broker asynchronously. After that, the messages will *not* be redelivered to the consumer. Cumulative acking can not be used with a shared subscription type. | `void` |
| `acknowledgeCumulativeId(Object)` | Acknowledge *all* the messages in the stream, up to and including the specified message ID. | `void` |
| `close()` | Close the consumer, disabling its ability to receive messages from the broker. | `Promise<null>` |

## Reader operations

The following table lists methods available for the Node.js reader.

| Method | Description | Return type |
| :----- | :---------- | :---------- |
| `readNext()` | Receive the next message on the topic (analogous to the `receive` method for [consumers](#consumer-operations)). When the message is available, the Promise object runs the executor function and gets the message object. | `Promise<Object>` |
| `readNext(Number)` | Receive a single message from the topic with specific timeout in milliseconds. | `Promise<Object>` |
| `hasNext()` | Return whether the broker has next message in target topic. | `Boolean` |
| `close()` | Close the reader. Therefore, the reader fails to receive messages from the broker. | `Promise<null>` |

### Message object operations

In Pulsar Node.js client, you can receive (or read) message object as a consumer (or reader).

The following table lists methods available for the producer message.

| Method                  | Description                                                  | Return type     |
| :---------------------- | :----------------------------------------------------------- | :-------------- |
| `getTopicName()`        | Getter method of topic name                                  | `String`        |
| `getProperties()`       | Getter method of properties                                  | `Array<Object>` |
| `getData()`             | Getter method of message data                                | `Buffer`        |
| `getMessageId()`        | Getter method of [message id object](#message-id-object-operations) | `Object`        |
| `getPublishTimestamp()` | Getter method of publish timestamp                           | `Number`        |
| `getEventTimestamp()`   | Getter method of event timestamp                             | `Number`        |
| `getPartitionKey()`     | Getter method of partition key                               | `String`        |

### Message ID object operations

In the Node.js client, you can get the message ID object from the message object.

The following table lists methods available for the message ID object.

| Method        | Description                                         | Return type |
| :------------ | :-------------------------------------------------- | :---------- |
| `serialize()` | Serialize the message id into a Buffer for storing. | `Buffer`    |
| `toString()`  | Get message id as String.                           | `String`    |

The client has static method of the message ID object. You can access it as `Pulsar.MessageId.someStaticMethod` too. The following table lists static methods available for the message ID object.

| Method                | Description                                                  | Return type |
| :-------------------- | :----------------------------------------------------------- | :---------- |
| `earliest()`          | MessageId representing the earliest, or oldest available message stored in the topic | `Object`    |
| `latest()`            | MessageId representing the latest, or last published message in the topic | `Object`    |
| `deserialize(Buffer)` | Deserialize a message Id object from a Buffer.               | `Object`    |
