
AutoAFM components, bill of materials, assembled view and pictures

See STIFMap methods section for in-depth explanation of AutoAFM principles

Contact Connor Stashko (cstashko@hmc.edu) for questions

AutoAFM Pipeline:
    1. Thaw slide on hand and wash away OCT in PBS for 5 min
    2. Probe PA gels of known stiffness as a baseline
    3. Load tissue sample with approx. 250 uL of PBS + propidium iodide + CNA35 
    4. Open ‘STIFMap_Jupyter_script.ipynb’ in Jupyter and run it all
    5. Open MicroManager
        a. Load macros from 'STIFMap_micromanager_macros.txt'
        b. Manually center AFM stage (in x and y axes) 
        c. Run ‘main’ in micromanager
            i. Initializes the folders, but don’t do anything else in micromanager yet
    6. Asylum things: Hook up motors, load ‘STIFMap_IGOR_Asylum_macros.txt’
        a. Power motors with 12 V
        b. 'Compile', 'connect', 'initialize', 'initialize'
        c. Setup WatchFolder (‘WatchFolderPanel()’)
            i. ‘In’ and ‘out’ in ‘AFM_expt_temp’
        d. Change save directory to ‘out’ and uncheck ‘save to mem’
        e. Change trigger to 1.8 nN
        f. Set the force dist to ‘inf’ and ensure the velocity is 2 um/s
    7. Move to the region of interest on the slide
        a. Line up the stage with the optimal position
        b. Follow the onscreen windows on MicroManager for ‘main’
    8. Close door to AFM
    9. At the end, check the position of the tip under BF to ensure it hasn’t changed much
    10. Probe PA gels again to ensure tip elasticity did not drift during sample probing

Known Issues:
    • ImageJ won’t move folders/directories if they’re open in file viewer
    • WatchFolderPanel can’t assign directories that don’t exist, so ‘main’ has to be run before setting input/output dirs
    • Need a way to quit more elegantly if forcepoints don't trigger in Asylum
