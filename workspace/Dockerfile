# Use an official Python runtime as a parent image
FROM python:3.12

# Set the working directory in the container
WORKDIR /usr/src/pydock

# Copy the current directory contents into the container at /app
COPY . /usr/src/pydock

# Set Timezone
ARG TZ=UTC
ENV TZ ${TZ}

RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# Install any needed packages specified in requirements.txt
RUN pip install --upgrade pip
RUN pip install --no-cache-dir -r requirements.txt

# Create a non-root user
RUN groupadd -r -g 1000 pydock && useradd -l -u 1000 -r -g pydock pydock

# Change the ownership of the /app directory to the non-root user
RUN chown -R pydock:pydock /usr/src/pydock

# Switch to the non-root user
USER pydock

# Make port 80 available to the world outside this container
EXPOSE 80

# Define environment variable
ENV NAME World

CMD ["tail", "-f", "/dev/null"]