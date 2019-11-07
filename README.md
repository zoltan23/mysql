# mysql

```
git clone https://github.com/stumurry/mysql.git
cd mysql
```

A database server usually run on seperate machine as opposed to writing code running directly inside of a container.
For this reason, we need to speak to the database server from a node instance so the code will be inside of your node container.
`docker run` only executes 1 container.  In our example we need 2 docker instances.  This is why we are using docker-compose instead of docker.(see stack.yml). 

To bring up mysql:
```
docker-compose -f stack.yml up

Seed the database
docker exec -i mysql_db_1 sh -c 'exec mysql -uroot -p"$MYSQL_ROOT_PASSWORD"' < seed.sql

```
The `adminer` is a separate container that contains a web interface to access the mysql container. Please refer to https://hub.docker.com/_/mysql for more information. It may help with sql queries, dumps, etc. 
``` 
http://localhost:8081/

#username: root
#password: example

Once inside the webpage click on JamWithOurBand database.  Then select `Sql Command`.

Assignment.  Add a table called `TrumpetPlayer` and join it to `User`.  Once your queries have been tested, add them to the `seed.sql` since once docker container is brought down, all of your work will be lost.  To test your work. Bring down the conatiner, then bring it back up.  Reseed.  Rinse and repeat.

