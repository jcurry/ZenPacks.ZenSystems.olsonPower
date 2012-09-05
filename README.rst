==============================
ZenPacks.ZenSystems.olsonPower
==============================


Description
===========

Provides support for Olson Power meters gathering performance information for voltage, current, power, energy and temperature. 
These are rather minimal devices that only support a very small subset of SNMP MIB-2. They also deliver performance data as 
strings rather than in a numeric format so a command script is used to gather and convert data.

This ZenPack is Zenoss 3 and Zenoss 4 compliant.

Components
==========

    * The ZenPack adds the following new Device Class

        * /Devices/Power/Olson but this is not a new object type :
     
    * The device class has no new component types
     
    * Modeler plugins are:  
     
        * OlsonNewDeviceMap   
            * Gets IP address and MAC address with enterprise-specific MIB as this device doesn't support those parts of MIB-2
            * Generates an interface for those IP / MAC addresses 
        * OlsonPowerMap   
            * Gathers Hardware and Software manufacturer and product
            * Serial number 
    * A device template olson_power provides: 
        * Data Sources   
            * A command data source olsonPower that runs the  getPowerValues.sh script in the ZenPack's lib directory. It delivers the following Data Points (of type GAUGE) 
                * Current
                * Energy
                * Power
                * Temp
                * Voltage 
        * No thresholds are provided
        * Graph Definitions   
            * Current
            * Energy
            * Power
            * Temp
            * Voltage 
    * Event classes are provided for:  
        * /Power
        * /Power/Olson with mappings for:
            * Current high
            * Current low
            * Voltage high
            * Voltage low
            * Temperature high

* The Olson manufacturer is provided.
* The Olson-9016-V01 MIB is provided.


Requirements & Dependencies
===========================

    * Zenoss Versions Supported: 3.x and 4.x
    * External Dependencies: The Olson-9016-V01 MIB needs to be available on target devices 
    * ZenPack Dependencies:
    * Note that the standard device class /Power needs to exist.  If not, recreate it.
    * Installation Notes: zenhub and zopectl restart after installing this ZenPack.
    * Configuration: 

Download
========
Download the appropriate package for your Zenoss version from the list
below.

* Zenoss 3.0+ `Latest Package for Python 2.6`_
* Zenoss 4.0+ `Latest Package for Python 2.7`_

Installation
============
Normal Installation (packaged egg)
----------------------------------
Copy the downloaded .egg to your Zenoss server and run the following commands as the zenoss
user::

   zenpack --install <package.egg>
   zenhub restart
   zopectl restart

Developer Installation (link mode)
----------------------------------
If you wish to further develop and possibly contribute back to this 
ZenPack you should clone the git repository, then install the ZenPack in
developer mode::

   zenpack --link --install <package>
   zenhub restart
   zopectl restart

Configuration
=============

This ZenPack was tested with Zenoss 3.1 and Zenoss 4.2 against Olson 9016 V01 devices

Change History
==============
* 1.0
   * Initial Release
* 1.1
   * Some updates for extra debug
* 1.2
   * Transferred to new github methods
* 1.3
   * Remove energy_days template
* 2.0
   * Tested for Zenoss 4

Screenshots
===========
|olsonPower|


.. External References Below. Nothing Below This Line Should Be Rendered

.. _Latest Package for Python 2.6: https://github.com/downloads/jcurry/ZenPacks.ZenSystems.olsonPower/ZenPacks.ZenSystems.olsonPower-1.3-py2.6.egg
.. _Latest Package for Python 2.7: https://github.com/downloads/jcurry/ZenPacks.ZenSystems.olsonPower/ZenPacks.ZenSystems.olsonPower-2.0-py2.7.egg


.. |olsonPower| image:: http://github.com/jcurry/ZenPacks.ZenSystems.olsonPower/raw/master/screenshots/olsonPower.jpg

                                                                        

