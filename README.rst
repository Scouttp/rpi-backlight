rpi-backlight
=============

.. image:: https://api.travis-ci.org/linusg/rpi-backlight.svg?branch=master
   :target: https://travis-ci.org/linusg/rpi-backlight
   :alt: Travis CI status

.. image:: https://landscape.io/github/linusg/rpi-backlight/master/landscape.svg?style=flat
   :target: https://landscape.io/github/linusg/rpi-backlight/master
   :alt: Code health

.. image:: https://img.shields.io/github/issues/linusg/rpi-backlight.svg
   :target: https://github.com/linusg/rpi-backlight/issues
   :alt: Issues
   
.. image:: https://img.shields.io/pypi/v/rpi_backlight.svg
   :target: https://pypi.python.org/pypi/rpi_backlight
   :alt: Version
   
.. image:: https://img.shields.io/github/license/mashape/apistatus.svg
   :target: https://github.com/linusg/rpi-backlight/blob/master/LICENSE
   :alt: License

.. image:: https://img.shields.io/badge/docs-latest-blue.svg
   :target: https://rpi-backlight.readthedocs.io/en/latest/
   :alt: Documentation

.. image:: https://img.shields.io/website-up-down-green-red/http/shields.io.svg
   :target: https://linusg.github.io/rpi-backlight/
   :alt: Website

A Python module for controlling power and brightness of the official Raspberry Pi 7" touch display.
---------------------------------------------------------------------------------------------------

.. image:: https://raw.githubusercontent.com/linusg/rpi-backlight/master/docs/example.gif
   :alt: Example

Features
--------

- Change the display brightness **smoothly** or **abrupt**
- Set the display power on or off
- Get the current brightness
- Get the maximum brightness
- Get the display power state (on/off)
- Command line interface
- Graphical user interface


Requirements
------------

- A **Raspberry Pi** including a correctly assembled **7" touch display v1.1 or higher** running a Linux-based OS
- Python 2 or 3
- Optional: ``pygobject`` for the GUI, is likely to be already installed on a recent Raspbian

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

Open a terminal and run ``rpi-backlight`` as root.

.. image:: https://raw.githubusercontent.com/linusg/rpi-backlight/master/docs/cli.png
   :alt: Command Line Interface

GUI
***

Open a terminal and run ``rpi-backlight-gui`` as root.

.. image:: https://raw.githubusercontent.com/linusg/rpi-backlight/master/docs/gui.png
   :alt: Graphical User Interface

Todo
----

- Allow to set the brightness fading duration in ``set_brightness(value)``
- (*Create a really simple GUI in* ``pygobject`` *to change the display brightness, maybe just a scale/slider*)

  - Most of it done, but not tested across several Python versions and distros
  - Ensure it runs on the Pi under both Python 2 and 3

I would be happy if you can help shortening this todo-list!

External Links
--------------

- `Website <https://linusg.github.io/rpi-backlight/>`_
- `Travis CI: Build tests <https://travis-ci.org/linusg/rpi-backlight>`_
- `Landscape.io: Code health tests <https://landscape.io/github/linusg/rpi-backlight/master>`_
- `readthedocs.org: Documentation <https://rpi-backlight.readthedocs.io/en/latest/>`_

License
-------

The source code and all other files in this repository are licensed under the MIT license, so you can easily use it in your own projects.
