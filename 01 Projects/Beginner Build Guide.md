================================================================================
  MODULE 00: ABSOLUTE BEGINNER — START HERE (STEP BY STEP)
================================================================================

"I don't know electronics, I don't know physics, I just want to build this."
Perfect. This guide assumes ZERO knowledge. We go one baby step at a time.

--------------------------------------------------------------------------------
STEP 1: WHAT ARE WE EVEN BUILDING? (THE "WHAT")
--------------------------------------------------------------------------------
Imagine you have a magic microphone that can hear things humans CANNOT hear.

- Normal microphone: Hears 20 Hz to 20,000 Hz (human voice, music, birds).
- OUR MICROPHONE: Hears 0.01 Hz to 20 Hz (EARTHQUAKES, VOLCANOES, ROCKETS, DISTANT EXPLOSIONS).

These are called INFRASOUND — sound that is TOO LOW for human ears.

WHY DOES NTRO (GOVT) WANT THIS?
- If a volcano erupts in Indonesia, the infrasound travels 1000s of km.
- If a nuclear test happens, infrasound tells you WHERE and HOW BIG.
- If a rocket launches, infrasound tracks it.

COMMERCIAL SENSORS COST: Rs. 4,50,000 (4.5 LAKH).
OUR TARGET COST: Rs. 1,900 (NINETEEN HUNDRED).

--------------------------------------------------------------------------------
STEP 2: THE BIG IDEA — HOW DOES IT WORK? (THE "HOW")
--------------------------------------------------------------------------------
Think of a BALLOON.

1. IF YOU SQUEEZE IT SLOWLY (Weather change over hours):
   Air leaks out slowly through a tiny pinhole. Balloon stays same shape.
   → NO SIGNAL. (We IGNORE weather)

2. IF YOU POP IT OR HIT IT FAST (Infrasound wave):
   Air CANNOT leak out fast enough through the pinhole.
   Balloon skin stretches INSTANTLY.
   → BIG SIGNAL! (We MEASURE this)

OUR SENSOR = A SEALED BOX WITH A TINY PINHOLE (CAPILLARY) + A SENSITIVE SKIN (DIAPHRAGM) INSIDE.

--------------------------------------------------------------------------------
STEP 3: THE 4 MAIN PARTS (THE "ANATOMY")
--------------------------------------------------------------------------------
Think of a human body:

1. NOSE (Wind Filter)        = Porous Hose Array (stops wind noise)
2. THROAT (Capillary Leak)   = 27G Needle (lets weather leak out, keeps infrasound)
3. LUNGS (Chamber)           = 350 mL Sealed Box (holds the reference air)
4. SKIN (Diaphragm/Sensor)   = MPXV7002DP Chip (feels the pressure difference)
5. BRAIN (Electronics)       = INA128 + OPA2188 + ESP32 (amplifies, filters, decides)
6. VOICE (Output)            = Python Graph on Laptop (shows you the wave)

--------------------------------------------------------------------------------
STEP 4: WHAT YOU NEED TO BUY (THE "SHOPPING LIST")
--------------------------------------------------------------------------------
TOTAL: ~Rs. 1,900 (Minimum) to Rs. 3,900 (Full kit)

GO TO: Robu.in / Amazon.in / Local Electronics Shop

| Part | What It Does | Approx Cost |
|------|--------------|-------------|
| MPXV7002DP Sensor | The "Skin" - feels pressure | Rs. 600 |
| ESP32-S3 DevKit | The "Brain" - tiny computer | Rs. 550 |
| ADS1115 Module | The "Ears" - reads sensor precisely | Rs. 300 |
| INA128 Chip | The "Amplifier" - makes tiny signal big | Rs. 220 |
| OPA2188 Chip | The "Filter" - cleans the signal | Rs. 200 |
| 27G Needle (2 pcs) | The "Pinhole" - critical size! | Rs. 50 |
| Acrylic Box 350mL | The "Lungs" - sealed chamber | Rs. 250 |
| Porous Hose + Fittings | The "Nose" - wind filter | Rs. 130 |
| Resistors/Capacitors | Tiny parts for circuit | Rs. 180 |
| Li-Po Battery + Charger | Power | Rs. 400 |
| Perfboard + Wires | To solder circuit | Rs. 150 |
| **TOTAL** | | **~Rs. 3,000** |

MINIMUM TO START (Rs. 1,900): Just MPXV7002DP + ESP32 + ADS1115 + Battery + Needle + Box.

--------------------------------------------------------------------------------
STEP 5: TOOLS YOU NEED
--------------------------------------------------------------------------------
- Soldering Iron (25W) + Solder wire — Rs. 300
- Multimeter (Digital) — Rs. 250 (borrow if possible)
- Wire Stripper / Cutter — Rs. 100
- Screwdriver set — Rs. 100
- Laptop with USB port (for programming ESP32)

--------------------------------------------------------------------------------
STEP 6: YOUR FIRST WEEK — NO SOLDERING YET! (SOFTWARE FIRST)
--------------------------------------------------------------------------------
DAY 1: INSTALL PYTHON & TEST THE "BRAIN" SIMULATION
1. Install Python from python.org (click "Add to PATH")
2. Open Command Prompt (cmd) and type:
   pip install pyserial numpy scipy matplotlib
