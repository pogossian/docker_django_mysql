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

4) Copy existing django project to current directory or create a new project.

```
docker-compose run --no-deps --rm www django-admin startproject project_name .
```

5) Change mysql root password in docker-compose.yml

```
     - MYSQL_ROOT_PASSWORD=newpass
```

6) Change databases to mysql in project_name/settings.py

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

7) Run compose 

```
    docker-compose up -d
```