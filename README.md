# Computer Hardware Lab

A repeatable hardware lab built around a real HP Pavilion Notebook. Each session simulates a physical support ticket you would receive working 1st or 2nd line IT support. Every task is documented, logged, and pushed to GitHub — treating physical hardware work with the same rigour as software workflows.

Built and maintained by Jesse Adejoh as part of ongoing IT support skill development.

-----

## Hardware Specs

|Component|Details                         |
|---------|--------------------------------|
|Device   |HP Pavilion Notebook            |
|Processor|Intel Core i3-5157U @ 2.50GHz   |
|RAM      |8GB DDR3                        |
|Storage  |932GB HDD                       |
|Graphics |Intel Iris Graphics 5100 (128MB)|
|OS       |Windows 10 Home — Version 22H2  |
|Hostname |LAPTOP-UR0A2U61                 |

-----

## Equipment

|Item                     |Purpose                                                                                                              |
|-------------------------|---------------------------------------------------------------------------------------------------------------------|
|Precision screwdriver set|Removing base panel and internal components                                                                          |
|Anti-static precautions  |Touch a grounded metal surface before handling components — reduces risk of electrostatic discharge damaging hardware|

-----

## Safety Rules — Read Before Every Session

1. Power off the laptop fully — not sleep or hibernate. Unplug the charger
1. Remove the main battery before touching any internal components
1. Touch a metal surface before handling any component to discharge static
1. Never force a component — if it does not move freely, check for a hidden screw or clip
1. Keep screws organised — use a small container or magnetic mat so nothing gets lost
1. Photograph the inside before touching anything — gives you a reference if something looks wrong later

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

Every completed session gets one row added to `logs/hardware_log.csv`.

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

-----

## Session Plan

-----

### Session 1: Component Identification and Documentation

**Scenario:** A laptop has been handed in with no documentation. Log the hardware spec before any work begins.

**Workflow:**

1. Power off the laptop fully and unplug the charger
1. Remove the battery if accessible from the outside
1. Unscrew the base panel — keep all screws in one place
1. Photograph the inside before touching anything
1. Identify and locate the following:
- RAM slots — note how many slots and how many are populated
- Storage drive — note whether it is HDD or SSD, and the form factor (2.5 inch SATA, M.2, etc.)
- CMOS battery — small round silver battery on the motherboard
- Cooling fan and heatsink
- Wi-Fi card if visible
1. Cross-reference what you see against the Windows System Information (already noted above)
1. Reassemble the laptop
1. Log the session in `logs/hardware_log.csv`
1. Push to GitHub

**Skills:** Hardware identification, documentation, safe disassembly and reassembly

-----

### Session 2: RAM Inspection and Re-seating

**Scenario:** A user reports their PC is running slowly and freezing. First physical check is RAM — inspect, remove, clean contacts, re-seat.

**Workflow:**

1. Power off, unplug, remove battery
1. Open the base panel
1. Locate the RAM sticks — note how many are installed and which slots they occupy
1. Carefully release the side clips on one RAM stick — it will pop up at an angle
1. Remove it fully — hold it by the edges only, never touch the gold contacts
1. Inspect the contacts — note any discolouration or debris
1. Re-seat the stick firmly until both clips click back into place
1. Repeat for the second stick if present
1. Reassemble and power on — confirm the system still shows 8GB in System Information
1. Log the session — note which slots were populated and whether the contacts looked clean
1. Push to GitHub

**Skills:** RAM handling, electrostatic discharge awareness, fault diagnosis process, hardware verification

-----

### Session 3: Storage Drive Inspection

**Scenario:** A user reports the laptop is slow to boot. Inspect the storage drive, confirm the type and connection, and run a health check from Windows.

**Workflow:**

1. Power off, unplug, remove battery
1. Open the base panel
1. Locate the storage drive — photograph it in place before removing
1. Note the form factor and connection type (SATA, M.2)
1. If SATA — unscrew and disconnect the data and power cable. If M.2 — unscrew the retaining screw and slide it out
1. Inspect the connector and drive casing for physical damage
1. Re-seat or reconnect the drive
1. Reassemble and boot into Windows
1. Open Command Prompt and run a drive health check:

```
wmic diskdrive get status
```

