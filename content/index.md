Energetic Particle Codes are stored on Omega at `/fusion/projects/toolbox/energetic_particles` 

The old wiki can be found in: https://diii-d.gat.com/diii-d/BPphysicsEnergetic. This site, under construction, will contain the detailed current status of these codes


> [!WARNING] Don't store your cooked food with your saucepans
> After you have cook an excellent dish, if you need to save a part of it, you don't store it in the same kitchen cabinet that your saucepans. You use the fridge. Please apply the same criteria here. The EP toolbox is the cabinet in your kitchen where you have your cooking utensils, do not store here your cooked food! Keep your tenso of GB data output and files in your user folder!

# Basic code usage
## For IDL based codes
Start by loading the EP module
```bash
module purge
module load ep
```

All IDL codes in the toolbox are now in your path, so you can open an idl terminal and call all those routines or open dedicated guis such as `multipow`, `aeresonance`, `fidagui`

Some codes require ADAS. If you haven’t been added as an ADAS user, go here and follow the instructions, including signing the ADAS User Agreement and sending it off as directed: https://diii-d.gat.com/diii-d/Adasuser

## For python codes
Some python codes requires specific packages, so a common environment can't be created for all EP code. You will find in each module the precise python env you should load for each case

# Basic code development
All codes in the EP common areas should be under version control in order to make it easier for other people to improve the codes and to track and compare past versions. **Users should not directly edit the production (public) version of the codes in** `/fusion/projects/toolbox/energetic_particles`.  To update codes, users can clone the production version to their own development area, update the code, and then push the updates to the relevant project on the GitHub server. The owners of the project can then update the production version of the codes on Omega.


> [!DANGER] Don't mess things up
> Users should not directly edit the production (public) version of the codes. Create your clone in the dev area, push to GitHub, and wait for the owner to update the public code
> 


## Sign up for GitHub
- Each user should be a part of the EP GitHub group: https://github.com/D3DEnergetic
- After creating your GitHub account, send an email to jrrueda@uci.edu so he can add you.

## Set up your dev area
 Create your own user dev folder:
```bash
cd /fusion/projects/toolbox/energetic_particles/
mkdir dev/$USER
# Make your directory only writable by you!
chmod g-w –R /fusion/projects/toolbox/energetic_particles/dev/$USER
```

## Example of code development
- 1: Identify something that needs to be done in one of the EP libraries
- 2: Open an issue in the corresponding GitHub page of that code
- 3:  Create a branch with the issue number, so GitHub associate them with the issue and things are trazable
- 4: Clone the repo to your dev folder: 
```bash
cd /fusion/projects/toolbox/energetic_particles/dev/$USER
git clone <MyCodeLink>
git checkout <MyCodeBranch>
git pull
```
- 5: Modify the code as needed
- 6: TEST the modification
- 7: Add the changes to git: 
```bash
git add <MyFilesChanged>
git commit -m "<A clear 1 line message explaining what you did"
git push
```
- 8: Notify the code owner for him to merge and update the public code

## Useful GitHub commands
- `git status` (see what branch you are and what changes have been made) 
- `git branch –v` (see all of your local branches) 
- `git branch –vv` (see your local branches and the branches they are tracking) 
- `git branch dev` (create but not switch to a branch named “dev”) 
- `git branch –d dev`  (delete a branch named “dev”) 
- `git checkout dev` (switch to an existing branch named “dev”) 
- `git checkout –b dev` (create and switch to the branch called “dev”) 
- `git add file` (add “file” to the list of staged commits) 
- `git rm file` (remove “file” from the list of staged commits) 
- `git remote –v` (display all shortnames and URLs for remote repos) 

# Abandoned folders
- [EP EFIT TOOLS](EP%20EFIT%20TOOLS.md)
- gacode_add

git config --global --add safe.directory /fusion/projects/toolbox/energetic_particles/ION_ORBITS_TRACK_MV