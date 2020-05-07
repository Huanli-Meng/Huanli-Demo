## Schema types

Currently, the following schema formats are available for Java.

* No schema or the byte array schema (which can be applied using `Schema.BYTES`):

  ```java
  Producer<byte[]> bytesProducer = client.newProducer(Schema.BYTES)
        .topic("some-raw-bytes-topic")
        .create();
  ```

  Or, 

  ```java
  Producer<byte[]> bytesProducer = client.newProducer()
        .topic("some-raw-bytes-topic")
        .create();
  ```

* `String` schema for normal UTF-8-encoded string data

  ```java
  Producer<String> stringProducer = client.newProducer(Schema.STRING)
        .topic("some-string-topic")
        .create();
  ```

* JSON schemas for POJOs

  ```java
  Producer<MyPojo> pojoProducer = client.newProducer(Schema.JSON(MyPojo.class))
        .topic("some-pojo-topic")
        .create();
  ```

* Protobuf schema. The following example shows how to create the Protobuf schema and use it to instantiate a new producer.

  ```java
  Producer<MyProtobuf> protobufProducer = client.newProducer(Schema.PROTOBUF(MyProtobuf.class))
        .topic("some-protobuf-topic")
        .create();
  ```

* Define Avro schemas. The following code snippet demonstrates how to create and use Avro schema.

  ```java
  Producer<MyAvro> avroProducer = client.newProducer(Schema.AVRO(MyAvro.class))
        .topic("some-avro-topic")
        .create();
  ```
