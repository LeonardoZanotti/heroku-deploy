<img src="https://blog.4linux.com.br/wp-content/uploads/2018/01/Heroku.png" alt="heroku" />

# Heroku deploy
Guide to deploy a Laravel (backend) + Vuejs (frontend) application.

**If you have a project just go to Deploy section.**

# Requirements
Im using the following, but you can use the versions you use in your project:
* [Composer 1.10.13](https://getcomposer.org/download/)
* [Git](https://git-scm.com/downloads)
* [Laravel 5.7.29](https://laravel.com/docs/5.8/installation)
* [MariaDB 10.4.13](https://mariadb.org/download/)
* [Node 13.14.0 and Npm 6.14.4](https://nodejs.org/en/)
* [PHP 7.4.10](https://www.php.net/downloads.php)
* [Vue 4.5.6](https://cli.vuejs.org/guide/installation.html)
* [A Heroku account](https://signup.heroku.com/)
* [And Heroku CLI](https://devcenter.heroku.com/articles/heroku-cli)

## Backend installation
If you dont have a project and just wants to know how to deploy a heroku application, you can clone this repository and use the sample project or create a new project with `composer create-project laravel/laravel your-project-name`.

```bash
# CLone this project 
$ git clone https://github.com/LeonardoZanotti/heroku-deploy.git

# Enter the backend folder
$ cd backend/

# Install the dependences
$ composer install

# Enter mysql
$ sudo mysql -u root

# Create the database
$ create database capacitacao;

# Create an user (replace 'newuser' and 'user_password' with your credentials)
$ CREATE USER 'newuser'@'localhost' IDENTIFIED BY 'user_password';

# Give permission to the user
$ GRANT ALL PRIVILEGES ON *.* TO 'newuser'@'localhost';

# Exit mysql
$ exit

# Clone the .env.example file to configura the database
$ cp .env.example .env

# .env configuration
$ nano .env

# Replace this infos with your credentials
"DB_DATABASE =  capacitacao"
"DB_USERNAME = your_user"
"DB_PASSWORD = your_password"

# Final configurations
$ php artisan key:generate
$ php artisan migrate:fresh --seed
$ php artisan storage:link
$ composer require laravel/passport
$ php artisan passport:install

# Run the project -> The Laravel page will be available on localhost:8000
php artisan serve
```

## Frontend installation
If you wants to create e new frontend project with vuejs you can type `vue create your-project-name`. Otherwise, just do the following:
```bash
# Enter the frontend folder
$ cd frontend/

# Install dependences
$ npm install

# Run the frontend -> The Vue page will be available on localhost:8080
$ npm run serve
```

## LeonardoZanotti