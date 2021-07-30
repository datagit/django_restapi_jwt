#### Rest API JWT
```bash
pip3 install django
# the guide: https://simpleisbetterthancomplex.com/tutorial/2018/12/19/how-to-use-jwt-authentication-with-django-rest-framework.html
# https://django-rest-framework-simplejwt.readthedocs.io/en/latest/getting_started.html
django-admin startproject django_restapi_jwt


pip3 install djangorestframework_simplejwt
pip3 install djangorestframework
# run migration
python3 manage.py migrate

# start local server for develop
python3 manage.py runserver

# admin
python3 manage.py createsuperuser
# login http://127.0.0.1:8000/admin/auth/user/
# create user1/123strong

# create new app -> new api
python3 manage.py startapp first_api

# login
curl --location --request POST 'http://127.0.0.1:8000/api/token/' \
--header 'Content-Type: application/json' \
--data-raw '{
    "username": "user1",
    "password": "123strong"
}'

# call first api hello
curl --location --request GET 'http://127.0.0.1:8000/api/v1/hello/' \
--header 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoiYWNjZXNzIiwiZXhwIjoxNjI3NjMzNDgxLCJqdGkiOiJiYTcxODRiYmMxODI0NTJlYjBlZmMxMDU4NzQ4YWQ2NSIsInVzZXJfaWQiOjJ9.cbeDZmfRDEaKWh9K1a5T4th4HXASwpgYfX8CCU3V24M' \
--data-raw ''

# generate file with all packages used in your PC
pip3 freeze > requirements.txt

# generate file with all packages used in project
pip3 install pipreqs
pipreqs ./
# > INFO: Successfully saved requirements file in ./requirements.txt
# if we have a file requirements.txt then we can install all packages in this file
pip3 install -r ./requirements.txt
```