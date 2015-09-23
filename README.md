# keepass_autotype
A short helper script for keepass autotype on Linux

## Usage

Call this script as the global shorcut for autotyping in *keepass*. In the worst case it will auto-type if keepass is already running (as usual) but it will start ``keepass`` if not. If this doesn't work tweak the variables and paths defined at the beginning of the script. 


# The problem
*Keepass* (the mono based one) suggests setting a global shortcut for autotype. However the problem is that if keepass is not running when calling ``keepass --auto-type`` then you are out of luck. The program just ignores the key press.

## The idea for a solution.

This script tries to determine is keepass is running. If it is it just calls ``keepass --autotype`` otherwise it runs starts keepass by calling the command ``keepass`` but also setting the environment variable ``autotype=t`` for the subprocess. 

Now, keepass has some scripting ability programmed into it so one can write a trigger such as:

* When finished opening the database check if envirnment variable ``autotype`` is set to ``t`` if yes preform auto-type. 

* Disable trigger for this instance. This is needed to avoid autotyping every time the database gets open by keepass. The disabling actually is (or can be made to be) instance local so when restarting autotype the check gets carried out again.  


