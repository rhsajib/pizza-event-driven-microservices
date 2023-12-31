
# Random Pizza Generator
an event-driven microservices demo with Python and Kafka

## Reference
- [Project details](https://www.confluent.io/en-gb/blog/event-driven-microservices-with-python-and-kafka/?session_ref=https://docs.confluent.io/&_gl=1*16rmq2t*_ga*Mzc4OTUwMTU2LjE3MDI4MDgyNzc.*_ga_D2D3EGKSGD*MTcwMjgxMTY4MC4yLjEuMTcwMjgxMjAxMi4zNC4wLjA.&_ga=2.217881554.593537590.1702808277-378950156.1702808277)
- [Source code](https://github.com/confluentinc/demo-scene/tree/master/python-microservices)

## Description

This demo consists of the following projects:

  - *pizza-service* a Flask app with Kafka support.
  - *sauce-service* a basic Python app with Kafka.
  - *cheese-service* a basic Python app with Kafka.
  - *meat-service* a basic Python app with Kafka.
  - *veggie-service* a basic Python app with Kafka.


The demo was built using Confluent Cloud, the Cloud-native service for Apache Kafka. If you don't have an account on Confluent Cloud, you can set that up [here](https://www.confluent.io/confluent-cloud).

## Running the demo

Before running this demo, you will need to update the `config.properties` file in each project. Replace the fields marked with `< >` using values from your Confluent Cloud cluster. Also, you will need to create 5 topics in Confluent Cloud. They can each have 1 partion (or more if you so desire): `pizza`, `pizza-with-sauce`, `pizza-with-cheese`, `pizza-with-meat`, and `pizza-with-veggies`. 

Once all five services are up and running, you can issue the following `curl` command to send an order for 3 random pizzas.
`curl -X POST http://localhost:5000/order/5`  

This will trigger a series of events which will result in a completed pizza order with the five pizzas, and it will return a UUID of that pizza order. Of course you can alter that last value in the URL to get a different number of pizzas.  (I was a bit hungry when I wrote this.)

To see your pizzas in all their hot, delicious glory, run the following `curl` command using the UUID returned from the first call.

curl http://localhost:5000/order/{{pizza-order-UUID}}


*When you are done working with this demo project, you can delete these topics to avoid additional charges.*


## Related Documentation that might be helpful

### Confluent Cloud 

[Quik-start Guide](https://docs.confluent.io/cloud/current/get-started/index.html)

### Python and Kafka 

- [Quick-start Guide](https://developer.confluent.io/get-started/python)
- [Python Kafka Client](https://docs.confluent.io/clients-confluent-kafka-python/current/overview.html)
- [Python Kafka Articles](https://www.confluent.io/blog/tag/python/)

---
