#### Based on a template by "KuranKaname" below are changes made by him originally. As I understand more of the firmware I will remove the things he changed from this top list.
#### Patton's changes are below in addition to my current setup
## Creality Ender-5 Pro with BTT SKR Mini E3 V3

The configuration was made on a Phaetus Dragon hotend and a BMG clone extruder, running the Leon-Me Gen 5 cooling shroud with dual 5015s.
### Changes:

#### OLD Configuration.h

- Set `SERIAL_PORT` to `2`
- Set `SERIAL_PORT_2` to `-1`
- Enabled `PIDTEMPBED` and set default values
- Set `EXTRUDE_MAXLENGTH` to `600` to allow BMG extruder load/unload
- Enabled `CLASSIC_JERK` and set default values
- Disabled `Z_MIN_PROBE_USES_Z_MIN_ENDSTOP_PIN`
- Enabled `USE_PROBE_FOR_Z_HOMING`
- Set `Z_MIN_PROBE_PIN` to `PC14`
- Set `PROBING_MARGIN` to `8`
- Set `XY_PROBE_FEEDRATE` and `Z_PROBE_FEEDRATE_FAST` to faster values
- Set `MULTIPLE_PROBING` to 2
- Set `INVERT_[XYZE]_DIR` to `true
- Enabled `SOFT_ENDSTOPS_MENU_ITEM`
- Enabled `AUTO_BED_LEVELING_BILINEAR`
- Enabled `RESTORE_LEVELING_AFTER_G28`
- Enabled `PREHEAT_BEFORE_LEVELING` and set default values
- Enabled `G26_MESH_VALIDATION`
- Enabled `EXTRAPOLATE_BEYOND_GRID`
- Enabled `MESH_EDIT_GFX_OVERLAY`, set `MESH_INSET` to `10` and `GRID_MAX_POINTS_X` to `9` (for UBL)
- Enabled `LCD_BED_LEVELING`
- Enabled `Z_SAFE_HOMING`
- Set `HOMING_FEEDRATE_MM_M` to faster values
- Enabled `NOZZLE_PARK_FEATURE`
- Disabled `SPEAKER` to work around fan stuck at 100% issue
- Enabled `FAN_SOFT_PWM` for my dual 5015 setup

#### OLD Configuration_adv.h

- Enabled `USE_CONTROLLER_FAN`
- Enabled `CONTROLLER_FAN_EDITABLE`
- Set `BLTOUCH_DELAY` to `500`
- Enabled `PROBE_OFFSET_WIZARD`
- Enabled `LONG_FILENAME_HOST_SUPPORT`
- Set `SDCARD_CONNECTION` to `ONBOARD`
- Enabled `BABYSTEP_ZPROBE_OFFSET` and `BABYSTEP_ZPROBE_GFX_OVERLAY`
- Enabled `ARC_P_CIRCLES`
- Enabled `ADVANCED_PAUSE_FEATURE`
- Set `FILAMENT_CHANGE_UNLOAD_LENGTH` to `500`
- Enabled `ADVANCED_PAUSE_CONTINUOUS_PURGE`
- Set `ADVANCED_PAUSE_PURGE_LENGTH` to `600`
- Enabled `PARK_HEAD_ON_PAUSE`
- Set all `SLAVE_ADDRESS` to SKR values
- Set `[XY]_STALL_SENSITIVITY` to `50`
- Enabled `IMPROVE_HOMING_RELIABILITY`


### Pattons Changes:
#### My Ender 5 Pro Hardware Configuration
- Screen: CR10 Style (Stock)
- Mainboard: SKR Mini E3 V3.0
- Hotend: Phaetus Dragonfly BMS (500 Degree cap)
- Thermistor: 100k ohm cartridge (350 Degree cap)
- Leveling: BLTouch
- Extruder: MicroSwiss DD carriage and gears
- Bed: Stock w/ smooth PEI plate
- Support struts around frame and on bed
- Linear Rails on Y axis

#### Configuration.h
- Set `CUSTOM_MACHINE_NAME` to `Shamrock`
- Set `MOTHERBOARD` to `BOARD_BTT_SKR_MINI_E3_V3_0`
- Set `X_BED_SIZE` to `220` (Can be expanded to a max of 235 after things are tuned)
- Set `Y_BED_SIZE` to `220` (Can be expanded to a max of 235 after things are tuned)
- Set `GRID_MAX_POINTS_X` to `9`
- Set `HEATER_0_MAXTEMP` to `300`
- Set `BED_MAXTEMP` to `120`
- Set `DEFAULT_Kp`, `DEFAULT_Ki`, and `DEFAULT_Kd` to `13.7`, `0.79`, and `59.28` respectively
- Set `DEFAULT_AXIS_STEPS_PER_UNIT` to `{ 80, 80, 800, 135 }`
- Set `X_BED_SIZE` and `Y_BED_SIZE` to `220` and `220` respectively
- Set `BED_TRAMMING_LEVELING_ORDER` to `LB, RB, RF, LF`
- Set `NOZZLE_TO_PROBE_OFFSET` to `{ -44, -5, -2 }` to match my BLtouch offset (Note that the actual Z offset will need to be tuned slightly after firmware load)
- Set `DEFAULT_LEVELING_FADE_HEIGHT` to `0` from `10`
- Set `[XYZE]_DRIVER_TYPE` to `TMC2209`
- Enabled `BLTOUCH`
- Enabled `LCD_BED_TRAMMING`
- Enabled `INDIVIDUAL_AXIS_HOMING_MENU` and `INDIVIDUAL_AXIS_HOMING_SUBMENU`
- Disabled `PID_EDIT_MENU` and `PID_AUTOTUNE_MENU` to save flash space as this can easily be adjusted using external methods.
- Disabled `MESH_EDIT_MENU`
- Created/Modified settings for PLA, TPU, PETG, and ASA based on my filament brand and experience


#### Configuration_adv.h
- Set `CONTROLLER_FAN_PIN` to `FAN2_PIN` (MOBO and PSU cooling fan)
- Set `E0_AUTO_FAN_PIN` to `FAN1_PIN` (Heatsink Fan)
- Enabled `DIAG_JUMPERS_REMOVED` to suppress SENSORLESS_HOMING warnings
- Disabled `LIN_ADVANCE`
- Disabled `CONTROLLER_FAN_EDITABLE`
- Disabled `PROBE_DEPLOY_STOW_MENU`
- Disabled `SD_MENU_CONFIRM_START`
- Disabled `BROWSE_MEDIA_ON_INSERT`
- REFERENCE: fan 0: Part Cooler fan, fan 1: Heatsink fan , fan 2: MOBO/PSU fan

### Research/ TODO:
- `ENDSTOP_INTERRUPTS_FEATURE`
- `DEFAULT_MAX_FEEDRATE`
- `DEFAULT_MAX_ACCELERATION`
- linear advance
- Jerk Settings
- Probe Settings
- Double check axis invertion settings
- Figure out best bed leveling method
- Figure out if `RESTORE_LEVELING_AFTER_G28` should be used or `ENABLE_LEVELING_AFTER_G28`
- Check G26 settings
- Determine if E5P has a buzzer or speaker by default
- Figure out LED strip additions and control
- Disable all chamber settings until needed
- Figure out heated chamber options if a good all in one enclosure can be established around the printer frame
- Research custom user buttons in adv.h
- Finish clearing/Understanding changes made by the template author