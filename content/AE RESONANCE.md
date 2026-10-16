# In a nutshel

| Developer   | Mike van Zeeland                             |
| ----------- | -------------------------------------------- |
| Git  admin  | Jose Rueda Rueda                             |
| Purpose     | Calculate resonance locations in phase space |
| GitHub link |                                              |
# Theory and Computation

The AE resonance calculation identifies when the following resonance condition is met,

ω+(m+l)ωθ−nωζ=0

where ω is the mode frequency, m is the poloidal mode number, l is an integer quantum number, ωθ is the ion poloidal transit frequency, n is the toroidal mode number, and ωζ is the ion toroidal transit frequency.

The code identifies values of p=m+l that satisfy the resonance condition through p=(ω−nωζ)/ωθ. The ion orbit frequencies are determined by calculating the orbits using the constants of motion method described in [Van Zeeland 2011]. These integer values of p are mapped onto the (Pϕ,μ) space according to the ion orbits satisfying the values of ωζ and ωθ. At every point along this p-mapping, the corresponding value of ion position (ρ) is determined. Value of ρ that are within the spatial extent of the mode are returned as resonance points. Each set of points along a single p-path are separately identified.

The search for resonances is conducted over a specific range of p values. The extrema of these p values are determined based on the user-provided l extrema according to pmax=lmax+nqmode and pmin=lmin−nqmode. This is equivalent to assuming m=nqmode. The functional dependence m=m(n,qmode) depends on the mode frequency [Heidbrink 2008], e.g., for a TAE with ω=vA/(2qR) we have m=nqmode−1/2.

The setting of m=nqmode is inconsequential because a range of p-values are searched for resonances. Even if the value of m is incorrect for a particular mode, the resonances will still be identified based on the wide range of p that is searched (a range determined by the user-provided range of l-values).

# Using the Widget

The widget can be compiled and started from the command line after loading the ep module,

```bash
module load ep
aeresonance 
```

