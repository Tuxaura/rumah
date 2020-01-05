# Monitoring Rumah

A simple web interface which is able to subscribe to a MQTT topic and display the information.

The screenshot shows an example how to keep track on what's going in your apartment or your house. It's not about controlling, this setup is about observing various states.


The web page is using bootstrap with jQuery.
Prerequisites/Installation
Get the files

Clone the repository

$ git clone https://github.com/Tuxaura/rumah.git

Dependencies

mqtt-panel is using the listed projects to provide its functionality:

    paho-mqtt/mosqitto
    mqtt

If you are using debian family and want to generate MQTT messages, install the mosquitto and mosquitto-clients

$ sudo apt install mosquitto mosquitto-clients

## MQTT broker/server

A MQTT broker/server with Websocket support is needed.

    hbmqtt - MQTT broker with build-in websockets capabilities
    mosca - A multi-transport MQTT broker for node.js
    mosquitto - An Open Source MQTT v3.1 broker

## Running Monitoring Rumah

    Make sure that your MQTT broker/server is running and listening. 

Generate MQTT messages

For manually sending messages to your MQTT broker/server you can use mosquitto_pub from mosquitto or hbmqtt_pub.

$ mosquitto_pub -h tailor.cloudmqtt.com -d -u ylumabjj -P Jw5x0j8_IN2D -p 11841 -t rumah/depan/pintu -m "false"
$ mosquitto_pub -h tailor.cloudmqtt.com -d -u ylumabjj -P Jw5x0j8_IN2D -p 11841 -t rumah/belakang/pintu -m "false"
$ mosquitto_pub -h tailor.cloudmqtt.com -d -u ylumabjj -P Jw5x0j8_IN2D -p 11841 -t rumah/ruangtamu -m 18
$ mosquitto_pub -h tailor.cloudmqtt.com -d -u ylumabjj -P Jw5x0j8_IN2D -p 11841 -t rumah/kamartidur -m 15


To check if the messages are are ok, subscribe to the topic home/# with mosquitto_sub.

$ mosquitto_sub -h tailor.cloudmqtt.com -d -u ylumabjj -P Jw5x0j8_IN2D -p 11841 -t rumah/#

## Credits

Monitoring Rumah was adopted from

  *  [mqtt-panel](https://github.com/fabaff/mqtt-panel) 

## License

mqtt-panel licensed under MIT, for more details check LICENSE.
