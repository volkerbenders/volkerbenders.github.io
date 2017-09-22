# Links on topic mqtt

My experiences up to now.
- I usually use `broker.mqtt-dashboard.com` as a public MQTT broker
- For local tests i use [eclipse mqtt docker image](https://hub.docker.com/_/eclipse-mosquitto/)

Using the default setup both do not require authentification. That makes testing pretty easy.

## Testing mqtt setup
TL;DR
- start broker
- terminal 1: subscribe to topic
- terminal 2: publish message to same topic
- check subscriber in terminal 1 has received the published message
 
There're 3 components involved:
1. MQTT broker
2. MQTT publisher
3. MQTT subscriber

The general idea is one can publish messages to server on a certain topic and someone else can subscribe to a topic and is receives those messages as they arrive.
 
ad 1) A broker is responsible for 
