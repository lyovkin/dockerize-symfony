# Dockerize Symfony Application :whale: :ant:

## Under the hood
- PHP7.1.5-fpm 
- NGINX
- Mongo DB

## Installation
1. Create a `.env` from the `.env.dist` file. Adapt it according to your symfony application

    ```bash
    cp .env.dist .env
    ```
    
2. Build/run containers 

    ```bash
    $ docker-compose up -d --build
    ```    
3. Update your system host file (add symfony.dev)

    ```bash
    # PROJECT_NAME means name in .env file
    $ docker insect PROJECT_NAME-nginx | grep IPAddress
    
    # set IPAddress by command or manually
    $ sudo echo "IPAddress symfony.dev" >> /etc/hosts
    ```    

To be continued ...
