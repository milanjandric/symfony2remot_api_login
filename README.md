staff-login-example-app
=======================

# Requirements

* php 5.6
* composer
* mysql

# Install

Create database and configure `parameters.yml` to reflect database configuration.

Generate the SSH Key:

```
$ mkdir -p app/var/jwt
$ openssl genrsa -out app/var/jwt/private.pem -aes256 4096
$ openssl rsa -pubout -in app/var/jwt/private.pem -out app/var/jwt/public.pem
```

Install dependencies:

```
$ composer install
```

Create database scheme:

```
app/console doctrine:schema:update --force
```

# Run

```
$ cd web
$ php -S localhost:8000
```

# Example

1. Register new user at http://localhost:8000/app_dev.php/register

2. Click logout button

3. Obtain JWT token: `curl -X POST http://localhost:8000/app_dev.php/api/login_check -d _username= -d _password=`

4. Login using JWT token: http://localhost:8000/app_dev.php/api/secure?token=
