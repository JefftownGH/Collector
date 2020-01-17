# iLogic Collector


![Logo](Images/iLogicCollector128.png)

A powershell script that compiles multiple Visual Basic files into a single file for
use in Autodesk's Inventor iLogic scripting environment. It is intended to allow use
of external IDEs such as Visual Studio and support class or module-per-file coding
organization.

It is also useful when developing an Inventor Add-In and you want to perform testing
in the iLogic environment.  The script will collect any source code files within a
single directory that contains the proper tag in the first line and insert them into
a single iLogic file.

## Use

To use, include tags into the source code files that you want to collect.

* ``</iLogicCollector>`` : include this tag in the first line of each file you want to collect.
* ``</iLogicCollectorHeader>`` : Include this tag in the first line of header and main files. This will ensure the file is placed at the top of the collected file.
* ``<\IlogicCollectorHide>`` : include this line after any line of code to comment out that line at collection time.  Use this for module wrappers that help VS, but need to be removed for iLogic to work properly.

When ready to compile, run this powershell script to combine the files into a single file.
If running from the command line, you may need to issue the command like so if permissions
issues prevent running the powershell script.

``powershell -ExecutionPolicy ByPass -File .\iLogicCollector.ps1``

The current directory name is used as the file name with an .iLogicVB extension.  This script will overwrite any file with that same name.

## Example

See the /Example/ folder for a simple set of code files that illustrates iLogic Collector
in action. The Example.iLogicVB file has been generated by the iLogicCollector.ps1 script.
The files "ExporterClass.vb", "Main.vb", and "SphereClass.vb" contain the iLogic Collector
tags that tells the script what to do.
