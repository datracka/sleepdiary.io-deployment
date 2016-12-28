### Installation

Clone the project and jump into the run folder.

You need to have already installed docker https://docs.docker.com/engine/installation/

Check that ports 80, 8000 and 5432 and not already busy. 

If you don't have one .env already rename the `.env.example` to `.env`

Run:

- `$ docker-compose build --no-cache`
- `$ docker-compose up -d`

if it is the first time you have to run migrations: 

- `$ docker-compose run back_python_accounts_calendar /usr/local/bin/python manage.py migrate`

open a browser and run http://localhost. Create an user with sign up form. 

enjoy it! 

### Inspiration / thanks to:

- https://realpython.com/blog/python/django-development-with-docker-compose-and-machine/
- https://semaphoreci.com/community/tutorials/dockerizing-a-python-django-web-application
- https://github.com/erroneousboat/docker-django

# backup restore db

Backup:  $ pg_dump -U {user-name} {source_db} -f {dumpfilename.sql}
Restore: $ psql -U {user-name} -d {desintation_db}-f {dumpfilename.sql}


