# Релизы

История релизов Клиппера. Пожалуйста, смотрите раздел [Installation](Installation.md) для получения информации об установке Klipper.

## Klipper 0.10.0

Available on 20210929. Major changes in this release:

* Support for "Multi-MCU Homing". It is now possible for a stepper motor and its endstop to be wired to separate micro-controllers. This simplifies wiring of Z probes on "toolhead boards".
* Klipper now has a [Community Discord Server](https://discord.klipper3d.org) and a [Community Discourse Server](https://community.klipper3d.org).
* The [Klipper website](https://www.klipper3d.org) now uses the "mkdocs" infrastructure. There is also a [Klipper Translations](https://github.com/Klipper3d/klipper-translations) project.
* Automated support for flashing firmware via sdcard on many boards.
* New kinematic support for "Hybrid CoreXY" and "Hybrid CoreXZ" printers.
* Klipper now uses `rotation_distance` to configure stepper motor travel distances.
* The main Klipper host code can now directly communicate with micro-controllers using CAN bus.
* New "motion analysis" system. Klipper's internal motion updates and sensor results can be tracked and logged for analysis.
* Trinamic stepper motor drivers are now continuously monitored for error conditions.
* Support for the rp2040 micro-controller (Raspberry Pi Pico boards).
* The "make menuconfig" system now utilizes kconfiglib.
* Many additional modules added: ds18b20, duplicate_pin_override, filament_motion_sensor, palette2, motion_report, pca9533, pulse_counter, save_variables, sdcard_loop, temperature_host, temperature_mcu
* Several bug fixes and code cleanups.

## Klipper 0.9.0

Доступно с 20201020 года. Основные изменения в этом выпуске:

* Поддержка "Формирования входных данных" - механизма противодействия резонансу принтера. Это может уменьшить или устранить "звон" в отпечатках.
* Новая система "Плавного повышения давления". Это обеспечивает "Повышение давления" без мгновенного изменения скорости. Кроме того, теперь можно настраивать повышение давления с помощью метода "Настроечной башни".
* New "webhooks" API server. This provides a programmable JSON interface to Klipper.
* The LCD display and menu are now configurable using the Jinja2 template language.
* The TMC2208 stepper motor drivers can now be used in "standalone" mode with Klipper.
* Improved BL-Touch v3 support.
* Improved USB identification. Klipper now has its own USB identification code and micro-controllers can now report their unique serial numbers during USB identification.
* New kinematic support for "Rotary Delta" and "CoreXZ" printers.
* Micro-controller improvements: support for stm32f070, support for stm32f207, support for GPIO pins on "Linux MCU", stm32 "HID bootloader" support, Chitu bootloader support, MKS Robin bootloader support.
* Improved handling of Python "garbage collection" events.
* Many additional modules added: adc_scaled, adxl345, bme280, display_status, extruder_stepper, fan_generic, hall_filament_width_sensor, htu21d, homing_heaters, input_shaper, lm75, print_stats, resonance_tester, shaper_calibrate, query_adc, graph_accelerometer, graph_extruder, graph_motion, graph_shaper, graph_temp_sensor, whconsole
* Several bug fixes and code cleanups.

### Klipper 0.9.1

Available on 20201028. Release containing only bug fixes.

## Klipper 0.8.0

Available on 20191021. Major changes in this release:

* New G-Code command template support. G-Code in the config file is now evaluated with the Jinja2 template language.
* Improvements to Trinamic stepper drivers:
   * New support for TMC2209 and TMC5160 drivers.
   * Improved DUMP_TMC, SET_TMC_CURRENT, and INIT_TMC G-Code commands.
   * Improved support for TMC UART handling with an analog mux.
* Improved homing, probing, and bed leveling support:
   * New manual_probe, bed_screws, screws_tilt_adjust, skew_correction, safe_z_home modules added.
   * Enhanced multi-sample probing with median, average, and retry logic.
   * Improved documentation for BL-Touch, probe calibration, endstop calibration, delta calibration, sensorless homing, and endstop phase calibration.
   * Improved homing support on a large Z axis.
* Many Klipper micro-controller improvements:
   * Klipper ported to: SAM3X8C, SAM4S8C, SAMD51, STM32F042, STM32F4
   * New USB CDC driver implementations on SAM3X, SAM4, STM32F4.
   * Enhanced support for flashing Klipper over USB.
   * Software SPI support.
   * Greatly improved temperature filtering on the LPC176x.
   * Early output pin settings can be configured in the micro-controller.
* New website with the Klipper documentation: http://klipper3d.org/
   * Klipper now has a logo.
* Experimental support for polar and "cable winch" kinematics.
* The config file can now include other config files.
* Many additional modules added: board_pins, controller_fan, delayed_gcode, dotstar, filament_switch_sensor, firmware_retraction, gcode_arcs, gcode_button, heater_generic, manual_stepper, mcp4018, mcp4728, neopixel, pause_resume, respond, temperature_sensor tsl1401cl_filament_width_sensor, tuning_tower
* Many additional commands added: RESTORE_GCODE_STATE, SAVE_GCODE_STATE, SET_GCODE_VARIABLE, SET_HEATER_TEMPERATURE, SET_IDLE_TIMEOUT, SET_TEMPERATURE_FAN_TARGET
* Several bug fixes and code cleanups.

## Klipper 0.7.0

Available on 20181220. Major changes in this release:

* Klipper now supports "mesh" bed leveling
* New support for "enhanced" delta calibration (calibrates print x/y dimensions on delta printers)
* Support for run-time configuration of Trinamic stepper motor drivers (tmc2130, tmc2208, tmc2660)
* Improved temperature sensor support: MAX6675, MAX31855, MAX31856, MAX31865, custom thermistors, common pt100 style sensors
* Several new modules: temperature_fan, sx1509, force_move, mcp4451, z_tilt, quad_gantry_level, endstop_phase, bltouch
* Several new commands added: SAVE_CONFIG, SET_PRESSURE_ADVANCE, SET_GCODE_OFFSET, SET_VELOCITY_LIMIT, STEPPER_BUZZ, TURN_OFF_HEATERS, M204, custom g-code macros
* Expanded LCD display support:
   * Support for run-time menus
   * New display icons
   * Support for "uc1701" and "ssd1306" displays
* Additional micro-controller support:
   * Klipper ported to: LPC176x (Smoothieboards), SAM4E8E (Duet2), SAMD21 (Arduino Zero), STM32F103 ("Blue pill" devices), atmega32u4
   * New Generic USB CDC driver implemented on AVR, LPC176x, SAMD21, and STM32F103
   * Performance improvements on ARM processors
* The kinematics code was rewritten to use an "iterative solver"
* New automatic test cases for the Klipper host software
* Many new example config files for common off-the-shelf printers
* Documentation updates for bootloaders, benchmarking, micro-controller porting, config checks, pin mapping, slicer settings, packaging, and more
* Several bug fixes and code cleanups

## Klipper 0.6.0

Available on 20180331. Major changes in this release:

* Enhanced heater and thermistor hardware failure checks
* Support for Z probes
* Initial support for automatic parameter calibration on deltas (via a new delta_calibrate command)
* Initial support for bed tilt compensation (via bed_tilt_calibrate command)
* Initial support for "safe homing" and homing overrides
* Initial support for displaying status on RepRapDiscount style 2004 and 12864 displays
* New multi-extruder improvements:
   * Support for shared heaters
   * Initial support for dual carriages
* Support for configuring multiple steppers per axis (eg, dual Z)
* Support for custom digital and pwm output pins (with a new SET_PIN command)
* Initial support for a "virtual sdcard" that allows printing directly from Klipper (helps on machines too slow to run OctoPrint well)
* Support for setting different arm lengths on each tower of a delta
* Support for G-Code M220/M221 commands (speed factor override / extrude factor override)
* Several documentation updates:
   * Many new example config files for common off-the-shelf printers
   * New multiple MCU config example
   * New bltouch sensor config example
   * New FAQ, config check, and G-Code documents
* Initial support for continuous integration testing on all github commits
* Several bug fixes and code cleanups

## Klipper 0.5.0

Available on 20171025. Major changes in this release:

* Support for printers with multiple extruders.
* Initial support for running on the Beaglebone PRU. Initial support for the Replicape board.
* Initial support for running the micro-controller code in a real-time Linux process.
* Support for multiple micro-controllers. (For example, one could control an extruder with one micro-controller and the rest of the printer with another.) Software clock synchronization is implemented to coordinate actions between micro-controllers.
* Stepper performance improvements (20Mhz AVRs up to 189K steps per second).
* Support for controlling servos and support for defining nozzle cooling fans.
* Several bug fixes and code cleanups

## Klipper 0.4.0

Available on 20170503. Major changes in this release:

* Improved installation on Raspberry Pi machines. Most of the install is now scripted.
* Support for corexy kinematics
* Documentation updates: New Kinematics document, new Pressure Advance tuning guide, new example config files, and more
* Stepper performance improvements (20Mhz AVRs over 175K steps per second, Arduino Due over 460K)
* Support for automatic micro-controller resets. Support for resets via toggling USB power on Raspberry Pi.
* The pressure advance algorithm now works with look-ahead to reduce pressure changes during cornering.
* Support for limiting the top speed of short zigzag moves
* Support for AD595 sensors
* Several bug fixes and code cleanups

## Klipper 0.3.0

Available on 20161223. Major changes in this release:

* Improved documentation
* Support for robots with delta kinematics
* Support for Arduino Due micro-controller (ARM cortex-M3)
* Support for USB based AVR micro-controllers
* Support for "pressure advance" algorithm - it reduces ooze during prints.
* New "stepper phased based endstop" feature - enables higher precision on endstop homing.
* Support for "extended g-code" commands such as "help", "restart", and "status".
* Support for reloading the Klipper config and restarting the host software by issuing a "restart" command from the terminal.
* Stepper performance improvements (20Mhz AVRs up to 158K steps per second).
* Improved error reporting. Most errors now shown via the terminal along with help on how to resolve.
* Several bug fixes and code cleanups

## Klipper 0.2.0

Initial release of Klipper. Available on 20160525. Major features available in the initial release include:

* Basic support for cartesian printers (steppers, extruder, heated bed, cooling fan).
* Support for common g-code commands. Support for interfacing with OctoPrint.
* Acceleration and lookahead handling
* Support for AVR micro-controllers via standard serial ports
