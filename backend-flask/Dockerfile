FROM python:3.10-slim-buster

# Creates a new folder inside container called backend-flask
WORKDIR /backend-flask

# requirements.txt on local machine is copied inside the container with file name requirements.txt
# The file, requirements.txt, contains the libraries we want instlled to run the app
COPY requirements.txt requirements.txt

# Install the python libraries used for the app inside the container
# RUN command is used to build the container
RUN pip3 install -r requirements.txt

# know that a single period means everything in the current directory
# . (the first period in the COPY command) means everything in /backend-flask *outside* container
# .. (the second period in the COPY command) means everything in /backend-flask *inside* container
# The directory /backend-flask was created in earlier command above so does not need to specified in the COPY command
COPY . .

# Set environment variables (ENV VARS)
# Inside container and will remain set when the container is running
ENV FLASK_ENV=development

EXPOSE ${PORT}

# CMD (command) is used to specify the first command to execute when container runs
# Execute the two below commands in terminal to set environment variables before running python command
# 1. export FRONTEND_URL="*"
# 2. export BACKEND_URL="*"
# 3. python3 -m flask run --host=0.0.0.0 --port=4567
# Don't forget to unlock the port 4567 in the Exposed Ports tab of VSCode
CMD [ "python3", "-m" , "flask", "run", "--host=0.0.0.0", "--port=4567"]