*Project will use docker and docker-compose, so please make sure that docker was installed and ran*

1) Clone project 

```
git clone https://github.com/pogossian/docker_django_mysql.git project_name
```

2) Go to cloned directory and remove old .git directory

```
cd project_name
rm -rf .git/
```

3) Initialize a new version control.

```
git init
```

4) Review and update `requirements.txt`


5) Copy existing django project to current directory or create a new project.

     *it's can take a long time, because before run compose would build an image*

```
docker-compose run --no-deps --rm www django-admin startproject project_name .
```

6) Change mysql root password in `docker-compose.yml`

```
     - MYSQL_ROOT_PASSWORD=newpass
```

7) Change databases to mysql in `project_name/settings.py`

```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'db',
        'USER': 'root',
        'PASSWORD': 'newpass',
        'HOST': 'db',   # Or an IP Address that your DB is hosted on
        'PORT': '3306',
    }
}
```

8) Run compose 

```
    docker-compose up -d
```

9) Django will run as soon as mysql be ready (if you want you can watch to running proccess `docker-compose logs`)
* http://localhost:8000


10) Create superuser

```
docker exec -it project_name_www_1 python3 manage.py createsuperuser
```

11) Try to login in admin page
* http://localhost:8000/admin/



P.S


use `docker exec -it project_name_www_1 python3 manage.py` command for working with `manage.py`

e.g.

`docker exec -it project_name_www_1 python3 manage.py migrate` - for migrate

`docker exec -it project_name_www_1 python3 manage.py makemigrations` - for makemigrations
