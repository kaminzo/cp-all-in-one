![image](../images/confluent-logo-300-2.png)

# JDBC Source for SQL Server

<https://www.confluent.io/hub/confluentinc/kafka-connect-jdbc>

Build image

`docker build -t localbuild/kafka-connect-datagen-jdbc-source:0.4.0-6.0.1 -f Dockerfile .`

# Query

Kafka connect will append the following to the query in `timestamp+incrementing` mode:

`WHERE "DBTime" < ? AND (("DBTime" = ? AND "DBKey" > ?) OR "DBTime" > ?) ORDER BY "DBTime","DBKey" ASC`

which reads as:

`WHERE "DBTime" < '53063-12-09T18:49:50+00:00' AND (("DBTime" = 'timestamp.initial' AND "DBKey" > '-1') OR "DBTime" > 'timestamp.initial') ORDER BY "DBTime","DBKey" ASC`

# Troubleshooting

Kafka may fail with `Error while fetching metadata with correlation id 39 : {4-3-16-topic1=LEADER_NOT_AVAILABLE}` - this can be fixed by creating the topic manually before running the connector.

# Documentation

You can find the documentation and instructions for this repo at [https://docs.confluent.io/platform/current/tutorials/build-your-own-demos.html](https://docs.confluent.io/platform/current/tutorials/build-your-own-demos.html?utm_source=github&utm_medium=demo&utm_campaign=ch.examples_type.community_content.cp-all-in-one)
