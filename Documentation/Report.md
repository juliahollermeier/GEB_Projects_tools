Paula Martínez i Júlia Hollermeier

# **Lab Session 1: GEB Projects tools**

The aim of this laboratory session was to gain familiarity with the GitHub platform, learn how to set up and use the ESP32 microcontroller, and explore the analysis and implementation of 3D orientation techniques.

### **First operating performances diagnosis**

At the beginning of the session, we observed that when applying rotations, the object did not behave as expected. This issue was caused because the axes were not aligned with the ESP32 reference frame, which led to incorrect orientation results. Therefore, a calibration process was required to properly align the axes and improve the system's performance, rotating the object until the axes mathced the ones seen on the screen.

### **Corrections implemented**

After creating a GitHub account and the Project repository in the Visual Studio Code, we updated the code with our credential information (username and email) in order to synchronize it to our GitHub account.

Then, in `platformIO.ini`, we added the "monitor_speed" option to set the serial monitor baud rate to 115200:
 
 ```ini
[env:esp32dev]
platform = espressif32
board = esp32dev
framework = arduino
monitor_speed = 115200
```

Moreover, we replaced the content of `src/main.cpp` with the following code:

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
For this first example there is no need to add libraries.    
After having modified the code we can upload it to the ESP32, by connecting it to the computer via USB. In PlatformIO we need to click the "Upload" button.    
Once it is finished we may want to modify its name and code. We need to save it changing its name and then open the PlatformIO and select `open project`, we select the copy saved, afterwards select `src/main.cpp` and modify the code.     

Now we proceed with the First Case Example called 3D orientation in space. The sensor used is called IMU.    
We started by connecting properly the Hardware setup. Afterwards we uploaded the `Endowrist_IMU` program using PlatformIO, We changed the IP adress of the Endo-module and PC to the one corresponding to our group in this case `deviceId = "G4_Endo"`.   

Then we run the `3D_Orientation.rdk` file in the roboDK program to visualize the robot arm and the Endowrist tool. After we run the `Receive_data_RPY_IMU_world.py` python program and review the corresponding orientation, on this case we needed to modify again the Endo_module to the one corresponding to our group `TARGET_DEVICE = "G5_Endo"`.


### **Conclusions**

<div align="center">
  <img src="./Images/Setup/Captura_plane.png" width="400"/>
  <p><em>Figure 2: Visualization of the 3D orientation of the plane object in RoboDK.</em></p>
</div>

<div align="center">
  <img src="./Images/Setup/Captura_needle.png" width="400"/>
  <p><em>Figure 3: Visualization of the 3D orientation of the surgical_needle object in RoboDK.</em></p>
</div>
