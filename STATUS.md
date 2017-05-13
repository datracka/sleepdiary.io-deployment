STATUS:

With new NGNIX image the angular container does not run. 
  
The error looks that it does not found the "host" link to Backend 
(run $ nginx in docker container to obtain the error)

- The problem looks is that 443 is not open

Solution: run docker-compose with ports 80 and 443 

