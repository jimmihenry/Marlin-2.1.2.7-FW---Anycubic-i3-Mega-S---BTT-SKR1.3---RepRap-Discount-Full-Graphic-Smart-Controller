Marlin v2.1.2.7 konfiguriert fuer folgende Hardware:

Anycubic i3 Mega (S).
BTT SKR1.3.
RepRapp Discount Full Graphic Smart Controller.
TMC2208 (Stand Alone).

DIE ANYCUBIC-SPEZIFIKATION
----------------------------------------------------------------------------------------
[x] 01. Hotend: PID-Tuning für V5 Original

[x] 02. Bett: PID-Tuning für Ultrabase (SKR 1.3 optimiert)

[x] 03. Extruder: 393 Steps für Titan-Geared-Drive

[x] 04. Beschleunigung: 1200mm/s² (Materialschonend)

[x] 05. Jerk: X5.0 Y2.0 (Gegen Geisterbilder auf Glas)

[x] 06. Dimensionen: 210x210x205 + Offsets (-10/-11)

[x] 07. Kommunikation: 32-Bit Turbo-Puffer (BUF 32 / TX 32)

[x] 08. Display: Full Graphic 12864 (Western Charset)

[x] 09. SD-Karte: LCD-Slot aktiv (Bequemes Laden)

[x] 10. Motherboard: BTT SKR 1.3 (LPC1768)

[x] 11. Endstops: Mechanisch 'false' / Z2 an Z-MAX

[x] 12. 2te Z-Achse: E1-Pin-Fix & G34 Alignment

[x] 13. Vorheizen: PLA (200/65) & ABS (235/85)

[x] 14. Lüfter: Soft-PWM (gegen Pfeifen)

[x] 15. Sicherheit: Emergency Parser (Sofort-Stopp)

[x] 16. Filament: 550mm Unload / 540mm Load (Bowden-Spezial)

[x] 17. Gedächtnis: EEPROM active (M500 / M502)

[x] 18. Schutz: Z-Software-Endstop aktiv (Glas-Schutz)

[x] 19. Audio: Speaker aktiv für G-Code Melodien

[x] 20. Cooling: 120s Auto-Controller-Fan Nachlauf

[x] 21. Treiber-Typ: 5x TMC2208 Standalone (Konfiguration über Hardware-Poti)

[x] 22. Treiber-Schutz: Linear Advance deaktiviert (Verhindert TMC2208-Extruder-Lock)

[x] 23. Daten-Sicherheit: TMC_DEBUG & MONITOR_DRIVER_STATUS inaktiv (Gegen M122-Absturz)

[x] 24. Interface-Akustik: AUDIO_ENABLE_CLICK inaktiv (Volle Performance & stummes Menü)

[x] 25. Dateisystem: FAT32 mit 1024 Byte Clustern (Schont 32-Bit-CPU & 128MB-Karte)

Diese Aenderungen wurden vorgenommen:
--------------------------------------------------------------------------------------------
============================================================================================
STATUS:         ULTIMATIV VERVOLLSTÄNDIGT
BOARD:          BIGTREETECH SKR 1.3 (Hauptprozessor: LPC1768)
VERSION:        Marlin 2.1.2.7 (Stable Release)
============================================================================================

1. DATEI: platformio.ini
--------------------------------------------------------------------------------------------
[x] default_envs = LPC1768
2. DATEI: Configuration.h
--------------------------------------------------------------------------------------------

A. @section serial & baudrate:

   [x] #define SERIAL_PORT -1
   [x] #define SERIAL_PORT_2 0
   [x] #define BAUDRATE 115200

B. @section machine & identity:

   [x] #define MOTHERBOARD BOARD_BTT_SKR_V1_3
   [x] #define CUSTOM_MACHINE_NAME "Analcubic"
   [x] #define STRING_CONFIG_H_AUTHOR "(Jimmi)"

C. @section stepper drivers (Typ-Zuweisung):

   [x] #define X_DRIVER_TYPE  TMC2208_STANDALONE
   [x] #define Y_DRIVER_TYPE  TMC2208_STANDALONE
   [x] #define Z_DRIVER_TYPE  TMC2208_STANDALONE
   [x] #define Z2_DRIVER_TYPE TMC2208_STANDALONE
   [x] #define E0_DRIVER_TYPE TMC2208_STANDALONE

D. @section movement (Mechanik & Jerk):

   [x] #define DEFAULT_AXIS_STEPS_PER_UNIT { 80, 80, 400, 393 }
   [x] #define DEFAULT_MAX_FEEDRATE { 300, 300, 5, 60 }
   [x] #define DEFAULT_MAX_ACCELERATION { 1200, 1000, 60, 10000 }
   [x] #define DEFAULT_ACCELERATION 1200
   [x] #define DEFAULT_RETRACT_ACCELERATION 3000
   [x] #define DEFAULT_TRAVEL_ACCELERATION 1500
   [x] #define DEFAULT_XJERK 5.0
   [x] #define DEFAULT_YJERK 2.0
   [x] #define DEFAULT_ZJERK 0.4
   [x] #define DEFAULT_EJERK 5.0

E. @section geometry & kinematics:

   [x] #define X_BED_SIZE 210
   [x] #define Y_BED_SIZE 210
   [x] #define X_MIN_POS -10
   [x] #define Y_MIN_POS -11
   [x] #define Z_MIN_POS 0
   [x] #define Z_MAX_POS 205
   [x] #define MIN_SOFTWARE_ENDSTOP_Z