3. Go to folder: Microbarometer Infrasound Sensor\src
4. Double-click: infrasound_sim.py
5. YOU SHOULD SEE A GRAPH POPPING UP WITH A 5 Hz WAVE!

THIS PROVES YOUR LAPTOP CAN DO THE MATH. The ESP32 will do the same math later.

DAY 2: INSTALL ARDUINO IDE / VS CODE
1. Download Arduino IDE 2.x from arduino.cc
2. Open it → File → Preferences → Additional Boards Manager URLs:
   https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json
3. Tools → Board → Boards Manager → Search "ESP32" → Install "esp32 by Espressif Systems"
3. Tools → Board → ESP32 Arduino → "ESP32S3 Dev Module"

DAY 3: TEST BLINK (HELLO WORLD)
1. Connect ESP32 to laptop via USB
2. Tools → Port → Select your COM port
4. File → Examples → 01.Basics → Blink
5. Click UPLOAD (right arrow button)
6. ONBOARD LED SHOULD BLINK!

IF THIS WORKS → YOUR BRAIN IS ALIVE.

--------------------------------------------------------------------------------
STEP 7: YOUR SECOND WEEK — MECHANICAL BUILD (THE BOX)
--------------------------------------------------------------------------------
FOLLOW: 02_Mechanical_Transducer_Build.txt

DAY 4-5: MAKE THE CHAMBER
1. Get acrylic box (or PVC pipe cap) ~350 mL
2. Drill 3 holes: Inlet (4mm), Capillary (2mm), Cable (8mm)
3. Mount MPXV7002DP sensor INSIDE box
4. Epoxy 27G needle (cut to 30mm) into 2mm hole
6. Seal ALL gaps with silicone/RTV

DAY 6: THE CRITICAL TEST — SYRINGE TEST
1. Connect 50 mL syringe to inlet
2. Push 1 mL air FAST → Voltage jumps
3. Watch voltage SLOWLY come back to zero over 8 SECONDS
   - 8 seconds = PERFECT! (fc = 0.02 Hz)
   - < 2 seconds = Needle too big / hole too large
   - > 30 seconds = Needle clogged / too small

THIS IS YOUR FIRST REAL MILESTONE. IF 8 SECONDS → YOU ARE A GENIUS.

--------------------------------------------------------------------------------
STEP 8: YOUR THIRD WEEK — ELECTRONICS (THE CIRCUIT)
--------------------------------------------------------------------------------
FOLLOW: 03_Basic_Circuit_and_AFE_Build.txt

DAY 7-8: SOLDER THE CIRCUIT ON PERFBOARD
Don't rush. One component at a time. Use the schematic in the file.

1. Solder INA128 first → Check 1.65V on output (Pin 6) with multimeter
2. Solder OPA2188 Vref buffer → Check 1.65V
3. Solder 4th-order Low-Pass Filter (4 resistors, 4 capacitors)
4. Connect sensor → Check clean signal on oscilloscope (or Arduino Serial Plotter)

DAY 9: CONNECT ADC + ESP32
1. ADS1115 → ESP32 (SDA=21, SCL=22, VCC=3.3V, GND=GND)
2. AFE Output → ADS1115 A0 pin
3. Flash src/main.cpp to ESP32
4. Open Serial Monitor at 115200 baud → Should see "DATA,..." scrolling

--------------------------------------------------------------------------------
STEP 9: YOUR FOURTH WEEK — LIVE DEMO & TESTS
--------------------------------------------------------------------------------
FOLLOW: 05_Step_by_Step_Assembly_and_Testing_Playbook.txt

TEST 1: Balloon Pop (3 meters away) → Red Alert on Screen!
TEST 2: Desk Fan on Windscreen → Noise drops 20x!
TEST 3: Speaker Sweep 5Hz→20Hz→50Hz → Filter works!
TEST 4: Battery Life → Runs 7+ days!

--------------------------------------------------------------------------------
STEP 10: THE PITCH (HOW TO EXPLAIN TO JUDGES)
--------------------------------------------------------------------------------
Memorize this 3-minute story:

"Sir, this is a Microbarometer. It hears infrasound — sound below human hearing.
Volcanoes, rockets, explosions make these waves. Commercial sensors cost 4.5 Lakh.
We built ours for 1,900 Rupees. 
Here is the live demo — *pop balloon* — see? Instant detection. 
It runs 180 hours on battery. Make in India. Thank you."

--------------------------------------------------------------------------------
YOUR LEARNING ROADMAP (PRINT THIS)
--------------------------------------------------------------------------------
[ ] Week 1: Python sim works + Arduino Blink works
[ ] Week 2: Chamber built + Syringe test = 8 seconds decay
[ ] Week 3: Circuit soldered + 1.65V baseline clean
[ ] Week 4: ESP32 reads ADC + Python graph shows live wave
[ ] Week 5: Balloon pop triggers RED ALERT on screen
[ ] Week 6: Pitch rehearsed 10x + All 4 tests pass

--------------------------------------------------------------------------------
NEED HELP? 
--------------------------------------------------------------------------------
- Read the files in ORDER: 01 → 02 → 03 → 04 → 05
- Every file has PICTURES in text (ASCII diagrams)
- Every file has EXACT NUMBERS (what to buy, what value, what pin)
- If stuck: Re-read the file. Sleep on it. Try again tomorrow.

YOU CAN DO THIS. ONE STEP AT A TIME.
================================================================================