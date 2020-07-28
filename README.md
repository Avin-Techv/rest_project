Rest Project
============
This is a sample project to demonstrate dockerizing a django rest app with postgresql as backend. This project creates groups, users and lists them.


## Steps Involved

1. create docker image by going into the folder which contains docker-compose.yml and type

```bash
docker-compose build
```

2. run the docker image by

```bash
docker-compose up
```
or 
```bash
docker-compose up -d 
```

to run as daemon

3. see the docker running process by going into a new terminal and typeing

```bash
docker ps
```
or 
```bash
docker ps -a
```

4. click the link of the docker from the terminal or got from "docker ps" command her its

```bash
http://127.0.0.1:8000/
```

5. to demonstate the docker works with postgres just go to the docker image via the command 1 and migrate the project database via command 2

```bash
docker exec -it rest_project_web_1 sh
```
```bash
python manage.py runserver
```

where resr_project_web_1 is the name of the docker image

6. then go to postgres in docker terminal by

```bash
docker-compose exec db psql --username=rest_project --dbname=rest_project_db
```

which will direct you to to the terminal and then

```bash
\l 
```

to list the databases and similar psql commands for the rest of the operations

## Verifying if values from Docker are getting displayed

1. go to docker terminal

```bash
docker exec -it rest_project_web_1 sh
```

2. create a superuser via the following command and give necessary details

```bash
./manage.py createsuperuser
```

3. after running the container check the following url in browser, the createuser details will be displayed in there

```bash
http://0.0.0.0:8000/users/
```
