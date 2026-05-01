KI's 4WD GUIDED ROBOT VEHICLE – Phase A Completed 🤖

robot car: **Phase A** (Guided Robot Vehicle with camera and manual commands)


**Phase B - (NOT IMPLEMENTED IN THIS PROJECKT)** (fully Autonomous Robot Vehicle with AI) is the next extreme challenge.


**Important note**  
This project is just a learning experiment. The goal is to learn, share everything, and let others improve or continue if they want.


### What you find in this repository

- **Original notes** ("Appunti originali" – raw thoughts and troubleshooting in Italian - copy paste with any ai for translate)
- **Arduino IDE code** (simple motor control sketch with commands: F, B, L, R, S)
- **Python sudo / startup code** (script to launch WiFi commands + HTTP video streaming from Raspberry Pi
- (to test start from last one [because there is a shorter version it was before try use sensors])
- **3D model files** (Fusion 360 exports – supports, chassis parts; remember: try simpler/stronger motors to avoid issues!)
- **Photos and videos** (all build stages, wiring, tests, final working Phase A)
- **Journey / Updates** (13 days of real work – from waiting for parts, learning Fusion, fixing pins & drivers, to motors finally moving and camera streaming)

Hardware base: Yahboom 4WD Smart Car Kit, Arduino Nano, Raspberry Pi 4, LiPo battery, webcam, L298N-style driver.

Phase A works: forward/back/turn/stop via serial or WiFi, live video feed.  
Sensors still need fixing/calibration – not required for basic guided mode.

Feel free to fork, rebuild, fix the sensors, calibrate turns (reduce power to ~30% for smoother left/right), or jump straight to Phase B autonomy.

All files are shared to save others time and to help beginners learn the messy real process.


FILES LINK : https://mega.nz/folder/HMEV2SpI#3rnfqE3ZJZFp212qDZV7Xw


WORK FLOW : 

Update day 1 - After buy the components : Install Fusion and 
Update day 2 - (continuative work flow build the 3D) 
Update day 3 - Ai seem clueless or confused... I am building the motors and all structure after doing the 3D model.
Update day 4 - Waiting the components
Update day 5 - Doing Support for 3D Stamp in Pla
Update day 6 - Today finally able to build all
Update day 7 - Today i build all
Update day 8 - Cables side 'Power', study on energy Power cables, System cables,
Update day 9 - Today i attach some energy cable, it seem ok
Update day 10 - Today all the electricity work
Update day 11 - Today i try do the second type of connections but motors not working.
Update day 12 - (After use Ide and Settings Raspberry) - I fix the Same Motors, they work ! so is not necessary change them. 
Update day 13 - We end the Projeckt - Today we Charge the lipo, do the final test the Commands without the cable - and test it. 
Add the Sensors 'not sure if the codes need a fix' but is not necessary for our Projecekt - FASE 'A' ENDED

Thanks to Grok for the guidance along the way! 🛠️❤️  

Facebook: [Ki William] : https://www.facebook.com/KiWilliamOfficial/

CHEECK if Curious - ELLIE WILLIAMS - CHAT 3D AI in Real TIME : https://www.facebook.com/KiWilliamOfficial/posts/pfbid02ckwtsggVim1PuFSTqFo1StdRzMUCkrTrozJkCXB8ohim7dyX7WXRgCJNyeGgnmoEl



!!! UPDATE NEW FUNCTIONALITY !!! - HOW APPLY :

Robot Grokkions Update: Phase A Completion and New Feature Enhancements

 I've included explanations on how to apply the new features (hardware modifications) to improve the robot's reliability, efficiency, and integration. These changes focus on unified power control, PWM pin confirmation, and sensor power sourcing – all while ensuring the system remains stable and avoids overloads.The codes for Arduino Nano and Raspberry Pi have been reviewed and slightly refined for clarity and robustness (e.g., minor comments, error handling, and confirmation of pin assignments). Since your current codes are already tested and working for your cable configuration (noting potential polarity differences in motors), I've replaced them with these updated versions. No major logic changes were needed, as the hardware mods don't alter the software control flow – but I've ensured compatibility (e.g., ENA/ENB pins are explicitly set to D3/D5 as per your request, and sensor handling remains on the Pi). Tested and Operational Features (Phase A Complete): Controlled Movement: Forward, Backward, Left, Right
 Manual/Automatic Stop: Sensors active and functioning
 Video Streaming: Smooth on Firefox via WiFi
 Speed Control: 4 adjustable levels
 Camera Zoom: In/Out working
 Web Interface: Intuitive and responsive
 Power System: Y-split functioning correctly   Final Configuration:Raspberry Pi:  Flask server with video streaming  
Sensor control in a separate thread  
Serial communication with Arduino

Arduino Nano:  Precise motor control via L298N  
PWM management for variable speed  
Immediate response to commands

Verified Physical Setup:  Y-Split Power: 12V → Motor Driver + 5V → Raspberry  
Motors connected correctly (OUT1-4)  
HC-SR04 Sensors functioning  
Camera Module 3 with active zoom

New Features Checklist and Application GuideThese enhancements improve the robot by simplifying power management (single switch for everything), optimizing PWM signals for smoother motor control, and distributing power load (sensors powered from Nano to reduce Pi strain). Apply them step-by-step after powering down the robot. Test incrementally to avoid shorts.Unified On/Off System (Single Switch Control)  Description: This creates a single-point power control, turning the entire robot (motors, Pi, Nano, sensors, camera) on/off with one button push. It improves usability by eliminating separate switches and reduces wear on components.  
How to Apply:  Add a red cable (positive wire) from the battery's positive terminal to the on/off button's input.  
From the button's output, run another red cable directly to the motor driver's power input (e.g., the 12V screw terminal on L298N).  
Ensure the black (ground) wire is shared across all components for a common ground.  
The existing Y-split remains: One branch for 12V to driver (now switched), the other for 5V regulator to Pi/Nano (also switched via the button).

Improvement to Robot: Safer startup/shutdown, prevents accidental partial power-ons, and extends battery life by ensuring full system isolation when off. No code changes needed – it's pure hardware. Test: Push the button; everything should power up/down together.

Change ENA and ENB to D3 and D5 (Confirm Assignment)  Description: ENA (right motors PWM) and ENB (left motors PWM) are already defined on D3 and D5 in the code, but this step confirms and optimizes for Arduino Nano's PWM capabilities (D3 and D5 support high-frequency PWM for smoother speed control).  
How to Apply:  Physically check and reconnect: ENA to Nano D3 (right side), ENB to Nano D5 (left side). If swapped, test which provides better balance (e.g., if right motors respond weaker, swap to D5 for ENA).  
Use jumper wires for secure connections; avoid breadboard if possible for reliability.

Improvement to Robot: Better PWM resolution reduces motor jitter at low speeds (e.g., 25%), leading to more precise exploration without stalling. Code already supports this – I've confirmed the defines in the updated Nano code below. Test: Run speed levels 1-4; motors should ramp smoothly without asymmetry.

Sensor Power Sourcing (5V to Nano/Breadboard, Other Pins to Pi)  Description: Power the sensors' VCC (5V) from the Nano or breadboard (sourced from the 5V regulator), while keeping Trig, Echo, and GND connected to the Pi. This balances load: Nano handles stable 5V supply (less strain on Pi's GPIO), Pi handles signal processing.  
How to Apply:  For each HC-SR04 sensor: Connect VCC pin to Nano's 5V pin (or breadboard rail powered by Nano's 5V).  
Keep the other pins: Trig to Pi GPIO (pins 17,23,22), Echo to Pi GPIO (27,24,5), GND to shared ground (connect to Pi GND or common rail).  
Use a breadboard for distribution if needed to avoid direct overload on Nano's 5V pin (max ~200mA total for 3 sensors).

Improvement to Robot: Prevents Pi voltage drops during sensor pings (improves stability during video streaming), reduces noise in signals, and allows independent testing of Nano/sensor subsystem. No code changes – sensors are still controlled via Pi GPIO. Test: Run obstacle check; distances should read accurately without Pi reboots.

Updated Code for Arduino NanoThis replaces your old code. Changes: Added comments for clarity, default speed to 180 (as before), and ensured ENA/ENB on D3/D5. No functional alterations.

NANO/RASP LINK:



Important Note: These codes match your cable polarity and configuration. If motors spin wrong, swap IN1/IN2 or IN3/IN4 wires. Upload, test all features, and enjoy the upgraded robot! If issues arise, share error logs

IF YOU HAVE ANY TROUBLE : FOR APPLY THE UPDATE - COPY ALL THIS CODES AND PASTE ON AI TO REWRITE THE SAME CODES CORRECTLY - APPLY THEN TO YOUR WORK FLOW 'ROBOT
