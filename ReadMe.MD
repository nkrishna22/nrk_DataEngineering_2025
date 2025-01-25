# Commands:

#### **1. Run docker with the python:3.12.8 image in an interactive mode, use the entrypoint bash.**
```docker 
docker run -it --entrypoint bash python:3.12.8

```
#### *What is the version of pip in the image?*
 __*ans*__: 24.3.1


#### **Sample Dockerfile**
```Dockerfile
# Base docker image that we will build on
FROM python:3.12.8

# Setup our image by install pre-reqs: pandas here
RUN pip install pandas

# Setup up the working directory inside the container
WORKDIR /app

# Copy the pipeline.py into container
COPY pipeline.py pipeline.py

# Define what to do first when the container runs
ENTRYPOINT [ "python3", "pipeline.py" ]
```

#### Build an image using Dockerfile
```docker
docker build -t test:pandas
```

#### Run a container using the image created
```docker
docker run -it test:pandas <any number as argument>

example: 
    docker run -it test:pandas 6

OUTPUT: ['pipeline.py', '6']
        job finished successfully for day 6
```
 

#### Command to create new docker network
```docker 
docker network create pg-network-1
```


#### Command to run postgres:13 container 
```docker
docker run -it \
-e POSTGRES_USER="root" \
-e POSTGRES_PASSWORD="root" \
-e POSTGRES_DB="ny_taxi_2019" \
-v $(pwd)/week_1/ny_taxi_postgres_data:/var/lib/postgresql/data \
-p 5431:5432 \
--network=pg-network-1 \
--name pg-database-1 \
postgres:13
```


#### Command to run pgadmin4
```docker
docker run -it \
-e PGADMIN_DEFAULT_EMAIL="admin@admin.com" \
-e PGADMIN_DEFAULT_PASSWORD="root" \
-p 8080:80 \
--network=pg-network \
--name pgadmin-1 \
dpage/pgadmin4
```