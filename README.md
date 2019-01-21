# Cloud Services Kata


The goal of this Kata is get this tiny flask app up and running in 3 different ways and send me the url so that I can access it (NB!).

These are the 3 different ways: 
1. Locally on your own machine
2. Using infrastructure in AWS (EC2)
3. Using application services in AWS (Elastic Beanstalk)

There are also 3 STRETCH challenges for those who manage to complete those 3 and can come show me. If you've managed, come let me know. 

## Layer 0: Local Installation

For this one, I'll give you some guidance. 
Time limit: 1 hr

### Installation

- Install python (This should have been done)
- Install postgresql (This should have been done)
- `git clone git@github.com:jaderabbit/cloudkata.git` 
- `cd path/to/cloudkata`
- `pip install -r requirements.txt`


### Database

- Create a user called `test` with password `test`: 
- Create a database called `test`. 


### Create the following environment variables

- FLASK_APP=app.py
- DBUSER=test 
- DBPASS=test 
- DBHOST=localhost
- DBNAME=test

In windows (run cmd as command):
```
setx -m FLASK_APP "app.py"
echo %FLASK_APP%
```
In linux:
```
export FLASK_APP app.py
echo $FLASK_APP
```

### To Run 

- `cd path/to/flask-postgresql-app/app`
- `flask db upgrade && flask run -h 0.0.0.0 -p 5000`
- Go to `http://0.0.0.0:5000/` in your browser

### The challenge: Figure out how you're going to give me a url 

Hint: Experts would grok this pretty quickly



## Layer 1: Infrastructure as a Service: AWS EC2

### What is IaaS?

It's a hardware that you can rent online. Or in fancy words: "is a form of cloud computing that provides virtualized computing resources over the internet"

### What is EC2?

It's Amazon web services IaaS. It's a VM in the cloud.


### How to proceed

For the web server:

1. Create an EC2 box. Linux one please
2. Download the certificate
3. Setup your ssh credentials for the box using the certificate. 
4. Login to your EC2 box
5. Install the web server
6. Install postgresql
7. Send me you URL when it works

## Layer 2: Platform as a Service

Use Elastic Beanstalk to create python web server, and then use it to create an RDS instance for the database. You'll need to set environment variables here too, but they can be done via the interface



