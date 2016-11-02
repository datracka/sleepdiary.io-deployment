## localhosst

1 - clone the project and jump into the run folder

check that ports 80, 8000 and 5432 and not already busy. If so,

2 - $ docker-compose build --no-cache
3 - $ docker-compose up -d

if it is the first time you have to run migrations: 

4 - $ docker-compose run back_python_accounts_calendar /usr/local/bin/python manage.py migrate
5 - open a browser and run http://localhost. Create an user with sign up form. 
