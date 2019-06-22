Exposes port 50000/udp for accepting Juniper JTI streaming telemetry (legacy method, streaming telemetry server and sensors are configured on the router).
```
docker-compose up -d
```

```
+---------+       +----------+       +----------+
|         |       |          |       |          |
| vMX JTI +------>+ Logstash +------>+ Kafka    |
|         |       |          |       |          |
+---------+       +----------+       +----------+
```

Includes kafka-webview for viewing topic content.  This will bind to port 8088.  You will need to configure the kafka cluster and topics.
