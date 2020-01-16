# Test-Driven Development with Python, Flask, and Docker

This is my repo for the project documented at https://testdriven.io/courses/tdd-flask/


1. The project is a code along to building a RESTful API using test-driven development. These are the tools used to create it:

Tools and Technologies
Python
Flask
Docker
Postgres
Pytest
Flask-RESTPlus
Flask-SQLAlchemy
Gunicorn
Coverage.py
flake8
Black
isort
HTTPie
Flask-Admin
GitLab
Heroku
Swagger/OpenAPI

It is documented here: https://testdriven.io/courses/tdd-flask/

2. Installed Flask along with Flask-RESTPlus and Dockerized the application along with a Postgres DB
3. Once the 2 containers are up and application is reachable, started adding the unit tests and testing using Pytest
4. Refactored the app, using Flask Blueprints, then added the rest of the RESTful routes
5. Added Gunicorn as WSGI server. Tested manual deployment to Heroku, so that the app is now reachable here : https://kimperial.herokuapp.com/users
6. Added the following testing tools:

a. Coverage.py for code coverage
b. Flake 8 - linter
c. Black - used for formatting code
d. isort - for sorting imports alphabetically

7. Added Continous Integration using Gitlab. Created the gitlab-ci.yml file which consists of build/test stages 

a. In the BUILD stage this happens:

Log in to the GitLab Container Registry
Pull the previously pushed image (if it exists)
Build and tag the new image
Push the image up to the GitLab Container Registry

b. Using the image created in the build stage along with the Postgres service, we run Pytest, flake8, Black, and isort in the TEST stage.

8. Added Continous Deployment so the deployment via Heroku is no longer done manually and happens after passing the test. In the deploy stage, we:

Install cURL
Build and tag the new image
Log in to the Heroku Container Registry
Push the image up to the registry
Create a new release via the Heroku API using the image ID within the release.sh script

Go here to view the CI/CD jobs triggered by my commits to Gitlab : https://gitlab.com/karen.c.imperial/flaskapi/-/jobs

9. Added more RESTful routes: DELETE and PUT. Parametarized test functions. Added Pytest monkeypatch fixture to mock functionality in tests. At this point I also disabled isort during the TEST stage because of conflicts with the Black formatting tool. 

10. Added the Flask Admin panel which is only available in the Dev environment

Flask-Admin adds a functional admin panel to Flask that provides a CRUD user interface for managing data based on your data models.

11. Finally added Swagger for documenting the API

Go here to check it:

http://kimperial.herokuapp.com/doc/





