# Computer Hardware Lab

A repeatable hardware lab built around a real Dell Latitude 3340. Each session simulates a physical support ticket you would receive working 1st or 2nd line IT support. Every task is documented, logged, and pushed to GitHub — treating physical hardware work with the same rigour as software workflows.

Built and maintained by Jesse Adejoh as part of ongoing IT support skill development.

-----

## Hardware Specs

|Component  |Details                                          |
|-----------|-------------------------------------------------|
|Device     |Dell Latitude 3340                               |
|Processor  |Intel Core i3-4005U @ 1.70GHz                    |
|RAM        |4GB DDR3                                         |
|Storage    |M.2 SSD (2230 or 2280 — confirmed on disassembly)|
|OS         |Windows 10 Pro — Version 22H2                    |
|Hostname   |DESKTOP-LQ8TJI2                                  |
|Service Tag|2HP9812                                          |

-----

## Equipment

|Item                   |Purpose                                                    |
|-----------------------|-----------------------------------------------------------|
|Phillips #0 screwdriver|Base panel and internal component screws                   |
|Phillips #1 screwdriver|Larger screws on base panel                                |
|Plastic pry tool       |Opening the base cover without cracking the plastic clips  |
|Anti-static wrist strap|Worn every session before touching any internal component  |
|Soft brush             |Dust removal from fan and heatsink during cleaning sessions|

-----

## Safety Rules — Read Before Every Session

- Power off the laptop fully — not sleep or hibernate. Unplug the charger
- Fasten your anti-static wrist strap and clip it to a bare metal surface before touching anything inside
- Never force a component — if it does not move freely, check for a hidden screw or clip
- Keep screws organised — use a small container so nothing gets lost
- Photograph the inside before touching anything — gives you a reference if something looks wrong later
- When disconnecting cables, pull from the connector — never pull the cable itself
- After working inside, replace all panels and screws before powering on

-----

## Repository Structure

```
Computer-Hardware-Lab/
├── logs/
│   └── hardware_log.csv        # One row per completed session
├── evidence/
│   └── session_XX/             # Photos or notes saved per session
├── README.md
└── LOGGING.md
```

-----

## Logging

Every completed session gets one row added manually to `logs/hardware_log.csv`.

|Column |Description                                                      |
|-------|-----------------------------------------------------------------|
|date   |Date the session was completed                                   |
|session|Session number                                                   |
|task   |Short task name                                                  |
|device |Device worked on                                                 |
|action |What was done                                                    |
|outcome|Pass, Fail, or Observation                                       |
|notes  |Anything worth flagging — unexpected findings, issues encountered|

Manual entry after each session. No scripts needed — this is physical work.

Push to GitHub after every session:

```
git add . && git commit -m "Session X complete — [task name]" && git push
```

-----

## Session Plan

### Session 1: Component Identification and Documentation

**Scenario:** A laptop has been handed in with no documentation. Your job is to identify and record the hardware before any work begins — exactly what a technician would do before opening a ticket or starting a repair.

**Workflow:**

1. Power off the laptop fully and unplug the charger
1. Enter Service Mode — hold the **B** key and press the power button for 3 seconds until the Dell logo appears. Follow the on-screen prompts. This safely cuts power without disconnecting the battery internally
1. Remove the base cover:
- Use a Phillips #0 to remove all base panel screws
- Use a plastic pry tool starting from the recesses near the hinges at the bottom edge — work around the perimeter to release the clips
1. Photograph the inside before touching anything
1. Identify and locate each component — record what you see:
- RAM slot — note whether one or two slots, and how many are populated
- M.2 SSD — note the size (2230 or 2280) and confirm it is seated correctly
- CMOS battery — small round coin cell on the motherboard
- Cooling fan and heatsink
- Wi-Fi card — small rectangular card with two antenna cables (black and white)
1. Cross-reference what you see against the Windows System Information already documented in the Hardware Specs section above
1. Reassemble — seat the base cover clips first, then replace all screws
1. Power on and confirm normal boot
1. Log the session in `logs/hardware_log.csv`
1. Push to GitHub

**Skills:** Hardware identification, documentation, safe disassembly and reassembly, Dell Service Mode

-----

### Session 2: RAM Inspection and Re-seating

**Scenario:** A user reports their laptop is running slowly and freezing intermittently. First physical check is RAM — inspect the stick, remove it, clean the contacts, and re-seat it.

**Workflow:**

1. Power off, enter Service Mode, unplug charger
1. Remove the base cover
1. Locate the RAM stick — note which slot it occupies
1. Release the side clips on the RAM stick — it will pop up at an angle
1. Remove it fully — hold by the edges only, never touch the gold contacts
1. Inspect the contacts — note any discolouration or debris
1. Re-seat the stick firmly at the correct angle until both clips click back into place
1. Reassemble and power on
1. Open System Information — confirm RAM still shows as 4GB
1. Log the session — note which slot was populated and whether the contacts looked clean
1. Push to GitHub

