# Computer Hardware Lab

A repeatable hardware lab built around a real Dell Latitude 3340. Each session simulates a physical support ticket you would receive working 1st or 2nd line IT support. Every task is documented, logged, and pushed to GitHub — treating physical hardware work with the same rigour as software workflows.

Built and maintained by Jesse Adejoh as part of ongoing IT support skill development.

-----

## Hardware Specs

|Component  |Details                                         |
|-----------|------------------------------------------------|
|Device     |Dell Latitude 3340                              |
|Processor  |Intel Core i3-4005U @ 1.70GHz                   |
|RAM        |4GB DDR3L — single stick in slot B, slot A empty|
|Storage    |2.5-inch SATA drive                             |
|OS         |Windows 10 Pro — Version 22H2                   |
|Hostname   |DESKTOP-LQ8TJI2                                 |
|Service Tag|2HP9812                                         |

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
- Remove the battery before touching any internal component
- Fasten your anti-static wrist strap and clip it to a bare metal surface before opening the chassis
- Never force a component — if it does not move freely, check for a hidden screw or clip
- Keep screws organised — use a small container so nothing gets lost
- Photograph the inside before touching anything — gives you a reference point and evidence of the initial state
- When disconnecting cables, pull from the connector — never pull the cable itself
- After working inside, replace all panels and screws before attempting to power on

-----

## Repository Structure

```
Computer-Hardware-Lab/
├── logs/
│   └── hardware_log.csv        # One row per completed session
├── evidence/
│   └── session_XX/             # Photos saved per session
├── README.md
└── LOGGING.md
```

-----

## Logging

Every completed session gets one row added manually to logs/hardware_log.csv.

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
1. Remove the battery
1. Remove the base cover:
- Use a Phillips #0 to remove all base panel screws
- Use a plastic pry tool starting from the recesses near the hinges — work around the perimeter to release the clips
1. Take a photograph of the full interior before touching anything — this is your evidence of the initial state
1. Examine each component carefully before recording anything:
- Motherboard — the main circuit board the entire laptop is built around. Every component connects to or sits on it
- RAM slot — note how many slots are present, which are populated, and what type of RAM is installed. Check the label on the stick itself
- Storage bay — locate the 2.5-inch SATA bay and note whether a drive is present. Check the SATA connector and cable condition
- CMOS battery — small round coin cell on the motherboard. Note its location and how it is connected
- Cooling fan and heatsink — locate the fan and the copper heatsink. Note the condition of the fan blades and whether dust is visible
- Wi-Fi card — small rectangular card with two antenna cables. Note the colour of each cable and which connector it sits on
1. Take a photograph of each component individually
1. Cross-reference what you see against the Hardware Specs table above — note any differences
1. Reassemble — seat the base cover clips first, then replace all screws. Battery goes in last
1. Log the session in logs/hardware_log.csv
1. Push to GitHub

**What you are learning:** How to approach an unfamiliar device methodically before doing any work. In a real MSP environment, documenting hardware before touching it protects you if something is already broken and gives the client an accurate record of their equipment.

**Skills:** Hardware identification, component documentation, safe disassembly and reassembly, evidence photography

-----

### Session 2: RAM Inspection and Re-seating

**Scenario:** A user reports their laptop is running slowly and freezing intermittently. First physical check is RAM — inspect the stick, remove it, examine the contacts, and re-seat it.

**Workflow:**

1. Power off, remove battery, unplug charger
1. Remove the base cover
1. Before touching the RAM — look at how it sits in the slot and note the angle it is installed at. This is what correctly seated RAM looks like
1. Take a photograph of the RAM in place before removing it
1. Release the side clips — press both clips outward simultaneously and the stick will pop up at an angle
1. Remove the stick fully — hold by the edges only, never touch the gold contacts along the bottom edge
1. Examine the gold contacts closely — clean contacts should be bright and uniform. Note any discolouration, debris, or damage
1. Re-seat the stick — align it at the correct angle and press firmly until both clips click into place
1. Take a photograph of the RAM re-seated
1. Reassemble
1. Log the session — note which slot was populated, contact condition, and any findings
1. Push to GitHub

**What you are learning:** RAM is one of the first physical components checked when a system freezes or crashes. Understanding what correctly seated RAM looks like and how to inspect the contacts is a fundamental diagnostic skill.

**Skills:** RAM handling, electrostatic discharge awareness, contact inspection, physical fault diagnosis

-----

### Session 3: Storage Drive Inspection

**Scenario:** A user reports the laptop is slow. Inspect the 2.5-inch SATA storage drive — confirm it is correctly connected, check the cable and connector, and document the condition.

