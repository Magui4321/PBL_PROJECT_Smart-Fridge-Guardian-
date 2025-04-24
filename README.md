# PBL_PROJECT_Smart-Fridge-Guardian-
Smart Fridge Guardian 

Project Goal: This project aims to develop a "Smart Fridge Guardian" system using IoT, fog computing, and cloud technologies to solve these problems in a fun and effective way, enhancing the shared refrigerator experience. 
## System Architecture
This system adopts a typical three-layer IoT architecture: 

### Edge Layer (Sensing Layer): 

Hardware: ESP32-CAM development board (integrated WiFi, Bluetooth, camera), reed switch to detect door opening. 
Software: MicroPython or Arduino C++ program. 
### Fog Layer (Fog Computing Layer): 

Hardware: Raspberry Pi (recommended Model 3B+ or 4). 
Software: Python script, MQTT Broker (such as Mosquitto, if using MQTT) or Web Server (such as Flask/Django, if using HTTP). 

Functions: 
Receive data from ESP32-CAM. If the connection to the cloud is temporarily interrupted, it can be buffered and uploaded after recovery (increasing system resilience). 
Upload to the Cloud: Securely send the processed data (events, photos) to AWS IoT Core or API Gateway via MQTT. 

### Cloud Layer (Cloud Computing Layer - AWS): 

Core Services: 
AWS IoT Core (Optional, recommended for MQTT): Provides secure device connection, management, and data communication. 
API Gateway: Provides RESTful API interfaces for Web/App frontends and fog nodes (if using HTTP) to call. 
AWS Lambda: Serverless computing service for processing data. 

Receives event/photo data from IoT Core or API Gateway. 
Stores metadata (event time, photo S3 path, item information, etc.) into DynamoDB. 

Stores photo files in S3. 
Executes expiration check logic (triggered by EventBridge on a schedule). 
Triggers SNS to send notifications.  

## Frontend and Dashboard: 

Web Dashboard: Displays refrigerator contents, event logs, etc. Can be part of the App or a separate page. 

## Technology Stack 

- Hardware: ESP32-CAM, Raspberry Pi 4 Model B, reed switch, jumper wires, USB power supply. 
- Edge Software: MicroPython / Arduino IDE (C++), Paho MQTT Client (if MQTT). 
- Fog Software: Python 3, Paho MQTT / Flask / Django, AWS SDK (boto3). 
- Cloud (AWS): IoT Core, API Gateway, Lambda (Python/Node.js), DynamoDB, S3, SNS, EventBridge. 
- Frontend (Optional): HTML, CSS, JavaScript (with React/Vue/Angular) or Mobile App framework (React Native/Flutter). 
