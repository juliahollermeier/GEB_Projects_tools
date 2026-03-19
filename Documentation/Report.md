Paula Martínez i Júlia Hollermeier

# **Lab Session 1: GEB Projects tools**

The objective of this laboratory session was to become familiar with the setup and use of the ESP32 microcontroller, as well as to analyze and implement 3D orientation techniques. 

### **First operating performances diagnosis**

At the beginning of the session, we observed that when applying rotations, the object did not behave as expected. This issue was caused by the axes not being aligned with the ESP32 reference frame, which led to incorrect orientation results. Therefore, a calibration process was required to properly align the axes and improve the system's performance.

### **Corrections implemented**

After creating a GitHub account and the Project repository in the Visual Studio Code, we updated the code with our credential information (username and email) in order to synchronize it to our GitHub account.
Moreover, in platformIO.ini, we added the "monitor_speed" option to set the serial monitor baud rate to 115200, and replaced the content of src/main.cpp with the following code:

![Captura Neelde](././Images/Setup/Captura_needle.png)
![Captura Neelde](././Images/Setup/Captura_plane.png)
