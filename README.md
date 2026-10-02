# rehab-biomech-log

**Learning biomechanics and biosignal processing in the open, thirty minutes a day, from 17 September 2026 to 14 February 2027.**

I am a robotics engineering master's student in Genoa, heading for wearable and assistive robotics: devices that read what a person's body is doing and act on it. This repository is the dated record of getting there — what I read, what I write, what I get wrong — one weekly note at a time.

The reason for keeping it in public is simple. A plan is a promise; a commit history is evidence. If the work happened, it is here with a date on it, and if a week went badly that is here too.

---

## Where this comes from

<table>
<tr>
<td width="50%"><img src="https://raw.githubusercontent.com/Tawakoll/active-ankle-prosthesis/main/media/hardware/ankle-assembled.png" width="100%"></td>
<td width="50%"><img src="https://raw.githubusercontent.com/Tawakoll/active-ankle-prosthesis/main/media/demo/gait-cycle-trace.gif" width="100%"></td>
</tr>
<tr>
<td align="center"><i>The ankle, as built</i></td>
<td align="center"><i>The controller tracking a gait cycle</i></td>
</tr>
</table>

In 2021, four of us built a **powered ankle prosthesis** as our B.Sc. graduation project in Cairo: a drill motor driving a ball screw, four load cells under the foot to tell the controller which part of the step the wearer was in, and a PID position loop running as FreeRTOS tasks on an ESP32. The firmware, the control design, the test bench and the electronics were mine.

> ### 🦿 [**Tawakoll/active-ankle-prosthesis**](https://github.com/Tawakoll/active-ankle-prosthesis)
> *Powered ankle prosthesis: ESP32 + FreeRTOS position control, load-cell gait-phase detection, ball-screw drive. B.Sc. graduation project, AASTMT Cairo, 2021. Sponsored by the Academy of Scientific Research and Technology (ASRT), Egypt.*

That project is the reason for this one. It is also the honest inventory of what I am still missing.

**What it gave me**

- Closed-loop position control of a real joint, on hardware I wired myself
- Concurrent control software: sensing, trajectory and control as separate tasks
- Gait-phase detection that worked, demonstrated on the bench

**What it did not**

- I have never recorded a biosignal, and I have never been in a room where a person was instrumented
- Phase detection was thresholds on four load cells — no ground truth, no validation, no dataset behind it
- The reference trajectory came from published kinematics and was never checked against a measured one
- Position control only: no torque, no impedance, none of the compliance a real ankle needs
- It was never tested on an amputee

The second list is what the next six months are for. The hardware half I have done once. This is the sensing-and-control half.

---

## The plan

Twenty-one weeks, thirty minutes a day, about seventy-four hours in total.
