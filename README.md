Docker compose file for setting up a EFK service
================================================

A basic docker compose file that will set up Elasticsearch, Fluent Bit, and Kibana.

The following docker compose allows to ingest data through Forward protocol or Syslog in UDP mode, examples:

### Send data through Forward protocol

```json
echo "{\"key\": 1234}" | fluent-cat test
```

### Send data through Syslog UDP socket

```bash
logger -d -n 127.0.0.1 --port 5140 "hello"
```

