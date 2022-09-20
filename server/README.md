# Modular Monolith Example

## Content
- PHP container running version 8.1.1
- MySQL container running version 8.0.26

## Instructions
- `make build` to build the containers
- `make start` to start the containers
- `make stop` to stop the containers
- `make restart` to restart the containers
- `make prepare` to install dependencies with composer (once the project has been created)
- `make run` to start a web server listening on port 1000 (8000 in the container)
- `make logs` to see application logs
- `make ssh-be` to SSH into the application container


.env configuration by orm and rabbitmq

    ###> doctrine/doctrine-bundle ###
    # DATABASE_URL="sqlite:///%kernel.project_dir%/var/data.db"
    #DATABASE_URL="mysql://root:root@codenip-php81-symfony54-mysql:3306/mysql_symfony?serverVersion=8.0"
    DATABASE_URL="postgresql://user:passwd@codenip-php81-symfony54-postgres:5432/postgres_symfony?serverVersion=14&charset=utf8"
    ###< doctrine/doctrine-bundle ###
    
    ###> symfony/messenger ###
    # Choose one of the transports below
    # MESSENGER_TRANSPORT_DSN=doctrine://default
    MESSENGER_TRANSPORT_DSN=amqp://guest:guest@docker-dev-env-for-symfony-rabbitmq:5672/%2f/messages
    # MESSENGER_TRANSPORT_DSN=redis://localhost:6379/messages
    ###< symfony/messenger ###

Happy coding!

### For testing
- Insert phpunit testing with composer 'composer require --dev phpunit/phpunit symfony/test-pack'
- Run `sf d:m:m -n --env=test` to apply migrations on test enviroment

composer dump-autoload --- when not found files after rename it