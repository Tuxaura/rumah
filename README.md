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

    paho-mqtt
    mqtt

If you are using Fedora and want to generate MQTT messages, install the paho-mqtt Python bindings.

$ sudo dnf -y install python-paho-mqtt

## MQTT broker/server

A MQTT broker/server with Websocket support is needed.

    hbmqtt - MQTT broker with build-in websockets capabilities
    mosca - A multi-transport MQTT broker for node.js
    mosquitto - An Open Source MQTT v3.1 broker

## Running Monitoring Rumah

    Make sure that your MQTT broker/server is running and listening. Or run python3 mqtt-server.py to use mqtt-panel with hbmqtt (make sure that you installed it with pip3 install hbmqtt).
    Adjust var host = '127.0.0.1'; and var port = 3000; in the file index.html to match your setup if you are not using mqtt-server.py.
    Open index.html.

Generate MQTT messages

Start the ./test-messages.py script to publish test messages if you have no other source for messages. Depending on your broker you may need to set the supported version. On line 33: protocol=mqtt.MQTTv311

For manually sending messages to your MQTT broker/server you can use mosquitto_pub from mosquitto or hbmqtt_pub.

$ mosquitto_pub -V mqttv311 -h localhost -d -t home/front/door -m "false"

To check if the messages are are ok, subscribe to the topic home/# with mosquitto_sub.

$ mosquitto_sub -V mqttv311 -h localhost -d -t home/#

## Credits

Monitoring Rumah was adopted from

  *  [mqtt-panel](https://github.com/fabaff/mqtt-panel) 

## License

mqtt-panel licensed under MIT, for more details check LICENSE.
