#Kafka Consumer Pact Contract Validator

##Running Locally
`./gradlew bootRun` then start services in `kafka-custer.yml` separately
or
`make start` will start the app and required services

##Creating Pacts and Running Tests
`./gradlew check` will create and test the pacts specified in `ProductsPactTest.java` and store the results in `build/pacts`

##Deploying Pacts
`./gradlew pactPublish` will deploy the pacts specified in `build/pacts` to https://mzamorahappymoney.pactflow.io/

##Other Information

This is an example of a Java kafka consumer that uses Pact, [Pactflow](https://pactflow.io) and Travis CI to ensure that it is compatible with the expectations its consumers have of it.

The project uses a Makefile to simulate a very simple build pipeline with two stages - test and deploy.

See the canonical consumer example here: https://github.com/pactflow/example-consumer
See also the full [Pactflow CI/CD Workshop](https://docs.pactflow.io/docs/workshops/ci-cd) for which this can be substituted in as the "consumer".

In the following diagram, we'll be testing the "Product API", a simple HTTP service that exposes product information as a REST API, which is fed events from an Event API on the `product` topic.

![Kafka Architecture](docs/kafka.png "Kafka Architecture")

## Pre-requisites

**Software**:

https://docs.pactflow.io/docs/workshops/ci-cd/set-up-ci/prerequisites/

## Usage

* Running the API and kafka listener locally: `make start`
* Producing test events into the `product` topic: `make test-events`
* Retrieve latest products: `curl localhost:8080/products`