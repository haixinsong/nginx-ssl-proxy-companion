# A docker-compose tamplate that nginx reverse proxy with automatically configures ssl

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
        image: nginx:alpine
        expose:
        - 80
        environment:
        VIRTUAL_HOST: example.com
        VIRTUAL_PORT: 80
        LETSENCRYPT_HOST: example.com
        LETSENCRYPT_EMAIL: foo@example.com

    networks:
        default:
            external:
                name: nginx-ssl-proxy

    ```

2. visit example.com and wait a few seconds to see if example.com has `https` enabled.

## detail

- [https://github.com/JrCs/docker-letsencrypt-nginx-proxy-companion](https://github.com/JrCs/docker-letsencrypt-nginx-proxy-companion)
- [https://github.com/jwilder/nginx-proxy](https://github.com/jwilder/nginx-proxy)
