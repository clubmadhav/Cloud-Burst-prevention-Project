# Cloud-Burst-prevention-Project
A next-generation cloudburst management system that combines AI, IoT, and computer vision to predict cloudbursts in real time. The system uses a 40 kHz ultrasonic cloud-penetration and droplet-dispersion mechanism to reduce localized rainfall intensity while providing automated alerts and evacuation support.

Detailed description of my project with entire setup 
Project Description
Cloudbursts are among the most destructive natural disasters, especially in mountainous regions where they can trigger flash floods, landslides, infrastructure damage, and loss of life within minutes. Existing warning systems primarily focus on forecasting and evacuation, leaving very little scope for exploring new mitigation approaches. This project was conceived to address that gap by combining early prediction, intelligent monitoring, and an innovative research concept into a single disaster-management system.
Over the course of my entire Class 9 academic year, I dedicated more than 100 hours to studying cloudburst formation, weather systems, disaster-management practices, atmospheric behaviour, artificial intelligence, computer vision, IoT, and acoustic technologies. This involved reading scientific literature, understanding meteorological data, learning machine learning techniques, and evaluating different engineering approaches. Rather than simply building another weather station, I wanted to develop a system that could contribute something original.
The proposed prototype integrates IoT sensors, computer vision, and machine learning to continuously monitor environmental conditions such as temperature, humidity, pressure, rainfall, and cloud characteristics. The collected data is analysed in real time to estimate cloudburst risk and automatically generate alerts, activate warning systems, and support emergency response planning.
A key research aspect of this project is the investigation of a 40 kHz ultrasonic cloud-penetration and droplet-dispersion mechanism within a controlled laboratory prototype. An acrylic cloud chamber will be used to study how ultrasonic waves interact with suspended mist under repeatable conditions. The observations from this prototype will help evaluate the feasibility of this approach and provide a foundation for future research.
To make the concept easy to understand, the working model also includes a realistic mountain terrain with villages, roads, rivers, and evacuation routes. During demonstrations, the system will simulate cloudburst conditions, perform AI-based risk analysis, display the decision-making process, and illustrate automated emergency alerts and response.
This project represents months of research, learning, design, and engineering. My goal is not only to build a functional prototype but also to encourage further scientific exploration into smarter and more effective ways of reducing the impact of cloudbursts and protecting vulnerable communities.
<img width="2340" height="1080" alt="IMG_20260705_23174785_gallery" src="https://github.com/user-attachments/assets/84b4f556-79d7-4e09-812d-5f42c24e792b" />
<img width="1536" height="709" alt="IMG_20260705_23174778_gallery" src="https://github.com/user-attachments/assets/20acdb03-0b9a-4e4f-9542-bffa8a5633b6" />
<img width="1402" height="1122" alt="file_0000000094707230a8b9db8dbc8507ec" src="https://github.com/user-attachments/assets/0ea8c64a-e184-4a9e-8a5c-14d7dfef5e92" />

<img width="1536" height="1024" alt="file_0000000018547230a5c638727dcb1d46" src="https://github.com/user-attachments/assets/f7c03671-fa72-4a58-a949-682e366ef457" />
Using an exchange rate of ₹86 = US$1, here's the Bill of Materials in table format.
Component
Qty
Unit Price (₹)
Total (₹)
Unit Price (US$)
Total (US$)
Example Link
ESP32 Dev Board
1
700
700
8.14
8.14
https://robu.in/?s=ESP32⁠�
DHT22 Temperature & Humidity Sensor
1
600
600
6.98
6.98
https://robu.in/?s=DHT22⁠�
BMP280/BME280 Pressure Sensor
1
700
700
8.14
8.14
https://robu.in/?s=BMP280⁠�
Rain Sensor Module
1
500
500
5.81
5.81
https://robu.in/?s=Rain+Sensor⁠�
USB Camera / Raspberry Pi Camera
1
1,300
1,300
15.12
15.12
https://robu.in/?s=USB+Camera⁠�
24 V Ultrasonic Mist Maker
2
1,000
2,000
11.63
23.26
https://robu.in/?s=24V+mist+maker⁠�
Acrylic Cloud Chamber (Custom)
1
1,800
1,800
20.93
20.93
Custom Fabrication
40 kHz, 60 W Ultrasonic Transducer
6
900
5,400
10.47
62.79
https://www.aliexpress.com/wholesale?SearchText=40khz+60w+ultrasonic+transducer⁠�
Buzzer / Electronic Siren
1
300
300
3.49
3.49
https://robu.in/?s=buzzer⁠�
Relay Module
2
250
500
2.91
5.81
https://robu.in/?s=relay+module⁠�
12 V Power Supply
1
700
700
8.14
8.14
https://robu.in/?s=12v+power+supply⁠�
24 V Power Supply
1
1,200
1,200
13.95
13.95
https://robu.in/?s=24v+power+supply⁠�
Wiring, Connectors & Terminal Blocks
—
500
500
5.81
5.81
https://robu.in/⁠�
Switches & Push Buttons
—
300
300
3.49
3.49
https://robu.in/?s=push+button⁠�
Grand Total
Currency
Total
Indian Rupees (₹)
14,500
US Dollars (US$)
168.60



<img width="1536" height="1024" alt="file_000000009ff47208af893341e4e20ab1" src="https://github.com/user-attachments/assets/57053a17-6e98-47b5-8b05-4d12c6aa6e0e" />


code for esp 
// Demo thresholds
const float HUMIDITY_LIMIT = 90.0;     // %
const float PRESSURE_LIMIT = 995.0;    // hPa
const int RAIN_LIMIT = 1800;           // ADC value (calibrate for your sensor)

bool danger = false;

if (humidity >= HUMIDITY_LIMIT) {
    Serial.println("High Humidity!");
    danger = true;
}

if (pressure <= PRESSURE_LIMIT) {
    Serial.println("Low Pressure!");
    danger = true;
}

if (rain <= RAIN_LIMIT) {
    Serial.println("Rain Detected!");
    danger = true;
}

if (danger) {

    // Turn ON Alert
    digitalWrite(RELAY_PIN, HIGH);
    digitalWrite(BUZZER_PIN, HIGH);

    // Turn ON Ultrasonic Driver (Experimental)
    digitalWrite(ULTRASONIC_DRIVER_PIN, HIGH);

    Serial.println("==============================");
    Serial.println("ALERT MODE ACTIVATED");
    Serial.println("Buzzer ON");
    Serial.println("Relay ON");
    Serial.println("Ultrasonic Driver ENABLED");
    Serial.println("==============================");

}
else {

    digitalWrite(RELAY_PIN, LOW);
    digitalWrite(BUZZER_PIN, LOW);
    digitalWrite(ULTRASONIC_DRIVER_PIN, LOW);

}
