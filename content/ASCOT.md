# In a nutshel

| Maintainer | Jose Rueda Rueda                     |
| ---------- | ------------------------------------ |
| Purpose    | Aux routines to prepare ASCOT inputs |

# Long description
[ASCOT5](https://arxiv.org/abs/1908.02482/) is a test-particle orbit-following code for solving minority species’ distribution functions, transport, and losses in tokamaks and stellarators. 

This folder does not contain the source from ASCOT itself, this can be found in the link above. This module allow to take data from a TRANSP/FIDASIM/FILDSIM simulation and transform it into ASCOT inputs.

# Module content
- `bgrid.py`:  Prepare equilibrium from G file.
- `boozer_xd.py`: Calculate boozer coordinates.
- `create_structure.py`: Aux routine to create the object containing the data.
- `fidasimUtils.py`: Allow to read markers from FIDASIM and FILDSIM (synthetic INPA) files.
- `geqdsk.py`: Read the G file.
- `nova2ascotPrepare.py`: Calculate the phi and alpha potentials from a nova displacement file.
- `readNova.py`: read a nova file.
- `resonanceFinder.py`: Eval the orbit frquencies of the markers followed in ASCOT.
- `transp2ascotPrepare.py`: read profiles and nubleam markers from TRANSP file.

# Examples
Please see example subfolder in the folder

# Recommended python environment
`/fusion/projects/codes/conda/omega/dev_envs/ruedaruedaj/ascot-env563`

To load it:
```bash
module purge
module load mamba
mamba activate /fusion/projects/codes/conda/omega/dev_envs/ruedaruedaj/ascot-env563
```