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