# Conditions-monitoring-service

### About the service

The conditions monitoring service is a Box Monitoring Tool. This service's task is to identify changes that could indicate a developing fault.

### Getting Started
---------------
Kindly follow below instructions for setting up your project locally. To get a local copy up and running follow these simple example steps.

### Prerequisites

- Install pyramid
```
    pip install pyramid
```

### Installation
- Clone the repo :
```
    https://github.com/Toorak-Capital/conditions-monitoring-service.git
```

### Environment set-up

- AWS_ACCESS_KEY_ID
- AWS_DEFAULT_REGION
- AWS_SECRET_ACCESS_KEY
- BUCKET_NAME
- TOPIC_ARN

### Steps to be followed after cloning

- Change directory into your newly created project.
```
    cd conditions-monitoring-service
```

- Create a Python virtual environment.
```
    python3 -m venv env
```

- Upgrade packaging tools.
```
    env/bin/pip install --upgrade pip setuptools
```

- Install the project in editable mode with its testing requirements. During this installation github will ask for authentication several times. Kindly provide authentication for the same.
```
    env/bin/pip install -e ".[testing]"
```

<br />
(Before moving to further steps kindly create a local database for the alembic commands to work. Also provide the path of the database in environment variables as      "Database_URL". The format for DATABASE_URL is : 'postgresql://username:password@localhost:port/databasename'. <br />  
 Example : postgresql://postgres:pass123@localhost:5432/conditions monitoring service )
<br />
<br />

- Initialize and upgrade the database using Alembic.

    - Generate your first revision.
      ```
        env/bin/alembic -c development.ini revision --autogenerate -m "init"
      ```

    - Upgrade to that revision.
      ```
        env/bin/alembic -c development.ini upgrade head
      ```

- Load default data into the database using a script.
    ```
    env/bin/initialize_condition_monitoring_service_db development.ini
    ```

- Run your project's tests.
  ```
    env/bin/pytest
  ```

- Run your project.
  ```
    env/bin/pserve development.ini
  ```

**_NOTE:_**  The above commands are applicable for Mac. For windows one will have to replace 'bin' with 'Scripts'.<br /> 
Example- env/Scripts/pserve development.ini
