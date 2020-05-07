## Declare and validate schema

This example shows how to declare a schema by passing a class that inherits from `pulsar.schema.Record` and defining the fields as class variables.

```python
from pulsar.schema import *

class Example(Record):
    a = String()
    b = Integer()
    c = Boolean()
```

With this simple schema definition, you can create producers, consumers and readers that refer to that schema definition.

```python
producer = client.create_producer(
                    topic='my-topic',
                    schema=AvroSchema(Example) )

producer.send(Example(a='Hello', b=1))
```

After the producer is created, the Pulsar broker validates that the existing topic schema is indeed of "Avro" type and that the format is compatible with the schema definition of the `Example` class. If there is a mismatch, an exception is triggered.

Once a producer is created with a certain schema definition, it only accepts objects that are instances of the declared schema class. Similarly, the consumer/reader returns an object and an instance of the schema record class.

```python
consumer = client.subscribe(
                  topic='my-topic',
                  subscription_name='my-subscription',
                  schema=AvroSchema(Example) )

while True:
    msg = consumer.receive()
    ex = msg.value()
    try:
        print("Received message a={} b={} c={}".format(ex.a, ex.b, ex.c))
        # Acknowledge successful processing of the message
        consumer.acknowledge(msg)
    except:
        # Message failed to be processed
        consumer.negative_acknowledge(msg)
```

## Supported schema types

You can use different built-in schema types in Pulsar. All the definitions are in the `pulsar.schema` package.

| Schema | Remark |
| ------ | ----- |
| `BytesSchema` | Get the raw payload as a `bytes` object. No serialization or deserialization is performed. This is the default schema mode. |
| `StringSchema` | Encode/Decode payload as a UTF-8 string. Use the `str` objects. |
| `JsonSchema` | Require record definition. Serialize the record into standard JSON payload. |
| `AvroSchema` | Require record definition. Serialize the record in AVRO format. |

## Schema definition reference

The schema definition is done through a class that inherits from `pulsar.schema.Record`. This class has a number of fields which can be of either `pulsar.schema.Field` type or another nested `Record`. All the fields are specified in the `pulsar.schema` package. The fields match the AVRO field types.

| Field type | Python type | Remark |
| ---------- | ----------- | ----- |
| `Boolean`  | `bool`      |    /   |
| `Integer`  | `int`       |    /   |
| `Long`     | `int`       |     /  |
| `Float`    | `float`     |    /   |
| `Double`   | `float`     |    /   |
| `Bytes`    | `bytes`     |    /   |
| `String`   | `str`       |   /    |
| `Array`    | `list`      | You need to specify the record type for items. |
| `Map`      | `dict`      | The key is always set to `String`. You need to specify the value type. |

In addition, any Python `Enum` type can be used as a valid field type.

### Field parameters

When adding a field, you can use these parameters in the constructor.

| Argument   | Default | Remark                                                        |
| ---------- | ------- | ------------------------------------------------------------ |
| `default`  | `None`  | Set a default value for the field, such as `a = Integer(default=5)`. |
| `required` | `False` | Mark the field as "required". It is set in the schema accordingly. |
