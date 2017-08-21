# Gas Sous Vide
Arduino + Ethernet Shield + Propane Turkey Fryer = Web Enabled Sous Vide Cooker with Real Time Data.

## The Arduino
The Arduino will run a PID loop which will control a servo to the gas flow valve.  There will be
one or more thermocouples in the bath, and possibly another for ambient temp.  A flame out detector
would probably be a good idea.  How about an igniter, too?

The Arduino will have an Ethernet shield, because I already have one.  You could use a Wi-Fi shield
as well or any other communications link that would work.  We will send commands to the Arduino
following a Restful API which will be defined.  Examples include:

    http://arduino/runs/create?id=105&setpoint=130&Kp=2&Ki=1&Kd=3
	
    http://arduino/runs/105/start
    
	http://arduino/runs/105/edit?setpoint=131?Kd=4

You get the idea.

The Arduino is also going to report parameters back to a controlling web application.  For example,
every 2 seconds, the Arduino will report run time, temperature of all thermocouples, servo position,
and all other pertinent information.  That information is going to be collected by a controlling web
application which will save the data to a database, and provide the user full real time data with
cool graphs and displays.

## The Controller Web App
The controller web application will start out as a Java/Jsp/Servlet web app.  With Restful API
defined, someone could port the app to any other technology, like PHP, etc.  The app will allow the
user to interact with the Arduino, and will display the real time data, probably using JavaScript,
possibly Flot or some other charting library.

## The Project
Since the project is going to start out as Java, I am going to use Maven and Eclipse.
