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

# manual SSL setup (docker configuration WIP)

#### install missing packages
- apt-get install software-properties-common -y && apt-get install gpg -y
- add-apt-repository -y ppa:certbot/certbot
- apt-get update -y
- apt-get install certbot -y

#### create certificate
- certbot certonly \
      --email datracka@gmail.com \
      --agree-tos \
      --text \
      --non-interactive \
      --webroot -w /app/sleepdiary.io/dist_prod -d app.sleepdiary.io
- openssl dhparam -out /etc/ssl/certs/dhparam.pem 2048

#### create support files for serverblock

- mkdir /etc/nginx/snippets/
- vi /etc/nginx/snippets/ssl-app.sleepdiary.io.conf 
 (copy content from ssl.app.sleepdiary.io.cong)
- vi /etc/nginx/snippets/ssl-params.conf
 (copy content from ssl-params.conf)
 
#### configure server block
- cp /etc/nginx/conf.d/sleepdiary.io.conf /etc/nginx/conf.d/sleepdiary.io.conf.back 
- rm -v /etc/nginx/conf.d/sleepdiary.io.conf
- vi /etc/nginx/conf.d/app.sleepdiary.io.conf
(copy content from conf.d/app.sleepdiary.ssl.conf)

#### restart services

- docker stop <id_container>
- docker start <id_container>
 
      

