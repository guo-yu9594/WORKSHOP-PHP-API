<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400"></a></p>

<p align="center">
<a href="https://travis-ci.org/laravel/framework"><img src="https://travis-ci.org/laravel/framework.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/dt/laravel/framework" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>

## About Laravel

Laravel is a web application framework with expressive, elegant syntax. We believe development must be an enjoyable and creative experience to be truly fulfilling. Laravel takes the pain out of development by easing common tasks used in many web projects, such as:

- [Simple, fast routing engine](https://laravel.com/docs/routing).
- [Powerful dependency injection container](https://laravel.com/docs/container).
- Multiple back-ends for [session](https://laravel.com/docs/session) and [cache](https://laravel.com/docs/cache) storage.
- Expressive, intuitive [database ORM](https://laravel.com/docs/eloquent).
- Database agnostic [schema migrations](https://laravel.com/docs/migrations).
- [Robust background job processing](https://laravel.com/docs/queues).
- [Real-time event broadcasting](https://laravel.com/docs/broadcasting).

Laravel is accessible, powerful, and provides tools required for large, robust applications.

## Learning Laravel

Laravel has the most extensive and thorough [documentation](https://laravel.com/docs) and video tutorial library of all modern web application frameworks, making it a breeze to get started with the framework.

If you don't feel like reading, [Laracasts](https://laracasts.com) can help. Laracasts contains over 2000 video tutorials on a range of topics including Laravel, modern PHP, unit testing, and JavaScript. Boost your skills by digging into our comprehensive video library.

# Step 0 - Installation

## Part 1

Install PHP 8.1 et Postman.

To install PHP 8.1 (we are not sure that the installation of php will works for all, so don't hesitate to ask us to help you)
```bash
# For Ubuntu
sudo apt install php8.1
sudo apt install php-cli php-mbstring php-xml
# For Fedora
sudo dnf -y update
sudo dnf -y install http://rpms.remirepo.net/fedora/remi-release-32.rpm # you can replace the 32 by your Fedora version
sudo dnf -y module reset php
sudo dnf -y install dnf-plugins-core
sudo dnf config-manager --set-enabled remi
sudo dnf -y module install php:remi-8.1
sudo dnf install php-cli php-mbstring php-xml

# If you don't have Apache, but normally we don't need Apache
sudo apt install libapache2-mod-php8.1 # Ubuntu
sudo dnf install httpd -y # Fedora
```

Now that you are done installing PHP, you need to install Composer which will allow you to create Laravel project.
```bash
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
sudo php composer-setup.php --filename=composer --install-dir=/usr/local/bin
```

To check if you have installed everything correctly.
```bash
php --version
composer --version
```

Now we need to install Postman which will help you to test your api.
```bash
# If you haven't Snap
sudo apt install snapd # Ubuntu
sudo dnf install snapd # Fedora

# If you already have Snap
sudo snap install postman
```

## Part 2

Now that you finished all required installation, it's time to create your first Laravel project !

We will use Composer to download Laravel and create your Laravel project in your current directory.
```bash
composer create-project --prefer-dist laravel/laravel .
```

Now that you normally created your project, Launch it !
```bash
php artisan serve
```

If something similar appears, it means that all is good.
```bash
Starting Laravel development server: http://127.0.0.1:8000
[Mon May  2 14:38:29 2022] PHP 8.1.4 Development Server (http://127.0.0.1:8000) started
```

Congratulations you created your Laravel project !

# Step 1 - Introduction
It's time to create your first api route.

For your first route, we just need something basic. Create a GET route '/hello' that return a string 'Hello World'.
To help you, here a very great documentation website : https://laravel.com/docs/9.x/routing

To test your newly born route, use your preinstalled Postman to send request to your server.
Here a documentation to learn how to make request with Postman : https://learning.postman.com/docs/sending-requests/requests/

# Step 2 - Controller
Now that you created your first basic php api route, it's time to start something more cleaner.
You must have noticed that the creation of the project generated a lot of files and folders.
Obviously they are not there to decorate.
Particulary 'app/Http/Controllers/'. Normally it's here where you have to create each route 'Controller' (class and function that let you treat the client request).

So you will learn how to create a route controller properly. (Normally we need also to set middleware, but we prefer not to inundate you with non-priority information)

Here is another documentation. This time, it will help to create your controller : https://laravel.com/docs/9.x/controllers

To create your own new controller file, we recommand you to use :
```bash
php artisan make:controller YourControllerName
```

For now you just need to create a controller class which contains the function that you created in the step 1 for the '/hello' route.
The testing process and expected result in Postman is the same as the step 1.

# Step 3 - Main methods

## Part 1 - Prelude
Now let's look at objects, a very important tool for back-end developer.
Using the json object below, you will need to create 4 API routes.
The object consists of 4 elements: First name / Last name / Age / Image (which is a photo of the person).
```json
{
    "0": {
        "Firstname": "Thomas",
        "Lastname": "Willson",
        "Age": 20,
        "Whoami": "https://intra.epitech.eu/file/userprofil/profilview/thomas.willson.jpg"
    },
    "1": {
        "Firstname": "Guo",
        "Lastname": "Yu",
        "Age": 19,
        "Whoami": "https://intra.epitech.eu/file/userprofil/profilview/guo.yu.jpg"
    },
    "2": {
        "Firstname": "Tokito",
        "Lastname": "Muichiro",
        "Age": 14,
        "Whoami": "https://kimetsu-no-yaiba.fandom.com/wiki/Muichiro_Tokito?file=Muichiro_looking_at_the_sky.png"
    },
    "3": {
        "Firstname": "Himejima",
        "Lastname": "Gyomei",
        "Age": 27,
        "Whoami": "https://kimetsu-no-yaiba.fandom.com/wiki/Gyomei_Himejima?file=Gyomei+colored+body.png"
    }
}
```
What to do with this object? It's very simple, now that you've seen how Postman works, including entering an API Route and its Method (ex: GET), let's focus on other tools that will allow us to manipulate the object above.

Below where you put your URL, you should see several "tabs", among these there is `Body`, click on it.
Then just below the bar of the different tabs, you have a parameter bar, click on `raw` and you will see on the right a parameter named `Text`, also click on it and change `Text` to ` JSON`, then insert the JSON object above.

## Part 2 - GET route
Now that you have your `Body` (object) as a parameter, you will have to create a GET route `/get-body` that will return it.
Thus, you will be able to manipulate this object as you wish for the next routes :).
Your response should look like this:
```json
[
    {
        "Firstname": "Thomas",
        "Lastname": "Willson",
        "Age": 20,
        "Whoami": "https://intra.epitech.eu/file/userprofil/profilview/thomas.willson.jpg"
    },
    {
        "Firstname": "Guo",
        "Lastname": "Yu",
        "Age": 19,
        "Whoami": "https://intra.epitech.eu/file/userprofil/profilview/guo.yu.jpg"
    },
    {
        "Firstname": "Tokito",
        "Lastname": "Muichiro",
        "Age": 14,
        "Whoami": "https://kimetsu-no-yaiba.fandom.com/wiki/Muichiro_Tokito?file=Muichiro_looking_at_the_sky.png"
    },
    {
        "Firstname": "Himejima",
        "Lastname": "Gyomei",
        "Age": 27,
        "Whoami": "https://kimetsu-no-yaiba.fandom.com/wiki/Gyomei_Himejima?file=Gyomei+colored+body.png"
    }
]
```

## Part 3 - POST route
Are you able to have your object on hand? Impecable, I would now like to be able to add a new element in my object using the POST method, so you will have to create a route `/add-elem` with this method and then add an element that will include the following information:
```json
    {
        "Firstname": "Workshop",
        "Lastname": "Api-PHP",
        "Age": 117,
        "Whoami": "https://Nobody.com"
    }
```
And add it to my initial object.
PS: Don't pay attention to the content of the link, I myself don't know why it's there :o.
Your response should look like this:
```json
[
    {
        "Firstname": "Thomas",
        "Lastname": "Willson",
        "Age": 20,
        "Whoami": "https://intra.epitech.eu/file/userprofil/profilview/thomas.willson.jpg"
    },
    {
        "Firstname": "Guo",
        "Lastname": "Yu",
        "Age": 19,
        "Whoami": "https://intra.epitech.eu/file/userprofil/profilview/guo.yu.jpg"
    },
    {
        "Firstname": "Tokito",
        "Lastname": "Muichiro",
        "Age": 14,
        "Whoami": "https://kimetsu-no-yaiba.fandom.com/wiki/Muichiro_Tokito?file=Muichiro_looking_at_the_sky.png"
    },
    {
        "Firstname": "Himejima",
        "Lastname": "Gyomei",
        "Age": 27,
        "Whoami": "https://kimetsu-no-yaiba.fandom.com/wiki/Gyomei_Himejima?file=Gyomei+colored+body.png"
    },
    {
        "Firstname": "Workshop",
        "Lastname": "Api-PHP",
        "Age": 117,
        "Whoami": "https://Nobody.com"
    }
]
```

## Part 4 - PUT route
From now on, the idea will be to be able to modify one element or several elements of my object, in this case here, I ask you to modify the Firstname of the first element of my object using the PUT method route `/modif-elem/{id}` as follows: `Thomas ` will become `Toto`.
Your response should look like this:
```json
[
    {
        "Firstname": "Toto",
        "Lastname": "Willson",
        "Age": 20,
        "Whoami": "https://intra.epitech.eu/file/userprofil/profilview/thomas.willson.jpg"
    },
    {
        "Firstname": "Guo",
        "Lastname": "Yu",
        "Age": 19,
        "Whoami": "https://intra.epitech.eu/file/userprofil/profilview/guo.yu.jpg"
    },
    {
        "Firstname": "Tokito",
        "Lastname": "Muichiro",
        "Age": 14,
        "Whoami": "https://kimetsu-no-yaiba.fandom.com/wiki/Muichiro_Tokito?file=Muichiro_looking_at_the_sky.png"
    },
    {
        "Firstname": "Himejima",
        "Lastname": "Gyomei",
        "Age": 27,
        "Whoami": "https://kimetsu-no-yaiba.fandom.com/wiki/Gyomei_Himejima?file=Gyomei+colored+body.png"
    }
]
```

## Part 5 - DELETE route
The DELETE method. Through this method, I will ask you to create a new route `/delete-elem/{id}`, which will remove the second element from my object.
Your response should look like this:
```json
{
    "0": {
        "Firstname": "Thomas",
        "Lastname": "Willson",
        "Age": 20,
        "Whoami": "https://intra.epitech.eu/file/userprofil/profilview/thomas.willson.jpg"
    },
    "2": {
        "Firstname": "Tokito",
        "Lastname": "Muichiro",
        "Age": 14,
        "Whoami": "https://kimetsu-no-yaiba.fandom.com/wiki/Muichiro_Tokito?file=Muichiro_looking_at_the_sky.png"
    },
    "3": {
        "Firstname": "Himejima",
        "Lastname": "Gyomei",
        "Age": 27,
        "Whoami": "https://kimetsu-no-yaiba.fandom.com/wiki/Gyomei_Himejima?file=Gyomei+colored+body.png"
    }
}
```

# Step 4 - Bonus
Create a route using GET method `/rand-picture`, which will return an url to a random picture using Unsplash API (yes, your api can request other api).
Unsplash api is free, you just need to create an account and generate your own Unsplash Access Key by creating an app on their website : https://unsplash.com/developers (it's well documented)