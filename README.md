[![Gitter chat](https://badges.gitter.im/gitterHQ/gitter.png)](https://gitter.im/big-data-europe/Lobby)

# bigdata-docker

# Docker Zeppelin

This repository contains [Apache Zeppelin 0.9.0](https://zeppelin.apache.org/) docker image, which is tuned to work with BDE clusters.

# Hadoop Docker


# Hive 
## Hive Docker
This is a docker container for Apache Hive 2.3.2. It is based on https://github.com/big-data-europe/docker-hadoop so check there for Hadoop configurations.
This deploys Hive and starts a hiveserver2 on port 10000.
Metastore is running with a connection to postgresql database.
The hive configuration is performed with HIVE_SITE_CONF_ variables (see hadoop-hive.env for an example).

To run Hive with postgresql metastore:
```
    docker-compose up -d
```

To deploy in Docker Swarm:
```
    docker stack deploy -c docker-compose.yml hive
```

To run a PrestoDB 0.181 with Hive connector:

```
  docker-compose up -d presto-coordinator
```

This deploys a Presto server listens on port `8080`
## Contributors
* Ivan Ermilov [@earthquakesan](https://github.com/earthquakesan) (maintainer)
* Yiannis Mouchakis [@gmouchakis](https://github.com/gmouchakis)
* Ke Zhu [@shawnzhu](https://github.com/shawnzhu)



## Hive Interpreter for Apache Zeppelin
Hive Interpreter has been deprecated and merged into JDBC Interpreter. 
You can use Hive Interpreter by using JDBC Interpreter with same functionality. 
See the example below of settings and dependencies.

### Properties
<table class="table-configuration">
  <tr>
    <th>Property</th>
    <th>Value</th>
  </tr>
  <tr>
    <td>default.driver</td>
    <td>org.apache.hive.jdbc.HiveDriver</td>
  </tr>
  <tr>
    <td>default.url</td>
    <td>jdbc:hive2://localhost:10000</td>
  </tr>
  <tr>
    <td>default.user</td>
    <td>hiveUser</td>
  </tr>
  <tr>
    <td>default.password</td>
    <td>hivePassword</td>
  </tr>
</table>

### Dependencies
<table class="table-configuration">
  <tr>
    <th>Artifact</th>
    <th>Exclude</th>
  </tr>
  <tr>
    <td>org.apache.hive:hive-jdbc:0.14.0</td>
    <td></td>
  </tr>
  <tr>
    <td>org.apache.hadoop:hadoop-common:2.6.0</td>
    <td></td>
  </tr>
</table>


### Configuration
<table class="table-configuration">
  <tr>
    <th>Property</th>
    <th>Default</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>default.driver</td>
    <td>org.apache.hive.jdbc.HiveDriver</td>
    <td>Class path of JDBC driver</td>
  </tr>
  <tr>
    <td>default.url</td>
    <td>jdbc:hive2://localhost:10000</td>
    <td>Url for connection</td>
  </tr>
  <tr>
    <td>default.user</td>
    <td></td>
    <td><b>( Optional ) </b>Username of the connection</td>
  </tr>
  <tr>
    <td>default.password</td>
    <td></td>
    <td><b>( Optional ) </b>Password of the connection</td>
  </tr>
  <tr>
    <td>default.xxx</td>
    <td></td>
    <td><b>( Optional ) </b>Other properties used by the driver</td>
  </tr>
  <tr>
    <td>zeppelin.jdbc.hive.timeout.threshold</td>
    <td>60000</td>
    <td>Timeout for hive job timeout</td>
  </tr>
  <tr>
    <td>zeppelin.jdbc.hive.monitor.query_interval</td>
    <td>1000</td>
    <td>Query interval for hive statement</td>
  </tr>
  <tr>
    <td>zeppelin.jdbc.hive.engines.tag.enable</td>
    <td>true</td>
    <td>Set application tag for applications started by hive engines</td>
  </tr>
</table>

# Spark 
## Spark Interpreter for Apache Zeppelin
[Apache Spark](http://spark.apache.org) is a fast and general-purpose cluster computing system.
It provides high-level APIs in Java, Scala, Python and R, and an optimized engine that supports general execution graphs.
Apache Spark is supported in Zeppelin with Spark interpreter group which consists of following interpreters.

<table class="table-configuration">
  <tr>
    <th>Name</th>
    <th>Class</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>%spark</td>
    <td>SparkInterpreter</td>
    <td>Creates a SparkContext/SparkSession and provides a Scala environment</td>
  </tr>
  <tr>
    <td>%spark.pyspark</td>
    <td>PySparkInterpreter</td>
    <td>Provides a Python environment</td>
  </tr>
  <tr>
    <td>%spark.ipyspark</td>
    <td>IPySparkInterpreter</td>
    <td>Provides a IPython environment</td>
  </tr>
  <tr>
    <td>%spark.r</td>
    <td>SparkRInterpreter</td>
    <td>Provides an vanilla R environment with SparkR support</td>
  </tr>
  <tr>
    <td>%spark.ir</td>
    <td>SparkIRInterpreter</td>
    <td>Provides an R environment with SparkR support based on Jupyter IRKernel</td>
  </tr>
  <tr>
    <td>%spark.shiny</td>
    <td>SparkShinyInterpreter</td>
    <td>Used to create R shiny app with SparkR support</td>
  </tr>
  <tr>
    <td>%spark.sql</td>
    <td>SparkSQLInterpreter</td>
    <td>Provides a SQL environment</td>
  </tr>
  <tr>
    <td>%spark.kotlin</td>
    <td>KotlinSparkInterpreter</td>
    <td>Provides a Kotlin environment</td>
  </tr>
</table>



## Connect Hive Interpreter With Spark in Apache Zeppelin




































