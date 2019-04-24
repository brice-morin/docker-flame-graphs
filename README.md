# docker-flame-graphs
Flame graphs for JVMs running inside Docker containers

# how to run

> Make sure JAVA_HOME is configured to point to a JDK. You need cmake >= 2.8.6 (tested version cmake version 3.5.1)

The commands below will generate flame graphs for a simple java-app.

```
git clone https://github.com/mboussaa/docker-flame-graphs
cd docker-flame-graphs
git clean
cmake . && make

docker run -d -v $(pwd):/docker-flame-graphs java-app    #just a sample java app

pgrep -fl java     #and pick up a java_id
docker ps          #and pick up the container_id

cd bin
./docker-perf-top container_id pid (edited vi docker-perf-top)
./docker-perf-java-flames container_id pid
```