where the user will be prompted to accept the ADAS User Agreement. This is necessary because ADAS-provided atomic cross sections are used in the beam deposition calculation. The DIII-D ADAS User Agreement may be found at, [[1]](https://diii-d.gat.com/DIII-D/comp/software/adas/agreement.html)


## Shortcuts

Many different keywords can be passed to the initial call in order to populate the fields as the widget window opens. It is also possible to save all of the inputs (including values in the NBI and Mode data tables) using _File_ → _Save All Setup_ to create an IDL save file. If you have such a file, then you can load as the widget opens by calling the calculator with the _SETUP_ keyword,

```IDL
ae_resonance, setup='SAVE FILE NAME'
```


The other keywords that can be set when opening the widget are,

> [!INPUTS]
> shot = shot number
> time (ms) =  time slice of interest
> efit = run ID for the desired EFIT (must exist in the MDSplus tree)
> e0 = energy of the ions to plot (keV, always a single energy)
> gadir = location of the GAprofiles (density, temperature, rotation, and impurity density)
> sf_orbit = name of a file containing (or to contain) the complete ion orbit phase space as calculated with _Orbit Phase Space_
> sf_nbi = name of a file containing (or to contain) the beam deposition profile
> sf_mode = name of a file containing (or to contain) the mode resonance results

The Full Phase Space tab is where the desired shot information is provided. The inputs are:

> [!INPUTS]
> - Shot = shot number
> - Time (ms) =  time slice of interest
> - EFIT = run ID for the desired EFIT (must exist in the MDSplus tree)
> - Ion Energy (keV) = energy of the ions to plot (always a single energy)
> - Ion Charge State = Z-value of the deposited partilces (almost always unity)
> - Radial Positions = density of radial starting locations for which to calculate ion orbits
> - Pitches = density of pitch angles for which to calculate orbit
> - GAprofiles Directory = location of the GAprofiles (density, temperature, rotation, and impurity density)
> - Orbit Save File = result of this calculation is saved to this file (if this file already exists, then those results will be plotted and no new calculation performed)

## Saving Graphics

Any of the graphics can be saved by right-clicking the graphic window and then following the IDL save prompt. The file type will be set according to the extension of the filename you provide. For example, naming a file _graphic.eps_ will save an EPS file, while _graphic.png_ will produce a PNG.

## NBI Deposition

The _NBI Deposition_ tab will place a set of deposited beam ions into the phase space plots. The user input parameters concern the beam firing profiles. You can either input these values into the data table (see Fig. 2) manually, or use the _Load GET_NBI for #_ (# will be replaced with the shot number provided in the _Full Phase Space_ tab) button to automatically populate the table. The Duty Cycle should be set according to the beam firing profile over the time range of interest.

The inputs for the NBI deposition calculation are:

> [!INPUTS]
> - Duty Cycle = fraction of time during which this beam is on (e.g., if you care about a 10 ms time window and the beam is on for 5 ms within that time period, then the duty cycle is 0.5 for that beam)
> - Power (MW) = beam power
> - Adj. Current (A) = beam current scaled according to its duty cycle. This number represents the total number of particles injected by this source within this time period.
> - Voltage (kV) = applied voltage of the beam 
> - Beam Ions Deposited = total number of ions to plot  (each beam will inject a fraction of this total that is determined based on the Duty Cycle)
> - Seed for Random Sequence = sets the random number sequence (The beam deposition code features a default seed, so you will get the same deposition every time unless you provide a unique seed. This entry field automatically generates a seed based on the current date and time.)
> - Beam Save File = file in which to store the output of this operation. If this file exists, then it will be read and displayed (no new calculation will be performed)

To maintain the relative beam ion concentration according to the beam usages, the beam current is adjusted according to the provided duty cycle. If a value within the data table is altered, then the data table will turn red until the _Update Currents Based on Duty Cycle_ button is pressed to adjust these values. 
Once the beam deposition is calculated, the individual particle birth positions will be overlaid on the _Full Plot_ graphic tab.

## Modes

The Alfven eigenmode resonances are calculated as described in the introduction on this wiki page. The input window is shown below, and the input parameters are,

> [!INPUTS]
> - Lab Freq. (kHz) = measured mode frequency
> - Omega (rad/s) = toroidal rotation at a radial location corresponding to the mode
> - n-number = toroidal mode number
> - Min. rho = minimum value of rho over which the mode exists
> - Center rho = central location of the mode
> - Max. rho = largest value of rho at which the mode exists
> - Minimum L = smallest value of L to use for resonance calculation
> - Maximum L = largest value of L to use for resonance calculation
> - Mode Save File (Prefix Only) = prefix to use for filenames that contain the results from each mode. (i.e., you can provide up to five modes, so this will be the prefix on each output save file)

The results from the resonance calculation will be plotted as yellow +-symbols on the _Full Plot_ tab. This is shown here,

Once the resonances are calculated, then all other graphical outputs will be generated. This includes the beam ion deposition density (this should probably be changed to allow this plot to be generated before the resonances are determined).

The beam deposition profile will be binned to determine the density across phase space. This is plotted with the resonances on the _Deposition Density_ tab. Here is the output from the present example,

The number of beam ions along each individual resonance path will be counted in order to provide a distinction between these resonances. The _Resonances Only_ tab will show these resonance paths with a color coding that indicates how many of the deposition ions lie along their path. Here is the output from the present example,

Finally, the gradient in the beam ion density (deposition) is calculated along each resonance path and displayed in the _Deposition Gradient_ tab. This plot maintains the color coding from the _Resonances Only_ tab (to a large extent, the only reason for counting the total ions along each path is to provide some classification scheme for distinguishing them). Here is the output from the present example,

# Utilities (command line)

There are subroutines within the AE Resonance widget that can be called at the command line. These may be useful for processing of new results, or for generating graphics based on saved results from the widget.

**Two-dimensional Histogram of NBI Deposition**  
The procedure _AER_NBI_DENSITY_ performs a histogram of the beam deposition data over the ϕμ phase space (e.g., this data is shown as the red data points in the beam deposition figure). The procedure is generic, however, so non-beam data could be passed to it. The call is (after compiling _AE_RESONANCE_),

```IDL
aer_nbi_density, beamPphi, beamMu, out, dPphi=dPphi, dMu=dMu
```


> [!INPUTS]
> beamPphi = X-axis data to be histogrammed (Pϕ in the beam deposition case)
> beamMu = Y-axis data to be histogrammed (μ in the beam deposition case)
> out = structure, variable into which the result will be stored
>       hist → 2D array of histogrammed result
>       x → x-axis of result
>       y → y-axis of result
> dPphi = keyword, set to binning size along x-axis (default is 0.01)
> dMu = keyword, set to binning size along y-axis (default is 0.1)

  

  

### Changelog

1.1 - uploaded on May 29, 2015
 Saved as ae_resonance-20150529.gz
 + added L-values in the setup save file
 + changed default L-value range to [-5.0, 5.0] (was [-3, 3])
 + fixed plot color error that caused first line in density gradient 
   plot to be displayed in white on a white background
 + added min/max keywords to AER_NBI_DENSITY

1.0 - sent out through email on May 26, 2015
 Saved as ae_resonance-20150526.gz

  
**References**

M.A. Van Zeeland, et al., "Measurements and modeling of Alfven eigenmode induced fast ion transport and loss in DIII-D and ASDEX Upgrade," _Phys. Plasmas_ **18**, 056114 (2011), [[2]](http://dx.doi.org/10.1063/1.3574663)

W.W. Heidbrink, “Basic physics of Alfven instabilities driven by energetic particles in toroidally confined plasmas,” _Phys. Plasmas_ **15**, 055501 (2008), [[3]](http://link.aip.org/link/?PHP/15/055501/1)|

|                  |
| ---------------- |
| <br>  <br><br>   |