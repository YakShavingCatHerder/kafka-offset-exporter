# kafka-offset-exporter

----

## This is a Prometheus exporter for topic and consumer group offsets in Kafka.

----

## Requirements

Kafka          => 0.10.0.0

golang         =  1.11

----

## Usage

The only required parameter is a set of brokers to bootstrap into the cluster.

By default, the oldest and newest offsets of all topics are retrieved and
reported.  You can also enable offset reporting for any consumer group but note
that due to the way Sarama works, this requires querying for offsets for _all_
partitions for each consumer group which can take a long time. It is recommended
to filter both topics and consumer groups to just the ones you care about.

```
$ ./kafka-offset-exporter -help
Usage of ./kafka-offset-exporter:
  -brokers string
        Kafka brokers to connect to, comma-separated
  -fetchMax duration
        Max time before requesting updates from broker (default 40s)
  -fetchMin duration
        Min time before requesting updates from broker (default 15s)
  -groups string
        Also fetch offsets for consumer groups matching this regex (default none)
  -level string
        Logger level (default "info")
  -path string
        Path to export metrics on (default "/")
  -port int
        Port to export metrics on (default 9000)
  -refresh duration
        Time between refreshing cluster metadata (default 1m0s)
  -topics string
        Only fetch offsets for topics matching this regex (default all)
```
