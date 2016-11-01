FROM python:3.5

RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app

ONBUILD RUN git clone https://github.com/datracka/sleepdiary_backend.git .
#ONBUILD COPY requirements.txt /usr/src/app/
ONBUILD RUN pip install --no-cache-dir -r requirements.txt


