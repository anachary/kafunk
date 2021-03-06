### 0.1.3-alpha - 14.07.2017

* Added ProducerResult.count indicating the number of messages produced in a batch for a partition.

### 0.1.2-alpha - 03.07.2017

* Fixed consumer offset commit [bug](https://github.com/jet/kafunk/issues/152) wherein after a rebalance a consumer gets assigned a new partition
  which doesn't receive any messages for longer than the offset retention period, the offsets would be lost.
  This would only happen after a rebalance not after initial join.

### 0.1.1-alpha - 25.05.2017

* Snappy compression.
* Fixed lag calculation bug in ConsumerInfo module.

### 0.1.0 - 01.05.2017

* Ensure recovery during broker restart (virtual broker routing).
* Add Producer.produceBatched with improved API and performance:
	- Takes a batch of messages rather than a function returning a batch.
	- Parallelizes requests across brokers.

### 0.0.43-alpha001 - 24.04.2017

* Fix message set decompression (take 3)

### 0.0.41-alpha001 - 24.04.2017

* Fix message set decompression (take 2)

### 0.0.40-alpha001 - 21.04.2017

* Fix message set decompression

### 0.0.39-alpha001 - 11.04.2017

* Unroll loop in producer to make more efficient
* Request buffer pool
* Added ZK offset migration script in tests project
* Support v10.0.1 for Offset API
* BREAKING:
	- MessageSet tuples replaced with structs
	- ProduceRequest tuples replaced with structs
	- ProduceResponse tuples replaced with structs
	- OffsetCommitRequest added support for v1 (in addition to v0 and v2)

### 0.0.38-alpha001 - 29.03.2017

* Fix use of IVar where concurrent puts are possible
* Fix #124
* Fix #126

### 0.0.37-alpha001 - 27.03.2017

* Fix producer bug where during recovery, messages in flight would be lost and never timeout.

### 0.0.36-alpha001 - 23.03.2017

* Improve produce and fetch codec performance.
* Fix possible deadlock with Async.AwaitTask usage.

### 0.0.35-alpha001 - 08.04.2017

* Fix CRC32 check.

### 0.0.34-alpha001 - 08.03.2017

* Make fetch response decoding more efficient (eliminate intermediate tuple allocations).
* Make CRC check on fetch response configurable (defaults to true).

### 0.0.33-alpha001 - 01.03.2017

* Ensure fetch errors are escalated to the top-level consumer.

### 0.0.32-alpha001 - 28.02.2017

* Fix bug in ConsumerInfo module where offset information for all partitions wouldn't be retrieved and would throw during the merge.
* Fix Async.parallel used internall for testing.

### 0.0.31-alpha001 - 24.02.2017

* Allow disabling of Console logger
* Ensure periodic offset committer commits offsets on start

### 0.0.30-alpha001 - 24.02.2017

* Improve producer batching performance
* Fix all offset commit

### 0.0.29-alpha001 - 23.02.2017

* Improve producer performance
* Improve producer error messaging

### 0.0.28-alpha001 - 22.02.2017

* Commit offsets even when unchanged to prevent loss due to retention.
* BREAKING:
	- Removed ConsumerConfig.initialFetchTime, consolidated into ConsumerConfig.autoOffsetReset
	- Replaced offsetOutOfRangeAction with autoOffsetReset and new union type AutoOffsetReset

### 0.0.27-alpha001 - 16.02.2017

* Hide internal members, including Async
* Refine fault tolerance defaults.

### 0.0.26-alpha001 - 14.02.2017

* Special Valentine's day edition.
* Refined flow for handling escalated failures.
* Fix error code MessageSizeTooLarge.
* Default client.id = "" rather than Guid; new Guid for connection id.
* Expose connection, producer, consumer config.

### 0.0.25-alpha001 - 10.02.2017

* Default producer to RequiredAcks.AllInSync
* Fix range consumer partition assignment strategy

### 0.0.24-alpha001 - 08.02.2017

* Adjust consumer group heartbeat defaults
* Added AsyncSeq tests

### 0.0.23-alpha001 - 08.02.2017

* Improve producer performance (batch size measurement)

### 0.0.22-alpha001 - 08.02.2017

* Producer in-memory buffer in bytes
* ConsumerInfo module for consumer progress tracking

### 0.0.21-alpha001 - 07.02.2017

* Updated exampled/readme
* Breaking changes:
	- Consumer.stream drops bufferSize parameter
	- ProducerResult contains a single partition-offset pair rather than array

### 0.0.20-alpha001 - 06.02.2017

* Producer buffering by size in bytes
* Fixex bug where producer errors weren't being surfaced
* Breaking changes:
    - ProducerConfig buffer size settings are new
    - Producer.produce takes a single message rather than array
    - Consumer.consume arguments reordered
* Logging improvements (more compact, more info)
* Improved producer-consumer test

### 0.0.19-alpha001 - 25.01.2017

* Producer buffering
* Ensure cancellation propagated to consumer on group close
* Logging improvements

### 0.0.18-alpha001 - 20.01.2017

* Fix ConsumerMessageSet.lag measure
* Propagate cancellation to consumer fetch process

### 0.0.17-alpha001 - 17.01.2017

* Discovery brokers by DNS when appropriate
* Explicit channel failure and recovery contract


### 0.0.16-alpha001 - 09.01.2017

* Fix bug in assignment strategy where all available metadate were used rather than that of subscribed topic

### 0.0.15-alpha001 - 09.01.2017

* Pass consumer state to consume callback (BREAKING)

### 0.0.14-alpha001 - 09.01.2017

* Consumer group assignment strategies configurable

### 0.0.13-alpha001 - 06.01.2017

* Refine Fetch consumer offsets API

### 0.0.12-alpha001 - 06.01.2017

* Current consumer state API
* Fetch consumer offsets API

### 0.0.11-alpha001 - 05.01.2017

* Hide internal members
* Documentation

### 0.0.10-alpha001 - 04.01.2017

* Log leader-size member assignments
* Fix consumer NotCoordinatorForGroup error recovery

### 0.0.9-alpha001 - 03.01.2017

* Refine TCP error recovery

### 0.0.8-alpha001 - 03.01.2017

* v0.10.1 support

### 0.0.7-alpha001 - 02.01.2017

* Fix overflow bug in Partitioner.roundRobin
* Error flow monitoring

### 0.0.6 - 30.12.2016

* Fix bug in Async.choose
* Consumer.commitOffsetsToTime
* Consumer doesn't fetch offsets until its starts consuming

### 0.0.5 - 30.12.2016

* Auto recover producer from error code 2

### 0.0.4 - 29.12.2016

* Consumer fetch request batching by broker
* Fix protocol codec issue for batched fetch responses
* Periodic offset commit

### 0.0.3 - 28.12.2016

* Fix a few reconnection/fault tolerance bugs
* Adjust consumer api to allow offset strategies to be parameterized

### 0.0.2 - 29.11.2016

* A more complete consumer API is now available
* We now use FSharp.Control.AsyncSeq instead of an internal version
* Adjustments have been made to connection recovery and general fault tolerance (still early)
* Improvements to message grouping should improve producer throughput

### 0.0.1 - 20.07.2016
* initial
