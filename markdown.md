# LEMP STACK IMPLEMENTATION

## INSTALLING NGNIX WEB SERVER

`sudo apt update`

![updating server package index]()

`sudo apt upgrade`

![sudo apt upgrade](./images/NGINX_images/pending_kernel_upgrade.PNG)

![sudo apt upgrade](./images/NGINX_images/outdated_libraries.PNG)

![sudo apt upgrade](./images/NGINX_images/sudo_apt_upgrade_page1.PNG)

![sudo apt upgrade](./images/NGINX_images/sudo_apt_upgrade_page2.PNG)

`sudo apt install nginx`

![nginx kernel upgrade](./images/NGINX_images/nginx_kernel_upgrade.PNG)

![nginx outdated libraries](./images/NGINX_images/nginx_oudated_libraries.PNG)

![nginx installation](./images/NGINX_images/sudo_apt_install_nginx.PNG)

`sudo systemctl status nginx`

![nginx status](./images/NGINX_images/nginx_status.PNG)

OPEN TCP P0RT 80

![open tcp port 80](./images/NGINX_images/tcp_port_80.PNG)

`curl http://35.180.156.219`

![curl http](./images/NGINX_images/curl_http.PNG)

[public ip address](http://35.180.156.219)

![ngnix web page](./images/NGINX_images/ngnix_web_page.PNG)

`curl -s http://35.180.156.219/latest/meta-data/public-ipv4`

![retrieving public ip](./images/NGINX_images/public_ip_retrieve.PNG)

### INSTALLING MYSQL

`sudo apt install mysql-server`

![sql server installation](./images/mysql_installation/mysql_kernel_upgrade.PNG)

![sql server installation](./images/mysql_installation/mysql_outdated_libraries.PNG)

![sql server installation](./images/mysql_installation/mysql_server_installation.PNG)

`sudo mysql`

![sudo mysql](./images/mysql_installation/sudo_mysql.PNG)

`sudo mysql_secure_installation`

![mysql_secure_installation](./images/mysql_installation/msql_secure_installation_page1.PNG)

![mysql_secure_installation](./images/mysql_installation/mysql_secure_installation_page2.PNG)

`sudo mysql -p`

![test to log into mysql](./images/mysql_installation/mysql_login_test.PNG)

INSTALLING PHP

`sudo apt install php-fpm php-mysql`

![installing php-fpm and php-mysql](./images/php_installation/pending_kernel_upgrade.PNG)

![installing php-fpm and php-mysql](./images/php_installation/outdated_libraries.PNG)

![installing php-fpm and php-mysql](./images/php_installation/php_fph-php_mysql_installation.PNG)

CONFIGURING NGINX TO USE PHP PROCESSOR

`sudo mkdir /var/www/projectLEMP`

`sudo chown -R $USER:$USER /var/www/projectLEMP`

`sudo nano /etc/nginx/sites-available/projectLEMP`

input nano code

#/etc/nginx/sites-available/projectLEMP

server {
    listen 80;
    server_name projectLEMP www.projectLEMP;
    root /var/www/projectLEMP;

    index index.html index.htm index.php;

    location / {
        try_files $uri $uri/ =404;
    }

    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php8.1-fpm.sock;
     }

    location ~ /\.ht {
        deny all;
    }

}

`sudo ln -s /etc/nginx/sites-available/projectLEMP /etc/nginx/sites-enabled/`

`sudo nginx -t`

![nano syntax error test](./images/configuring_nginx_4_php_processor/nano_syntax_error_test.PNG)

`sudo unlink /etc/nginx/sites_enabled/default`

`sudo systemctl reload nginx`

`sudo echo 'Hello LEMP from hostname' $(curl -s http://35.180.156.219/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://35.180.156.219latest/meta-data/public-ipv4) > /var/www/projectLEMP/index.html`

