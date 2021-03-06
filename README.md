# chaos-monkey
A program that uses docker VM to perform on chaos tests on applications

Create DB called chaosmonkey to store Logs and Jobs
```
psql postgres -U <user>
```
```
CREATE DATABASE chaosmonkey;
```
Build Docker Image
```
docker build -t chaos .
```
Run Docker Container
```
docker run -it -p 8080:5000 chaos 
```
Sample Docker File: Flask Application
```
FROM python:3
ADD . /src
RUN apt-get update

RUN apt-get -y install libboost-all-dev
RUN apt-get -y install libgmp-dev
RUN apt-get -y install vim
RUN apt-get -y install tmux 
RUN apt-get install stress

RUN pip install --upgrade pip

RUN pip install requests
RUN pip install Flask
RUN pip install Flask-SQLAlchemy
RUN pip install SQLAlchemy
RUN pip install pymysql
RUN pip install flask_cors

EXPOSE 5000
WORKDIR /src
CMD bash
```
