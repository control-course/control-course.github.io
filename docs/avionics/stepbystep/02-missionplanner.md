# Mission Planner

Mission Planner is a full-featured ground station application for the ArduPilot open source autopilot project. We will use it to set up the Cube and for initial learning and operation.

!!! info
    Mission Planner requires Windows - I've had some success running it via [Whisky](https://getwhisky.app) on my Mac, but the uni cannot offer support for this approach and I would advise against it for flight (and wind tunnel) operations.

Take a look at Ardupilot's overview page, then install Mission Planner.

* [:material-step-forward:Ardupilot - Mission Planner Overview](https://ardupilot.org/planner/docs/mission-planner-overview.html)
* [:material-step-forward:Ardupilot - Installing Mission Planner](https://ardupilot.org/planner/docs/mission-planner-installation.html)

## Connecting

For this first stage we'll power the Cube from your computer's USB port.

!!! warning "A really important note on power"
    **Do not plug anything else into the Cube if you're just powering from USB**. Your laptop's USB port is limited in the current it can supply, and servos can draw significant current when stalled (more on this in later steps). In short, if you plug stuff in and do the wrong thing you can at best **fry the Cube** (putting your Team, Division, and Company's success at risk), and at worst **fry your laptop** (possibly putting your degree and life at risk - back things up, kids!).

!!! warning "Another important note on connectors"
    The micro-USB connector on the side of the Cube is notoriously fragile. To prevent *expensive* damage, please use the USB socket/buzzer assembly supplied to connect (these are much cheaper to replace).

Connect the USB/buzzer assembly to the carrier board's `USB` port. Follow the Ardupilot instructions, making sure you use that USB socket. When you are asked to select firmware, choose ArduPlane. Connect Mission Planner to the Autopilot and check things work as expected (ignore the parts about telemetry and multiple vehicles).

* [:material-step-forward:Ardupilot - Installing Firmware](https://ardupilot.org/planner/docs/common-loading-firmware-onto-pixhawk.html)
* [:material-step-forward:Ardupilot - Connect Mission Planner to AutoPilot](https://ardupilot.org/planner/docs/common-connect-mission-planner-autopilot.html)

## Parameters

When first connecting to the cube, there are a few parameters that need changing. In Mission Planner, a parameter is a configurable setting that tells the flight controller (like the Cube) how to behave. Parameters control everything from flight modes, sensor settings, failsafes, and PID tuning, to things like which servo does what and how fast a drone should climb or descend.

To access parameters, go to config and then full parameter list. This opens up every single parameters available for you to change. Scroll or search for `NFT_BUZZ_VOLUME` and turn it down so the cube doesn’t scream at you every time you turn it on. Then click `write params` and congratulations you’ve changed the cube settings. 

![Param MP](assets/Param-MP.png)

!!! info "Don’t forget to save your parameters every so often so you don’t lose them."

Uselful Parameters:

| Parameter           | Value     | Meaning                                                      |
|---------------------|-----------|--------------------------------------------------------------|
| `NTF_BUZZ_VOLUME`   | 1–5       | Sets buzzer volume level                                     |
| `ARMING_CHECK`      | 0         | Disables all arming checks                                   |
| `ARMING_REQUIRE`    | 0         | Disables requirement for arming                              |
| `THR_FAILSAFE`      | 2         | Enables throttle failsafe in **land** mode.                  |
| `FLIGHTMODE_CH`     | 5         | RC channel used to switch flight modes (usually RC5).        |
| `FLTMODE1`          | 0         | Flight mode 1 = Stabilize mode.                              |
| `FLTMODE6`          | 10        | Flight mode 6 = Auto mode.                                   |
| `RC6_OPTION`        | 4         | RC6 triggers Arm/Disarm.                                     |
| `RC7_OPTION`        | 31        | RC7 triggers `Mission Start`.                                |
| `RC8_OPTION`        | 208       | RC8 triggers `Relay Toggle` (custom or user-defined action). |
| `TERRAIN_FOLLOW`    | 0         | Terrain following disabled during missions.                  |
| `TERRAIN_ENABLE`    | 0         | Terrain data not used (no elevation mapping).                |
| `SERIAL1_PROTOCOL`  | 2         | MAVLink protocol enabled on SERIAL1.                         |
| `SERIAL1_BAUD`      | 921       | Baud rate set to 921600                                      |

Default Channel Order:

| Function  | Channel | Port  |
|-----------|---------|-------|
| Aileron   | 1       | Main  |
| Elevator  | 2       | Main  |
| Throttle  | 3       | Main  |
| Rudder    | 4       | Main  |

Flap Control:

| Parameter        | Value   | Meaning                                |
|------------------|---------|----------------------------------------|
| `SERVO5_OPTION`  | 0 / 2   | 0 = PyMAVLink control, 2 = RC Control  |
| `SERVO5_MAX`     | CALC    | Maximum PWM output for SERVO5.         |
| `SERVO5_MIN`     | CALC    | Minimum PWM output for SERVO5.         |
| `SERVO5_TRIM`    | CALC    | Neutral (center) PWM value for SERVO5. |

Aileron Control:

| Parameter        | Value | Meaning                                     |
|------------------|--------|--------------------------------------------|
| `SERVO1_OPTION`  | 4      | RC passthrough or assigned aileron output. |
| `SERVO1_MAX`     | CALC   | Maximum PWM signal.                        |
| `SERVO1_MIN`     | CALC   | Minimum PWM signal.                        |
| `SERVO1_TRIM`    | CALC   | Neutral PWM value.                         |

Elevator Control:

| Parameter        | Value    | Meaning                                     |
|------------------|----------|---------------------------------------------|
| `SERVO2_OPTION`  | 0 / 19   | 0 = PyMAVLink control, 19 = RC Control      |
| `SERVO2_MAX`     | CALC     | Maximum PWM signal.                         |
| `SERVO2_MIN`     | CALC     | Minimum PWM signal.                         |
| `SERVO2_TRIM`    | CALC     | Neutral PWM value.                          |

Rudder Control:

| Parameter        | Value  | Meaning                         |
|------------------|--------|---------------------------------|
| `SERVO4_OPTION`  | 21     | Assigned rudder control output. |
| `SERVO4_MAX`     | CALC   | Maximum PWM value.              |
| `SERVO4_MIN`     | CALC   | Minimum PWM value.              |
| `SERVO4_TRIM`    | CALC   | Neutral PWM value.              |


## Servo Actions

`Ctrl F` opens up some a settings menu. Click `toggle servo safety` as seen below to turn off the safety. 

![Toggle safety MP](assets/toggle_safety-MP.png)

In `Actions` there’s the arm button as seen below. This panel also allows you to manually set the flight mode.

![Arm MP](assets/arm-MP.png)

The `Servo/Relay` panel allows you to manually move servos in Mission Planner.

![servo MP](assets/servo-MP.png)

!!! tip "Make sure safety toggle is off or you won't be able to move anything"
    You'll also need to have set up the parameters for the servo you want to move
