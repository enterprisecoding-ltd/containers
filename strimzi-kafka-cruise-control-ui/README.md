# strimzi-kafka-cruise-control-ui

A container image based on [Strimzi Kafka](https://github.com/rancher/shell) with [cruise-control-ui](https://github.com/adnanh/webhook)

Use following commands to build & push to Quay.io

```
export KAFKA_VERSION=0.36.1-kafka-3.5.1
export CC_UI_VERSION=0.4.0
docker build --pull -t quay.io/enterprisecoding/kafka:${KAFKA_VERSION}-ui-${CC_UI_VERSION} --build-arg="KAFKA_VERSION=${KAFKA_VERSION}" --build-arg="CC_UI_VERSION=${CC_UI_VERSION}" .
docker push quay.io/enterprisecoding/kafka:${KAFKA_VERSION}-ui-${CC_UI_VERSION}
```