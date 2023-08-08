# **Docker Basics**

This document covers the Docker basic commands which a basic HTML webpage is running in a container. The Docker container is created on Linode.

- Search for docker in marketplace

  ![image](https://github.com/pohwj/docker-basics/assets/118417467/582765f8-170b-4f54-b432-a7fc2c3327bf)

- Create a VM on Linode. Choose your image, region, Linode plan, set your root password and click Create Linode

  ![image](https://github.com/pohwj/docker-basics/assets/118417467/01dbc61e-405a-40f4-a963-f46525901997)

- On cmd, ssh into your VM via the command of ssh root@your-VM-IP-address. Enter your root password.

- In your desired directory, create a src folder and a Dockerfile

  ![image](https://github.com/pohwj/docker-basics/assets/118417467/becef5c3-a278-4432-841a-07b9a7d4481c)

- Create a index.html file in your src folder. You can customise the html file to your liking.

  ![image](https://github.com/pohwj/docker-basics/assets/118417467/761ef8db-ca89-4424-a691-3c7e679dd500)

- Return to the Dockerfile and include the following commands
  - FROM nginx:latest --> using the latest image of nginx for the container
  - COPY src/index.html /usr/share/nginx/html --> copy the index.html in src folder to /usr/share/nginx/html
  - EXPOSE 80 --> Docker container listen on port 80
  - CMD ["nginx", "-g", "daemon off;"] --> Run nginx with daemon off when container starts up

  ![image](https://github.com/pohwj/docker-basics/assets/118417467/3abf056f-b5ee-4756-bcb9-4c90d0f556a1)

- Return to the directory where the Dockerfile is located and build the docker image with following command, where -t means tagging.

  docker build -t website-name .

- Enter the following command to check if the image has been created.

  docker images

- To run the docker container in detached mode and listen on port 8080 of host, enter the following

  docker run -d -p 8080:80 website-name

- To check if the container is running, enter the following

  docker ps

- Open the web browser and enter the following to see the webpage

  http://your-VM-IP-address:8081



