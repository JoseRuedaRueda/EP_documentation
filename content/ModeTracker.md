
| Maintainer | Jose Rueda Rueda                                                                          |
| ---------- | ----------------------------------------------------------------------------------------- |
| Purpose    | Tracks modes in a spectrogram using cost functions                                        |
| Git repo   | [https://github.com/JoseRuedaRueda/uFILDSIM](https://github.com/D3DEnergetic/ModeTracker) |
# Main overview
Program to get the mode frequency vs time time trace in a spectrogram using cost functions

The whole idea of the code can be seen in these slides:
![](assets/ManagingToolsToFindModes.pdf)
# Usage

## Python env loading

```bash 
module purge
module load mamba
mamba activate /fusion/projects/toolbox/energetic_particles/PythonEnvs/epScintSuite
```

To learn how to use the code, see the examples in:
`/fusion/projects/toolbox/energetic_particles/ModeTracker/Examples`


> [!INPUTS] 
> - Initial positon [r, phi, z] (m)
> - g eqdsk file
> 
> KEYWORDS
> - step: how often to record orbit coordinates (m)  (not used in actual integration)
> - time_reverse set to run orbit backward in time 
   amu particle atomic mass (default=2)
> - z: particle charge (default=1)
> - er_fname:  STRING, giving the name of the file in which the radial electric field data is saved. This IDL save file should contain two arrays: er_rho (V/m) & rho (normalized)


>[!RETURN] 
> - yout(*,nactual) is the saved 6-vector coordinates of the orbiti n cylindrical coordinates (v_r,v_phi,v_z,r,phi,z)
> - pitch - Orbit property = v_|| / v
