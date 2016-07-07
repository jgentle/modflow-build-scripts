# MODFLOW 96 Build Scripts for TACC HPC Systems

### MODFLOW 96 Wrangler Build Usage Notes
_2016.06.15_
_John Gentle_

___

Notes:

There are two scripts to build MODFLOW 96, one is optimized and one is not.
These instructions detail using the optimized build scripts.
In order to use the unoptimized build script, simply substitute he correct file name as follows:

    Wherever you see:  'modflow.wra.build'
    Replace it with:  'modflow.wra_noopt.build'

Do NOT run these in the same location.
To build the alternative version you need to start with a fresh modflow96-wrangler-build copy.

___

Usage Instructions:

1. Connect to the HPC system you want to use (submit password when prompted):

    > ssh USERNAME@HPC_SYSTEM.tacc.utexas.edu

2. Navigate to the $HOME directory in the HPC system you want to build modflow on:

    > cd $HOME

3. Download a copy of the build scripts fom github:

    > git clone git@github.com:jgentle/modflow-build-scripts.git

4. cd into the modflow-build-scripts directory

    $ cd modflow-build-scripts

5. cd into the folder where the scripts live:

    > cd modflow96-tacc-hpc-build

6. Make the build script executable:

    > chmod +x modflow.wra.build

7. Run the build script:

    > ./modflow.wra.build

8. Verify that you have a folder named modflw96.3_3

    > ll

9. Change directories into the modflw96.3_3 folder:

    > cd modflw96.3_3

10. Verify that there is an executable in the /bin directory:

    > cd bin && ls bin

    (look for 'modflw96' )

11. Test running modflow:

    > modflw96
    Enter the name of the NAME FILE:

    ** This means success.
    Press CTRL + C to halt the script.

12. Export modflow as an environment variable so you can use it from anywhere:

    > export PATH=${PATH}:${PWD}/modflw96.3_3/bin

13. Verify that the binary is now in the system path:

    > echo $PATH

    Look for: /Path/To/Build/modflw96.3_3/bin appended to the output.

14. Verify modflow works from anywhere:

    > cd 
    > modflw96.3_3
    Enter the name of the NAME FILE:

    ** This means success.
    Press CTRL + C to halt the script.

15. Upload GAM files to your working directory on HPC system using scp command.

16. Get an interactive node to work in:

    > idev

    This will eventually chnage your prompt from 'login' to 'c###-###' which means you are now working on a node.

17. Run your simulations!

    > modflw96 spring.nam

18. Use scp to copy your output.dat files back to your local system as well.

    > scp user_name@hpc.tacc.utexas.edu:/path/to/source/files/ /path/to/destination/for/files

___