1. Open Disk Management — confirm the drive is showing correctly with the right capacity
1. Log the session — note drive type, connection, and health check result
1. Push to GitHub

**Skills:** Storage hardware, SATA vs M.2 identification, Windows disk tools, physical fault diagnosis

-----

### Session 4: CMOS Battery and BIOS Reset

**Scenario:** A device is showing incorrect date and time after every reboot, or a BIOS password needs clearing. Simulate a CMOS reset.

**Workflow:**

1. Power off, unplug, remove battery
1. Open the base panel
1. Locate the CMOS battery — small round silver battery, usually CR2032
1. Note its position and how it is seated before removing
1. Remove the CMOS battery carefully — use a plastic pry tool or fingernail, not a metal screwdriver
1. Wait 60 seconds — this clears the volatile memory on the motherboard
1. Re-seat the CMOS battery
1. Reassemble and power on
1. Enter BIOS — press F10 on HP laptops during startup
1. Confirm the date and time have reset — set them correctly and save
1. Boot into Windows — confirm the system is functioning normally
1. Log the session — note what reset and what the BIOS showed on entry
1. Push to GitHub

**Skills:** BIOS navigation, CMOS reset, motherboard components, HP boot key, hardware fault simulation

-----

### Session 5: Thermal Inspection and Fan Check

**Scenario:** A user reports the laptop is overheating and shutting down. Inspect the cooling system and document the condition.

**Workflow:**

1. Power off, unplug, remove battery
1. Open the base panel
1. Locate the cooling fan and heatsink
1. Photograph the fan and heatsink before touching
1. Inspect for dust buildup — note whether the fan blades are visibly clogged
1. If compressed air is available — blow dust out from the vents (do this outside or away from other equipment)
1. Check the fan spins freely by gently rotating a blade with a fingertip — it should move without resistance
1. Reassemble and power on
1. Open Task Manager — go to Performance > CPU and monitor temperature under load
1. If HWMonitor or Core Temp is available, run it and note the idle temperature
1. Log the session — note dust level, fan condition, and temperature readings
1. Push to GitHub

**Skills:** Thermal management, preventative maintenance, Windows performance tools, hardware inspection

-----

### Session 6: Full Rebuild and Fault Simulation

**Scenario:** Simulate receiving a laptop that has been partially disassembled by someone else. Identify what is missing or incorrect, reassemble correctly, and confirm it POSTs.

**Workflow:**

1. Power off, unplug, remove battery
1. Open the base panel
1. Deliberately remove one RAM stick and leave it out
1. Reassemble the laptop
1. Power on — note what happens. The laptop may beep, fail to post, or show a memory error
1. Document the symptom — this is what a real fault report would look like
1. Power off, open the panel, re-seat the missing RAM stick
1. Reassemble and power on — confirm normal boot
1. In Windows, verify RAM shows correctly in System Information — should show 8GB
1. Log the session — document the fault symptom, diagnosis, and resolution
1. Push to GitHub

**Skills:** Fault diagnosis, POST errors, RAM troubleshooting, reassembly under fault conditions, documentation

-----

## Looping the Lab

After Session 6, restart with harder constraints:

|Loop  |Constraint                                                                                    |
|------|----------------------------------------------------------------------------------------------|
|Loop 2|Time each session — aim to complete disassembly, task, and reassembly within 20 minutes       |
|Loop 3|No notes or README during the session — work from memory, then verify against the README after|
|Loop 4|Combine tasks — Session 2 and 3 in one sitting, treating it as a full hardware audit ticket   |

-----

## Skills Covered

**Hardware** — Component identification, RAM handling, storage drive types, CMOS battery, cooling systems, form factors, connectors

**Diagnostics** — POST error interpretation, Windows disk tools, temperature monitoring, fault simulation and resolution

**Safety** — Electrostatic discharge prevention, safe disassembly, battery removal, component handling

**Documentation** — Evidence photography, structured logging, GitHub as audit trail

**BIOS** — Navigation, date and time reset, CMOS clear procedure, HP boot keys

-----

## Audit Trail

Every session is logged manually to `logs/hardware_log.csv` immediately after completion. Evidence photos are saved to `evidence/session_XX/`. See `LOGGING.md` for the full schema.
