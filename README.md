## ImageSweep

ImageSweep is a python script used to remove unused drawables from your application. During the build process, all indexed .pngs inside of 'drawable' folders get crunched so that their size is much much smaller; However, even unused images get bundled with your apk. This means that your apk is potentially much much larger than it needs to be even after compression.

##Usage
		 python image_sweep.py project_src_directory

Where project_src_directory is the relative or absolute file-path where your source code lives. Make sure the chosen directory contains ALL of your source code / AndroidManifest.xml, but none of the libraries you've included (the script auto-determines where the /res folder is and libraries can potentially break that).

##Requirements
This script has been tested on Python 2.7 and Python 3.0.
Works with all versions of Android.

##How It Works
At a high level, the script scans each file and does a search for 'R.drawable.' or "@drawable/". Afterwards it checks each resource inside of drawable folders to see if it was referenced anywhere.


## How Well Does it Work
In the 'Canvas for Android' project, we were able to cut about 46% off the raw apk size and 26% off the installed app size. It works best as a supplement to ProGuard.

##Warnings!
* This script only works for top-level projects that aren't referenced from other projects.
* The files deleted **cannot** be reversed. **Please only run this script on projects located in source control.** Just in case.
