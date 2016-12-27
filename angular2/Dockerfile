FROM tutum/nginx

RUN apt-get update && apt-get install -y \
        git \
        vim

RUN git clone https://github.com/datracka/sleepdiary.io.git /app/sleepdiary.io

WORKDIR /app/sleepdiary.io/

#checkout production branch
RUN git checkout develop

RUN cp /app/sleepdiary.io/src/index.html /app/sleepdiary.io/dist/index.html
RUN cp /app/sleepdiary.io/src/index.html /app/sleepdiary.io/dist_prod/index.html

RUN rm /etc/nginx/sites-enabled/default
# copy server block
ADD sites-enabled/ /etc/nginx/sites-enabled
# enable gzip on types other than html
ADD conf.d/ /etc/nginx/conf.d