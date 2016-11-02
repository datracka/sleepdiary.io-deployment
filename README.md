## localhost


Clone the project and jump into the run folder.
You need to have already installed docker https://docs.docker.com/engine/installation/
Check that ports 80, 8000 and 5432 and not already busy. If it is so run,

- $ docker-compose build --no-cache
- $ docker-compose up -d

if it is the first time you have to run migrations: 

- $ docker-compose run back_python_accounts_calendar /usr/local/bin/python manage.py migrate

open a browser and run http://localhost. Create an user with sign up form. 

enjoy it! 