**Workflow:**

1. Power off, remove battery, unplug charger
1. Remove the base cover
1. Locate the 2.5-inch SATA drive sitting in its metal caddy screwed to the chassis
1. Take a photograph of the drive in place before removing anything
1. Examine the SATA ribbon cable connecting the drive to the motherboard — look for fraying, kinking, or a loose connection at either end
1. Unscrew the drive caddy from the chassis
1. Carefully slide the caddy away from the SATA interposer port on the motherboard — do not pull by the cable
1. Inspect the SATA connector on both the drive and the motherboard port — look for bent pins, debris, or corrosion
1. Re-seat the drive — slide the caddy back into the interposer port and secure the screws
1. Take a photograph of the drive re-seated
1. Reassemble
1. Log the session — note drive condition, cable condition, connector condition, and any findings
1. Push to GitHub

**What you are learning:** A loose or damaged SATA connection causes slow boot times and file read errors. Physically inspecting and re-seating the drive rules out a connection fault before escalating to a drive replacement.

**Skills:** SATA storage identification, cable and connector inspection, drive handling, physical fault diagnosis

-----

### Session 4: CMOS Battery and BIOS Reset

**Scenario:** A device is showing incorrect date and time after every reboot. You have been asked to perform a CMOS reset to clear the stored settings.

**Workflow:**

1. Power off, remove battery, unplug charger
1. Remove the base cover
1. Locate the CMOS coin-cell battery on the motherboard — small round silver battery, usually CR2032
1. Before removing it — understand what it does. This battery keeps BIOS settings stored when main power is removed. When it dies, the system loses its date, time, and configuration on every reboot
1. Take a photograph of the CMOS battery in place
1. Remove the CMOS battery carefully using a plastic pry tool — do not use a metal screwdriver
1. Wait 60 seconds — this drains residual charge and clears the volatile BIOS memory
1. Re-seat the CMOS battery
1. Reassemble and power on
1. Enter BIOS — press F2 during startup
1. Confirm the date and time have reset to default — set them correctly and save
1. Take a photograph of the BIOS screen showing the reset state
1. Log the session — note what the BIOS showed on entry and what was corrected
1. Push to GitHub

**What you are learning:** CMOS resets clear BIOS passwords, fix clock faults, and restore default hardware settings. It is a standard first step for any BIOS-related fault before escalating further.

**Skills:** CMOS battery handling, BIOS navigation, motherboard components, Dell boot keys

-----

### Session 5: Thermal Inspection and Fan Check

**Scenario:** A user reports the laptop is overheating and shutting down unexpectedly. Inspect the cooling system and document the condition.

**Workflow:**

1. Power off, remove battery, unplug charger
1. Remove the base cover
1. Locate the cooling fan and heatsink — the fan sits over the CPU and the copper heatsink pipes draw heat away from it
1. Take a photograph of the fan and heatsink before touching anything — this is your before evidence
1. Examine the fan blades closely — dust buildup here directly restricts airflow and causes overheating. Note the level of buildup
1. Examine the heatsink fins — note whether the gaps between the fins are clogged
1. Gently rotate one fan blade with a fingertip — it should spin freely. Any grinding or stiffness indicates a bearing fault
1. Use a soft brush to gently sweep dust from the fan blades and heatsink fins
1. Take a photograph of the fan and heatsink after cleaning — this is your after evidence
1. Reassemble
1. Log the session — note dust level before and after, fan condition, and any findings
1. Push to GitHub

**What you are learning:** Dust buildup is one of the most common causes of overheating and unexpected shutdowns. Inspecting and cleaning the cooling system is a standard preventative maintenance task.

**Skills:** Thermal management, fan inspection, preventative maintenance, before and after evidence documentation

-----

### Session 6: Full Rebuild and Fault Simulation

**Scenario:** You receive a laptop that has been partially disassembled by someone else. It will not POST. Your job is to diagnose the fault, fix it, and confirm normal operation.

**Workflow:**

1. Power off, remove battery, unplug charger
1. Remove the base cover
1. Deliberately remove the RAM stick and leave it out
1. Reassemble the laptop fully
1. Attempt to power on — observe exactly what happens. Note any beep codes, LED patterns, or error behaviour
1. Document the symptom exactly — record it as you would on a real support ticket
1. Power off, remove the base cover
1. Examine the empty RAM slot — this is what a missing component fault looks like from the inside
1. Re-seat the RAM stick correctly — press firmly until both clips click
1. Reassemble and attempt to power on — note whether the behaviour changes
1. Log the session — document the fault symptom, diagnosis, fix applied, and outcome
1. Push to GitHub

