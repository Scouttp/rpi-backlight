rpi-backlight
=============

A Python module for controlling power and brightness of the official Raspberry Pi 7" touch display.
---------------------------------------------------------------------------------------------------

**WARNING: This comes with absolutely no warranty, do anything on your own risk!**

The code is very small and simple, but will be extended in the future for new features. Feel free to contribute!

Features:
---------

- Change the display brightness **smoothly** or **abrupt**
- Set the display power on or off
- Get the current brightness
- Get the maximum brightness
- Get the display power state (on/off)
- Command line interface
- Graphical user interface

.. image:: https://github.com/linusg/rpi-backlight/blob/master/docs/example.gif
   :alt: Example

Requirements
------------

- A **Raspberry Pi** including a correctly assembled **7" touch display v1.1 or higher**
- Python 2 or 3
- Optional: ``pygobject`` for the GUI

Installation
------------

- Install from PyPI using ``pip install rpi_backlight``, or
- clone this repository and ``python setup.py install``.

Note: You may need to edit the backlight rules file in order to run the code:

    sudo nano /etc/udev/rules.d/backlight-permissions.rules

insert the line

    SUBSYSTEM=="backlight",RUN+="/bin/chmod 666 /sys/class/backlight/%k/brightness /sys/class/backlight/%k/bl_power"


Usage
-----

API
***

Example in a Python shell::

    >>> import rpi_backlight as bl
    >>> bl.set_brightness(20)
    >>> bl.set_brightness(255)
    >>> bl.set_brightness(20, smooth=False)
    >>> bl.get_max_brightness()
    255
    >>> bl.get_current_brightness()
    20
    >>> bl.get_power()
    True
    >>> bl.set_power(False)

**NOTE: Code using** ``set_`` **functions of this library has to be run as root, e.g.** ``sudo python file.py`` **!**

CLI
***

.. image:: https://github.com/linusg/rpi-backlight/blob/master/docs/cli.png
   :alt: Command Line Interface

Open a terminal and run ``rpi-backlight`` as root.

GUI
***

.. image:: https://github.com/linusg/rpi-backlight/blob/master/docs/gui.png
   :alt: Graphical User Interface

Open a terminal and run ``rpi-backlight-gui`` as root.

**NOTE: This is currently experimental, but should work quite well.**

Todo
----

- Allow to set the brightness fading duration in ``set_brightness(value)``
- Create a really simple GUI in ``pygobject`` to change the display brightness, maybe just a scale/slider

  - Partially done, but only tested on Ubuntu 16.04 / Python 3.5
  - Make GUI more stable
  - Ensure it runs on the Pi under both Python 2 and 3

I would be happy if you can help shortening this todo-list!

License
-------

The source code and all other files in this repository are licensed under the MIT license, so you can easily use it in your own projects.
