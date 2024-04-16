# Requirements Document

## Project Overview

The project is a Flask-based backend service that receives images and captions from a React frontend, saves the images temporarily, and uploads them to Dropbox. The backend is designed to handle incoming requests, process images, and interact with Dropbox.

### Python Version

The project is developed using Python 3.10. or later.

## Dependencies

### Flask (v2.0.2)

Flask is a micro web framework for Python that provides the tools to build web applications. It is used in this project to handle HTTP requests and responses.

- [Flask Documentation](https://flask.palletsprojects.com/en/2.0.x/)

### Flask-cors (v3.0.10)

`flask-cors` is a Flask extension for handling Cross-Origin Resource Sharing (CORS). It enables the backend to handle requests from a different domain (e.g., a React frontend running on a different server).

- [flask-cors Documentation](https://flask-cors.readthedocs.io/en/latest/)

### Dropbox (v11.10.0)

The Dropbox Python SDK is used to interact with the Dropbox API. It facilitates uploading images to Dropbox.

- [Dropbox Python SDK Documentation](https://dropbox-sdk-python.readthedocs.io/en/latest/)

### Flask-OAuthlib (v0.9.6)

`flask-oauthlib` is a Flask extension that provides OAuth support for Flask applications. It is used in this project to handle OAuth 2.0 authorization flow for interacting with the Dropbox API.**CURRENTLY UNNECESSARY BUT WILL BE KEPT HERE JUST IN CASE**

- [Flask-OAuthlib Documentation](https://flask-oauthlib.readthedocs.io/en/latest/)

### PyMySQL (v0.10.1)

`pymysql` is a Python library that provides an interface to communicate with MySQL databases. It serves as a connector between Python applications and MySQL servers, allowing for the execution of SQL queries and the retrieval of results.


## Installation
Use this command in the `/APIFiles` directory to install all the dependencies required to run the backend.
  ```bash
  pip install -r requirements.txt
 ```

**Note: you MUST update this requirements doccument when installing new dependencies.**


