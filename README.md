# This is a docker-based nginx proxy project that automatically configures ssl

## Create a docker network

1. use the following command:

    ```docker network create nginx-ssl-proxy```

## Start the service

1. use the following command to start the service:

    ```docker-compose up -d```

## Start you app

1. create you app with docker-compose.yml file, eg:

    ```yml
    version: '3'

    services:
    example-app:
        image: nginx:1.14.0-alpine
        expose:
        - 80
        environment:
        VIRTUAL_HOST: example.com
        LETSENCRYPT_HOST: example.com
        LETSENCRYPT_EMAIL: foo@example.com

    networks:
        default:
            external:
                name: nginx-ssl-proxy

    ```

2. visit example.com and wait a few seconds to see if example.com has `https` enabled.
