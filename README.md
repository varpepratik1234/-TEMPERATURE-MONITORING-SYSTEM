# -TEMPERATURE-MONITORING-SYSTEM
TEMPERATURE-MONITORING-SYSTEM
COMPONY: CODETECH IT SOLUTIONS

NAME: PRATIK BHASKAR VARPE

INTERN ID: CT12NUW

DOMAIN: EMBEDDED SYSTEMS

DURATION: 8 WEEKS

START DATE: 20TH JANUARY 2025

MENTOR: NEELA SANTOSH

#DESCRIPTION

Introduction:

Monitoring temperature is a vital task in many applications, such as in households, industrial settings, and even in weather stations. A simple temperature monitoring system can be built using a microcontroller (such as an Arduino), a temperature sensor, and an LCD display. The project aims to measure the ambient temperature and display it on an LCD screen, providing real-time monitoring and feedback to the user. This can be a useful tool for applications that require temperature control or alerting systems.

Components Required:

Arduino Uno (or any compatible microcontroller) LM35 Temperature Sensor (or any analog temperature sensor) 16x2 LCD Display (with I2C interface for easier connection) Breadboard and jumper wires Resistors (if required, typically for sensors or LED indicators) Power Source (USB cable for Arduino or battery pack) Optional: Buzzer or LED for temperature threshold alarms Working Principle:

The main principle behind this project is to read the analog output from the temperature sensor (LM35) and convert it into a digital value that can be processed by the microcontroller (Arduino). The Arduino will then calculate the temperature in Celsius and display it on the LCD screen. The LCD, which is connected via I2C for easy communication, will show the temperature in real time.

The LM35 temperature sensor provides a linear voltage output that is proportional to the temperature in Celsius. It outputs 10mV per degree Celsius, meaning for every 1°C rise in temperature, the output voltage increases by 10mV. The Arduino reads this voltage using its analog input pin, converts it to a temperature value, and then sends the result to the LCD.

Steps for Implementation:

Setting Up the Circuit:

Begin by connecting the LM35 temperature sensor to the Arduino. The sensor has three pins: VCC (connect to 5V on the Arduino) GND (connect to ground) OUT (analog output pin, connected to one of the Arduino's analog input pins, like A0) Connect the 16x2 LCD display to the Arduino. Since using an I2C module simplifies the wiring, connect the LCD as follows: VCC (to 5V on Arduino) GND (to ground on Arduino) SDA (to A4 pin on Arduino) SCL (to A5 pin on Arduino) Programming the Arduino:

Open the Arduino IDE on your computer and write the code to read the temperature sensor’s output and display it on the LCD screen.

In the code, use the analogRead() function to obtain the sensor's voltage reading. The analogRead() function converts the voltage into a value between 0 and 1023, based on the 10-bit ADC of the Arduino.

Convert this reading to a temperature value using the sensor's calibration factor (10mV per °C). For an LM35, you can use the formula:

Temperature in Celsius analogRead value 1024 × 5 × 100 Temperature in Celsius= 1024 analogRead value​×5×100 Once the temperature is calculated, use the lcd.print() function to display the value on the LCD.

Optionally, set up a threshold for the temperature. If the temperature exceeds a certain value, trigger a buzzer or an LED to alert the user.

Upload the code to the Arduino and observe the results.

Code:

#include "LiquidCrystal.h" LiquidCrystal lcd(8,7,6,5,4,3); int sensorPin = 0;

void setup() { Serial.begin(9600); lcd.begin(16,2); }

void loop() {

int reading = analogRead(sensorPin);

// measure the 5v with a meter for an accurate value //In particular if your Arduino is USB powered

float voltage = reading * 4.68; voltage /= 1024.0;

// now print out the temperature

float temperatureC = (voltage - 0.5) * 100; Serial.print(temperatureC); Serial.println(" degrees C");

lcd.setCursor(0,0); lcd.print("Temperature Value "); lcd.setCursor(0,1); lcd.print(" degrees C"); lcd.setCursor(11,1); lcd.print(temperatureC);

delay(100); } // Convert the Explanation of Code:

The LiquidCrystal_I2C library is used to communicate with the LCD display over the I2C bus. The address 0x27 is the default address for many I2C LCDs. In the setup() function, we initialize the LCD and display the title "Temperature:". In the loop(), the analog value from the LM35 is read, converted to a temperature in Celsius, and displayed on the second line of the LCD. The loop runs every second, updating the displayed temperature. Applications:

Home Automation: The system can be used to monitor indoor temperatures and control heating or cooling systems. Industrial Applications: Monitoring temperatures of machines, ovens, or any critical systems requiring temperature control. Weather Stations: Simple weather station setup where the temperature data is displayed locally. Smart Agriculture: Use in greenhouses to keep track of environmental conditions, ensuring optimal growth conditions for plants. Conclusion:

This project serves as a practical, hands-on introduction to working with microcontrollers, sensors, and displays. By building this temperature monitoring system, you learn how to interface sensors with an Arduino, display real-time data on an LCD, and perform basic data conversion for practical use. The system can be extended in the future to include features like temperature alerts, wireless communication for remote monitoring, or even control mechanisms based on temperature thresholds.
