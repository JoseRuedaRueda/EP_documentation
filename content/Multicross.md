This folder contains two different codes. Both allow to get the end number of a fluctuation

# Toroidal fit


| Maintainer | Mike Van Zeeland                                                    |
| ---------- | ------------------------------------------------------------------- |
| Purpose    | Get the crosspower of different CO2 and ECE channels                |
| Git repo   | /fusion/projects/toolbox/energetic_particles/magnetics/toroidal_fit |

## General overview

This program takes in a shot, minimum time (tmin) in ms and maximum time (tmax) retrieves the co2 r0 and v2 phase data (change in phase and integratesit) and calculates a bunch of crosspower between the two the contour is the log_10(crosspower^.5), with frequency ranges set by flowcont:fhighcont (kHz)
The Crosspower in a single band (flowbpf:fhighbpf (kHz) is also integrated and plotted.

All of the data are returned in the aeco2dat structure explained a few lines down,below the keyword inputs

IT requires the some routines from:  /u/vanzee/idl/lib


## Usage

Load the ep module and open an idl command box

```bash
module load ep
idl
```

Within IDL
Follow documentation of the header of each file