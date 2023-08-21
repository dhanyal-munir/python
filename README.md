# Vote App Frontend 

This is a frontend app, part of [Example Voting App](https://github.com/dockersamples/example-voting-app.git).  

### Technology Stack 
Following technology stack is being used to develop and run the application. 
 * Python
 * Docker Engine 

## Tasks to Perform

To build and run this app as a container, following steps need to be performed in a Dockerfile: 

  * use `python:alpine3.17` container base image
  * map/expose `container port 80`
  * copy over the source code
  * run `pip install -r requirements.txt` to install dependencies
  * launch the app with `gunicorn app:app -b 0.0.0.0:80` command

## Steps 
### Step 1: Dockerfile
A Dockerfile is created with following conetents. 
```
  FROM python:2.7-alpine
  WORKDIR /app
  COPY . .
  RUN pip install -r requirements.txt
  EXPOSE 80
  CMD gunicorn app:app -b 0.0.0.0:80
```  
### Step 2: Build Image
To execute the application, an image is built from Dockerfile using following command. 

`docker build -t asadhanif/vote:v1 .` 

![Build Image](./screenshorts/build-image.png)

### Step 3: Run the Container
Run the container with following command:

`docker run -dp 5000:80 asadhanif/votefend:v1` 

![Run Container](./screenshorts/run-container.png)

### Running App
Open the browser and brows `<ip-address>:5000`

![Run App](./screenshorts/running-app.png)