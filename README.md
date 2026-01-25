# docker-lemp

# 📖 Description
Docker container with PHP 8.3, NGINX and MySQL.

# ✅ Prerequisites
* If you are using Windows, you will need WSL2, Ubuntu and Docker Desktop.
* If you are using Linux, you will need the Docker engine.

You must to create the following directories:

   ```bash
   mkdir grafana-data
   mkdir loki-data   
   mkdir loki-wal   
   mkdir mysql   
   ```

# 🚀 Usage
1. Download the project using git clone.
2. On the same directory, you can start the containers with the following commands:
   - To start the containers without rebuilding the images:
     ```bash
     docker-compose up
     ```
   - To start the containers and rebuild the images:
     ```bash
     docker-compose up --build
     ```
3. Create a folder named src outside docker-lemp folder.
4. Create an index.php with phpinfo inside on src folder.
5. Go to localhost/ and you will see the php information.

# 🛠️ MySQL
* You can access to MySQL from the host using: ``mysql -h localhost -uroot -proot``
* Inside containers, you can access to MySQL using the host ``mysql``

# 🌐 NGINX
* You can add custom server configuration adding all ``*.conf`` files you want.


# 🛡️ Troubleshooting

## 🔒 Permission Denied Error

If you encounter a "permission denied while trying to connect to the docker API at unix:///var/run/docker.sock" error, follow these steps:

1. Verify if the `docker` group exists:

   ```bash
   getent group docker
   ```

2. If the group does not exist, create it:

   ```bash
   sudo groupadd docker
   ```

3. Add your user to the `docker` group:

   ```bash
   sudo usermod -aG docker $(whoami)
   ```

4. Restart your session or run:

   ```bash
   newgrp docker
   ```

5. Verify that you can run Docker commands without `sudo`:

   ```bash
   docker ps
   ```

## 🛠️ Docker Credential Helper Error

If you encounter a `docker.credentials.errors.InitializationError: docker-credential-pass not installed or not available in PATH` error, follow these steps:

1. Install `pass` and `gnupg`:

   ```bash
   sudo apt update && sudo apt install -y pass gnupg
   ```

2. Generate a new GPG key (if you don't already have one):

   ```bash
   gpg --generate-key
   ```
   Follow the instructions and remember the password you set.

3. List your GPG keys to get the key ID:

   ```bash
   gpg --list-keys
   ```

4. Initialize `pass` with your GPG key ID:

   ```bash
   pass init <GPG_KEY_ID>
   ```

5. Install the Docker credential helper:

   ```bash
   sudo apt install -y golang-docker-credential-helpers
   ```

6. Configure Docker to use `pass` as the credential store by editing or creating the `~/.docker/config.json` file and adding:

   ```json
   {
     "credsStore": "pass"
   }
   ```

7. Test the configuration by logging in to Docker:

   ```bash
   docker login
   ```

   If everything is set up correctly, your credentials will be stored using `pass`.


# 🗑️ Removing Images and Containers

To manage your Docker environment, you may need to remove images or containers. Here are the commands to do so:

- To remove a specific container:
  ```bash
  docker rm <container_name_or_id>
  ```

- To remove a specific image:
  ```bash
  docker rmi <image_id>
  ```

- To remove all stopped containers:
  ```bash
  docker container prune
  ```

- To remove all unused images:
  ```bash
  docker image prune
  ```

- To remove all containers:
  ```bash
  docker rm -v -f $(docker ps -qa)
  ```



# 📝 Changelog

## [Unreleased]
- Initial release with PHP 8.3, NGINX, and MySQL setup.
- Basic instructions for setting up and running the Docker LEMP stack.
- Support for custom NGINX server configurations.