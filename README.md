[![Build Status](https://travis-ci.com/ceqi/logDemo.svg?branch=master)](https://travis-ci.com/ceqi/logDemo)

# logDemo


Add a alert flag to long-running events.

Load file using Java NIO Files.lines(), reading events line by line sequentially is considered sufficient as it toke 
about 3.5 
seconds to read in a 1GB file.

If the log file to read is large (gigabytes), after being loaded into db, the events will be read from db by slices, 
multiple slices are handled by threads, the processing is done in parallel, thus improving the efficiency.

By default the slice size is 10000 events.   

## Getting Started

From the root directory (logDemo), run the following commands:
### Run

```
./gradlew build

java -jar build/libs/logDemo-0.0.1-SNAPSHOT.jar log.txt

```
The results are written into 'EVENTS' table. 'RAW_EVENTS' table stores the orignal events.

### Running the tests
```
./gradlew check
```

### Test Report
```
{path_to_root_dir}/build/reports/tests/test/index.html
```

### Access to DB
```
java -cp hsqldb-2.4.1/hsqldb/lib/hsqldb.jar  org.hsqldb.util.DatabaseManagerSwing

type: hsql database engine standalone
url: jdbc:hsqldb:file:testdb
user: SA
password:
```

## Built With

* [SpringBoot](http://www.dropwizard.io/1.0.2/docs/) - Dependency Injection & JPA & Testing frameworks (JUnit, AssertJ)
* [Gradle](https://maven.apache.org/) - Dependency Management
* [Jackson](https://github.com/FasterXML/jackson-databind) - Data binding
* [Logback](https://logback.qos.ch/) - Logging 
* [HSQLDB](http://hsqldb.org/) - Database
