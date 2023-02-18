FROM python:3.10-slim-buster

# Inside container
# make a new folder inside container
WORKDIR /backend-flask

<<<<<<< HEAD
# Outside container -> Inside container
# this contains the libraries we want instlled to run the app
=======
# Inside container
# install the python libraries used for the app
>>>>>>> 7e401c02bf75c2165866b0ce412bcd4fd4869759
COPY requirements.txt requirements.txt

# Inside container
# install the python libraries used for the app
RUN pip3 install -r requirements.txt

# Outside container -> Inside container
# . means everything in the current directory
# . (the first period) means /backend-flask (outside container)
# .. (the second period) means /backend-flask (inside container)
COPY . .

# Set environment variables (ENV VARS)
# Inside container and will remain set when the container is running
ENV FLASK_ENV=development

<<<<<<< HEAD
EXPOSE ${PORT}

# python3 -m flask run --host=0.0.0.0 --port=4567
CMD [ "python3", "-m" , "flask", "run", "--host=0.0.0.0", "--port=4567"]
=======

EXPOSE ${PORT}

# python3 -m flask run --host=0.0.0.0 --port=4567
CMD [ "python3", "-m" , "flask", "run", "--host=0.0.0.0", "--port=4567"
>>>>>>> 7e401c02bf75c2165866b0ce412bcd4fd4869759