**Why this matters:** Poorly seated RAM causes random freezes, blue screens, and boot failures. Re-seating is one of the first physical checks a technician performs before escalating to a hardware replacement.

**Skills:** RAM handling, electrostatic discharge awareness, fault diagnosis process, hardware verification

-----

### Session 3: Storage Drive Inspection

**Scenario:** A user reports the laptop is slow to boot. Inspect the M.2 SSD — confirm the type, check the connection, and run a health check from Windows.

**Workflow:**

1. Power off, enter Service Mode, unplug charger
1. Remove the base cover
1. Locate the M.2 SSD — photograph it in place before removing
1. Note the drive size — measure or check whether it is 2230 (shorter) or 2280 (longer)
1. Unscrew the retaining screw and carefully slide the drive out at an angle
1. Inspect the connector and drive casing for physical damage or debris
1. Re-seat the drive — slide in at an angle, press down, and replace the retaining screw
1. Reassemble and boot into Windows
1. Open Command Prompt and run a drive health check:
   ```
   wmic diskdrive get status
   ```
1. Open Disk Management — confirm the drive is showing correctly with the right capacity
1. Log the session — note drive size, connection condition, and health check result
1. Push to GitHub

**Why this matters:** A loose or failing M.2 drive causes slow boot times, file corruption, and system instability. Physical inspection rules out connection issues before replacing hardware.

**Skills:** M.2 SSD identification, storage connection types, Windows disk tools, physical fault diagnosis

-----

### Session 4: CMOS Battery and BIOS Reset

**Scenario:** A device is showing incorrect date and time after every reboot. You have been asked to perform a CMOS reset to clear the stored settings.

**Workflow:**

1. Power off, enter Service Mode, unplug charger
1. Remove the base cover
1. Locate the CMOS coin-cell battery on the motherboard — small round silver battery
1. Note its position and orientation before removing
1. Remove the CMOS battery carefully using a plastic pry tool — do not use a metal screwdriver
1. Wait 60 seconds — this clears the volatile memory and resets BIOS settings to default
1. Re-seat the CMOS battery
1. Reassemble and power on
1. Enter BIOS — press **F2** during startup on the Dell Latitude 3340
1. Confirm the date and time have reset — set them correctly and save
1. Boot into Windows and confirm normal operation
1. Log the session — note what reset and what the BIOS showed on entry
1. Push to GitHub

**Why this matters:** CMOS resets are used to clear BIOS passwords, fix incorrect system clock behaviour, and restore default hardware settings. It is a standard first step before escalating a BIOS-related fault.

**Skills:** BIOS navigation, CMOS reset, motherboard components, Dell boot keys, hardware fault simulation

-----

### Session 5: Thermal Inspection and Fan Check

**Scenario:** A user reports the laptop is overheating and shutting down unexpectedly. Inspect the cooling system and document the condition.

**Workflow:**

1. Power off, enter Service Mode, unplug charger
1. Remove the base cover
1. Locate the cooling fan and heatsink
1. Photograph the fan and heatsink before touching — this is your before evidence
1. Inspect for dust buildup — note whether the fan blades are visibly clogged
1. If compressed air is available — hold the fan blade still with a fingertip to stop it spinning, then blow dust out in short bursts. Do this away from other equipment
1. If no compressed air — use a soft brush to gently sweep dust from the fan blades and heatsink fins
1. Check the fan spins freely by gently rotating a blade — it should move without resistance
1. Reassemble and power on
1. Open Task Manager — go to Performance > CPU and monitor under load
1. If HWMonitor or Core Temp is available, note the idle temperature
1. Log the session — note dust level, fan condition, and temperature readings
1. Push to GitHub

**Why this matters:** Thermal throttling and unexpected shutdowns are among the most common hardware complaints. Dust buildup restricts airflow and causes the CPU to overheat. Cleaning the fan is one of the first physical checks in any overheating diagnosis.

**Skills:** Thermal management, preventative maintenance, Windows performance tools, hardware inspection

-----

### Session 6: Full Rebuild and Fault Simulation

**Scenario:** You receive a laptop that has been partially disassembled by someone else. It will not POST. Your job is to diagnose the fault, fix it, and confirm normal operation.

**Workflow:**

1. Power off, enter Service Mode, unplug charger
1. Remove the base cover
1. Deliberately remove the RAM stick and leave it out
1. Reassemble the laptop fully
1. Power on — observe what happens. The Dell Latitude 3340 will emit diagnostic beep codes or display an error if RAM is missing
1. Document the symptom exactly — this is your fault report
1. Power off, remove the base cover, re-seat the RAM stick correctly
1. Reassemble and power on — confirm normal boot
1. Open System Information — confirm RAM shows as 4GB
1. Log the session — document the fault symptom, diagnosis, and resolution
1. Push to GitHub

