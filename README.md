# JDAC

A simple open-source data collection system that collects data from different sensors using an Arduino board.  

JDAC is a Java application, that connects to the Arduino, plots the data in real-time and allows the user to export the data in CSV or PNG format.  

More informations on the project are available on the [project website](https://lizzit.it/jdac)

## Java application
| ![Logo](/screenshots/screen1.png) |
|---|
| A screenshot of the JDAC Java application |

JDAC can be launched by executing the jar file available in this repository.  

| ![Logo](/logo.png) |
|---|
| The application logo |

## Arduino firmware
JDAC can connect to any Arduino board that sends the data, separated by the newline character, via serial at 115200bps.  
In this repository there are some example Arduino sketches:  
### Random
Generates random data without requiring any sensor to be connected.  
Useful for testing purposes.  
### DS18B20
It interfaces with a DS18B20 temperature probe.
### Casio EA200
Connects to a Casio EA200 or Casio CLAB, and collects the data from one of the sensors connected.  
In order to connect to a Casio CLAB or Casio EA200, the Arduino must be connected to the 2.5mm jack connector on the unit, as specified in the Config.h file.  
The 2.5mm jack on the Casio unit is actually a 5V TTL serial port working at 38400baud, the unit usually connects to a Casio calculator and transfers the data to the calculator, however it can be connected to any other device implementing the right protocol.  
More information on the protocol used by the unit is available on the official Casio website: http://support.casio.com/storage/en/manual/pdf/EN/004/EA200_TechnicalReference_EN.pdf  
The Arduino firmware "EA200" implements the protocol as specified in the official technical reference and collects the data from the sensor specified in the Config.h file.  
The Config.h file is placed in the "casioEA200" folder and contains some preprocessor directives that configure the firmware during compilation.  
### Custom firmware
In order to write a JDAC compatible firmware the firmware has to collect the data and send it via the USB serial port at 115200baud, each value has to be separated by a newline character ("\n", ASCII code 10) and has to use a dot (".") as decimal mark, as soon as a value is received the JDAC application adds a point to the chart.
