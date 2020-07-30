# Docker compose file for setting up a EFK service

A basic docker compose file for Elasticsearch, Fluentd, and Kibana. Includes an example `httpd` service to generate logs.

## Example

The file `example/httpd.yml` shows how to configure a service to use EFK as its logging facility. To test using this file, just run:

```bash
docker-compose -f docker-compose.yml -f example/httpd.yml up
```

Watch the logs and wait for everything to startup.

1. Load http://localhost:80 multiple times to generate log events.
2. Load Kibana: http://localhost:5601/app/kibana#/discover which will redirect to the Kibana configuration to _Create index Pattern_.
3. Enter `fluentd-*` in the _Index pattern_ field. See "Success! Your index pattern matches 1 index."
4. Click the _Next setup_ button.
5. Select `@timestamp` in the the _Time Filter field name_.
6. Click the _Create index pattern_ button.
7. Wait for processing
8. See the Index pattern details.
9. Go to Discover:  http://localhost:5601/app/kibana#/discover

## Example cleanup

Clean up with:

```bash
docker-compose -f docker-compose.yml -f example/httpd.yml rm -f
```
