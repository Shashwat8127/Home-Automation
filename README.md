# Home-Automation
This code is an Arduino sketch that controls appliances (such as lights, fans, and locks) based on commands received over Ethernet and sends temperature and humidity data from a DHT sensor to a server via HTTP POST requests. Here's a breakdown of the code:
1.	The necessary libraries are included: SPI, Ethernet, Adafruit_Sensor, and DHT.
2.	Constants are defined for the relay pins and DHT sensor pin.
3.	MAC and IP addresses are defined for Ethernet communication.
4.	An Ethernet client object is created.
5.	A DHT object is created, specifying the DHT sensor pin and type (DHT11).
6.	The sendRequest function is defined to send an HTTP POST request to the server.
7.	The readSensorData function reads temperature and humidity data from the DHT sensor and returns it as a string.
8.	The controlAppliances function controls the appliances based on the received command.
9.	In the setup function:
•	The relay pins are initialized as outputs.
•	The Ethernet connection is started with the specified MAC and IP addresses.
•	The DHT sensor is initialized.
10.	In the loop function:
•	If the client is connected, it reads a command from the server and trims any leading/trailing whitespace.
•	If the client is not connected, it generates data from the DHT sensor and creates an HTTP POST request with the data.
•	The request is sent to the server using the sendRequest function.
•	A delay of 5 seconds is added before the next iteration.
