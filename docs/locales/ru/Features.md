# Features

Клиппер обладает несколькими привлекательными функциями:

* Высокоточный шаговый механизм. При расчете перемещений принтера Klipper использует процессор приложений (например, недорогой Raspberry Pi). Процессор приложения определяет, когда запускать каждый шаговый двигатель, он сжимает эти события, передает их в микроконтроллер, а затем микроконтроллер выполняет каждое событие в запрошенное время. Каждое событие stepper запланировано с точностью до 25 микросекунд или выше. Программное обеспечение не использует кинематические оценки (такие как алгоритм Брезенхэма "Bresenham") - вместо этого оно вычисляет точное время шага на основе физики ускорения и физики кинематики машины. Более точное шаговое перемещение обеспечивает более тихую и стабильную работу принтера.
* Best in class performance. Klipper is able to achieve high stepping rates on both new and old micro-controllers. Even old 8bit micro-controllers can obtain rates over 175K steps per second. On more recent micro-controllers, several million steps per second are possible. Higher stepper rates enable higher print velocities. The stepper event timing remains precise even at high speeds which improves overall stability.
* Klipper поддерживает принтеры с несколькими микроконтроллерами. Например, один микроконтроллер может использоваться для управления экструдером, в то время как другой управляет нагревателями принтера, а третий управляет остальной частью принтера. Программное обеспечение хоста Klipper реализует синхронизацию тактовых импульсов для учета дрейфа тактовых импульсов между микроконтроллерами. Для включения нескольких микроконтроллеров не требуется специального кода - для этого просто требуется несколько дополнительных строк в конфигурационном файле.
* Настройка с помощью простого конфигурационного файла. Нет необходимости перепрошивать микроконтроллер, чтобы изменить настройки. Вся конфигурация Klipper хранится в стандартном конфигурационном файле, который можно легко редактировать. Это упрощает настройку и обслуживание оборудования.
* Klipper supports "Smooth Pressure Advance" - a mechanism to account for the effects of pressure within an extruder. This reduces extruder "ooze" and improves the quality of print corners. Klipper's implementation does not introduce instantaneous extruder speed changes, which improves overall stability and robustness.
* Klipper supports "Input Shaping" to reduce the impact of vibrations on print quality. This can reduce or eliminate "ringing" (also known as "ghosting", "echoing", or "rippling") in prints. It may also allow one to obtain faster printing speeds while still maintaining high print quality.
* Klipper uses an "iterative solver" to calculate precise step times from simple kinematic equations. This makes porting Klipper to new types of robots easier and it keeps timing precise even with complex kinematics (no "line segmentation" is needed).
* Portable code. Klipper works on ARM, AVR, and PRU based micro-controllers. Existing "reprap" style printers can run Klipper without hardware modification - just add a Raspberry Pi. Klipper's internal code layout makes it easier to support other micro-controller architectures as well.
* Simpler code. Klipper uses a very high level language (Python) for most code. The kinematics algorithms, the G-code parsing, the heating and thermistor algorithms, etc. are all written in Python. This makes it easier to develop new functionality.
* Custom programmable macros. New G-Code commands can be defined in the printer config file (no code changes are necessary). Those commands are programmable - allowing them to produce different actions depending on the state of the printer.
* Builtin API server. In addition to the standard G-Code interface, Klipper supports a rich JSON based application interface. This enables programmers to build external applications with detailed control of the printer.

## Additional features

Klipper supports many standard 3d printer features:

* Works with Octoprint. This allows the printer to be controlled using a regular web-browser. The same Raspberry Pi that runs Klipper can also run Octoprint.
* Standard G-Code support. Common g-code commands that are produced by typical "slicers" (SuperSlicer, Cura, PrusaSlicer, etc.) are supported.
* Support for multiple extruders. Extruders with shared heaters and extruders on independent carriages (IDEX) are also supported.
* Support for cartesian, delta, corexy, corexz, hybrid-corexy, hybrid-corexz, rotary delta, polar, and cable winch style printers.
* Automatic bed leveling support. Klipper can be configured for basic bed tilt detection or full mesh bed leveling. If the bed uses multiple Z steppers then Klipper can also level by independently manipulating the Z steppers. Most Z height probes are supported, including BL-Touch probes and servo activated probes.
* Automatic delta calibration support. The calibration tool can perform basic height calibration as well as an enhanced X and Y dimension calibration. The calibration can be done with a Z height probe or via manual probing.
* Support for common temperature sensors (eg, common thermistors, AD595, AD597, AD849x, PT100, PT1000, MAX6675, MAX31855, MAX31856, MAX31865, BME280, HTU21D, DS18B20, and LM75). Custom thermistors and custom analog temperature sensors can also be configured. One can monitor the internal micro-controller temperature sensor and the internal temperature sensor of a Raspberry Pi.
* Basic thermal heater protection enabled by default.
* Support for standard fans, nozzle fans, and temperature controlled fans. No need to keep fans running when the printer is idle. Fan speed can be monitored on fans that have a tachometer.
* Support for run-time configuration of TMC2130, TMC2208/TMC2224, TMC2209, TMC2660, and TMC5160 stepper motor drivers. There is also support for current control of traditional stepper drivers via AD5206, MCP4451, MCP4728, MCP4018, and PWM pins.
* Support for common LCD displays attached directly to the printer. A default menu is also available. The contents of the display and menu can be fully customized via the config file.
* Constant acceleration and "look-ahead" support. All printer moves will gradually accelerate from standstill to cruising speed and then decelerate back to a standstill. The incoming stream of G-Code movement commands are queued and analyzed - the acceleration between movements in a similar direction will be optimized to reduce print stalls and improve overall print time.
* Klipper implements a "stepper phase endstop" algorithm that can improve the accuracy of typical endstop switches. When properly tuned it can improve a print's first layer bed adhesion.
* Support for filament presence sensors, filament motion sensors, and filament width sensors.
* Support for measuring and recording acceleration using an adxl345 accelerometer.
* Support for limiting the top speed of short "zigzag" moves to reduce printer vibration and noise. See the [kinematics](Kinematics.md) document for more information.
* Sample configuration files are available for many common printers. Check the [config directory](../config/) for a list.

To get started with Klipper, read the [installation](Installation.md) guide.

## Step Benchmarks

Below are the results of stepper performance tests. The numbers shown represent total number of steps per second on the micro-controller.

| Micro-controller | 1 stepper active | 3 steppers active |
| --- | --- | --- |
| 16Mhz AVR | 157K | 99K |
| 20Mhz AVR | 196K | 123K |
| SAMD21 | 686K | 471K |
| STM32F042 | 814K | 578K |
| Beaglebone PRU | 866K | 708K |
| STM32G0B1 | 1103K | 790K |
| STM32F103 | 1180K | 818K |
| SAM3X8E | 1273K | 981K |
| SAM4S8C | 1690K | 1385K |
| LPC1768 | 1923K | 1351K |
| LPC1769 | 2353K | 1622K |
| RP2040 | 2400K | 1636K |
| SAM4E8E | 2500K | 1674K |
| SAMD51 | 3077K | 1885K |
| STM32F407 | 3652K | 2459K |
| STM32F446 | 3913K | 2634K |
| STM32H743 | 9091K | 6061K |

If unsure of the micro-controller on a particular board, find the appropriate [config file](../config/), and look for the micro-controller name in the comments at the top of that file.

Further details on the benchmarks are available in the [Benchmarks document](Benchmarks.md).