[website url](http://35.180.156.219/)

![website screenshot](./images/configuring_nginx_4_php_processor/website_screenshot.PNG)

ec2-35-180-156-219.eu-west-3.compute.amazonaws.com

![public DNS](./images/configuring_nginx_4_php_processor/public_DNS.PNG)

TESTING PHP WITH NGINX

`sudo nano /var/www/projectLEMP/info.php`

<?php
phpinfo();

![nano php code insertion](./images/testing_php_with_nginx/php_script_on_nano_editor.PNG)

[ip/info.php](http://35.180.156.219/info.php)

![browser screensot after inserting test php file](./images/testing_php_with_nginx/browser_page_php_script.PNG)

`sudo rm /var/www/projectLEMP/info.php`

![removing info.php file](./images/testing_php_with_nginx/removed_info.php_file.PNG)

RETRIEVING DATA FROM MYSQL DATABASE WITH PHP

`sudo mysql -p`

![logging into mysql database](./images/retrieving_data_from_mysqlDatabase_using_php/logging_into_mysql_database.PNG)

` 'create database example_database;`

![creating database named example_database](./images/retrieving_data_from_mysqlDatabase_using_php/example_database_creation.PNG)

`show databases;`

![show databases command](./images/retrieving_data_from_mysqlDatabase_using_php/show_databases_command.PNG)


`CREATE USER example_user @ IDENTIFIED WITH mysql_native_password BY 'HappyKonga@802';`

![creating user named example_user](./images/retrieving_data_from_mysqlDatabase_using_php/created_user_named_example_user.PNG)

`GRANT ALL ON example_database.* TO example_user @;`

1[granting permissions to created used named example_user](./images/retrieving_data_from_mysqlDatabase_using_php/granting_permissions_to_example_user.PNG)

`exit`

![exiting mysql](./images/retrieving_data_from_mysqlDatabase_using_php/exiting_mysql.PNG)

`mysql -u example_user -p`

![example_user login](./images/retrieving_data_from_mysqlDatabase_using_php/example_user_login.PNG)

`SHOW DATABASES;`

![SHOW DATABASES COMMAND](./images/retrieving_data_from_mysqlDatabase_using_php/SHOW_DATABASES_command2.PNG)

CREATE TABLE example_database.todo_list(
    -> item_id INT AUTO_INCREMENT,
    -> content VARCHAR(255),
    -> PRIMARY KEY(item_id));

![creating table named todo_list inside example_user database](./images/retrieving_data_from_mysqlDatabase_using_php/created_table_in_example_database.PNG)

mysql>  INSERT INTO example_database.todo_list (content) VALUE("My first important item");

mysql> INSERT INTO example_database.todo_list (content) VALUE("My second important item");

mysql> INSERT INTO example_database.todo_list (content) VALUE("My third important item");

mysql> INSERT INTO example_database.todo_list (content) VALUE("Visit the dentist");

mysql> INSERT INTO example_database.todo_list (content) VALUE("Study for at least 6 hours daily");

![inserting rows of content](./images/retrieving_data_from_mysqlDatabase_using_php/inserting_rows_of_content.PNG)

SELECT * FROM example_database.todo_list;

mysql> exit


![mysql exit](./images/retrieving_data_from_mysqlDatabase_using_php/mysql_exit_command.PNG)

`nano /var/www/projectLEMP/todo_list.php`

Input nano script

<?php
$user = "example_user";
$password = "password";
$database = "example_database";
$table = "todo_list";

try {
  $db = new PDO("mysql:host=localhost;dbname=$database", $user, $password);
  echo "<h2>TODO</h2><ol>";
  foreach($db->query("SELECT content FROM $table") as $row) {
    echo "<li>" . $row['content'] . "</li>";
  }
  echo "</ol>";
} catch (PDOException $e) {
    print "Error!: " . $e->getMessage() . "<br/>";
    die();
}

![nano script insertion](./images/retrieving_data_from_mysqlDatabase_using_php/nano_script_inserted.PNG)

[testing access to webpage](http://35.180.156.219/todo_list.php)

![webpage screenshot](./images/retrieving_data_from_mysqlDatabase_using_php/webpage_screenshot.PNG)

END OF PROJECT

