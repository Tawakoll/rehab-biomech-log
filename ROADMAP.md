# The plan, in full

**17 September 2026 → 14 February 2027. Twenty-one weeks, thirty minutes a day, roughly seventy-four hours.**

The destination is wearable and assistive robotics: sensing, control, and a person who moves differently at the end of it. Not clinical measurement — I want the instrument *and* the outcome.

Two things make the shape of this plan work. The first is that about two-thirds of the groundwork is identical across every branch of the field, so the early weeks commit me to nothing. The second is that one dataset feeds all of it, so the choice of branch never becomes a choice of data.

---

## Core 1 · Weeks 1–3 · 17 September – 11 October

### Movement vocabulary, and the linear algebra map

I cannot hold a conversation in this field until *swing phase*, *sagittal knee flexion* and *time-normalised to 100% of the cycle* come out without hesitation. Three weeks, and the highest return per hour in the plan.

| | |
|---|---|
| **Read** | Winter, *Biomechanics and Motor Control of Human Movement*, ch. 1–3 — planes, joint coordinate systems, the gait cycle, anthropometry |
| **Watch** | 3Blue1Brown, *Essence of Linear Algebra* — episodes 1–9 and 13–14, about three hours. Geometric intuition only; the derivations come on demand later |
| **Set up** | This repository. One markdown note per week |
| **Start** | The EPIC dataset download — it is large, so it runs in the background from week 1 |

**Daily thirty:** twenty minutes reading, ten minutes writing it into the week's note in my own words.

**Deliverable, 11 October:** repository live, three weekly notes, one hand-annotated gait-cycle diagram, and a linear-algebra cheat sheet in my own notation.

---

## Core 2 · Weeks 4–8 · 12 October – 15 November

### Biosignals in Python — EMG, IMU, movement

The heart of the plan, and still field-agnostic: every branch of the fork needs exactly this.

| | |
|---|---|
| **Data** | [EPIC lab dataset](https://www.epic.gatech.edu/opensource-biomechanics-camargo-et-al/) (Camargo et al., 2021): 22 subjects, IMU + EMG + goniometer + motion capture + force plates, across level ground, ramps and stairs |
| **EMG** | Recording basics, rectification, linear envelope, normalisation to MVC. The input to every prosthesis controller ever built |
| **Movement** | Filtering and what the cutoff costs you, gait-event detection, time-normalisation to 0–100%, ensemble mean ± SD curves |
| **The maths** | PCA on multi-channel body signals. Not a side topic — a body–machine interface *is* a linear map from high-dimensional body motion to low-dimensional device control. PCA is SVD is change of basis. Implement it once, on real data |

**Daily thirty:** one function or one figure per session. Commit every day, even four lines.

**Deliverable, 15 November:** a public notebook that loads real EMG and movement data, processes both correctly, and reduces many channels to a few meaningful ones — with a README explaining every choice.

---

## The fork · 15 November

By this date I will know three things I do not know today: who replied, what the coursework felt like from the inside, and what the notebook looks like to someone who does this for a living. So the choice belongs on that date and not before. All three branches run on the dataset I already have and the skills I already built.

### Branch A — control the device *(the one I am aiming at)*

Gait-phase detection from IMU, then a simulated assistance torque timed to push-off. The front end of every exoskeleton and powered prosthesis controller in existence. Needs no hardware, and it is the direct descendant of [the ankle](https://github.com/Tawakoll/active-ankle-prosthesis) — the same problem my load cells solved with two thresholds and no ground truth.

### Branch B — control with the body

Map EMG and movement onto a low-dimensional control signal and drive something with it. The body–machine-interface line: the same PCA from Core 2, pointed at a device.

### Branch C — measure the movement

A markerless video pipeline validated against the dataset's own motion-capture ground truth. Strong and useful, and the safest of the three — but measurement alone is not the agency I am after. A fallback, not a plan.

---

## Build · Weeks 9–17 · 16 November – 17 January

### The specialisation

Nine weeks on whichever branch. The shape is the same either way.

| | |
|---|---|
| **Weeks 9–12** | Get it working at all. Ugly is fine. A pipeline that runs beats an elegant one that does not exist |
| **Weeks 13–15** | Break it deliberately. Different subjects, different speeds, ramps and stairs rather than flat ground. Record every failure mode — that section is what makes it read as research rather than as a tutorial |
| **Weeks 16–17** | Clean it up, write the README, freeze the scope |

January exam preparation runs **separately** from the daily thirty minutes. It is not allowed to eat this.

**Deliverable, 17 January:** a working pipeline in this repository, with figures and an honest account of where it fails.

---

## Write · Weeks 18–21 · 18 January – 14 February

### The short paper

Four pages, IEEE format.

| | |
|---|---|
| **Question** | One sentence. Bounded, and answerable with the data I have |
| **Analysis** | RMSE, agreement (Bland–Altman), performance across conditions. Where it fails reported as prominently as where it works |
| **Discipline** | Code freeze 24 January. Everything after that date is writing |

**Daily thirty:** one paragraph or one figure per session. Writing, not coding.

**Deliverable, 14 February:** a short paper with my name on it. Not peer-reviewed, and that is fine. It proves I can frame a question, measure, and report honestly.

---

## The rules this plan runs on

1. **Thirty minutes, daily, is the whole budget.** Coursework, exams and applications run outside it and do not borrow from it.
2. **Commit every day, even four lines.** The dated history is the evidence; a perfect week that leaves no trace did not happen.
3. **Write in my own words or it does not count.** Copying a definition into a note is not learning it.
4. **Failure modes are findings.** The section on where it breaks is the section that makes it research.
5. **The plan is allowed to change; changes get written down** — in the week's note, with the reason, on the date.

---

## Sources this plan leans on

- Winter, D. A. *Biomechanics and Motor Control of Human Movement*, 4th ed.
- Camargo, J., Ramanathan, A., Flanagan, W., Young, A. (2021). A comprehensive, open-source dataset of lower limb biomechanics in multiple conditions of stairs, ramps, and level-ground ambulation and transitions. *Journal of Biomechanics*, 119, 110320. [doi:10.1016/j.jbiomech.2021.110320](https://doi.org/10.1016/j.jbiomech.2021.110320) · [dataset](https://www.epic.gatech.edu/opensource-biomechanics-camargo-et-al/)
- 3Blue1Brown, [*Essence of Linear Algebra*](https://www.3blue1brown.com/topics/linear-algebra)