**Why this matters:** POST errors are the first diagnostic tool a technician uses when a device will not boot. Learning to simulate and interpret them builds the fault-finding process used on every hardware support ticket.

**Skills:** Fault diagnosis, POST error interpretation, RAM troubleshooting, reassembly under fault conditions, documentation

-----

### Session 7: Wi-Fi Card Inspection and Antenna Check

**Scenario:** A user reports intermittent Wi-Fi dropping and slow wireless speeds. The Wi-Fi card and antenna connections need physical inspection.

**Workflow:**

1. Power off, enter Service Mode, unplug charger
1. Remove the base cover
1. Locate the Wi-Fi card — small rectangular card held by one screw, with two thin antenna cables attached (black and white)
1. Photograph the card and antenna connections before touching anything
1. Note the colour of each antenna cable and which connector it is attached to — this is critical when reconnecting
1. Carefully disconnect both antenna cables by pulling straight up from the connector — never pull by the cable itself
1. Unscrew the retaining screw and remove the Wi-Fi card
1. Inspect the card and connectors for physical damage, corrosion, or debris
1. Re-seat the card, secure the retaining screw, and reconnect both antenna cables — press each one down firmly until it clicks
1. Reassemble and power on
1. Open Settings > Network and Internet > Wi-Fi — confirm Wi-Fi is detected and available networks are visible
1. Log the session — note antenna cable colours, connector condition, and whether Wi-Fi was detected after reassembly
1. Push to GitHub

**Why this matters:** Loose antenna cables are a common cause of poor wireless signal and intermittent disconnections. Physical inspection rules out connection issues before replacing the card or escalating to a software fix.

**Skills:** Wireless hardware, antenna cable handling, connector identification, physical fault diagnosis, Wi-Fi verification

-----

### Session 8: Deep Clean and Preventative Maintenance

**Scenario:** The laptop is running hot and the fan is audibly louder than normal. Carry out a full preventative maintenance clean — a standard scheduled task in any MSP environment.

**Workflow:**

1. Power off, enter Service Mode, unplug charger
1. Remove the base cover
1. Photograph the full interior before touching anything — this is your before evidence
1. Locate the fan and heatsink — note the level of dust visually before cleaning
1. If compressed air is available — hold the fan blade still, then blow compressed air through the vents in short bursts away from other equipment
1. If no compressed air — use a soft dry brush to gently sweep dust from the fan blades and heatsink fins. Do not use cloths that generate static
1. Check all visible surfaces for dust buildup — pay attention to the vents along the edges of the chassis
1. Inspect all visible cables and connectors while the panel is open — note anything that looks loose or out of place
1. Photograph the interior again after cleaning — this is your after evidence
1. Reassemble and power on
1. Open Task Manager > Performance > CPU — note the idle temperature and compare against Session 5
1. Log the session — note dust level before and after, fan condition, and temperature reading
1. Push to GitHub

**Why this matters:** Preventative maintenance is a scheduled task in every MSP contract. Documenting before and after evidence is standard practice — it protects the technician and gives the client a record of work completed.

**Skills:** Preventative maintenance, thermal management, safe cleaning procedure, before and after documentation, MSP scheduled maintenance workflow

-----

## Looping the Lab

After Session 8, restart with harder constraints:

|Loop  |Constraint                                                                                            |
|------|------------------------------------------------------------------------------------------------------|
|Loop 2|Time each session — aim to complete disassembly, task, and reassembly within 20 minutes               |
|Loop 3|No notes or README during the session — work from memory, then verify against the README after        |
|Loop 4|Combine tasks — Sessions 2 and 3 in one sitting, treating it as a full hardware audit ticket          |
|Loop 5|Sessions 7 and 8 back to back — full wireless inspection and deep clean as a single maintenance ticket|

-----

## Skills Covered

**Hardware** — Component identification, RAM handling, M.2 SSD types, CMOS battery, cooling systems, Wi-Fi card, antenna cables, form factors, connectors

**Diagnostics** — POST error interpretation, Windows disk tools, temperature monitoring, fault simulation and resolution, Wi-Fi verification

**Safety** — Electrostatic discharge prevention, safe disassembly, Service Mode, component handling, anti-static wrist strap

**Maintenance** — Preventative cleaning, thermal management, before and after documentation, MSP scheduled maintenance workflow

**Documentation** — Evidence photography, structured logging, GitHub as audit trail

**BIOS** — Navigation, date and time reset, CMOS clear procedure, Dell boot keys (F2 for BIOS, F12 for boot menu)

-----

## Audit Trail

Every session is logged manually to `logs/hardware_log.csv` immediately after completion. Evidence photos are saved to `evidence/session_XX/`. See LOGGING.md for the full schema.
