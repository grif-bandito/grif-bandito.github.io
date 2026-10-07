# Craftsman Field & Bench Notes
---

[Back to Portfolio Homepage](../index.md)

---

### Overview


---

<br>

## Snap-on Verdict CMOS Swap

---
### Project Description

---
### Details

* **Device:** Snap-on Verdict D7 Diagnostic Scanner LCD Display (MN:EEHD300)
* **Primary Issue:** Boot stall / RTC Checksum Error & Suite Lockout
* **Key Solution:** Clock recovery via 2-pim Molex CR2023 swap
* **Tools & Cost:** Precision screwdriver set, $6.39 replacement battery

---
### Project Log

<details markdown="1">
<summary><b></b>2026-04-02 Verdict D7 CMOS: Introduction</summary>b></summary>

A local shop owner entrusted me with a pretty unique and expensive piece of equipment. The Snap-on Verdict D7 display unit (MN:EEHD300). Brand new from Snap-on this is a $6,000 unit. The stakes felt high, a pretty big jump from fumbling around with my own broken tech.


### Customer Report_

The shop owner explained to me that out of nowhere when booting up the D7, the screen would stall at a wall of terminal like text and he needed a keyboard to plug into the device to hit F2 to skip it. The issue was, once the devices was booted to the desktop, Running Windows Embedded Standard (Essentially a stripped down windows 7), they were still unable to open the Snap-on Diagnostic suite (A program used as a dashboard to translate a cars computer into readable information). 

This led them to believe that Snap-on essentially remotely bricked the device via some licensing agreement, which is becoming a very painfully common ordeal. 

My heart rate spiked a bit, I was already thinking of the nightmare before me. Side stepping some nonsense licensing hook or having to translate the drive to another system entirely, but then how do I ensure the OBD cables can still work with whatever new system I Frankenstein together? I kept these theories to myself for the most part, but I think they were rightfully concerned.


### Hands-On Diagnosis_

Getting the D7 home and booting it up... I was hit with a huge reality check. The black screen appeared and my eyes locked onto the real culprit. "CMOS checksum error - Defaults loaded". The wave of relief I felt was beautiful.

The CMOS coin battery was dead, that's nothing compared to the system level war I was mentally preparing for. 


### Execution_

Opening up the D7 was straightforward, one by one finding screws around the edges of the back of the shell, two under the Li-ion battery. Boom, I was in, the CR2032 CMOS coin battery was right there atop the PCB. Connected only by a single 2 pin Molex and a adhesive pad under the coin, It put up a little fight coming out, but no deal.

Placed an order for a Rome Tech CR2032 CMOS battery for $6.39 before tax and shipping. When it arrived the following day, I plugged in the Molex, stuck the coin it down to the PCB, put the shell back together and booted her up. Once on the desktop, I altered the date and time and restarted the device. The date and time held true and the Snap-on diagnostic suite loaded up without a hitch.


### Conclude_

The shop owner was very happy and clearly a bit surprised. It really felt amazing to restore his device that otherwise may have been written off as some system level lockout. The simplest solution is often correct, but can lead to waste and abandonment if undiscovered.

</details>

---

<br>

## Apple iBook G4 - Field Diagnostic & System Restoration

---
### Project Description

---
### Details

* **Device:** Apple iBook G4 (12-inch PowerPC)
* **Primary Issue:** Startup boot & GUI stall
* **Key Solution:** Open Firmware disk ejection & Single-User Mode filesystem repair (fsck -fy)
* **Tools Used:** PowerPC Open Firmware, BSD root shell, legacy USB 2.0 thumb drive
---
### Project Log

<details markdown="1">
<summary><b></b>2026-04-24: Introduction</summary>b></summary>

</details>

---

<br>

## JBL Live 660NC Headphone Restoration

---
### Project Description

---
### Details

* **Device:** JBL Live 660NC Wireless ANC Headphones
* **Primary Issue:** Rattling within internal shell, Cracked screw bosses, Degraded clamping force
* **Key Solution:** Debris clearing, Adhesive structural reinforcement, Replacement ear cups & Sleeve band addition 
* **Tools Used:** Spudgers / Prying tools & Precision screwdriver set, Electrical tape, Super glue
---
### Project Log

<details markdown="1">
<summary><b></b>2026-04-24: Introduction</summary>b></summary>

</details>