**What you are learning:** POST failures are the first thing diagnosed when a device will not boot. Simulating a fault, documenting the symptom, and tracing it to a physical cause is the core of hardware fault diagnosis.

**Skills:** Fault simulation, POST behaviour, RAM fault diagnosis, reassembly under fault conditions, ticket documentation

-----

### Session 7: Wi-Fi Card Inspection and Antenna Check

**Scenario:** A user reports intermittent Wi-Fi dropping and slow wireless speeds. The Wi-Fi card and antenna connections need physical inspection.

**Workflow:**

1. Power off, remove battery, unplug charger
1. Remove the base cover
1. Locate the Wi-Fi card — small rectangular card held by one screw, with two thin antenna cables attached
1. Take a photograph of the card and antenna connections before touching anything
1. Examine both antenna cables — note the colour of each and which connector it sits on. Look for fraying, kinking, or cables that appear loose
1. Carefully disconnect both antenna cables by pulling straight up from the connector — never pull by the cable
1. Unscrew the retaining screw and remove the Wi-Fi card
1. Examine the card connectors and card edge for corrosion, debris, or physical damage
1. Re-seat the card, secure the retaining screw, and reconnect both antenna cables — press each firmly until it clicks
1. Take a photograph of the card re-seated with both cables connected
1. Reassemble
1. Log the session — note antenna cable colours, connector condition, and any findings
1. Push to GitHub

**What you are learning:** Loose antenna cables are a frequent cause of poor wireless signal and intermittent drops. Physical inspection rules out a connection fault before replacing the card or moving to a software investigation.

**Skills:** Wi-Fi card handling, antenna cable identification, connector inspection, physical fault diagnosis

-----

### Session 8: Deep Clean and Preventative Maintenance

**Scenario:** The laptop is running hot and the fan is audibly louder than normal. Carry out a full preventative maintenance clean — a standard scheduled task in any MSP environment.

**Workflow:**

1. Power off, remove battery, unplug charger
1. Remove the base cover
1. Take a photograph of the full interior before touching anything — this is your before evidence
1. Work through the interior methodically — examine every visible surface for dust, debris, or anything out of place:
- Fan blades and heatsink fins
- Vents along the edges of the chassis
- All visible cable connections and connectors
1. Use a soft dry brush to sweep dust from the fan blades, heatsink fins, and chassis vents — work carefully and do not dislodge any cables
1. Note anything that looks loose, damaged, or unusual — this is the kind of finding that goes into a client report
1. Take a photograph of the full interior after cleaning — this is your after evidence
1. Reassemble
1. Log the session — note dust level before and after, fan condition, any loose connections found, and overall condition
1. Push to GitHub

**What you are learning:** Preventative maintenance is a scheduled deliverable in MSP contracts. Documenting the before and after state with photographs is standard practice — it protects the technician and gives the client evidence of work completed.

**Skills:** Preventative maintenance, systematic inspection, evidence documentation, MSP maintenance workflow

-----

## Looping the Lab

After Session 8, restart with harder constraints:

|Loop  |Constraint                                                                                    |
|------|----------------------------------------------------------------------------------------------|
|Loop 2|Time each session — complete disassembly, task, and reassembly within 20 minutes              |
|Loop 3|No notes or README during the session — work from memory, verify against the README after     |
|Loop 4|Sessions 2 and 3 in one sitting — treat it as a full hardware audit ticket                    |
|Loop 5|Sessions 7 and 8 back to back — full wireless inspection and deep clean as one maintenance job|

-----

## Skills Covered

**Hardware** — Component identification, motherboard orientation, RAM handling, SATA storage, CMOS battery, cooling systems, Wi-Fi card, antenna cables, connectors

**Diagnostics** — POST behaviour, fault simulation and resolution, physical fault diagnosis, cable and connector inspection

**Safety** — Electrostatic discharge prevention, safe disassembly, battery removal, anti-static wrist strap, component handling

**Maintenance** — Preventative cleaning, thermal management, before and after documentation, MSP maintenance workflow

**Documentation** — Evidence photography, structured logging, GitHub as audit trail

**BIOS** — Navigation, date and time reset, CMOS clear procedure, Dell boot keys (F2 for BIOS, F12 for boot menu)

-----

## Audit Trail

Every session is logged manually to logs/hardware_log.csv immediately after completion. Evidence photos are saved to evidence/session_XX/. See LOGGING.md for the full schema.
