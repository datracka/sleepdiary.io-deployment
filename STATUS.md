CURRENT STATUS FEATURE:

- Added new images replacing tutum/nginx

We are still checking that utw is properly installed as necessarily
step for ssl configuration.

UFW did not work well with old docker image (kernel problem)

For that:

- We have to build a new production image using master branch in
sleepdiary.io-deployment. (We trust that this image will work)

- Run again all the steps following the dockerfile.prod from
ssl-cerrificates branch

If it works in PRODUCTION we have to check why does not allow to
validate certificate when building the docker repository:

this works running directly in docker container in production

certbot certonly \
    --email datracka@gmail.com \
    --agree-tos \
    --text \
    --non-interactive \
    --webroot -w /app/sleepdiary.io/dist_prod -d app.sleepdiary.io

But it does not work if ran through the dockerfile


