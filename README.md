# Cardio-Vigilant-Band
The Cardio Vigilant Band monitors heart health by tracking vital signs such as heart rate, blood pressure, and oxygen levels. It's worn on the wrist, providing real-time data and alerts for irregularities. Ideal for continuous cardiovascular monitoring, it helps users manage heart conditions and improve overall heart health.

1. Introduction
The Cardio Vigilant Band is a wearable device designed to monitor heart health by tracking various vital signs. This project aims to develop the software infrastructure for such a device, including data collection, analysis, and alert mechanisms.

2. Components
Hardware: The band itself, equipped with sensors for heart rate, blood pressure, and oxygen levels.
Software: Code to interface with the hardware, process the data, and provide actionable insights to the user.

3. Features
Real-Time Monitoring: Continuously tracks heart rate, blood pressure, and oxygen levels.
Data Analysis: Analyzes trends and identifies irregular patterns.
Alerts and Notifications: Sends alerts to the user and possibly their healthcare provider if abnormalities are detected.
User Interface: A mobile or web application to display data and alerts.

4. Data Flow
Data Collection: Sensors on the band collect vital sign data.
Data Transmission: Data is transmitted to a connected device (e.g., smartphone) via Bluetooth.
Data Processing: The connected device processes the data to analyze trends and detect irregularities.
Data Storage: Data is stored locally on the device and optionally synced to a cloud server.
User Notification: Alerts are sent to the user through the app.

5. Implementation Steps
5.1. Hardware Interface
Use libraries such as pyserial for communication with the band's sensors.
Code to read raw data from sensors.
5.2. Data Processing
Implement algorithms for calculating heart rate, blood pressure, and oxygen levels.
Use statistical methods to detect anomalies.
5.3. User Interface
Develop a mobile app using frameworks like Flutter or React Native.
Display real-time data and historical trends.
Implement alert mechanisms using push notifications.
5.4. Data Storage and Syncing
Store data locally using SQLite or another lightweight database.
Implement optional cloud syncing with services like Firebase.

#sample code
import serial

# Initialize serial connection to the band
ser = serial.Serial('/dev/ttyUSB0', 9600)

def read_sensor_data():
    if ser.in_waiting > 0:
        line = ser.readline().decode('utf-8').rstrip()
        data = line.split(',')
        heart_rate = data[0]
        blood_pressure = data[1]
        oxygen_level = data[2]
        return heart_rate, blood_pressure, oxygen_level

while True:
    heart_rate, blood_pressure, oxygen_level = read_sensor_data()
    print(f"Heart Rate: {heart_rate}, Blood Pressure: {blood_pressure}, Oxygen Level: {oxygen_level}")

#Analyzing 
def analyze_data(heart_rate, blood_pressure, oxygen_level):
    # Simple thresholds for demonstration
    if heart_rate < 60 or heart_rate > 100:
        alert("Abnormal heart rate detected")
    if blood_pressure < 90 or blood_pressure > 140:
        alert("Abnormal blood pressure detected")
    if oxygen_level < 95:
        alert("Low oxygen level detected")

def alert(message):
    print(f"Alert: {message}")
    # Here you can add code to send notifications to the user

