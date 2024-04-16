# Backend Software Manual

### Framework
The project is a Flask-based backend service that receives images
and captions from a React frontend, saves the images temporarily,
and uploads them to Dropbox. The backend is designed to handle incoming
requests, process images, and interact with Dropbox.

### Supported API functions

#### 1. Analysing An Image
**HTTP METHOD**: POST\
**URL**: https://snapmatchapi.org/api/identifyObjectInPhoto \
**Description**: This function receives photo data from the front-end, decodes it then creates a unique name 
for the image and temporarily uploads it to dropbox via the dropbox api. We then receive a link to that 
image and provide it to the clarifai image recognition model, which provides a set of objects that appear
in the object. This is then jsonified and sent back to the front-end.

#### 2. Uploading An Image
**HTTP METHOD**: POST\
**URL**: https://snapmatchapi.org/api/uploadChallenge \
**Description**: This function receives photo data, caption and selected object from the front-end, decodes the image 
it then creates a unique name for the image uploads it to dropbox via the dropbox api. We then receive a link to that 
image and enter the link, caption, object selected and the users id to the database. Finally, 
it returns a jsonified message stating the image was successfully uploaded.

#### 3. Viewing Your Own Challenges
**HTTP METHOD**: GET\
**URL**: https://snapmatchapi.org/api/getChallengesByUserID \
**Description**: This function returns a jsonified set containing the information of all the 
challenges in the Challenge table that share the user id of the current user.

#### 4. Viewing Other Challenges
**HTTP METHOD**: GET\
**URL**: https://snapmatchapi.org/api/getAllChallenges \
**Description**: This function returns a jsonified set containing the information of all the 
challenges in the Challenge table that do not share the user id of the current user. 

#### 5. Registering To The App
**HTTP METHOD**: POST\
**URL**: https://snapmatchapi.org/api/register \
**Description**: This function receives a username and password from the front-end and ensures that 
they comply to the rules required (i.e. No repeat usernames, no # in password e.t.c). Finally, 
it enters the username and password into the database and returns a jsonified message stating registry 
was successful.

#### 6. Logging in To The App
**HTTP METHOD**: POST\
**URL**: https://snapmatchapi.org/api/login \
**Description**: This function receives a username and password from the front-end and ensures that 
they appear in the database. If so, the user id of the corresponding user is stored in the session 
ensuring that the user id is not forgotten when the page is refreshed. Finally, it returns a jsonified
message stating the login was successful.

### How The API Is Run
The API is hosted on an AWS EC2 instance in production and served using Gunicorn,
a WSGI HTTP server. Unlike simply running a Flask app, Gunicorn efficiently
manages incoming requests and concurrent connections, making it suitable
for handling high levels of traffic.

### How AWS EC2 Works
An AWS EC2 instance is like having your own virtual computer in the cloud. It allows
you to run applications and host websites without needing physical hardware. You
can choose the type of instance you need based on factors like processing power, memory, and storage.
Once you select your instance type, you can easily launch it and access it remotely via SSH or a
similar protocol. EC2 instances are scalable, meaning you can increase or decrease their capacity
as needed, making them ideal for handling varying workloads. Overall, EC2 instances provide a flexible
and cost-effective way to deploy and manage your applications in the cloud.

### How We Allow For HTTPS Requests: Nginx And Certbot
Nginx and Certbot work together to provide secure and efficient web hosting. Nginx is a web server
software that handles incoming HTTP requests and serves web pages to users. It's known for its speed
and scalability, making it popular for hosting websites and applications. Certbot, on the other
hand, is a tool used for automatically obtaining and renewing SSL/TLS certificates from the
Let's Encrypt certificate authority. These certificates encrypt the communication between the
server and the user's browser, ensuring that sensitive information transmitted over the web
remains secure. By using Nginx with Certbot, you can easily configure your server to support
HTTPS (HTTP Secure) connections, providing an additional layer of security for your website or
application.In your Nginx configuration, you specify the IP address and port where Gunicorn
is listening for incoming requests. This allows Nginx to forward requests to your
Gunicorn server for processing. The IP address is provided by AWS EC2.

### How The Database Is Deployed: AWS RDS 
To deploy our database, we utilize an AWS RDS instance. This instance allows us to establish connectivity using MySQL software tools such as MySQL Workbench. Through this connection, we import our created database. By configuring the appropriate permissions and security settings, we ensure that the API has access to the online database, facilitating a shared database environment for seamless storage and retrieval of data for all users.
