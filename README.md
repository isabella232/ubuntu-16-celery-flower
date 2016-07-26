
# Celery Flower in Docker

* Celery is a Distributed Task Queue: http://www.celeryproject.org/
* Flower is a Celery monitoring tool: http://flower.readthedocs.io/en/latest/
* Docker is an software containerization tool: https://www.docker.com/

## Quick Start

 1. First run a broker for Celery. I use RabbitMQ (https://www.rabbitmq.com/).
    ```
    docker run -d -P --name=rabbitmq rabbitmq:3-management 
    ```

 2. Run the Flower image.
    ```
    docker run -d -P --link rabbitmq:rabbitmq --name=flower astrolox/ubuntu-16-celery-flower
    ```

## Environment variables

All configuration is via environment variables.

* ``CELERY_BROKER_URL`` - defaults to amqp://guest:guest@rabbitmq:5672//
* ``CELERY_BROKER_API`` - defaults to http://guest:guest@rabbitmq:15672/api/
* ``HTTP_USERNAME``     - Username to access Flower, defaults to flower
* ``HTTP_PASSWORD``     - Password to access Flower, defaults to insecure
