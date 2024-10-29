# IoT Data Analytics & Concurrent Client Handling Sever
Java program to simulate an IoT analytics server which receives sensor data and provides various services to clients such as notification, aggregation, and predictive modelling. Through socket programming, the handling of concurrent clients was ensured while maintaining principles of Quality of Services (QoS). Event handling was implemented using a Earliest Deadline First (EDF) approach to optimize client satisfaction.

Implemented a serverless application running on **AWS Lambda**.`template.yaml` is the config file for the **Lambda** function that specifies the **ReST API path** : `\lmbdafn`, and the **Handler** : `cpen221.mp3.lambda.Function::handleRequest`.
Then utilized **AWS's** `sam` to build and deploy `mp3-Erling` on AWS. Currently the lambda function is triggered at the endpoint `https://2a9yquga3f.execute-api.us-east-2.amazonaws.com/default/IoT_Prediction_Overhead/lmbdafn` with a `HTTP GET`  request with three parameters. This endpoint is hit by a `PredictorThread`.

## Key Components

### Entities and Events
- **Sensors** are elements that generate data through `SensorEvents`, while **Actuators** are active entities with mutable states that can be controlled remotely via `ActuatorEvents`.
- Events are sent to the server through a socket connection, with a configurable frequency
- Entities requires an endpoint to send events.

## Client-Server Interactions

### Client Requests
- Supported request types include:
  - `CONFIG`: Configure entity settings.
  - `CONTROL`: Adjust actuator states.
  - `ANALYSIS`: Run analytics on sensor data.
  - `PREDICT`: Forecast sensor data patterns.

### Server Service
- Offers control and analytics services.
- Manages actuator states and event ordering using an Earliest Deadline First scheduling algorithm.

