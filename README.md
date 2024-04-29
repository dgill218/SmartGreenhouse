# Rust powered smart greenhouse

Welcome to my garden

## Project structure

This project is split into two pieces as our greenhouse is a good distance
from our house: 

- Transmitter: This is an Adafruit radiofeather (LoRa) microcontroller.
  Connected to it are moisture sensors, a temperature/ humidity/ pressure sensor,
  and a relay which turns on and off a pump.

  Sensor readings are taken periodically and transmitted over LoRa to the 
  base station (RPI). Immediately after transmitting a message the LoRa 
  radio will enter RX mode and listen for a message from the base station.

- Receiver/ Base Station: This is a Raspberry Pi with a LoRa hat.
  It continuously listens for messages from the transmitter and
  stores sensor readings in a influxdb database.

  It also hosts a control panel for turning on and off the pump.

  Messages to send to the greenhouse device are queued and transmitted after
  a message is received.
