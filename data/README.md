# Data

**Nothing in this directory is committed.** The dataset belongs to its authors; this file is how to get it.

## EPIC lab open-source biomechanics dataset

Camargo, J., Ramanathan, A., Flanagan, W., Young, A. (2021). *A comprehensive, open-source dataset of lower limb biomechanics in multiple conditions of stairs, ramps, and level-ground ambulation and transitions.* Journal of Biomechanics, 119, 110320. [doi:10.1016/j.jbiomech.2021.110320](https://doi.org/10.1016/j.jbiomech.2021.110320)

Download: <https://www.epic.gatech.edu/opensource-biomechanics-camargo-et-al/>

**What is in it.** 22 able-bodied subjects. Per subject, recorded synchronously:

| Modality | Detail |
|---|---|
| EMG | 13 lower-limb muscles |
| IMU | trunk, thigh, shank, foot |
| Goniometers | hip, knee, ankle |
| Motion capture | marker trajectories, and the joint kinematics derived from them |
| Force plates | ground reaction forces and moments |

Conditions: level ground at several speeds, ramps at several inclines, stairs at several rise heights, and the transitions between them.

**Size.** Roughly 1 GB per subject. Start the download early and let it run.

## Why this one dataset

Every branch of the 15 November fork is fed by it. IMU and force plates give gait-phase detection with ground truth to check it against; EMG gives the body–machine-interface work; motion capture gives a reference for anything markerless. Choosing a branch later therefore never means choosing data again.

## Layout expected by the notebooks

```
data/
  epic/
    AB06/
    AB07/
    ...
```

Nothing here is redistributed. Cite the paper wherever the data is used.
