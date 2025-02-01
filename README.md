# job_services_clone_repository

## Details

Name: jobs-service


## Dependencies:
---
`config-service`     - Gets all the properties to connect to different endpoints including database.

`notification-service`    - Sends notification using notification service url.

`api_commons`     - Depends on this for lot of common functionality like logging, connection classes etc.



## Features
---
Restful services for the following functions.


## Run on IDE
--- 
Launch.json file is created with service definition for VSCode.

## Create a virtual environment
```
python3 -m venv .venv
```
```
source .venv/bin/activate
```
## Docs
---
/openapi


### Tests
---
The tests are documented in the tests folder for postman.




## Deployment and run tests
---
```
docker-compose  --env-file .env/dev.env up -d
```
The following environments are supported by default. Replace qa in the above command with appropriate environment name. 

- `qa` - QA environment

- `stg` - Staging environment

- `prod` - Production environment

### Upgrade pip and setuptools
```
pip install --upgrade pip setuptools
```
### Install the dependencies
```
pip install -r requirements.txt
```
### To run the unit tests install the dev dependencies 
```
pip install -r requirements-dev.txt
```
```
pip install app_commons-1.0.61-py2.py3-none-any.whl
``` 
(or) 
```
pip install --no-cache-dir app_commons-1.0.61-py2.py3-none-any.whl
```
### Run migrations

  export workspaceFolder=`pwd`
```
  python3 -m dotenv -f ${workspaceFolder}/.env/dev.env run python3 ${workspaceFolder}/src/manage.py makemigrations;
```
```
  python3 -m dotenv -f ${workspaceFolder}/.env/dev.env run python3 ${workspaceFolder}/src/manage.py migrate;
```
### Load test data ( Only in development and QA environments)
  <!-- Install the build dependencies -->
```
  pip install -r requirements-dev.txt
```

05-Load Common data
```
  python3 -m dotenv -f ${workspaceFolder}/.env/dev.env run python3 ${workspaceFolder}/src/manage.py loaddata 05-init;
```

10-Load App Common default data

```
  python3 -m dotenv -f ${workspaceFolder}/.env/dev.env run python3 ${workspaceFolder}/src/manage.py loaddata 10-app-categories;
```
```
python3 -m dotenv -f ${workspaceFolder}/.env/dev.env run python3 ${workspaceFolder}/src/manage.py loaddata 10-app-degrees;
```
```
python3 -m dotenv -f ${workspaceFolder}/.env/dev.env run python3 ${workspaceFolder}/src/manage.py loaddata 10-app-languages;
```
```
python3 -m dotenv -f ${workspaceFolder}/.env/dev.env run python3 ${workspaceFolder}/src/manage.py loaddata 10-app-skills;
```
```
python3 -m dotenv -f ${workspaceFolder}/.env/dev.env run python3 ${workspaceFolder}/src/manage.py loaddata 10-app-languages; 
```

20 Users - Load App Sample Users
```
  python3 -m dotenv -f ${workspaceFolder}/.env/dev.env run python3 ${workspaceFolder}/src/manage.py loaddata 20-sample-users;
```

21 Companies - Load App Sample Data
```
  python3 -m dotenv -f ${workspaceFolder}/.env/dev.env run python3 ${workspaceFolder}/src/manage.py loaddata 21-sample-companies;
```

22 Jobs - Load App Sample Data
```
  python3 -m dotenv -f ${workspaceFolder}/.env/dev.env run python3 ${workspaceFolder}/src/manage.py loaddata 22-sample-jobs;
```
### Run unit tests
```
  python3 -m dotenv -f ${workspaceFolder}/.env/dev.env run pytest ${workspaceFolder}/src/tests/data.py;
```
# Operation requirements
---
Cronjob to delete the blacklisted tokens every 24 hours.


# Additional information
https://django-localflavor.readthedocs.io/en/latest/

<!-- Lot of useful django utility functions available as command line options for manage.py -->
https://django-extensions.readthedocs.io/en/latest/index.html
