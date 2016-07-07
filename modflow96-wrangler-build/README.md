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

1. Copy cyrus-wrangler-build directory from UT Box into Wrangler home directory.
Requires downloading to local system first, then scp files up to wrangler:

    $ scp /path/to/local/copy/modflow96-wrangler-build USERNAME@wrangler.tacc.utexas.edu:/home/NUMBER/USERNAME

2. Connect to wrangler:

    $ ssh USERNAME@wrangler.tac.utexas.edu

3. cd into cyrus-wrangler-build directory

    $ cd modflow96-wrangler-build

4. Make the build script executable:

    $ chmod +x modflow.wra.build

5. Run the build script:

    $ ./modflow.wra.build

6. Verify that you have a folder named modflw96.3_3

    $ ll

7. Change directories into the modflw96.3_3 folder:

    $ cd modflw96.3_3

8. Verify that there is an executable in the /bin directory:

    $ cd bin && ls bin

    (look for 'modflw96' )

9. Test running modflow:

    $ modflw96
    Enter the name of the NAME FILE:

    ** This means success.
    Press CTRL + C to halt the script.

10. Export modflow as an environment variable so you can use it from anywhere:

    $ export PATH=${PATH}:${PWD}/modflw96.3_3/bin
    (OLD COMMAND: $ export PATH=${PATH}:${HOME}/modflow96-wrangler-build/modflw96.3_3/bin)

11. Verify that the binary is now in the system path:

    $ echo $PATH

    Look for: .:/Path/To/Build/modflw96.3_3/bin appended to the output.

12. Verify modflow works from anywhere:

    $ cd 
    $ modflw96.3_3
    Enter the name of the NAME FILE:

    ** This means success.
    Press CTRL + C to halt the script.

13. Upload GAM files to your working directory on HPC system using scp command again.

14. Get an interactiove node to work in:

    $ idev

    This will eventually chnage your prompt from 'login' to 'c###-###' which means you are now working on a node.

15. Run your simulations!

16. Use scp to copy your output.dat files back to your local system as well.

___

