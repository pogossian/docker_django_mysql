docker-compose run --no-deps --rm www django-admin startproject project_name .


DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'pirattv',
        'USER': 'root',
        'PASSWORD': 'Access4pirattv',
        'HOST': 'db',   # Or an IP Address that your DB is hosted on
        'PORT': '3306',
    }
}
