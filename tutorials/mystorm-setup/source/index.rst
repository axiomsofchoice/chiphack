
.. What's New in High-Performance Python? slides file, created by
   hieroglyph-quickstart on Sat Apr 30 21:13:03 2016.


MyStorm Setup
=============

| Dan Gorringe


The MyStorm Board
-----------------

.. figure:: mystorm.jpg

Installing the tools
--------------------

The instructions are all online:

* http://chiphack.org/chiphack-2017-install-linux.html
* http://chiphack.org/chiphack-2017-install-mac.html
* http://chiphack.org/chiphack-2017-install-windows.html

**Note** that the tools work fine on RaspberryPi.

Cloning the code from GitHub
----------------------------

You will want to access four repositories:

* The simple examples used on day 1
* Hatim Kanchwala's EDSAC code
* The reimagined EDSAC peripherals
* The MyStorm board design

::

   git clone https://github.com/embecosm/chiphack.git
   git clone https://github.com/librecores/gsoc-museum-edsac.git
   git clone https://github.com/embecosm/edsac-peripherals.git
   git clone https://gitlab.com/Folknology/mystorm.git

Your first design (Mac/Linux)
-----------------------------

Completed examples are in the ``cheat_sheet`` directory. We'll build the very
simplest of these to drive the red LED on the board.  First change into the
directory with the completed examples::

  cd chiphack/cheat_sheet

Then ``make`` the LED example::

  make led

This will synthesize the code in ``led/led.v`` to a bitstream in
``chip.bin``.

Your first design (Windows)
---------------------------

From ``cheat_sheet``, change to the ``led`` directory and copy in the parent PCF
file::

  cd led
  cp ..\blackice.pcf .

Then synthesize the LED example with ``apio``::

  apio build --size 8k --type hx --pack tq144:4k

This will synthesize the code in ``led\led.v`` to a bitstream in
``hardware\chip.bin``.

Uploading your design (Mac/Linux)
---------------------------------

For Linux::

  make SERIAL=/dev/ttyACM0 upload-linux

For Mac::

  make SERIAL=/dev/cu.usbmodem1421 upload-linux

You may need to use a different value for ``SERIAL`` depending on your
machine.

Uploading your design (Windows)
-------------------------------

Start up *teraterm*

* Select the serial option, then go to setup>serial.
* Delete the Baud rate option
* Set data as 8 bit, no parity, 1 bit stop and no flow control.
* Then file>send file navigate to hardware.bin
* tick the Binary option box and open

Your first design
-----------------

.. figure:: mystorm-led.jpg
