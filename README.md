# async-mixpanel-client
[![Build Status](https://travis-ci.org/BrandwatchLtd/async-mixpanel-client.svg)](https://travis-ci.org/BrandwatchLtd/async-mixpanel-client) 
[![Coverage Status](https://coveralls.io/repos/BrandwatchLtd/async-mixpanel-client/badge.svg?branch=master&service=github)](https://coveralls.io/github/BrandwatchLtd/async-mixpanel-client?branch=master) 
[![Maven Central](https://maven-badges.herokuapp.com/maven-central/com.brandwatch.mixpanel/async-mixpanel-client/badge.svg)](https://maven-badges.herokuapp.com/maven-central/com.brandwatch.mixpanel/mixpanel-client)

## What Is This? 
This repo hosts a wrapper around the official Mixpanel Java client.

## Why?
The official Mixpanel client falls down in a few ways. First it relies a lot on null parameters. When something is optional you just don't pass it in. However this can be confusing and can make code more complicated than is required so this wrapper provides full methods for every valid combination of parameters.

Second the official client is synchronous adding delay to your code. We live in a multicore world these days so this wrapper offloads that sending delay to another thread and deals with queueing and scheduling for you.

## How?
To add the dependency to Maven:

```xml
<dependency>
  <groupId>com.brandwatch.mixpanel</groupId>
  <artifactId>mixpanel-client</artifactId>
  <version>${mixpanel.version}</version>
</dependency>
```

You can find the latest version number on the releases page.

```java
ClientConfig config = new ClientConfigBuilder()
                          .maxBatchSize(1000)
                          .maxBatchTimeInSeconds(10)
                          .projectToken("aaabbbccc111222333")
                          .build();

MixpanelClient client = new MixpanelClient(config);

client.event("my-event-key");
```

## Requirements
Java 8 or above

## Building The Project
`mvn clean package`

## Licence
This library is made avaliable under the LGPL 3.0 licence. Please see LICENCE.txt for more details.
