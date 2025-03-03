---
title: "Camel Quarkus 1.7.0 Released"
date: 2021-02-24
authors: ["ppalaga"]
categories: ["Releases", "Camel Quarkus"]
preview: "Camel Quarkus 1.7.0 Released"
summary: "The highlights of Camel Quarkus 1.7.0"
---

<sub><sup>Original image by <a href="https://commons.wikimedia.org/wiki/User:99of9">Toby Hudson</a> <a href="https://creativecommons.org/licenses/by-sa/3.0">CC BY-SA 3.0</a> via <a href="https://en.wikipedia.org/wiki/Camel_racing#/media/File:CamelRacingCamelCup2009Heat.JPG">Wikipedia</a></sup></sub>

We are pleased to announce the release 1.7.0 of Camel Quarkus! Here are the highlights.

## Camel 3.8.0 and Quarkus 1.12.0.Final

We stand on the shoulders of two giants. Please check the release announcements for
[Camel 3.8.0](/blog/2021/02/Camel38-Whatsnew/) and [Quarkus 1.12.0.Final](https://quarkus.io/blog/quarkus-1-12-0-final-released/) to learn about the news they bring.

The [change of default packaging format](https://quarkus.io/blog/quarkus-1-12-0-final-released/#fast-jar-as-default)
to Fast JAR in Quarkus 1.12 is worth mentioning also here. Before Camel Quarkus 1.7.0 you used to start your application
in JVM mode via something like

```sh
$ java -jar target/*-runner.jar
```

and now since Camel Quarkus 1.7.0, you have to use

```sh
$ java -jar target/quarkus-app/quarkus-run.jar
```

Your Docker files and deployment scripts might need an adjustment when you upgrade to Camel Quarkus 1.7.0.

You can go back to the original behavior by setting `quarkus.package.type=legacy-jar` in your
`application.properties`.

## Support for more Camel components

Camel Quarkus brings support for six new Camel components:

* [Azure Event Hubs](/camel-quarkus/next/reference/extensions/azure-eventhubs.html)
* [Kamelet](/camel-quarkus/next/reference/extensions/kamelet.html)
* [OAI-PMH](/camel-quarkus/next/reference/extensions/oaipmh.html)
* [Spring RabbitMQ](/camel-quarkus/next/reference/extensions/spring-rabbitmq.html)
* [XML Security Sign and Verify](/camel-quarkus/next/reference/extensions/xmlsecurity.html)
* [JFR](/camel-quarkus/next/reference/extensions/jfr.html) (JVM only)

Components newly supported in native mode:

* [AtlasMap](/camel-quarkus/next/reference/extensions/atlasmap.html)
* [AWS 2 Eventbridge](/camel-quarkus/next/reference/extensions/aws2-eventbridge.html)
* [AWS 2 Kinesis and Firehose](/camel-quarkus/next/reference/extensions/aws2-kinesis.html)
* [Azure Storage Queue Service](/camel-quarkus/next/reference/extensions/azure-storage-queue.html)
* [Cassandra CQL](/camel-quarkus/next/reference/extensions/cassandraql.html)
* [IPFS](/camel-quarkus/next/reference/extensions/ipfs.html)
* [PubNub](/camel-quarkus/next/reference/extensions/pubnub.html)
* [StAX](/camel-quarkus/next/reference/extensions/stax.html)
* [CBOR](/camel-quarkus/next/reference/extensions/cbor.html)
* [Syslog](/camel-quarkus/next/reference/extensions/syslog.html)

## Deprecated extensions

We are following the deprecation of the underlying Camel components:

- AWS EC2 (SDK v1)
- AWS ECS (SDK v1)
- AWS EKS (SDK v1)
- AWS IAM (SDK v1)
- AWS Kinesis (SDK v1)
- AWS KMS (SDK v1)
- AWS Lambda (SDK v1)
- AWS S3 (SDK v1)
- AWS SDB (SDK v1)
- AWS SNS (SDK v1)
- AWS SQS (SDK v1)
- AWS SWF (SDK v1)
- AWS Translate (SDK v1)
- Azure (old SDK)
- Javax Websocket (JSR 356)

## More test coverage for AWS 2 components

So far, our AWS SDK v2 extensions were not tested properly. We started adding
[tests](https://github.com/apache/camel-quarkus/tree/master/integration-tests-aws2) that check their behavior
against the real AWS services. Some of the tests can also run against a
[Localstack](https://github.com/localstack/localstack) mock container.

## Full Changelog of Camel Quarkus 1.7.0

* [Fixed issues](https://github.com/apache/camel-quarkus/milestone/11?closed=1)
* [All commits](https://github.com/apache/camel-quarkus/compare/1.6.0...1.7.0)

## Known issues

* [Upgrading to Jackson 2.12.1 via Quarkus BOM 1.12 breaks Azure SDK v12 extensions](https://github.com/apache/camel-quarkus/issues/2207) - possible workarounds: force Jackson 2.11.3 in your application or stay on Camel Quarkus 1.6.0
* [Camel Quarkus OptaPlanner does not work as of Quarkus 1.12 in apps generated by code.quarkus.io](https://github.com/apache/camel-quarkus/issues/2253) - this is caused by a conflicting OptaPlanner version in Quarkus Universe BoM. Workaround:
use plain Camel Quarkus BoM instead of Quarkus Universe BoM.

## What's next?

Camel Quarkus 1.8.0 should appear within a couple of weeks, shortly after Quarkus 1.13.

There is still a lot of [Camel components to port](https://github.com/apache/camel-quarkus/issues?q=is%3Aissue+is%3Aopen+label%3Aextension) to Quarkus.
Please upvote your favorites, or even better [contribute](/camel-quarkus/next/contributor-guide/index.html)!
