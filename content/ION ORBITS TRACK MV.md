| Maintainer | Mike Van Zeeland                               |
| ---------- | ---------------------------------------------- |
| Purpose    | Tracks EP orbits in toroidally symetric fields |
| Git repo   | https://github.com/JoseRuedaRueda/uFILDSIM     |
# Main overview
Program to calculate fast-ion orbits in efit equilibrium using Van Zeeland's integrator
It can run super quick if you just need the poloidal projection of the orbit, to classify the topology, as for this, you only need to calculate the surfaces of constant mu and ptor. It also allows you to get the full 3D orbit integrating in time

# Usage


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
