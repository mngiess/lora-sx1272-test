# lora-sx1272-test
Lora SX1272 test code

## Compile ardiPi libraray for Raspberry Pi 2.0

    cd raspberrypi_2.0
    ./compile_rpi2 

## Compile SX1272 driver

    g++ -I./raspberrypi_2.0/ardupi2.0 -c SX1272.cpp -o SX1272.o
    
## Compile transmitter application

    g++ -I./raspberrypi_2.0/ardupi2.0 -lpthread -lrt transmitter.cpp SX1272.o ./raspberrypi_2.0/ardupi2.0/arduPi.o -o transmitter
    
## Compile receiver application

    g++ -I./raspberrypi_2.0/ardupi2.0 -lpthread -lrt receiver.cpp SX1272.o ./raspberrypi_2.0/ardupi2.0/arduPi.o -o receiver
