# STM32 MCSDK documentation list/hub

STMicroelectronics provide for motor control applications using STM32 microcontrollers X-Cube-MCSDK firmware package. The MCSDK encapsulates firmware solutions for sensored/sensorless applications with GUI for generating firmware projects. Unfortunately, the documentation for MCSDK is dispersed at different locations (st.com application notes/STM32 wiki/locally with MCSDK). Purpose of this text is to list all the documentation on one place.

## Basic insight to MCSDK

At the beginning it is useful to divide the documentation according to surrounding topics (as an introduction). 

On STM32 wiki there may be found [introduction article](https://wiki.st.com/stm32mcu/wiki/STM32MotorControl:Introduction_to_Motor_Control_with_STM32) (_Note: for MCSDK V5 and outdated_).

Firstly, MCSDK provides two PC applications:
 - **MC Workbench** used for generating firmware project 
 - **Motor Pilot** used for controlling the firmware over UART for tuning. It also includes **Profiler** component for identifying PMSM parameters (3-shunt only).

Secondly, by firmware components/application scope, applications may be divided by used motor:

- **PMSM/BLDC**

    For PMSM/BLDC control may be used two algorithms:
    - **6-step** -- sensorless/sensored (HALL)
    - **FOC** (field-oriented/vector)

        For FOC there is need to obtain position this may be done 
        - sensored -- HALL/Encoder
        - sensorless (by observer from sensed bEMF)
            - **Luenberger** PLL/CORDIC
            - **HSO** (high sensitivity, STM32G4 only)
                - **ZeST** as **HSO** "extension" for low speed-full torque (by now for selected customers only)
- **ACIM** (example in v6.4.0, no direct support)

## Documentation related to MCSDK

_Note: Certain mentioned documents are related to older MCSDK version that may have changed/added features, or improved GUI look in recent version. Nevertheless there still may be found useful information._ 

Firstly it is good to be aware of [**FAQ** section at wiki](https://wiki.st.com/stm32mcu/wiki/STM32MotorControl:Frequently_Asked_Questions) (_Note: for MCSDK V5_) and [hub](https://wiki.st.com/stm32mcu/wiki/Category:Motor_Control) for articles there.


- **MC workbench** related:
    - [**UM3027**  How to use STM32 motor control SDK v6.0 workbench](https://www.st.com/resource/en/user_manual/um3027-how-to-use-stm32-motor-control-sdk-v60-workbench-stmicroelectronics.pdf) is description of workbench.
    - **STM32 MCSDK – Tools – ST MC Workbench** is description (locally @/Documentation) (similar to **UM3027**, however should be related to the version).
    - [STM32 MC Workbench](https://wiki.st.com/stm32mcu/wiki/STM32MotorControl:STM32_MC_Workbench) is description @wiki (similar to **UM3027**).
    - [**UM2380** STM32 motor control SDK v5.4 tools](https://www.st.com/resource/en/user_manual/um2380-stm32-motor-control-sdk-v54-tools-stmicroelectronics.pdf) (_Note: for MCSDK V5_) (locally @/Documentation)

    For getting started: `TODO new board selector`
    - [Getting started SDK 6.0.0](https://wiki.st.com/stm32mcu/wiki/STM32MotorControl:Getting_started_SDK_6.0.0) @wiki (_Note: for old MCSDK V6_)
    - this short [video](https://www.youtube.com/watch?v=iTnj0DT3lBM) may be used as introduction for the workbench (_Note: for older MCSDK V6_)
    - [**UM2374** Getting started with STM32 motor control SDK v5.0](https://www.st.com/resource/en/user_manual/um2374-getting-started-with-stm32-motor-control-sdk-v50-stmicroelectronics.pdf) (_Note: for MCSDK V5_) (locally @/Documentation)
    - [Getting started](https://wiki.st.com/stm32mcu/wiki/STM32StepByStep:Getting_started_with_Motor_Control) @wiki (_Note: for MCSDK V5_)

    Part of workbench is **Board Designer**
    - [Motor Control Boards Description](https://wiki.st.com/stm32mcu/wiki/STM32MotorControl:Motor_Control_Boards_Description) @wiki
    - Documentation for the board designer may be found locally @/utilities/pc_software/stmcbd/resource/docs/
    - **AN5166** for MCSDK v5 (locally @/Documentation)

- **Pilot** and **Profiler** related: `TODO custom board offset`
    - [article about Pilot](https://wiki.stmicroelectronics.cn/stm32mcu/wiki/STM32MotorControl:STM32_MC_Motor_Pilot_-_Start-up_guide) @wiki 
    - [**UM3016**  How to use STM32 motor control SDK v6.0 profiler](https://www.st.com/resource/en/user_manual/um3016-how-to-use-stm32-motor-control-sdsk-v60-profiler-stmicroelectronics.pdf) Basic guide for the profiler (_Note: For older MCSDK v6 version_)
    - [STM32 MC Motor Profiler](https://wiki.st.com/stm32mcu/wiki/STM32MotorControl:STM32_MC_Motor_Profiler) @wiki (Note: for old MCSDK)
    - in this [video](https://www.youtube.com/watch?v=e6agHbJVbe4) from EW2015 explained profiler operation 
    

    Motor parameters may be acquired also manually, shown in 
    - [guide](https://wiki.st.com/stm32mcu/wiki/STM32MotorControl:How_To_manually_configure_the_motor_parameters) @wiki 
    - [video](https://www.youtube.com/watch?v=XnGHpT96Ri4) by Tomas

### For firmware library details key document is **.chm/.html doxygen** (locally @/Documentation).

- **6-step** related: `TODO clarify what for is each note good/unique`
    - [**UM3259** STM32 motor control SDK - 6-step firmware sensor-less parameter optimization](https://www.st.com/resource/en/user_manual/um3259-stm32-motor-control-sdk--6step-firmware-sensorless-parameter-optimization-stmicroelectronics.pdf)
    - [**UM3042** STM32 motor control SDK - 6-step firmware library](https://www.st.com/resource/en/user_manual/um3042-stm32-motor-control-sdk--6step-firmware-library-stmicroelectronics.pdf)
    - [**UM2916** MCSDK - 6-step firmware examples: insights of the firmware and how to customize it](https://community.st.com/ysqtg83639/attachments/ysqtg83639/mcu-motor-control-forum/946/1/um2916-mcsdk--6step-firmware-examples-insights-of-the-firmware-and-how-to-customize-it-stmicroelectronics.pdf) (_Note: obsolete, replace by **UM3042** (probably); for MCSDK V5_; not available at st.com) 6-step guide, it may be good as an **UM3259** alternative, for understanding the principle.
    - [6-step Firmware Algorithm](https://wiki.st.com/stm32mcu/wiki/STM32MotorControl:6-step_Firmware_Algorithm) @wiki
    - [6-step - Optimization and troubleshooting of sensor-less firmware parameters](https://wiki.st.com/stm32mcu/wiki/STM32MotorControl:6-step_-_Optimization_and_troubleshooting_of_sensor-less_firmware_parameters) @wiki
    - [https://wiki.st.com/stm32mcu/wiki/STM32MotorControl:6-step_Firmware_Examples_User_Manual](https://wiki.st.com/stm32mcu/wiki/STM32MotorControl:6-step_Firmware_Examples_User_Manual) @wiki (_Note: probably outdated_)

- **Position control** (_Note: sensored position needed!_):
    - [**AN5464** Position control of a three-phase permanent magnet motor
 using X‑CUBE‑MCSDK or X‑CUBE‑MCSDK-FUL](https://www.st.com/resource/en/application_note/an5464-position-control-of-a-threephase-permanent-magnet-motor-using-xcubemcsdk-or-xcubemcsdkful-stmicroelectronics.pdf) 
 (_Note: for MCSDK V5_)

- **FOC** and **Luenberger** related:
    - **UM2392** was MCSDK v5 surrounding manual, FOC is described in detail (locally  @/Documentation of MCSDK v5)

    Advanced optional features:
    - [Discontinuous PWM](https://wiki.st.com/stm32mcu/wiki/STM32MotorControl:SDK_discontinuous_PWM) @wiki (_Note: for MCSDK V5_)
    - [Overmodulation](https://wiki.st.com/stm32mcu/wiki/STM32MotorControl:SDK_Overmodulation) @wiki (_Note: for MCSDK V5_)

- **HSO** related:
    - **HSO startup guide** (locally  @/Documentation)

- **ZeST** related (provided for selected customers):

- **ACIM** related:
    - [ACIM article](https://wiki.st.com/stm32mcu/wiki/STM32MotorControl:SDK_AC_induction_motor) @wiki (_Note: for MCSDK V5_)

- **Y-tricks** `TODO clarify what is applied in current version` (_Note: for MCSDK V5_) @wiki
    - [Single Shunt Phase Shift](https://wiki.st.com/stm32mcu/wiki/STM32MotorControl:Single_Shunt_Phase_Shift)
