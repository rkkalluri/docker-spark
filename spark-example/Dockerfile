FROM gettyimages/spark
ENTRYPOINT ["spark-submit", "--master", "spark://spark", "--class","org.sparkexample.WordCount", "/work/first-example-1.0-SNAPSHOT.jar"]
WORKDIR /work
ADD target/first-example-1.0-SNAPSHOT.jar /work/
CMD ["hdfs://hdfs:9000/user/root/data/4300.txt" "hdfs://hdfs:9000/user/root/data/ouput"
