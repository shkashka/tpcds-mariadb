# Toolbox for TPC-DS on MariaDB

This repository is a toolbox for [TPC-DS benchmark](http://www.tpc.org/tpcds/) execution on MariaDB.  The
tools help modifying, building, and running TPC-DS kit source code for MariaDB.


## Pre-requisites

You should get TPC-DS kit source code before using the tools.  You can download
it from [TPC website](http://www.tpc.org/tpc_documents_current_versions/download_programs/tools-download-request.asp?bm_type=TPC-DS&bm_vers=2.5.0&mode=CURRENT-ONLY) as a zip file after agree to their license.


## Versions

This toolbox is tested for TPC-DS tools v2.5.0rc2 and MariaDB 10.2.8, the
latest version as of this writing.


## Limitations

TPC-DS has 99 queries for performance test.  However, some queries use SQL
keywords that MariaDB doesn't support.  Our tools just ignore such queries on
power test.  As a result, we use only 49 queries for power test.


## Makefile

Use the command `make help` to see all command of Makefile.        
Note that this Makefile is more a tool that a real compile process.  This will help you to setup your install and test different component.


## Quick Start

This section describes simple steps for TPC-DS test setup and execution.  Every
example assumes that your current working directory is this repository.


#### Extract TPC-DS Toolkit Source Code

```
$ ./extract_src.sh <path to your zip file>
```


#### Modify TPC-DS kit Code

```
$ ./patch-tpcds-kit.sh
```


#### Build TPC-DS Kit

```
$ ./build.sh
```


#### Generate Data

```
$ ./datgen.sh <scale factor>
```


#### Execute Load Test

Before next command, you should start mysqld daemon.  Next command assumes that
your mysqld has user `root` without password.  In other words, it should be
able to use `$ mysql -u root` to connect to MariaDB prompt.
```
$ ./loadtest.sh <scale factor>
```


#### Execute Power Test

```
$ ./mkqueries.sh <scale factor>
$ ./powertest.sh
```


#### Execute Query 2 Only

```
$ ./mkqueries.sh <scale factor>
$ ./runquery.sh 2
```


## Author

SeongJae Park <sj38.park@gmail.com>    
Edited by Detobel36

