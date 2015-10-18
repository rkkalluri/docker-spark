
# spark

This is the beginnings of a spark/hdfs cluster that runs on a single node.

based on the work of

[GettyImages](https://github.com/gettyimages/docker-spark)

[SquenceIQ](https://hub.docker.com/r/sequenceiq/hadoop-docker/)

Uses [docker-compose](http://docs.docker.com/compose):


    docker-compose up

The SparkUI will be running at `http://${YOUR_DOCKER_HOST}:8080` with one worker listed. To run `spark-shell`, exec into a container:

    docker exec -it dockerspark_master_1 /bin/bash
    /usr/spark/bin/spark-shell --master spark://master:7077

To run `SparkPi`, exec into a container:

    docker exec -it dockerspark_master_1 /bin/bash
    MASTER=spark://master:7077 /usr/spark/bin/run-example SparkPi 10

To add data to the HDFS files sytem via CLI

    docker exec -it dockerspark_hdfs_1 /bin/bash
    $HADOOP_PREFIX/hadoop fs -copyFromLocal /tmp/data/4300.txt data/

    (Data should be copied to the docker host at /home/ubuntu/data)

To run the 'WordCount Java sample'

    cd spark-example
    mvn package
    docker build -t spark/wordcount
    docker run --link dockerspark_hdfs_1:hdfs -ti tamr/sparktest

