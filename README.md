# CombatBot_BeetleESP32C3_BrushlessMotors_BLE_Android_V.1.1
Rebuild{Robotics} - https://wwww.rebuildrobotics.fi

Designed for 150-450 g combat robots controlled by Android smartphone/tablet via bluetoothLE. Controlling is done with Rebuild{Robotics} Bot Controller Android app.
In this version driving motors are controlled by ESCs or DC motor drivers using PPM signal. Other version is available for DC motor drivers using PWM signal.
Script and controller can be also used to control basic Arduino based bots with servo.

  *****
  FEATURES:
  *****
  - High accuracy tank type steering.
  - Channel mixing between ch1(fwd/bwd) and ch2(left/right) channels.
  - Motor rotation inverting and trim.
  - Support for single servo or brushless motor controlled by ESC as weapon motor.
  - Uses PPM for drivemotor speed control and PPM for weapon/servo control.
  - PPM pulses(brushless ESC/servo) are controlled with ESP32_C3_ISR_Servo library.
  - 1-2S LiPo battery voltage monitoring.
  - Customizable AI slot (ch4, void runAI).
  - Failsafe feature (Stops all signals when disconnected).
  - Onboard led indicates error-, standby-, bluetooth- and weapon statuses as followed:
      - Blink, dim/slow     =   Standby
      - Blink, bright/fast  =   Script weapon parameter error
      - Solid, dim          =   Bluetooth connected
      - Solid, bright       =   Weapon signal active
  - Presets mentioned below are saved into eeprom.
  - Bot name, channel mix, weapon/servo presets, drive motor directions and trim levels can be updated straight from controller.
  
  *****
  HARDWARE:
  *****
  - DFRobot Beetle ESP32-C3, no headers.
  - DFRobot/Gravity: DC Micro Metal Gear Motors w/Drivers, Robson Robotics Red ESC or brushless motors with ESC.
  - 5V BEC to convert battery voltage for boards and servo if needed (Included in Rebuild Robotics - ESP32-C3 CombatBot Expansion Board).
  - Servo for flipper or brushless motor for spinning weapon.
  - 2S 180-450mAh Li-Po battery.
  
  *****
  ARDUINO IDE BOARD MANAGER & LIBRARY VERSIONS:
  *****
  Tested stable versions:
  - Board: esp32 by Espressif Systems 2.0.13 (In version 2.0.14 weapon channels pin (7) writes small pulses but seems to be usable, test later versions with precaution!)
  - Servo/Weapon control: ESP32_C3_ISR_Servo 1.2.0 
  
  *****  
  OUTPUTS:
  *****
  - 2 Servo PPM outputs for motors.
  - 1 Servo PPM output for weapon ESC or servo.
  - If using Bidirectional signal with ESC, it has to be enabled from ESC separately.
  
  *****
  SAFETY:
  *****
  - Combat robotics is fun and educating but dangerous hobby, always think safety first!
  - Script includes failsafe function to prevent up accidents. Function shuts down drive- and weapon motors automaticly when controllers signal is lost. This is same kind of option than good RC receivers have and it's required in combat robotics.
  - Remember to set pins correctly, if they are not set right script and failsafe won't work properly!
  - Accidentally motor spins will happen when ESP is powered or script is uploading! These can be prevented by using our designed ESP32-C3 CombatBot Expansion Board and tested IDE library versions.
  - Configure ESC properly before connecting controller into bot, or it causes serious hazard because bidirectional signal uses different zero position than normal mode!
  - Test new library versions with precaution and only weapon motor attached, not weapon itself!
  - Modify script only if you know what you are doing!
  
  *****  
  COMMUNICATION:
  *****
  - Script uses 2,4GHz Bluetooth Low Energy (BLE) network to collect data from mobile phone controller as string.
  - Can handle incoming bluetooth messages in 20ms intervals.
  - String format ch1:ch2:ch3:ch4\n .
  - ch1 = fwd/bwd speed, ch2 = left/right speed, ch3 = servo angle or weapon speed, ch4 = AI on/off.
  - ch1 and ch2 values are in scale of -100~100, ch3 and ch4 0~100. 0 is stop. Signals are converted to PWM value scale 0~255. Negative numbers are absoluted.
  
  *****
  PRESETS:
  *****
  - Script presets are not necessary to change if using default hardware and presets.
  - Basic presets can be changed from controller or from script below.
  
  *****
  CONTROLLER:
  *****
  - Controller is specially made for controlling combat robots and Arduino based bots.
  - Bot name, channel mix, weapon presets and servo angles can be updated from controller.
  - Android: Rebuild Robotics - Bot Controller (Google play/Github).
  - Iphone: Not available until MIT App invertor is ready for it.
  
This script and controller have been made respecting the regulations of combat robotics and they should be usable all around the world.
Script builder and component manufacturers are not responsiple from possible damages.

Written by Ville Ollila. Examples used are credited in functions.
Bug reports & contacts: support@rebuildrobotics.fi
Licensed under MIT license.
