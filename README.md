			  Fluxoscope README
		Simon Leinen <simon.leinen@switch.ch>

Fluxoscope is a system for IP traffic accounting using Cisco
NetFlow(TM) v5 or v9 or compatible accounting data.

Copyright (c) 1997-2015 Simon Leinen  <simon.leinen@switch.ch>

Fluxoscope is free software: you can redistribute it and/or modify it
under the terms of the GNU General Public License as published by the
Free Software Foundation, either version 3 of the License, or (at your
option) any later version.

This program is distributed in the hope that it will be useful, but
WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.

Installation
============

1. Set up logical pathname translations.

The following logical pathname patterns should be defined to point to
source and configuration files:

  sysman:src;**;*.lisp
    Should point to the source files of the "sysman" SNMP package.

  fluxoscope:src;*.lisp
    Should point to the Fluxoscope source files.

2. Download, build and load the SNMP package ("sysman").

Download the source from
    http://www.switch.ch/misc/leinen/snmp/lisp/lisp-snmp.tar.gz

Uncompress them into the directory pointed to by the SYSMAN logical
pathname host.

Load sysman:src;defsys.lisp, compile and load the systems:

  If using MAKE:DEFSYSTEM:

    (mk:oos :sysman :compile)
    (mk:oos :snmp-agent :compile)

  If using Allegro Defsystem:

    (excl:compile-system :sysman)
    (excl:compile-system :snmp-agent)

3. Compile the Fluxoscope system.

Load fluxoscope:src;defsystem.lisp, compile and load the system:

  If using MAKE:DEFSYSTEM:

    (mk:oos :fluxoscope :compile)

  If using Allegro Defsystem:

    (excl:compile-system :fluxoscope)

4. Select or write an Aggregator specialized for your context.

5. Write a startup script that uses the Aggregator.

As an example, see `switch-init.lisp'.

6. Run Fluxoscope

The RUN function (see `start-stats.lisp') can be called to start a
NetFlow listener with a user-selectable set of "flow consumers".
