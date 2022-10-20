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

