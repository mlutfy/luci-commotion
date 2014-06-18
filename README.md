luci-commotion
==============

Commotion configuration pages for the LuCI web interface.

luci-commotion is selected as a default build option in Commotion-Router (https://github.com/opentechinstitute/commotion-router)


## Roadmap

### Version 1.2

  * [Import / Export functionality for Commotiond profiles](https://github.com/opentechinstitute/luci-commotion/issues/88)
  * re-runnable setup wizard
  * [Status-page auto-updating values](https://github.com/opentechinstitute/luci-commotion/issues/162)
  * [Updated Nearby Mesh devices](https://github.com/opentechinstitute/luci-commotion/issues/137)
  * Command Line Setup Wizard (Possibly not in this repo as it will not be luci-based.)
  * [Babel Integration](https://github.com/opentechinstitute/luci-commotion/pull/200)

### Version 2.0

  * lua-info plugin for less memory-intesive access to OLSR info
  * [mesh-agnostic network-viz](https://lists.chambana.net/pipermail/commotion-dev/2014-February/001761.html)

luci-theme-commotion
=======================

The LuCI Commotion Theme was designed for the Commotion Wireless Project's openwrt-based software and is included by default in the commotion-feeds package, which is called by the commotion-router setup script.

Design changes should follow the Human Interface Guidelines described on the main project site.

This theme appears as luci-theme-commotion in Commotion-Router's menuconfig options

## Links

* <a href="http://commotionwireless.net">Commotion Wireless Project</a>
* <a href="https://commotionwireless.net/developer/hig/introduction">Commotion Human Interface Guidelines</a>
* <a href="https://github.com/opentechinstitute/commotion-router">Commotion-Router source code</a>
* <a href="https://github.com/opentechinstitute/commotion-feeds">Commotion-Feeds source code</a>

Commotion-apps
==============

Commotion-apps contains a LuCI application portal for OpenWRT, as well as a script to check for new applications nearby on the network.

The LuCI application portal adds some pages to the Commotion-Router menu. The main page shows all local applications on the mesh that have been approved by the node administrator. There are also pages for creating an application, as well as administrator pages for approving/blacklisting apps and changing settings related to applications.

Commotion-apps is selected as a default build option in Commotion-Router (https://github.com/opentechinstitute/commotion-router).

Advertising applications
------------------------
Applications are advertised on a Commotion mesh network using Avahi/mDNS. Each application should have a `.service` file in the `/etc/avahi/services/` directory. The structure of the service file should follow this template:

    <?xml version="1.0" standalone='no'?><!--*-nxml-*-->
    <!DOCTYPE service-group SYSTEM "avahi-service.dtd">
    
    <!-- This file is part of commotion -->
    <!-- Reference: http://en.gentoo-wiki.com/wiki/Avahi#Custom_Services -->
    <!-- Reference: http://wiki.xbmc.org/index.php?title=Avahi_Zeroconf -->
    
    <service-group>
      <name replace-wildcards="yes">Service Name on %h</name>
    
      <service>
        <type>_https._tcp</type> <!-- _svc-type.sub-type._tcp|udp -->
        <domain-name>mesh.local</domain-name>
        <!--<host-name>%h.mesh.local</host-name>--> <!-- DON'T set hostname, because avahi will fail to resolve it when using mesh.local domain-->
        <port>443</port> <!--optional-->
        <txt-record>name=Example Application</txt-record>
        <txt-record>ttl=2</txt-record> <!--optional: how many hops away the service should be advertised-->
        <txt-record>uri=https://commotionwireless.net</txt-record> <!-- IP address or URL of service host -->
        <txt-record>type=collaboration</txt-record>
        <txt-record>type=circumvention</txt-record> <!-- each type should have its own txt-record -->
        <txt-record>fingerprint=FA7E03D576F9A6752194CFCBE402C455B7F0F8C8894F7C05F17ECE500D2DC648</txt-record>
        <txt-record>signature=E07B1282AE1601C334CEA861DF795D57D00603BA00D97F382720F4146DDCD4427973D171C89BCA0EAAF1D72E9EF0DB2367CE07BBFFF6FF27FF01F1DFBEB65D0B</txt-record>
        <txt-record>icon=https://exampleapplication.com/icon.png</txt-record>
        <txt-record>description=Commotion is an open-source communication tool that uses mobile phones, computers, and other wireless devices to create decentralized mesh networks.</txt-record>
        <txt-record>lifetime=86400</txt-record>
        <txt-record>version=1.0</txt-record>
        
      </service>
    </service-group>

Commotion Splash
================

luci-commotion-splash is an OpenWRT package that adds a LuCI web user interface for configuring the popular [Nodogsplash][] captive portal.

Commotion Splash is selected as a default build option in Commotion-Router (https://github.com/opentechinstitute/commotion-router).

Changelog
---------

7 May 2013: Release v1.0  
29 Aug 2013: Release v1.1.1  
28 Dec 2013: Release v1.2  

[Nodogsplash]: http://kokoro.ucsd.edu/nodogsplash/

commotion-dashboard-helper
==========================

Scripts and configuration to send data to a bigboard gatherer, along with LuCI interface for configuration.

Commotion Dashboard Helper is selected as a default build option in Commotion-Router (https://github.com/opentechinstitute/commotion-router).

##commotion-debug-helper

Commotion Debug Helper is a LuCI based bug collector for users to quickly gather relevant data for  OpenWRT router issues

Commotion Debug Helper is selected as a default build option in Commotion-Router (https://github.com/opentechinstitute/commotion-router).

commotion-lua-helpers
=====================

A set of lua "helper" modules for Commotion packages.


Commotion Lua Helpers are selected as a default build option in Commotion-Router (https://github.com/opentechinstitute/commotion-router)
