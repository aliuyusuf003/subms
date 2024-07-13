# PROBLEM STATEMENT
Create a simple subscription platform(only RESTful APIs with MySQL) in which users can subscribe to a website (there can be multiple websites in the system). Whenever a new post is published on a particular website, all it's subscribers shall receive an email with the post title and description in it. (no authentication of any kind is required)

## Installation Setup
1. Clone the repository
2. Run `composer install` to install the dependencies.
3. Run `composer run-script post-root-package-install` to generate your local `.env` file.
4. Run `composer run-script post-create-project-cmd` to generate your application key.
5. Open your `.env` and configure your database credentials.
6. Run `php artisan migrate --seed`
7. locate hosts file path
C:\Windows\System32\drivers\etc
add this to hosts file
127.0.0.1 sub.test
locate httpd-vhosts.conf file
C:\xampp\apache\conf\extra
Add the below
<VirtualHost *:80>
    
    DocumentRoot "C:/xampp/htdocs/subms/public"
    ServerName subms.test
    ServerAlias www.subms.test
	
<Directory "C:/xampp/htdocs/ subms /public">
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>   
</VirtualHost>


## Documentation
https://documenter.getpostman.com/view/7012999/2sA3e5eoCR

## Queue
The post notification to subscribers are queued, so you will need to run `php artisan queue:listen`
## Send email command
command to send email to the subscribers 
 `php artisan notify:subscribers`.

