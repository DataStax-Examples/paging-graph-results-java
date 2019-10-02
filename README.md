# Paging Graph Results
This example shows you how to handle use paging with graph result sets.  It contains three different methods for processing results:
* Unpaged results - This does not use paging at all and is included for comparisons sake
* Synchronously Paged Results - This using the continuous paging functionality of DataStax Graph along with synchronous processing of results
* Asynchronously Paged Results -  This using the continuous paging functionality of DataStax Graph along with asynchronous processing of results

Continuous paging is method within the DataStax Java Driver which allows for streaming of bulk records by having the server continuously prepare pages of results of the specified size.  With this method the driver returns a "page" of results to allow for processing of those results while additional "pages" are being retrieved.

## Objectives
* To understand the three different methods of processing graph results in Java

## How it Works

This code contains methods for processing unpaged results (`unpagedResults`), synchronously paged results (`continuousPagingSynchronous`), and asynchronously paged results (`continuousPagingAsynchronous`).

In both the methods where paging is enabled by setting the Paging Options on the statement to be executed as seen below:

```ContinuousPagingOptions options = ContinuousPagingOptions.builder().withPageSize(pageSize, ContinuousPagingOptions.PageUnit.ROWS).build();statement.setPagingEnabled(true).setPagingOptions(options);```

Using the `ContinuousPagingOptions.builder()` you can set the page size that you would like to return.  With graph results the only valid `PageUnit` is `ROWS`.

## Before you Begin

### Prerequisites
* Java 8
* A DSE Cluster running a DS Core Graph 	
* The DataStax Enterprise Java Driver for the 1.8.2.20190711-LABS Experimental 6.8 DataStax Graph Release
* Maven

## Setup and Running

### Building

In order to build this we need to run a Maven build using:

```mvn clean package```

This will build and package a fat jar.  

### Running
Once completed you can run this program from the command line using where you must include the Cluster contact point and the graph name you want run against.  This graph must exist
```
java -cp ./target/paging-graph-results-0.1-jar-with-dependencies.jar com.datastax.graphpractice.example.App <insert cluster contact point> <insert graph name>
```

## Attribution
Created and Maintained by [bechbd](https://github.com/bechbd)

 
