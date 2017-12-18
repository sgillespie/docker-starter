# docker-starter
A starter project for a new docker service including Docker and Docker Compose

# Prerequisites
Before beginning, you must have the following software installed
 * Docker Engine
 * Docker Compose

To install Docker Engine, check the official installation instructions:

https://docs.docker.com/engine/installation

# Getting Started
 * Start in an empty repository
 
        mkdir my-empty-repo     # Or,
        git clone my-empty-repo

        cd my-empty-repo

 * Fetch this repository

        git init
        git fetch https://github.com/sgillespie/docker-starter.git 
        git checkout FETCH_HEAD -- .
    
 * Change placeholder references
  * docker/Dockerfile
  * docker/assets
  * docker-compose.yml
  * docker-compose.override.yml
  * docker-compose.prod.yml
 * Start hacking

# Usage and Workflow
This is only one of many workflows, but it has worked for me so far.

Build and start the dev containers

    docker-compose build # Build the containers
    docker-compose up -d # Start the dev containers
    
When you're satisfied with the results

    # Tag and push the image
    git tag VERSION
    docker tag MY_SERVICE_IMAGE dockerhubuser/MY_SERVICE_IMAGE:VERSION
    docker push dockerhubuser/MY_SERVICE_IMAGE:VERSION

    # Make sure the dev containers are not running
    docker-compose down

    # Start the production containers
    docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
    
# Author
**Sean Gillespie**
 * [sean@mistersg.net](sean@mistersg.net)
 
# License
This is licensed under the Unlicense. See [LICENSE](LICENSE).
