# Cloud Services Kata


The goal of this Kata is get this tiny flask app up and running in 3 different ways and send me the url so that I can access it (NB!).

These are the 3 different ways: 
1. Locally on your own machine
2. Using infrastructure in AWS (EC2)
3. Using application services in AWS (Elastic Beanstalk)

There are also 3 STRETCH challenges for those who manage to complete those 3 and can come show me. If you've managed, come let me know. 

----------------------------------------------------

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

- FLASK_APP=application.py
- DBUSER=test 
- DBPASS=test 
- DBHOST=localhost
- DBNAME=test

In windows (run cmd as command):
```
setx FLASK_APP "application.py"
echo %FLASK_APP%
```
In linux:
```
export FLASK_APP=application.py
echo $FLASK_APP
```

### To Run 

- `cd path/to/cloudkata/app`
- `flask db upgrade && flask run -h 127.0.0.1 -p 5000`
- Go to `http://127.0.0.1:5000/` in your browser

### The challenge: Figure out how you're going to give me a url 

Hint: Experts would grok this pretty quickly

--------------------------


## Layer 1: Infrastructure as a Service: AWS EC2

### What is IaaS?

It's a hardware that you can rent online. Or in fancy words: "is a form of cloud computing that provides virtualized computing resources over the internet"

### What is EC2?

It's Amazon web services IaaS. It's a VM in the cloud.


### How to proceed

For the web server:

1. Create an EC2 box (linux!). 
2. Download the certificate. 
3. Setup your ssh credentials for the box using the certificate. ([putty & puttygen](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/putty.html) or OpenSSL - you might have installed OpenSSL when you installed git!)
4. Login to your EC2 box
5. Clone the github repo and install the web server: similar to the first kata
6. Install postgresql: https://github.com/snowplow/snowplow/wiki/Setting-up-PostgreSQL
7. Setup the security groups so we can access it. (Do as demoed! Open up the ports!)  
7. Send me you URL when it works.

----------------------------------------------------------------------------------------------------------------------------------


## Layer 2: Platform as a Service: Elastic Beanstalk and RDS

Use Elastic Beanstalk to install and run the python web server, and then use it to create an RDS instance for the database. You'll need to set environment variables here too, but they can be done via the interface

You have the option of using the INTERFACE or using the [AWS CLI](https://aws.amazon.com/cli/)

Interface:
1. Create an elastic beanstalk app
2. Update the WSGIPath to point to app/application.py
3. Create a database by going to the elastic beanstalk configuration and clicking on database and creating a new postgres database
4. Once created, go to the elastic beanstalk configuration and click software. Add your environment variables
5. Challenge: Run Migrations on startup! You'll need to create a folder with the flask command

CLI: 
- [Here](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/create-deploy-python-flask.html)



### What is Platform as a Service?

Platform as a Service is an abstraction away from the hardware or VM. It's meant to remove the low level installation, running and management of services. 


### What is Elastic Beanstalk?

AWS Elastic Beanstalk is what we call an "application service". It makes deploying technologies super easy via the use of a super simple wizard. Additionally, it makes autoscaling, load-balancing and a variety of other things, SUPER easy

### What is RDS?

AWS RDS is a database service. Almost had it with installing postgresql in various places? Well, now you need not worry: AWS RDS handles that for you


Source: [Azure Samples for a Flask Postrgesql App](https://github.com/Azure-Samples/flask-postgresql-app)
