FROM ubuntu:latest

# Update APT
RUN apt-get update

# Upgrade installed software
RUN apt-get upgrade -y

# Install Python3 and pip3
RUN apt-get install -y python3 python3-pip

# Remove external management restriction if it exists
RUN rm -f /usr/lib/python*/EXTERNALLY-MANAGED

# Install Flask using pip3
RUN pip3 install flask

# Set working directory
WORKDIR /app

# Copy the Flask application
COPY ./api.py /app/api.py

# Command to run the Flask application
CMD ["python3", "api.py"] 