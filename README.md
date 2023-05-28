# Accelerometer-mouse-using-an-Arduino-Nano-33-BLE-Sense
Control your computer's mouse cursor by tilting the board in various directions
Creating an accelerometer mouse using an Arduino Nano 33 BLE Sense is a fun project. The Arduino Nano 33 BLE Sense board already has a built-in accelerometer, so you can utilize that to detect motion and control your mouse cursor. Here's a step-by-step guide to help you get started:

**Materials Needed:**
1. Arduino Nano 33 BLE Sense board
2. USB cable
3. Computer
4. Jumper wires

**Step 1: Setting up Arduino IDE**
1. Download and install the Arduino IDE from the official Arduino website (https://www.arduino.cc/en/software).
2. Open the Arduino IDE and go to "Tools" > "Board" and select "Arduino Nano 33 BLE" from the list of boards.
3. Connect your Arduino Nano 33 BLE Sense board to your computer using the USB cable.

**Step 2: Install Required Libraries**
1. Go to "Sketch" > "Include Library" > "Manage Libraries" in the Arduino IDE.
2. In the Library Manager, search for "Arduino_LSM9DS1" and install the library. This library will help you interface with the accelerometer on the Arduino Nano 33 BLE Sense board.

**Step 3: Writing the Code**
Copy and paste the following code into the Arduino IDE:

```cpp
#include <Arduino_LSM9DS1.h>
#include <Mouse.h>

void setup() {
  Serial.begin(9600);
  while (!Serial);

  if (!IMU.begin()) {
    Serial.println("Failed to initialize IMU!");
    while (1);
  }

  Mouse.begin();
}

void loop() {
  if (IMU.accelerationAvailable()) {
    IMU.readAcceleration();

    int x = map(IMU.acceleration().x, -9, 9, -10, 10);
    int y = map(IMU.acceleration().y, -9, 9, -10, 10);

    Mouse.move(x, y, 0);
    delay(50);
  }
}
```

**Step 4: Uploading the Code**
1. Verify the code by clicking on the "Verify" button in the Arduino IDE.
2. Once verified, click on the "Upload" button to upload the code to your Arduino Nano 33 BLE Sense board.
3. Wait for the upload process to complete.

**Step 5: Using the Accelerometer Mouse**
1. Disconnect the Arduino Nano 33 BLE Sense board from your computer.
2. Connect it to your computer again.
3. Tilt the board in different directions to control the mouse cursor on your computer.

Congratulations! You have successfully created an accelerometer mouse using an Arduino Nano 33 BLE Sense board. Now, you can control your computer's mouse cursor by tilting the board in various directions. Feel free to customize the code to add additional features or improve functionality to suit your needs.
