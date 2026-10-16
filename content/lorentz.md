| Maintainer | Bill Heidbrink                                       |
| ---------- | ---------------------------------------------------- |
| Purpose    | Basic Lorentz Orbit Code                             |
| Git repo   | /fusion/projects/toolbox/energetic_particles/lorentz |
|            |                                                      |

# Overview
Basic lorentz orbit code ported from venus

# Usage
To use this code, initialize the ep module

```
module load ep
```
After it, the only file you need to interact with is orb.pro

```idl
PRO orb,g,InitialPosition,ivel, $
      nsteps=nsteps,step=step,time_reverse=time_reverse, $
      e0=e0,amu=amu,z=z, $
      chk_conserved=chk_conserved,detail=detail,hc=hc, $
      orb_dat=orb_dat

; Sample call for a co-tangential on-axis beam that ionizes
; on the midplane
; IDL>g=readg(159243,745)
; IDL> r=2.1
; IDL> vphi=1.15/r               
; IDL> vr=-sqrt(1-vphi^2)
; IDL> orb,g,[r,0,0],[vr,vphi,0],nsteps=10000

; Cleaned up (a bit) on 6/1/2007 by WWH

; WWH 4/6/2001
; SI units
; Program to calculate fast-ion orbits in efit equilibrium using rk4
;
; INPUTS
;	InitialPosition	  [r,phi,z] vector (m)
;	ivel		[v_r,v_phi,v_z] initial vector (a.u.)
;	g		eqdsk saved as idl structure

; OUTPUT	elevation and plan view plots
; KEYWORDS
;	nsteps	orbit length is step*nsteps (m)
;	step	how often to record orbit coordinates (m)
;		(not used in actual integration)
;   time_reverse    set to run orbit backward in time
;	e0	particle energy (keV)--default is 80
;	amu	particle atomic mass (default=2)
;	z	particle charge (default=1)
;   chk_conserved  plots constants of motion
;   detail	plots detail of orbit near starting point
;   hc		writes postscript file of the graphs 
;   orb_dat	writes orbit coordinates to a local file
;		'orb.dat'
; yout(*,nactual) is the saved 6-vector coordinates of the orbit
; in cylindrical coordinates (v_r,v_phi,v_z,r,phi,z)
```