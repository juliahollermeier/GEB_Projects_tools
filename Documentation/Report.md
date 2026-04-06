Paula Martínez i Júlia Hollermeier

# **Lab Session 1: GEB Projects tools**

The aim of this laboratory session was to gain familiarity with the GitHub platform, learn how to set up and use the ESP32 microcontroller, and explore the analysis and implementation of 3D orientation techniques.

### **Hardware and Software Setup**

First, we configured the working environment. We created a GitHub account and a project repository using Visual Studio Code, and we updated the code with our credential information (username and email) in order to synchronize it to our GitHub account.

Then, in `platformIO.ini`, we added the "monitor_speed" option to set the serial monitor baud rate to 115200:
 
 ```ini
[env:esp32dev]
platform = espressif32
board = esp32dev
framework = arduino
monitor_speed = 115200
```

Moreover, we replaced the content of `src/main.cpp` with a LED blinking program to verify that the ESP32 is working correctly:

```cpp
#include <Arduino.h>

const int ledPin = 2; // GPIO2, sovint connectat a un LED integrat

void setup() {
  Serial.begin(115200); // Inicialitza el port sèrie
  pinMode(ledPin, OUTPUT);
}

void loop() {
  digitalWrite(ledPin, HIGH);
  Serial.println("Led switched ON");
  delay(1000);

  digitalWrite(ledPin, LOW);
  Serial.println("Led switched OFF");
  delay(1000);
}
```  
After modifying the code, we uploaded it to the ESP32 by connecting it to the computer via USB and clicking the “Upload” button in PlatformIO. 

Next, we proceeded with the case example *3D orientation in space* using an IMU sensor.

We started by connecting the hardware setup and uploaded the `Endowrist_IMU` program. We then We configured the IP addresses according to our group:

 ```ini
deviceId = "G4_Endo"
```

Next, we ran the `3D_Orientation.rdk` file in roboDK and executed the `Receive_data_RPY_IMU_world.py` script to visualyize the corresponding orientation. We also modified the target device:

 ```ini
TARGET_DEVICE = "G4_Endo""
```

### **First operating performances diagnosis**

At the beginning, we observed that when applying rotations, the object did not behave as expected. This issue ocurred because the axes of the 3D object were not aligned with the ESP32 reference frame, leading to incorrect orientation results. Therefore, a calibration process was required to align both coordinate systems.

Then, to change the 3D object orientation to "surgical_needle", we modified:

 ```ini
object_NAME = "surgical_needle"
```

Once the object is changed we can observe that the orientation is not correct, because the sensor and the model have its own local coordinate system. (FALTA INFO)


### **Conclusions**

<div align="center">
  <img src="./Images/Setup/Captura_plane.png" width="400"/>
  <p><em>Figure 2: Visualization of the 3D orientation of the plane object in RoboDK.</em></p>
</div>

<div align="center">
  <img src="./Images/Setup/Captura_needle.png" width="400"/>
  <p><em>Figure 3: Visualization of the 3D orientation of the surgical_needle object in RoboDK.</em></p>
</div>
