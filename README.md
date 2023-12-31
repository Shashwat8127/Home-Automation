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
HARDWARE SETUP:
Connect the Arduino board to an Ethernet shield.
Connect a relay module to the Arduino, which allows switching appliances on/off.
Connect a DHT temperature and humidity sensor to the Arduino.
SOFTWARE SETUP: Install the required libraries: Ethernet, Adafruit_Sensor, and DHT.
Assign appropriate IP addresses, MAC addresses, and pin numbers in the code to match your setup.
Initialization: The code initializes the relay pins as outputs and starts the Ethernet connection.
MAIN LOOP:  The main loop performs the following tasks repeatedly:
Checks if the Ethernet client is connected to the server.
If connected, it reads a command from the server and controls the appliances accordingly.
If not connected, it reads temperature and humidity data from the DHT sensor.
It creates an HTTP POST request with the sensor data and sends it to the server.
Waits for a few seconds before the next item
CONTROL APPLIANCES: The controlAppliances function takes a command as input and controls the corresponding appliances:
If the command is "light_on," it turns on the light by setting the relay pin 1 to HIGH.
If the command is "light_off," it turns off the light by setting the relay pin 1 to LOW.
If the command is "fan_on," it turns on the fan by setting the relay pin 2 to HIGH.
If the command is "fan_off," it turns off the fan by setting the relay pin 2 to LOW.
If the command is "lock," it locks the door by setting the relay pin 3 to HIGH.
If the command is "unlock," it unlocks the door by setting the relay pin 3 to HIGH
SEND REQUEST: The sendRequest function is responsible for sending an HTTP POST request to the server with the provided request data. It establishes a connection with the server, sends the request, and closes the connection.
READ SENSOR DATA: The readSensorData function reads the temperature and humidity values from the DHT sensor. If the sensor data is valid, it returns a string containing the data in the format "temperature=<value>&humidity=<value>". If there is an error reading the data, it returns the string "Error".
SERVER SIDE : On the server side, you need to implement the necessary endpoints to handle the incoming requests from the Arduino.
The server receives the sensor data and can store it or perform any required operations.
The server can also send commands to the Arduino by sending appropriate responses to the Arduino's HTTP requests.
By running this code on your Arduino board and setting up the corresponding server, you can control appliances and monitor temperature and humidity remotely using the mobile application or web interface.

