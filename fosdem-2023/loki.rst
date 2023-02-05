Loki: Logging, but make it cloud native
=======================================

> Loki is a time series database, but for strings.

A timeseries database is a key value store, where the key is a timestamp and the value a number.
The metadata are indexed but not the data themselves, so it permits having small index to a lot of data.

They use Loki as Grafana Labs.
It is fast because it can query up to 900GB/s.

You often ``grep`` logs, so for Loki there is a kind of distributed ``grep`` which is a DSL called ``logql``.
This DSL permits you to aggregate logs, *e.g.* aggregating error messages per container.

Loki accepts all type of logs (``nginx``, 10 years old legacy application, *etc.*).

When a request is done to get all the log for a given hour, the request will be splitted in 4 intervals of 15 minutes which will be each queried.
By having a lot of queries and lot of cores, you increase the parallelism, so you get quick queries.

Regarding retention, they store the applications logs for one month and the audit one for one year.

You can activate some specific features on the index schema only at given time, *e.g.* search from AWS S3 on 1st January 2022.
