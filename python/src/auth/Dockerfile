FROM python:3.11.5-slim-bullseye

# Update package list and install necessary packages
RUN apt-get update \
  && apt-get install -y --no-install-recommends \
     build-essential \
     default-libmysqlclient-dev \
  && rm -rf /var/lib/apt/lists/* \
  && pip install --no-cache-dir --upgrade pip

# Set the working directory
WORKDIR /app

# Copy the requirements file and install Python dependencies
COPY ./requirements.txt /app/
RUN pip install --no-cache-dir --requirement /app/requirements.txt

# Copy the rest of the application code
COPY . /app

# Expose the port the application will run on
EXPOSE 5000

# Set the command to run the application
CMD ["python3", "server.py"]