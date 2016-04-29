---
title: Monitoring Redis for Pivotal Cloud Foundry&reg;
owner: London Services
---

## Monitoring with Datadog

Pivotal uses Datadog to monitor Redis' performance and health. An example Datadog configuration, displaying the significant metrics outlined below, is available [here](https://github.com/pivotal-cf/metrics-datadog-dashboard).

## Redis metrics

Redis emits a number of metrics that can be used to monitor the health and performance of your Redis deployment.

### keyspace_hits

<table border='1' class='nice'>
<tr>
  <th width="22%">Description</th>
  <td>Number of successful lookups of keys in the main dictionary
  </td>
</tr>
<tr>
  <th>Significance</th>
  <td>In conjunction with <code>keyspace_misses</code>, it can be used to calculate the hit ratio.</td>
</tr>
<tr>
  <th>Notes</th>
  <td>A successful lookup is a lookup on a key that exists.</td>
</tr>
</table>

### keyspace_misses

<table border='1' class='nice'>
<tr>
  <th width="22%">Description</th>
  <td>Number of unsuccessful lookups of keys in the main dictionary
  </td>
</tr>
<tr>
  <th>Significance</th>
  <td>In conjunction with <code>keyspace_hits</code>, it can be used to calculate the hit ratio.</td>
</tr>
<tr>
  <th>Notes</th>
  <td>An unsuccessful lookup is a lookup on a key that does not exist.</td>
</tr>
</table>

### used_memory

<table border='1' class='nice'>
<tr>
  <th width="22%">Description</th>
  <td>Number of bytes allocated by Redis
  </td>
</tr>
<tr>
  <th>Significance</th>
  <td>Grows as the number of unsaved keys increases.</td>
</tr>
</table>

### blocked_clients

<table border='1' class='nice'>
<tr>
  <th width="22%">Description</th>
  <td>Number of connected clients pending on a blocking call
  </td>
</tr>
<tr>
  <th>Significance</th>
  <td>Can be used as an indicator to detect deadlocks.</td>
</tr>
</table>

### connected_clients

<table border='1' class='nice'>
<tr>
  <th width="22%">Description</th>
  <td>Number of clients connected to the Redis instance
  </td>
</tr>
</table>

### rdb\_changes\_since\_last\_save

<table border='1' class='nice'>
<tr>
  <th width="22%">Description</th>
  <td>Number of keys currently in memory
  </td>
</tr>
<tr>
  <th>Significance</th>
  <td>Memory usage will grow in proportion to the number of keys in memory. If the Redis instance is stopped ungracefully, these changes may be lost.</td>
</tr>
<tr>
  <th>Notes</th>
  <td>Performing a BGSAVE will write these keys to disk and free up memory.</td>
</tr>
</table>

### total\_commands\_processed

<table border='1' class='nice'>
<tr>
  <th width="22%">Description</th>
  <td>Total number of commands processed by Redis
  </td>
</tr>
<tr>
  <th>Significance</th>
  <td>A crude indicator of activity. Can be used in conjunction with <code>uptime_in_seconds</code>.</td>
</tr>
</table>


## Other metrics

We also expose the following metrics. Please refer to the [Redis documentation](http://redis.io/commands/INFO) for more information about each of these.

* <code>arch\_bits</code>
* <code>uptime\_in\_seconds</code>
* <code>uptime\_in\_days</code>
* <code>hz</code>
* <code>lru\_clock</code>
* <code>client\_longest\_output\_list</code>
* <code>client\_biggest\_input\_buf</code>
* <code>used\_memory\_rss</code>
* <code>used\_memory\_peak</code>
* <code>used\_memory\_lua</code>
* <code>mem\_fragmentation\_ratio</code>
* <code>loading</code>
* <code>rdb\_bgsave\_in\_progress</code>
* <code>rdb\_last\_save\_time</code>
* <code>rdb\_last\_bgsave\_time\_sec</code>
* <code>rdb\_current\_bgsave\_time\_sec</code>
* <code>aof\_rewrite\_in\_progress</code>
* <code>aof\_rewrite\_scheduled</code>
* <code>aof\_last\_rewrite\_time\_sec</code>
* <code>aof\_current\_rewrite\_time\_sec</code>
* <code>total\_connections\_received</code>
* <code>total\_commands\_processed</code>
* <code>instantaneous\_ops\_per\_sec</code>
* <code>total\_net\_input\_bytes</code>
* <code>total\_net\_output\_bytes</code>
* <code>instantaneous\_input\_kbps</code>
* <code>instantaneous\_output\_kbps</code>
* <code>rejected\_connections</code>
* <code>sync\_full</code>
* <code>sync\_partial\_ok</code>
* <code>sync\_partial\_err</code>
* <code>expired\_keys</code>
* <code>evicted\_keys</code>
* <code>keyspace\_hits</code>
* <code>keyspace\_misses</code>
* <code>pubsub\_channels</code>
* <code>pubsub\_patterns</code>
* <code>latest\_fork\_usec</code>
* <code>migrate\_cached\_sockets</code>
* <code>connected\_slaves</code>
* <code>master\_repl\_offset</code>
* <code>repl\_backlog\_active</code>
* <code>repl\_backlog\_size</code>
* <code>repl\_backlog\_first\_byte\_offset</code>
* <code>repl\_backlog\_histlen</code>
* <code>used\_cpu\_sys</code>
* <code>used\_cpu\_user</code>
* <code>used\_cpu\_sys\_children</code>
* <code>used\_cpu\_user\_children</code>
* <code>cluster\_enabled</code>
* <code>rdb\_last\_bgsave\_status</code>
* <code>aof\_last\_bgrewrite\_status</code>
* <code>aof\_last\_write\_status</code>