F. @section endstops:

   [x] #define USE_ZMAX_PLUG
   [x] #define Z_HOME_DIR -1

G. @section motion:

   [x] #define INVERT_X_DIR true
   [x] #define INVERT_Y_DIR false
   [x] #define INVERT_Z_DIR true
   [x] #define INVERT_E0_DIR true

H. @section bed pid (Ultrabase):

   [x] #define PIDTEMPBED
   [x] #define DEFAULT_BED_KP 251.78
   [x] #define DEFAULT_BED_KI 49.57
   [x] #define DEFAULT_BED_KD 319.73

I. @section hotend pid (V5):

   [x] #define DEFAULT_KP 15.94
   [x] #define DEFAULT_KI 1.17
   [x] #define DEFAULT_KD 54.19

J. @section preheat constants:

   [x] #define PREHEAT_1_TEMP_HOTEND 200
   [x] #define PREHEAT_1_TEMP_BED 65
   [x] #define PREHEAT_1_FAN_SPEED 0
   [x] #define PREHEAT_2_TEMP_HOTEND 235
   [x] #define PREHEAT_2_TEMP_BED 85

K. @section storage & interface (SOUND DEAKTIVIERT FÜR VOLLE PERFORMANCE):

   [x] #define EEPROM_SETTINGS
   [x] #define EEPROM_CHITCHAT
   [x] #define REPRAP_DISCOUNT_FULL_GRAPHIC_SMART_CONTROLLER
   [x] #define SDSUPPORT
   [x] #define SPEAKER                       // Erlaubt M300-Töne am Druckende
   [ ] //#define AUDIO_ENABLE_CLICK            // Stumm im Menü (Performance-Schutz)
   [x] #define DISPLAY_CHARSET_HD44780 WESTERN

L. @section extruder & safety:

   [x] #define EXTRUDE_MAXLENGTH 600
   [x] #define NOZZLE_PARK_FEATURE
   [x] #define NOZZLE_PARK_POINT { 10, 10, 10 }

M. @section fans & filament:

   [x] #define FAN_SOFT_PWM
   [x] #define FILAMENT_RUNOUT_SENSOR
   [x] #define FIL_RUNOUT_STATE LOW


3. DATEI: Configuration_adv.h
--------------------------------------------------------------------------------------------
A. @section serial & advance blocks:

   [x] #define BUFSIZE 32
   [x] #define TX_BUFFER_SIZE 32
   [x] #define RX_BUFFER_SIZE 128
   [x] #define EMERGENCY_PARSER
   [x] #define HOST_ACTION_COMMANDS
   [ ] //#define LIN_ADVANCE                   // Deaktiviert wegen TMC2208 Standalone

B. @section fans (Silent Mod):

   [x] #define USE_CONTROLLER_FAN
   [x] #define CONTROLLER_FAN_PIN 67
   [x] #define CONTROLLERFAN_IDLE_TIME 120
   [x] #define E0_AUTO_FAN_PIN P2_04

C. @section calibrate (Dual-Z):

   [x] #define NUM_Z_STEPPER 2
   [x] #define Z_STEPPER_ALIGN
   [x] #define Z_STEPPER_ALIGN_ITERATIONS 5
   [x] #define Z_MULTI_ENDSTOPS
   [x] #define Z2_USE_ENDSTOP _ZMAX_

D. @section advanced pause:

   [x] #define ADVANCED_PAUSE_FEATURE
   [x] #define PARK_HEAD_ON_PAUSE
   [x] #define FILAMENT_CHANGE_UNLOAD_LENGTH 550
   [x] #define FILAMENT_CHANGE_FAST_LOAD_LENGTH 540
   [x] #define ADVANCED_PAUSE_RESUME_PRIME 2

E. @section tmc standalone overrides (BEREINIGT FÜR REINEN POTI-BETRIEB):

   [ ] //#define MONITOR_DRIVER_STATUS         // Ausgeschaltet für Standalone
   [ ] //#define CHOPPER_TIMING                // Hardware regelt sich selbst
   [ ] //#define TMC_DEBUG                     // Verhindert M122-Verbindungsabsturz

F. @section manuell (SKR 1.3 Pin-Hacks):

   [x] #define SD_CARD_CONNECTION LCD
   [x] #define Z2_STEP_PIN E1_STEP_PIN
   [x] #define Z2_DIR_PIN E1_DIR_PIN
   [x] #define Z2_ENABLE_PIN E1_ENABLE_PIN

4. Build-Rezept & EEPROM-Aktivierung
--------------------------------------------------------------------------------------------
1. [x] VS Code: Mülleimer (Clean) klicken.
2. [x] VS Code: Häkchen (Build) klicken.
3. [x] firmware.bin auf FAT32 SD-Karte kopieren.
4. [x] Karte ins Board -> Drucker EIN -> 20 Sek. warten.
5. [x] Pronterface verbinden -> Befehl M502 eingeben (Werkswerte laden).
6. [x] Pronterface verbinden -> Befehl M500 eingeben (Dauerhaft speichern).

5. Slicer End-G-Code (In Cura / PrusaSlicer eintragen)
--------------------------------------------------------------------------------------------
M104 S0 ; Extruder aus
M140 S0 ; Bett aus
M84     ; Motoren aus

; === Echte Anycubic End-Töne ===
M300 S440 P200
M300 S660 P250
M300 S880 P300

;===========================================================================================
VERWENDE CODE MIT VORSICHT!
============================================================================================
