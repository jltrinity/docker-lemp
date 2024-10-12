# docker-lemp

# Description
Docker container with PHP 8.2, NGINX and MySQL.

# Prerequisites
* If you are using Windows, you will need WSL2, Ubuntu and Docker Desktop.
* If you are using Linux, you will need the Docker engine.

# Usage
1. Download the project using git clone.
2. On the same directory, tip ``docker-compose up``
3. Create a folder named src outside docker-lemp folder.
4. Create an index.php with phpinfo inside on src folder.
5. Go to localhost/ and you will see the php information.

# MySQL
* You can access to MySQL from the host using: ``mysql -h localhost -uroot -proot``
* Inside containers, you can access to MySQL using the host ``mysql``

#NGINX
* You can add custom server configuration adding all ``*.conf`` files you want.