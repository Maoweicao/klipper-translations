# Обзор

Добро пожаловать в документацию Klipper. Если вы новичок в Klipper, начните с документации о [возможностях](Features.md) и [установке](Installation.md).

## Обзорная информация

- [Функции](Features.md): Общий список возможностей Klipper.
- [ЧАВО](FAQ.md): Часто задаваемые вопросы.
- [Releases](Releases.md): История релизов Klipper.
- [Изменения конфигурации](Config_Changes.md): Недавние изменения программного обеспечения, которые могут потребовать от пользователей обновления файла конфигурации принтера.
- [Связатся](Contact.md): Информация по сообщениям об ошибках и общению с разработчиками Klipper.

## Установка и настройка

- [Установка](Installation.md): Гайд по установке Klipper.
- [Справочник по конфигурации](Config_Reference.md): Описание параметров конфигурации.
   - [Дистанция поворота](Rotation_Distance.md): Расчет параметра дистанции попорота(Rotation_distance).
- [Проверки конфигурации](Config_checks.md): Проверка основных настроек контактов в файле конфигурации.
- [Bed level](Bed_Level.md): Information on "bed leveling" in Klipper.
   - [Delta calibrate](Delta_Calibrate.md): Калибровка дельта-киноматики.
   - [Probe calibrate](Probe_Calibrate.md): Калибровка автоматический Z-зондов.
   - [BL-Touch](BLTouch.md): Конфигурация Z-зондов "BL-Touch".
   - [Manual level](Manual_Level.md): Калибровка крайних точек Z ( и подобные).
   - [Bed Mesh](Bed_Mesh.md): Bed height correction based on XY locations.
   - [Endstop phase](Endstop_Phase.md): Позиционирование концевого упора Z с помощью шарового двигателя.
- [Resonance compensation](Resonance_Compensation.md): Инструмент для уменьшения звона при печати.
   - [Measuring resonances](Measuring_Resonances.md): Information on using adxl345 accelerometer hardware to measure resonance.
- [Pressure advance](Pressure_Advance.md): Calibrate extruder pressure.
- [G-Codes](G-Codes.md): Information on commands supported by Klipper.
- [Command Templates](Command_Templates.md): G-Code macros and conditional evaluation.
   - [Status Reference](Status_Reference.md): Information available to macros (and similar).
- [TMC Drivers](TMC_Drivers.md): Using Trinamic stepper motor drivers with Klipper.
- [Multi-MCU Homing](Multi_MCU_Homing.md): Homing and probing using multiple micro-controllers.
- [Slicers](Slicers.md): Configure "slicer" software for Klipper.
- [Skew correction](Skew_Correction.md): Adjustments for axes not perfectly square.
- [PWM tools](Using_PWM_Tools.md): Guide on how to use PWM controlled tools such as lasers or spindles.
- [Exclude Object](Exclude_Object.md): The guide to the Exclude Objecs implementation.

## Документация для разработчиков

- [Обзор кода](Code_Overview.md): Разработчики должны прочитать это в первую очередь.
- [Кинематика](Kinematics.md): Технические подробности о том, как Klipper реализует движение.
- [Protocol](Protocol.md): Information on the low-level messaging protocol between host and micro-controller.
- [API Server](API_Server.md): Information on Klipper's command and control API.
- [MCU commands](MCU_Commands.md): A description of low-level commands implemented in the micro-controller software.
- [CAN bus protocol](CANBUS_protocol.md): Klipper CAN bus message format.
- [Debugging](Debugging.md): Information on how to test and debug Klipper.
- [Benchmarks](Benchmarks.md): Information on the Klipper benchmark method.
- [Contributing](CONTRIBUTING.md): Information on how to submit improvements to Klipper.
- [Packaging](Packaging.md): Information on building OS packages.

## Device Specific Documents

- [Example configs](Example_Configs.md): Information on adding an example config file to Klipper.
- [SDCard Updates](SDCard_Updates.md): Flash a micro-controller by copying a binary to an sdcard in the micro-controller.
- [Raspberry Pi as Micro-controller](RPi_microcontroller.md): Details for controlling devices wired to the GPIO pins of a Raspberry Pi.
- [Beaglebone](Beaglebone.md): Details for running Klipper on the Beaglebone PRU.
- [Bootloaders](Bootloaders.md): Developer information on micro-controller flashing.
- [CAN bus](CANBUS.md): Information on using CAN bus with Klipper.
- [TSL1401CL filament width sensor](TSL1401CL_Filament_Width_Sensor.md)
- [Hall filament width sensor](Hall_Filament_Width_Sensor.md)
