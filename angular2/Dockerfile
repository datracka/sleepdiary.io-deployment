FROM nginx

RUN apt-get update && apt-get install -y \
        git \
        vim

RUN git clone https://github.com/datracka/sleepdiary.io.git /app/sleepdiary.io

WORKDIR /app/sleepdiary.io/

#checkout production branch
RUN git checkout develop

# add custom server block
RUN cp /app/sleepdiary.io/src/index.html /app/sleepdiary.io/dist/index.html
RUN cp /app/sleepdiary.io/src/index.html /app/sleepdiary.io/dist_prod/index.html

RUN rm /etc/nginx/conf.d/default.conf

# add custom config file with gzip enabled
 RUN cp /etc/nginx/nginx.conf /etc/nginx/nginx.conf.backup
 RUN rm -v /etc/nginx/nginx.conf
 ADD nginx.conf /etc/nginx/

# copy server block
ADD conf.d/ /etc/nginx/conf.d
# enable gzip on types other than html
# ADD conf.d/ /etc/nginx/conf.d