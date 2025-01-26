# Base docker image that we will build on
FROM python:3.12.8

RUN apt-get install wget

# Setup our image by install pre-reqs: pandas here
RUN pip install pandas sqlalchemy psycopg2 pyarrow

# Setup up the working directory inside the container
WORKDIR /app

# Copy the pipeline.py into container
COPY Ingest_Data.py Ingest_Data.py

# Define what to do first when the container runs
ENTRYPOINT [ "python3", "Ingest_Data.py" ]