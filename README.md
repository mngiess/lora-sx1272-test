# LoRa SX1272 test code

This repo contains test code for LoRa SX1272 radios connected to Raspberry Pis.

## Hardware Requirements

* 2 x Raspberry Pi 2 Model B
* 2 x Raspberry Pi to Arduino shields connection bridge
* 2 x LoRa Module SX1272 (868/900MHz) 

![Raspberry Pi with LoRa radio](https://raw.githubusercontent.com/mngiess/lora-sx1272-test/master/pi%2Blora.jpg)

## Compile software

### Clone repo both Raspberry Pis

    git clone https://github.com/mngiess/lora-sx1272-test.git

### Compile arduiPi library for Raspberry Pi 2.0

    cd raspberrypi_2.0
    ./compile_rpi2
    cd ..

### Compile SX1272 driver

    g++ -I./raspberrypi_2.0/ardupi2.0 -c SX1272.cpp -o SX1272.o
    
### Compile transmitter application

    g++ -I./raspberrypi_2.0/ardupi2.0 -lpthread -lrt transmitter.cpp SX1272.o ./raspberrypi_2.0/ardupi2.0/arduPi.o -o transmitter
    
### Compile receiver application

    g++ -I./raspberrypi_2.0/ardupi2.0 -lpthread -lrt receiver.cpp SX1272.o ./raspberrypi_2.0/ardupi2.0/arduPi.o -o receiver
  
  
## Running it

### First Raspberry Pi run the receiver

    ./receiver
    
### Second Raspberry Pi the the transmitter

    ./transmitter
    
### Sample log transmitter

    root@raspberrypi:/usr/src/lora-sx1272-test# ./transmitter 
    SX1272 module and Raspberry Pi: send packets with ACK and retries
    Setting power ON: state 0
    Setting Mode: state 0
    Setting Header ON: state 0
    Setting Channel: state 0
    Setting CRC ON: state 0
    Setting Power: state 0
    Setting Node address: state 0
    SX1272 successfully configured
    
    Packet sent, state 0
    Packet sent, state 0
    Packet sent, state 0
    
### Sample log receiver

    root@raspberrypi:/usr/src/lora-sx1272-test# ./receiver 
    SX1272 module and Raspberry Pi: receive packets with ACK and retries
    Setting power ON: state 0
    Setting Mode: state 0
    Setting Header ON: state 0
    Setting Channel: state 0
    Setting CRC ON: state 0
    Setting Power: state 0
    Setting Node address: state 0
    SX1272 successfully configured
    
    Receive packet with ACK and retries, state 1
    Receive packet with ACK and retries, state 0
    Message: Packet 1, wanting to see if received packet is the same as sent packet
    Receive packet with ACK and retries, state 0
    Message: Packet 2, broadcast test
    Receive packet with ACK and retries, state 0
    Message: Packet 1, wanting to see if received packet is the same as sent packet
    Receive packet with ACK and retries, state 0
    Message: Packet 2, broadcast test
    Receive packet with ACK and retries, state 0
    Message: Packet 1, wanting to see if received packet is the same as sent packet
    Receive packet with ACK and retries, state 0
    Message: Packet 2, broadcast test
