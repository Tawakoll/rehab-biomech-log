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

Twenty-one weeks, thirty minutes a day, about seventy-four hours in total. Two blocks that commit me to nothing, one decision, one build, one short paper. The full version is in [ROADMAP.md](ROADMAP.md).

| Block | Weeks | Dates | What | Deliverable |
|---|---|---|---|---|
| **Core 1** | 1–3 | 17 Sep – 11 Oct | Movement vocabulary and the linear-algebra map | Three weekly notes, an annotated gait-cycle diagram, a cheat sheet in my own notation |
| **Core 2** | 4–8 | 12 Oct – 15 Nov | Biosignals in Python: EMG, IMU, movement, PCA | A public notebook that loads real EMG and movement data, processes both correctly, and reduces many channels to a few meaningful ones |
| **Fork** | — | 15 Nov | Choose the specialisation, with five weeks of evidence in hand | A decision, written down with its reasons |
| **Build** | 9–17 | 16 Nov – 17 Jan | Make the pipeline work end to end, then break it deliberately | A working pipeline, with figures and an honest account of where it fails |
| **Write** | 18–21 | 18 Jan – 14 Feb | Four pages, IEEE format | A short paper. Code freeze 24 January |

One dataset carries all of it: the [EPIC lab open-source biomechanics dataset](https://www.epic.gatech.edu/opensource-biomechanics-camargo-et-al/) (Camargo et al., 2021) — IMU, EMG from thirteen muscles, goniometers, motion capture and force plates on the same 22 subjects, walking level ground, ramps and stairs. See [data/README.md](data/README.md).

### The fork, on 15 November

Three branches, all fed by the same dataset and the same first eight weeks:

- **A — control the device.** Gait-phase detection from IMU, then a simulated assistance torque timed to push-off. The front end of every powered prosthesis controller there is, and the direct descendant of the ankle above.
- **B — control with the body.** Map EMG and movement onto a low-dimensional control signal and drive something with it.
- **C — measure the movement.** A markerless video pipeline validated against the dataset's own motion-capture ground truth. The fallback.

A is where I am pointing. The decision gets written into [notes/](notes) on the day, with what changed my mind if it changes.

---

## The log

One note per week, written in my own words, committed dated. Template: [notes/TEMPLATE.md](notes/TEMPLATE.md).

| Week | Dates | Focus | Note |
|---|---|---|---|
| 01 | 17–23 Sep 2026 | Planes, axes, the gait cycle · linear algebra 1–3 | [week-01.md](notes/week-01.md) |

---

## What is in here

```
notes/        one markdown note per week, plus the template
data/         how to get the dataset; the data itself is not committed
ROADMAP.md    the twenty-one week plan in full
```

Notebooks and pipeline code arrive in Core 2 and get their own directories then.

**What is deliberately not in here:** the application deadlines, the emails, the people I am writing to and what I am asking them. That track runs in parallel and belongs in my own notes, not in a public repository.

---

## Licence

Code is [MIT](LICENSE). The notes and writing are [CC BY 4.0](LICENSE-DOCS). The EPIC dataset is not redistributed here — it belongs to its authors and is cited where it is used.
