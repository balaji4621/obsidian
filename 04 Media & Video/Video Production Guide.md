================================================================================
  COMPREHENSIVE VIDEO PRODUCTION PLAN & SCRIPT: FROM SCRATCH TO FINAL EXPORT
  PROJECT: GROUND-UP MICROBAROMETER INFRASOUND SENSOR (PS ID 26144 - NTRO)
================================================================================

================================================================================
PART 1: PRE-PRODUCTION (CONCEPT, SCRIPTING & STORYBOARDING)
================================================================================

1.1 CONCEPT & TARGET AUDIENCE
  - Concept: A cinematic, high-impact technical tutorial demonstrating how to build
    a Rs. 1,900 ($23) indigenous microbarometer sensor from first principles.
  - Duration: 3 Minutes (180 Seconds) / 6 Key Chapters.
  - Resolution & Aspect Ratio: 1920x1080 (16:9 60fps for YouTube/Presentation)
    and 1080x1920 (9:16 Shorts/Reels teaser).

1.2 FULL VOICE-OVER SCRIPT (TIMESTAMPED)

[0:00 - 0:30] CHAPTER 1: THE HOOK & PROBLEM STATEMENT
  (SFX: Deep 5 Hz sub-audible rumble + thunder crack sound effect)
  VOICEOVER: "Can you hear a mountain explode 500 kilometers away? When volcanoes
  erupt, rockets launch, or distant explosions occur, they release sub-audible
  infrasound waves below 20 Hertz. Strategic defense agencies like NTRO require
  high-sensitivity infrasound networks. But commercial sensors cost over Rs. 4.5 Lakhs
  each and are ITAR-restricted. Today, we're building a 100% indigenous microbarometer
  from scratch for under Rs. 1,900!"

[0:30 - 1:00] CHAPTER 2: PHASE 1 — MECHANICAL ACOUSTIC CORE
  (SFX: Precise laser-cutting & syringe tap sounds)
  VOICEOVER: "To measure tiny 0.01 Pascal pressure pulses without weather interference,
  we build a 350 mL sealed acoustic chamber. By inserting a 27-Gauge hypodermic needle—
  measuring exactly 0.288 millimeters inner diameter by 30 millimeters length—we create
  a hydraulic resistance that acts as an acoustic high-pass filter at 0.020 Hertz.
  Slow weather changes leak out, while fast infrasound waves flex our sensor diaphragm!"

[1:00 - 1:30] CHAPTER 3: PHASE 2 — ANALOG FRONT-END (AFE) CIRCUITS
  (SFX: Electrical hum turning into clean sine tone)
  VOICEOVER: "Sub-Pascal pressures generate millivolt signals. To amplify them cleanly,
  we solder an INA128 instrumentation amplifier set to 101x gain. To eliminate low-frequency
  1/f flicker noise, we use zero-drift OPA2188 op-amps in a 4th-order Sallen-Key Butterworth
  low-pass filter tuned to 20 Hertz, completely wiping out 50 Hertz power grid noise."

[1:30 - 2:00] CHAPTER 4: PHASE 3 — DIGITIZATION & ESP32 DSP PIPELINE
  (SFX: High-speed digital clock ticks)
  VOICEOVER: "Our 16-bit ADS1115 ADC samples the analog signal at a strict 100 Hertz
  timer loop. An ESP32-S3 microcontroller runs an IIR filter to remove DC baseline drift,
  executes dynamic thermal tracking via Sutherland's law of air viscosity, and runs an
  STA/LTA algorithm that detects transients in under 100 milliseconds."

[2:00 - 2:30] CHAPTER 5: PHASE 4 — LIVE DEMO & VALIDATION TESTS
  (SFX: Balloon pop impulse + loud alarm chime)
  VOICEOVER: "Watch the live telemetry dashboard. To solve wind turbulence noise, our
  4-arm porous hose array cancels wind eddies by over 20 decibels. And when we pop a balloon
  3 meters away—BOOM! The live Python waterfall UI instantly triggers a red alert banner,
  pinpointing the 5 Hertz acoustic signature!"

[2:30 - 3:00] CHAPTER 6: IMPACT, BATTERY LIFE & MAKE-IN-INDIA
  (SFX: Inspiring orchestral crescendo)
  VOICEOVER: "By turning off the display during acquisition, our average power drops below
  45 milliwatts—giving over 180 hours of battery life. We've replaced Rs. 4.5 Lakh imports
  with a Rs. 1,900 Make-in-India solution. We built the ear that hears what humans can't.
  Thank you!"

================================================================================
PART 2: PRODUCTION (FILMING TECHNIQUES, EQUIPMENT & SHOT LIST)
================================================================================

2.1 CAMERA EQUIPMENT & LIGHTING SETUP
  - Main Camera: 4K Mirrorless / Smartphone (1080p 60fps / 4K 30fps).
  - Lenses: Macro lens (for circuit soldering close-ups) + Wide-angle (for bench setup).
  - Lighting: 2x Softbox LED lights (45-degree key light + rim light for hardware).
  - Audio: Wireless Lavalier mic for voiceover + Shotgun mic for balloon pop SFX.

2.2 SHOT LIST & CAMERA MOVEMENT
  - Shot 1 (Macro): Close-up of 27G needle tip being measured with digital caliper.
  - Shot 2 (Overhead 90°): Hands gluing acrylic chamber and sealing cable gland.
  - Shot 3 (Pan): Smooth slider movement across the soldered AFE perfboard.
  - Shot 4 (Medium): Fan blowing on porous hose array vs bare port comparison.
  - Shot 5 (Screen Recording): 60fps capture of Python live PyQtGraph waterfall UI.
  - Shot 6 (Hero Shot): Team holding finished IP65 enclosure with LED indicators.

================================================================================
PART 3: POST-PRODUCTION (EDITING WORKFLOW & EXPORT SPECS)
================================================================================

3.1 EDITING WORKFLOW (DaVinci Resolve / Premiere Pro / CapCut)
  - Step 1: Assembly cut based on voice-over track.
  - Step 2: Add lower-third graphic overlays (Component names & specs).
  - Step 3: Insert animated circuit overlays & signal trace diagrams.
  - Step 4: Color Grading (Teal & Orange contrast, dark technical background).

3.2 SOUND DESIGN & AUDIO MIXING
  - Voiceover: EQ (High-pass @ 80 Hz, boost @ 3 kHz), Compressor (3:1 ratio), De-esser.
  - SFX: Mechanical clicks, electrical hums, balloon pop, alarm chime (-6 dB relative to VO).
  - Music: Ambient cinematic synth track (DIP music to -18 dB during voiceover).

3.3 FINAL EXPORT SETTINGS
  - Format: MP4 (H.264 / AAC)
  - Resolution: 1920 x 1080 (Full HD)
  - Frame Rate: 30 fps (or 60 fps for smooth telemetry plots)
  - Bitrate: 15 - 20 Mbps (VBR 2-Pass)
  - Audio: AAC 320 kbps, 48 kHz Stereo.
================================================================================
