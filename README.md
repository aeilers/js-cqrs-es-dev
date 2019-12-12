# hive-io-dev
This project contains the [development stack](./domain/development/docker-compose.yml) and [production stack](./domain/production/docker-compose.yml) for testing the [Domain example](https://www.npmjs.com/package/hive-io-domain-example). It also contains the [development stack](./rest/development/docker-compose.yml) and [production stack](./rest/production/docker-compose.yml) for testing the [REST example](https://www.npmjs.com/package/hive-io-rest-example).
- **NOTE:** Since topics are automatically created when the first event is sent to Kafka, `hive-consumer-js` will need to be restarted after each new topic is created in the Domain stacks. Also, the first event sent for each new topic will throw an error on `hive-producer-js` or `hive-stream-processor-js` but this error can be ignored as the event does go through.

I have also included a copy of the Postman configs for the [REST](./Hive^io_REST_example.postman_collection.json) and [Domain](./Hive^io_CQRS-ES_example.postman_collection.json) to test each endpoint for accuracy. Change each as you see fit.
- **NOTE:** Content IDs are automatically generated when the `CreateContent` command is sent. You will need to update the rest of the commands to reference the ID that is returned.
- **NOTE:** In order to test event snapshot population in Redis or denormalized data in MongoDB, you will have to clear the data from the containers by either deleting the containers since the data in the container is ephemeral.

Here is a reference for relevant `docker-compose` CLI:
- `docker-compose build` to build the development/production images.
- `docker-compose up [--build]` to (re)create/start and optionally build the development/production containers.
- `docker-compose restart` to restart ...
- `docker-compose stop` to stop ...
- `docker-compose rm` to delete ...
- `docker-compose down` to stop and remove ...
