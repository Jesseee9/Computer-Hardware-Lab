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
- After working inside, replace all panels and screws before setting the device aside

-----

## Repository Structure

```
Computer-Hardware-Lab/
├── logs/
│   └── hardware_log.tsv        # One row per completed session
├── evidence/
│   └── session_XX/             # Photos saved per session
├── README.md
└── LOGGING.md
```

-----

## Logging

Every completed session gets one row added manually to `logs/hardware_log.tsv`.

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

1. Remove the battery and unplug the charger
1. Remove the base cover:
- Use a Phillips #0 to remove all base panel screws
- Use a plastic pry tool starting from the recesses near the hinges — work around the perimeter to release the clips
1. Take a photograph of the full interior before touching anything — this is your evidence of the initial state
1. Examine each component carefully before recording anything:
- **Motherboard** — the main circuit board the entire laptop is built around. Every component connects to or sits on it
- **RAM slot** — note how many slots are present, which are populated, and what type of RAM is installed. Check the label on the stick itself
- **Storage bay** — locate the 2.5-inch SATA bay. Check whether a drive is present, and inspect the SATA connector and cable condition
- **CMOS battery** — small round coin cell on the motherboard. Note its location and how it is connected
- **Cooling fan and heatsink** — locate the fan and the copper heatsink. Note the condition of the fan blades and whether dust is visible
- **Wi-Fi card** — small rectangular card with two antenna cables. Note the colour of each cable and which connector it sits on
1. Take a photograph of each component individually
1. Cross-reference what you see against the Hardware Specs table above — note any differences
1. Reassemble — seat the base cover clips first, then replace all screws. Battery goes in last
1. Log the session in `logs/hardware_log.tsv`
1. Push to GitHub

**What you are learning:** How to approach an unfamiliar device methodically before doing any work. In a real MSP environment, documenting hardware before touching it protects you if something is already broken and gives the client an accurate record of their equipment.

**Skills:** Hardware identification, component documentation, safe disassembly and reassembly, evidence photography

-----

### Session 2: RAM Inspection and Re-seating

**Scenario:** A user reports their laptop is running slowly and freezing intermittently. First physical check is RAM — inspect the stick, remove it, examine the contacts, and re-seat it.

**Workflow:**

1. Remove the battery and unplug the charger
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

1. Remove the battery and unplug the charger
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

### Session 4: CMOS Battery Inspection and Replacement

**Scenario:** A device is brought in with a suspected dead CMOS battery — it was losing its date and time settings on every reboot before it stopped working. Your job is to locate the CMOS battery, remove it, inspect it, and re-seat it correctly.

**Workflow:**

1. Remove the battery and unplug the charger
1. Remove the base cover
1. Locate the CMOS coin-cell battery on the motherboard — small round silver battery, usually CR2032
1. Before removing it — understand what it does. This battery keeps BIOS settings stored when main power is removed. When it fails, the system loses its date, time, and configuration on every reboot
1. Take a photograph of the CMOS battery in place — note its position and how it connects to the board
1. Remove the CMOS battery carefully using a plastic pry tool — do not use a metal screwdriver
1. Examine the battery and its housing — note any corrosion, damage, or debris around the contacts
1. Re-seat the CMOS battery firmly
1. Take a photograph of the CMOS battery re-seated
1. Reassemble
1. Log the session — note battery condition, housing condition, and any findings
1. Push to GitHub

**What you are learning:** CMOS battery failure is a common fault on older laptops. Knowing how to locate, remove, and inspect it — and understanding what it does — is a standard part of hardware diagnosis before escalating to a motherboard fault.

**Skills:** CMOS battery handling, motherboard component identification, physical fault diagnosis

-----

### Session 5: Thermal Inspection and Fan Check

**Scenario:** A user reports the laptop is overheating and shutting down unexpectedly. Inspect the cooling system and document the condition.

**Workflow:**

1. Remove the battery and unplug the charger
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

**What you are learning:** Dust buildup is one of the most common causes of overheating and unexpected shutdowns. Inspecting and cleaning the cooling system is a standard preventative maintenance task in any MSP environment.

**Skills:** Thermal management, fan inspection, preventative maintenance, before and after evidence documentation

-----

### Session 6: Physical Fault Simulation

**Scenario:** A laptop has been returned after someone attempted a repair. You need to inspect the internals, identify what has been disturbed or incorrectly seated, document it, and restore the correct configuration.

**Workflow:**

1. Remove the battery and unplug the charger
1. Remove the base cover
1. Deliberately disturb the following — do one at a time and photograph each before restoring:
- Unseat the SATA drive caddy from the interposer port — leave it slightly disconnected
- Partially unseat the RAM stick — press one clip back without fully releasing it
- Disconnect one Wi-Fi antenna cable
1. Take a photograph of each disturbed component — this is your fault evidence
1. For each component — document exactly what you see, what the fault would cause in a working device, and what the correct state looks like
1. Restore each component to the correct state:
- Re-seat the SATA drive caddy firmly
- Re-seat the RAM stick until both clips click
- Reconnect the Wi-Fi antenna cable until it clicks
1. Take a photograph of each component restored
1. Reassemble
1. Log the session — document each fault found, what it would cause, and how it was resolved
1. Push to GitHub

**What you are learning:** In a real support environment you will regularly receive devices that have been partially disassembled by someone else. Being able to identify what is incorrectly seated, document it clearly, and restore it is a core 2nd line hardware skill.

**Skills:** Fault identification, physical inspection, component re-seating, fault documentation, hardware audit

-----

### Session 7: Wi-Fi Card Inspection and Antenna Check

**Scenario:** A user reports intermittent Wi-Fi dropping and slow wireless speeds. The Wi-Fi card and antenna connections need physical inspection.

**Workflow:**

1. Remove the battery and unplug the charger
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

**What you are learning:** Loose antenna cables are a frequent cause of poor wireless signal and intermittent drops. Physical inspection rules out a connection fault before replacing the card or escalating to a driver investigation.

**Skills:** Wi-Fi card handling, antenna cable identification, connector inspection, physical fault diagnosis

-----

### Session 8: Deep Clean and Preventative Maintenance

**Scenario:** The laptop has come in for a scheduled maintenance clean. Carry out a full preventative maintenance inspection and clean — a standard deliverable in any MSP contract.

**Workflow:**

1. Remove the battery and unplug the charger
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

**Diagnostics** — Physical fault identification, fault simulation and resolution, cable and connector inspection, component condition assessment

**Safety** — Electrostatic discharge prevention, safe disassembly, battery removal, anti-static wrist strap, component handling

**Maintenance** — Preventative cleaning, thermal management, before and after documentation, MSP maintenance workflow

**Documentation** — Evidence photography, structured logging, GitHub as audit trail

-----

## Audit Trail

Every session is logged manually to `logs/hardware_log.tsv` immediately after completion. Evidence photos are saved to `evidence/session_XX/`. See LOGGING.md for the full schema.
