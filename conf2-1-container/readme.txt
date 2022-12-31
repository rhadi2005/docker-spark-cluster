
https://dev.to/mvillarrealb/creating-a-spark-standalone-cluster-with-docker-and-docker-compose-2021-update-6l4
https://medium.com/@marcovillarreal_40011/creating-a-spark-standalone-cluster-with-docker-and-docker-compose-ba9d743a157f
https://github.com/mvillarrealb/docker-spark-cluster

Creating a Spark Standalone Cluster with Docker and docker-compose(2021 update)

|
|--|apps # Apps directory for volume mounts(any app you want to deploy just paste it here)
|--|data # Data directory for volume mounts(any file you want to process just paste it here)
|--|Dockerfile #Dockerfile used to build spark image
|--|start-spark.sh # startup script used to run different spark workloads
|--|docker-compose.yml # the compose file

to build : docker build -t cluster-apache-spark:3.0.2 .
to start : docker-compose up -d

to submit example app : 
           To submit the app connect to one of the workers or the master and execute :

/opt/spark/bin/spark-submit --master spark://spark-master:7077 \
--jars /opt/spark-apps/postgresql-42.2.22.jar \
--driver-memory 1G \
--executor-memory 1G \
/opt/spark-apps/main.py


to check database server just use the psql command(or any database client of your choice):
psql -U postgres -h 0.0.0.0 -p 5432
#It will ask for your password defined in the compose file



