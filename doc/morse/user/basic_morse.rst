Getting started: basic MORSE usage 
==================================


Starting MORSE
--------------

Use the ``morse`` executable program, with the corresponding option, to start
a simulation.

To verify that your installation and configuring of MORSE is correct, execute::

  $ morse check

To start the simulation right away, do::

  $ morse run <filename>

Where ``filename`` can be a Blender file or a Python script that uses the
:doc:`Builder API <../user/builder>` to describe a simulation scenario.

To load the simulation scene in the Blender interface::

  $ morse edit <filename>

This will give you the chance to modify the scene before pressing :kbd:`p` to
start the simulation.

Additionally, the following options can be given to the MORSE executable:

- **-h** / **--help**: print an explanation of the available options and exit
- **-b BASE** / **--base BASE**: in Edit mode, specify a Blender scene
  used as base to apply the Python script
- **--name NAME**: when running in multi-node mode, sets the name of this
  node (defaults to current hostname)
- **-c** / **--color**: uses colors for MORSE output.
- **--reverse-color**: uses darker colors for MORSE output.
- **-g GEOM** / **--geometry GEOM**:
  sets the simulator window geometry. Expected format:
  ``WxH`` or ``WxH+dx,dy`` to set an initial x,y delta (from
  lower left corner).
- **-v** / **--version**: returns the current MORSE version


MORSE controls
--------------

A simulation in MORSE is executed using Blender's Game Engine mode. When
in this mode, Blender's button panels are disabled and the controls
change.  When running ``morse edit <filename>``, it is recommended to switch
the Blender 3D View window to full screen before starting a simulation. Press
:kbd:`Ctrl-Up` when the mouse is over a window to toggle it to full screen and
back.

Simulation camera control
+++++++++++++++++++++++++

The default MORSE scene, as well as most of the provided scenario files,
contain an object called **CameraFP**.  This allows the user to control the
view of the scene during the simulation using the mouse and keyboard,
in the same way as in a First Person Shooter game. The camera can be moved around
using:
    
- :kbd:`w`/:kbd:`z`, :kbd:`s` to move forward and backward
- :kbd:`a`/:kbd:`q`, :kbd:`d` to move left and right
- :kbd:`r`, :kbd:`f` to move up and down

The direction the camera points in is controlled by the mouse. Hold down the
:kbd:`Ctrl` key while moving the mouse.

It is possible to adjust the speed of the camera's movement by selecting the
**CameraFP** object in the scene, and adjusting the camera object's game
properties: **Sensitivity** for the mouse, and **Speed** for the keyboard.

Standard keyboard functions
+++++++++++++++++++++++++++

The following key bindings are predefined in any simulation scene

- :kbd:`p` key: start the simulation (start the Game Engine)

- :kbd:`h` key: show an on screen display with this list of keyboard functions

- :kbd:`v` key: toggle the display of a "picture-in-picture" screen that can
  display the image viewed from a specified camera. The camera to display is
  determined from the :doc:`Builder API <../user/builder>` Environment class'
  **select_display_camera** option.

- :kbd:`Esc` key: stop and exit the simulation (cleaning up the connections)

- :kbd:`F7` key: move the camera **CameraFP** near to the robot

- :kbd:`F8` key: reset the position and orientation of the **CameraFP** to its
  initial state

- :kbd:`F9` key: cycle through the camera views of all the scene's
  Blender camera objects. This includes the cameras mounted on robots,
  as well as the default **CameraFP**

- :kbd:`F11` key: reset all objects to their original positions at the start of
  the simulation

.. warning::  
  There is a bug in the code, which will make any forces acting on an
  object continue to be active when the position is reset. This can cause an object to start
  rotating or moving for no apparent reason.

- :kbd:`F12` key: emergency exit from the simulation, without clean up. Useful
  when the :kbd:`Esc` key does not make the simulation finish (generally happens
  when the simulation could not properly initialise).

.. note::  
  If this doesn't work either, switch to the command terminal where MORSE was
  started and type: :kbd:`Ctrl-\\`.  This will kill Blender.
