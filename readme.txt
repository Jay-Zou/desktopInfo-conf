Desktop Info
by Glenn Delahoy
(C) Copyright 2005-2018
All rights reserved

Web Site: www.glenn.delahoy.com


Description
-----------
This little application displays system information on your desktop. Looks 
like wallpaper but stays resident in memory and updates in real time. Perfect 
for quick identification and walk-by monitoring of production or test server 
farms or any computer you're responsible for. Everything is customisable 
(nearly).
 
License Agreement
-----------------
This software is distributed free of charge. It may be used as many times as 
you like, for as long as you like, in a domestic or corporate environment. You 
may copy and distribute copies of this program provided that you keep all 
original documentation including this readme.txt file with copyright notice 
and disclaimer of warranty intact. You may not charge money or fees for the 
software product to anyone except to cover distribution costs.
 
Warranty
--------
This program is provided "as is" without warranties of any kind, either 
expressed or implied, including, but not limited to, the implied warranties of 
merchantability and fitness for a particular purpose. The entire risk as to 
the quality and performance of the program is with you. Should the program 
prove defective, you assume the cost of all necessary servicing, repair or 
correction. In no event will any copyright holder be liable to you for 
damages, including any general, special, incidental or consequential damages 
arising out of the use or inability to use the program (including but not 
limited to loss of data or data being rendered inaccurate or losses sustained 
by you or third parties or a failure of the program to operate with any other 
programs).
 
Technical Support
-----------------
No guarantees whatsoever are implied that technical support will be provided or
that technical support, when provided, will be accurate. This software is
basically unsupported and supplied on an as-is basis. (Try the web site above.)

32 Bit
------
This program is a 32 bit Windows application.  It should run fine in any 64 
bit environment with some restrictions. There will not be a native 64 bit 
version any time in the foreseeable future.

Usage
-----
Just run it. You can kill it via the right click context menu or from Task 
Manager. Open the desktopinfo.ini file or select Configuration from the right 
click context menu and adjust each item in the items section to control 
visibility, refresh times, colors and other properties. The display updates 
itself automatically when you save the ini file.

Configuration
-------------
There is no configuration program. Options are set by modifying the ini file 
in a text editor such as Notepad. You can access the configuration from the 
right click context menu or directly using File Explorer. The ini file has two 
sections: Options and Items. The Options section has global options to control 
the size, position etc. The Items section controls each individual display item.
 
The included ini file shows all the available options and items. The included
language files match the ini file.

Options
-------
Display values are relative to the primary display so if you have a multi 
monitor display, you may need to specify negative values or positive values 
outside of the range of your primary display for any of these depending on the 
display arrangement. Here are the rules for the position options:

     if left is specified, it is left aligned
     if right is specified, it is right aligned
     if neither left or right, it is left
     if both are specified, it is left
     if top is specified, it is top aligned
     if bottom is specified, it is bottom aligned
     if neither top or bottom, it is top
     if both are specified, it is top
     if font size is not specified, it is 8
     if font size is less than 6, it is 8
     if width is not specified, it is half the primary monitor width
     height is always the number of items

column1width            The width of column 1. -1 is automatic, 0 will
                        effectively eliminate the column allowing the data
                        column to occupy the whole space.
centerv                 Center vertically. 1=centered, 0=not centered.
centerh                 Center horizontally. 1=centered, 0=not centered.
fontface                The name of the font.
fontsize                The size of the font.
cleartype               Enables/disables ClearType for the font.
ssfontsize              The font size in screen saver mode
formcolor               Background color
transparency            Background transparency. 0 is opaque, 100 is totally
                        transparent.
contextmenu             Enables/disables the right click context menu.
allowdrag               Enables/disables the ability to drag the form. If the
                        /f option is used the form is always draggable.
offset                  Enables/disables the display offset of the network
                        adapter and fixed disk sub-items.
language                File name containing language specific display text.
inimonitortime          How often to check for desktopinfo.ini changes.
log                     Write debug information to the specified log file.


Colors
------
Colors are specified as a six character bgr (reverse rgb) hexadecimal number. 
Think of this number as divided into three parts, each part is a two digit 
number. The first two digits represent the level of blue, the second represent 
the level of green, the third two represent the level of red. Each element has 
a range of 00-ff (or 0-255 in decimal). ff0000 is blue, 00ff00 is green, 
0000ff is red. ffffff is white (all color elements at maximum), 000000 is 
black (all color elements are off).

You can set each color element to any value between 00 and ff. Half way 
between fully off and fully on would be 80. If all three were set to half way, 
808080, you would have a gray (grey) color.  

If an item color is not defined it will take on the color of the previous 
item.  In this way you can set the color for a block of items once for the 
first item and all successive items will be the same.

Items
-----
The items section in the ini file controls the order and state of each info 
item. Each item contains a comma delimited list of key:value pairs.

 key               value
 ---               -----
 active          : A value of 0 is off, 1 is on, 2 is on and hidden
 interval        : The refresh interval in seconds where 0 means never refresh
                   after the first time
 lid             : Language id. This is the id used to reference text in the
                   language files.
 color           : A bgr value as described above. If not specified, the item
                   takes the color of the previous item.
 chart           : Chart type to display where 0 = no chart, 1 = bar chart,
                   2 = line chart. See below for items that have charts.
 threshold       : The value where the item text will change color
 tcolor          : The new text color when the value reaches the threshold
                   value
 style           : Font style where b = bold, i = italic, u = underline,
                   w = full width underline
 offset          : For network items, a value of 0 is off, 1 is on
 count           : For multi items, sets the maximum number of items displayed
 activeonly      : For network adapters, shows only active adapters
 csv             : Output data to a csv file
 csvdatatype     : 0=raw data, 1=formatted data
 text            : Alternative column 1 description text. You should use the 
                   language file instead of this option.
 set             : Save the display output to the given user variable
 display         : Template for the item display
 
There may be other key:value pairs specific to individual items noted later.

The visibility of each item is controlled by the 'active' value. If the active
value of an item is set to '1' the item will be visible. If the active value is
set to '2' the item will be active (ie collecting data) but not visible.  You
can then make it visible by selecting the right click menu 'Show Hidden Items'
option. Child items for NETWORKADAPTER and FIXEDDISK will be set hidden if the
parent item is hidden.

An example is:

DATETIME=active:1,interval:1,color:ffffff

where the datetime item is active, refreshed every second and the color is
white.

CPU=active:1,interval:2,color:0000ff,chart:1,style:b

is active, refreshed every two seconds, the color is red, chart number 1 is
displayed and the font style is bold.

If an item does not have a chart, the chart value is ignored. If you don't
specify an item at all, it will not display. A better idea is to set active to
0.

Some items such as network adapter, fixed disk control all items
of that class. For example if you switch on fixed disk, all detected fixed
disks are displayed including most usb disks.

The following items return more than one value. Use replaceable parameters in
the display template property to display these values. See the formatting 
section later for more information and the ini file for examples.

Item              %1                %2               %3               %4               %5               %6               %7               %8
--------          --------          --------         --------         --------         --------         --------         --------         --------
ALLIPADDRESS      ip address        subnet mask      subnet class
CPU               cpu               kernel
BOOTTIME          day of week       date             month            year             hours            minutes          seconds
DATETIME          day of week       date             month            year             hours            minutes          seconds
DISKIO            reads per sec     writes per sec   queue size
FIXEDDISK         drive             volume           used space       free space       total size       size available   percent used     percent free
IPADDRESS         adapter ip        subnet mask      subnet class     mac address
NETPACKETS        packets rcvd      packets sent
NETPSACKRETSRATE  packets rcvd /sec packets sent / sec
OEMINFO           manufacturer      model
PAGEFAULTS        total faults      hard faults
PAGEFILE          used              total            percent used
PHYSICALRAM       used ram          total ram        percent used ram
PROCESSMEM        working set size  page file usage
TOPPROCESSCPU     process name      process id       percent
TOPPROCESSMEM     process name      process id       bytes
TOPPROCESSPF      process name      process id       page faults
UPTIME            days              hours            minutes          seconds
UTCTIME           hours             minutes          seconds
VIRTUALMEMORY     used ram          total ram        percent used ram

Each custom WMI item will have as many replaceable parameters as there are
properties in the result set.

All other items will return a single value. If no display template property is 
specified for an item, the first value will be displayed. In other words,
   display:%1
is the default. For WMI, you must always specify the display.

Example: the CPU item returns two values: cpu and kernel. To display these use
%1 for the first value and %2 for the second value. You can add any other text 
to the display.
  display:Tot: %1% Krnl: %2%
Will display something like:
  Tot: 5% Krnl: 2%
  
If you want to use a comma in a text or display property, you must precede it
with a backslash.

Incorrect Use Of A Comma
  display:Receive:%1 bps, Transmit:%2 bps

Correct Use Of A Comma
  display:Receive:%1 bps\, Transmit:%2 bps

Formatting Numbers
------------------
Any item that displays a number can be formatted in the 'display' template 
property. You specify the replaceable parameter for the value you want (see 
the table above) and follow it with the number format option. The general form 
of the number format is:

  %1[w.pt]

This is the replaceable parameter representing the value you want to display 
immediately followed by exactly four characters inside square brackets. The 
first character 'w' is a single digit that defines the maximum width of the 
number. The second character is a dot. The third character 'p' is a single 
digit that defines the precision of the number. That is, the number of places 
after the decimal point. The fourth character 't' defines the type of number.

The three general number types are:
  d = decimal   w = minimum width left padded with zeros, p=not used
  f = float     w = minimum width left padded with spaces, p=decimal places
  n = float     same as 'f', commas inserted for thousands

In this case, decimal means integer, a whole number, float means a number that
may not be a whole number.

So a simple example is:
  display:%1[3.0d]
This displays the first value with no decimal place, a minimum 3 characters
wide, left padded with zeros. eg "005"  or  "016" or "000" or "83738"

Example:
  display:%2[5.0d]
This displays the second value with no decimal place, a minimum 5 characters
wide, left padded with zeros. eg "00040" or "00597" or "00000"

Example:
  display:%3[4.1f]
This displays the third value with 1 decimal place, a minimum 4 characters
wide, left padded with spaces. eg "12.5" or " 9.0" or " 0.1"

Example:
  display:%1[7.0n]
This displays the first value with no decimal places, a minimum 7 characters
wide, commas inserted for thousands, left padded with spaces. eg "123,456" or
"  3,654" or "     67"

Transforming Numbers
--------------------
Sometimes it's useful to change a number from thousands of things to 
kilothings or megathings or gigathings. This is usually bytes but it doesn't 
have to be. Formatting types are available to help transform these values.  
These also follow the rules for the 'f' number type. Width excludes the units 
in the case of 'b' or 'B'.

Note: There is a difference between binary bytes and decimal bytes. Binary 
bytes are powers of 2. So a kilobyte is 1024 bytes. Decimal bytes are powers 
of 10. So a kilobyte is 1000 bytes. Make sure you choose the correct transform 
option for the data. For example, most hard drive manufacturers quote their 
drive size as decimal bytes, Windows quotes memory in binary bytes.

See also: https://en.wikipedia.org/wiki/Kilobyte

In the following table, binary transforms use the lower case number type, 
decimal transforms use the upper case number type.

  k K : convert to kilo, w = minimum width left padded with spaces, p=decimal places
  m M : convert to mega, w = minimum width left padded with spaces, p=decimal places
  g G : convert to giga, w = minimum width left padded with spaces, p=decimal places
  t T : convert to tera, w = minimum width left padded with spaces, p=decimal places
  b B : automatically convert, w = minimum width left padded with spaces, 
      p=decimal places, append unit

Example:
  %3[1.0k]
Displays the third value, binary converted to kilothings, no decimal places, a 
minimum of 1 character wide. eg "4" or "0" or "4567"

Example:
  %3[3.1M]
Displays the third value, decimal converted to megathings, 1 decimal place, a 
minimum of 3 characters wide.  eg "4.1" or "12.0" or "1483.6" or "0.5"

Example:
  %3[3.1b]
Displays the third value, binary converted automatically, 1 decimal place, a 
minimum of of 3 characters wide, unit appended. eg "6.1Ki" or "6.5Mi" or "1.1Gi"

If that was a decimal transform:
  %3[3.1B]
Displays the third value, decimal converted automatically, 1 decimal place, a 
minimum of of 3 characters wide, unit appended. eg "6.1K" or "6.5M" or "1.1G"

You add your own 'thing' after the number. Example:
  %3[3.1b]B
Displays the third value, binary converted, "6.1KiB"

or
  %3[3.1B]B
Displays the third value, decimal converted, "6.1KB"

Formatting Dates
----------------
The following can be used to help format dates:

  [ddd]      = short day name
  [dddd]     = long day name
  [mmm]      = short month name
  [mmmm]     = long month name
  [yy]       = last two digits of the year
  [yyyy]     = four digit year

Example:
  %1[ddd]
The first value is the day of the week.  It can be displayed as a normal number
or formatted to show the short day name.  eg "Mon" "Tue"

Example:
  %1[dddd]
The day of the week can be displayed as a long day name. eg "Monday" "Tuesday"

Example:
  %1[dddd] %2 %3[mmmm] %4[yyyy]
This will display the first four values of DATETIME. eg "Thursday 6 September 2018"

Example:
  %1[ddd] %2 %3[mmm] %4[yy]
This will display DATETIME as "Thu 6 Sep 18"

Formatting Times
----------------
If you want a basic 24 hour display, the regular number format would work:
  %5[1.0d]:%6[2.0d]:%7[2.0d]
Will display something like "9:24:45" or "13:15:01"

To format a 12 hour display there are a few additional format options:

  [1.0a]      : convert the hour to 12 hour, ie apply this to the hour value
                and any value from 13 to 24 is reduced by 12
  [2.0p]      : show 'am' or 'pm' depending on the hour in the value
  [2.0P]      : show 'AM' or 'PM' depending on the hour in the value

Example:
  %5[1.0a]:%6[2.0d]:%7[2.0d] %5[2.0P]
This will display DATETIME as "9:24:45 AM"  or "1:15:01 PM". Notice that the 
last parameter is the hour (%5) but in this case is being used to decide how to 
display the AM or PM.

Example:
  %5[1.0a]:%6[2.0d]:%7[2.0d] %5[2.0p]
This will display DATETIME as "9:24:45 am"  or "1:15:01 pm"

Formatting Booleans
-------------------
Boolean values can have 1 of only 2 possible values: 1 or 0, true or false, 
yes or no, on or off etc. In WMI land, booleans tend to be displayed as True 
or False. Sometimes it makes sense to display these values using normal 
everyday language. To convert boolean values into words use the following 
format:

  [b:true:false]

In the place of the word 'true', you put whatever word you want. The same with the
word 'false'. The correct word will be displayed based on the value of the
boolean number.

In the following example, Win32_ComputerSystem has two properties relating to
daylight savings. These can be displayed meaningfully thus:

Example:
  display:Enabled: %EnableDaylightSavingsTime%[b:Yes:No]\, In Effect: %DaylightInEffect%[b:Yes:No]
This will display something like "Enabled: Yes, In Effect: No"

Charts
------
Where an item has two values such as NETPACKETSRATE and DISKIO, the bar chart
value will be the sum of the two values. On line charts the first value
takes the color configured for that item, the second value takes a standard
brown/orange/tan kind of color. Any item that shows a value that can move up
and down such as CPU, CPUTEMP, BATTERY, DISKIO etc will have both bar and line
charts available. Check the ini file. Try adding a chart if it's not there on
the item.

Thresholds
----------
Items that display values may be configured to change color when that item
reaches a given value. It could be an absolute value such as PAGEFAULTS,
DISKQUEUE, it could be a percent such as CPU, PHYSICALRAM or a rate such as
NETPACKETSRATE, DISKIO.

Filters
-------
The filter option is used to reduce the result set of certain items.

    NETWORKADAPTER Defines which adapters will be displayed. It should be the
                   last option on the line and consists of the keyword "filter:"
                   followed by include options prefixed with a + (plus sign) and
                   exclude options prefixed with a - (minus sign).

                   NETWORKADAPTER=active:1,interval:30,filter:+PCI+wireless-virtual

                   This example will show all adapters that contain the keywords
                   "PCI" and "wireless" and will exclude adapters that contain
                   the keyword "virtual".

    FIXEDDISK      Defines which drives will be displayed. To show only drive C:
                   add "filter:C:". To show drives C: and E: add "filter:C:E:".
                   It's case sensitive.

                   FIXEDDISK=active:1,interval:10,filter:C:E:

File Monitors
-------------
Desktop Info can monitor files and folders for changes to size, write time or
version number. Add one or more items called FILE anywhere in the items section.
In addition to the normal item values, add the following values:

   text     Display name of the item
   type     Monitor type (text, size, time, version)
   file     File or folder name

The text type will display the first line of the given text file when the last
write time changes. This might be useful for monitoring semaphore or progress
files created by batch processes. The size type will display the file size when
the size changes. The time type will display the last write and access times
when either changes. The version type will display the file version resource
string when the file changes.

This monitor will work for local and network files and folders. If the file
or directory does not exist, the display will show "<N/A>". When monitoring
a directory make sure there is no trailing backslash.

This example displays the contents of the given file whenever it changes:

FILE=active:1,interval:10,type:text,text:Status,file:c:\temp\semaphore.txt

This example shows the executable version number whenever it changes:

FILE=active:1,interval:10,type:version,text:Desktop Info,file:d:\development\desktopinfo\desktopinfo.exe

Registry Monitors
-----------------
Desktop Info can monitor registry keys or values for changes. The results are
returned in the %1 and %2 replaceable parameters. %1 is the value required, %2
is the date/time it last changed. 

If you specify a key, %1 is not used. You can also choose to monitor just that 
key or the entire tree starting at that key.

Add one or more items called REGISTRY anywhere in the items section. In addition
to the normal item values, add the following values:

   text         Display name of the item
   tree         1 to monitor the tree, 0 to monitor only the key specified
   key          The key or key and value to monitor

The following example will monitor a value in the Run key.

REGISTRY=active:1,tree:0,text:Run Key Test,key:HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Run\Test

If the registry key contains a comma, precede it with a backslash.

Invalid Key
  HKEY_LOCAL_MACHINE\SOFTWARE\Apple Computer, Inc.

Valid Key
  HKEY_LOCAL_MACHINE\SOFTWARE\Apple Computer\, Inc.

Event Log Monitors
------------------
Desktop Info can monitor event logs for changes. Add one or more items called
EVENTLOG anywhere in the items section. In addition to the normal item values,
add the following values:

   text     Display name of the item
   log      The name of the event log to monitor

The following example will monitor the system event log:

EVENTLOG=active:1,interval:10,text:System Events,log:System

Data Logging
------------
You can log individual items by adding 'csv:filename'. For example,
"csv:c:\cpu.log".  This outputs the data to a csv formatted file where the cells
are enclosed in quotes and separated by commas and the first row contains column
identifiers.

The data is output in it's raw form.  You can output the formatted data by
adding 'csvdatatype:1'.

This example outputs raw data to a file in the root directory:
   PAGEFAULTS=active:1,interval:10,csv:\pagefaults.csv

This example outputs formatted data:
   PAGEFAULTS=active:1,interval:10,csv:\pagefaults.csv,csvdatatype:1

Fixed Text
----------
The TEXT item allows you to put any fixed key/value text on the display. 
Useful for any kind of internal identification or other static information 
such as a machine's context, use, operator, tech support info. It can also be 
used to display a number of user variables on one line.  The value in the 
'text' property goes on the left column, the value in the 'display' field goes 
in the right column.

The COMMENT item allows you to put any fixed text on the display. There is a
single output property called 'text' which spans both columns. You can use this
to create a blank line to help separate blocks. Just create a COMMENT item with
no text.

Hardware Sensors
----------------
Hardware sensors are problematic. The problem is manufacturers don't expose 
them to the operating system in a standard way. Windows provides standard WMI 
properties to be used by manufacturers but almost nobody implements them. 

The only other approach is to laboriously study each manufacturer's hardware  
sensor implementation and write specific code for each one.  This is not a 
path I wish to follow, better to leave that to a dedicated team. There are a 
number of tools available to read hardware sensor information such as 
CoreTemp, Open Hardware Monitor, HWMonitor, Speedfan, Real Temp, Hardware 
Sensors Monitor, OCCT. I have implemented the CORETEMP item and there may be 
others down the track.

CPUTEMP
-------
This item uses the standard WMI method for retrieving cpu temperature.  If the 
hardware manufacturer has implemented it and you run Desktop Info as 
Administrator then it may work but more than likely it will not.

CORETEMP
--------
This item reads the shared memory area of Core Temp. This tool must be 
running, visible or hidden, for Desktop Info to interact with it. Desktop Info 
does not need to be run as administrator using this approach. Best of all it's 
much more likely to succeed on any computer than the WMI method. 

Get Core Temp at: http://www.alcpu.com/CoreTemp/       
Hint: Pay attention during the installation process!
 
OEM Information
---------------
Your mileage will vary for oem information. Desktop Info reads the
OEMInformation registry key. Because of the 64 bit registry redirection done
for 32 bit applications, the information needs to exist in the Wow6432Node
branch. On my Asus, for example, the oem information exists only in the 64
branch, not the 32 bit branch. I can't bypass this redirection so it will either
work or not. OEMINFO displays Manufacturer and Model from OEMInfo.ini if
available or the OEMInformation key in the registry if available. OEMPRODUCT
displays Name and IdentifyingNumber from the WMI Win32_ComputerSystemProduct
key if available.

IP Addresses
------------
There are two ways to display an IP address. The first method is IPADDRESS which
is dependant on NETWORKADAPTER. That is, you switch on NETWORKADAPTER and
IPADDRESS then for each adapter you will have one or more IP addresses listed
in the IPADDRESS item. The second method is ALLIPADDRESS which does not depend
on NETWORKADAPTER. This allows you to switch off the adapter item and just
show the IP address. You will see all IP addresses for all active adapters.

Custom WMI Queries
------------------
You can add items to show the results of a simple WMI select query using the WMI
item.

     text         display text on the left column
     namespace    WMI namespace such as 'root\wmi' or 'root\cimv2'
     query        the wmi class and optional where clause but NOT the select
                  clause (this is implied)
     set          save the display output to the given user variable
     display      template containing the text to display including any returned 
	              values. Returned values are indicated by enclosing a wmi 
				  property name in % signs.  eg a bios property, SerialNumber, 
				  is indicated as %SerialNumber%. This is replaced by the actual 
				  value returned by the wmi query.

You can put any text in the display template property. Because there is an 
implied "select * from ", all properties are returned so you can include as 
many properties as you like in the display option.

Example:
  WMI=active:1,interval:0,text:Serial Number,namespace:root\cimv2,query:Win32_Bios,display:%SerialNumber%

A Network example:
  WMI=active:1,interval:5,text:Wifi bytes rcvd/sec,namespace:root\cimv2,query:Win32_PerfFormattedData_Tcpip_NetworkInterface where Name like "%Wireless%",display:%BytesReceivedPersec% bytes per sec

This one displays multiple values from the wmi query with added text:
  WMI=active:1,interval:5,text:Wifi Traffic,namespace:root\cimv2,query:Win32_PerfFormattedData_Tcpip_NetworkInterface where Name like "%Wireless%",display:Rcvd: %BytesReceivedPersec% Sent: %BytesSentPersec% bytes per sec

In the where clause, strings should be quoted:
  query:Win32_PerfFormattedData_Tcpip_NetworkInterface where Name="Atheros"

The where clause can also include the 'like' keyword with wildcards:
  query:Win32_PerfFormattedData_Tcpip_NetworkInterface where Name like "%Wireless%"

You can add the NOT key to exclude rows from the result. It goes before the
property in question thus:
  query:Win32_PerfFormattedData_Tcpip_NetworkInterface where not Name like "%Wireless%"

In this example, WMI doesn't have a single query that returns the screen
resolution and color depth so we run two queries and combine the output. The 
first query returns the color depth and stores it in a user variable (see below). 
The second query returns the resolution and displays it along with the previous 
user variable.
  WMI=active:2,interval:0,text:Screen BPS,namespace:root\cimv2,query:Win32_DisplayConfiguration,set:BitsPerPel,display:%BitsPerPel%
  WMI=active:1,interval:0,text:Screen,namespace:root\cimv2,query:Win32_DesktopMonitor,display:%ScreenWidth%x%ScreenHeight%x%BitsPerPel%

You can also append the number formatting as described earlier. You should make
sure the selected format matches the type of value you are trying to format.

WMI Explorer is a nice easy tool to explore the WMI system.
http://www.ks-soft.net/

User Variables
--------------
User variables are a way to store data and text so that it can be used later.
There are two ways to set a user variable:

1. Using the "set" parameter in any item. For example:
     HOST=active:2,interval:0,set:hostname
   stores the data returned by the HOST item in a variable called "hostname".
   The item must be active, visible or hidden (active:1 or active:2).

2. Using the SET item you can store anything you can type in. For example:
     SET=active:2,key:MyTestKey1,value:MyTestValue1
   stores the value of "MyTestValue1" into a variable called "MyTestKey1".

Having stored these values into user variables, you can display them using any
item's display by typing the variable name enclosed in percent signs. For example:
   TEXT=active:1,interval:0,text:Host/User,display:%hostname%/%username%
   displays the "hostname" and "username" variables together on a single line.
      Host/User          DESKTOP-PC/Glenn

This is the complete example. Notice the first two items are active but hidden.

   HOST=active:2,interval:0,set:hostname
   USER=active:2,interval:0,set:username
   TEXT=active:1,interval:0,text:Host/User,display:%hostname%/%username%

Here's the same thing done a slightly different way. It does the USER item first
and stores that result then does the HOST item and displays both at once.

   USER=active:2,interval:0,set:username
   HOST=active:1,interval:0,text:Host/User,display:%1/%username%

Here's another example.  It combines boot time and up time into a single line
display. Notice both the UPTIME interval and the TEXT interval are set so it
continues to update.

   UPTIME=active:2,interval:1,set:uptime,display:%1d :%2h :%3m :%4s
   BOOTTIME=active:1,interval:1,display:%1 (Up: %uptime%)

In this example we want to read a small text file containing important information
that gets updated by the domain admin.  First we monitor the file for changes,
read the first line into a user variable then display that variable. In this
case it's the support extension number that changes daily. It could be asset or
other information the domain support people want to push out to computers.

   FILE=active:2,interval:60,type:text,text:Contact,file:\contact.txt,set:supportext
   TEXT=active:1,interval:60,text:Support,display:Call Glenn on ext %supportext%

An interesting thing to note is the TEXT item itself can have the set parameter.
This means you can cascade user variables or build them from other variables.
If you can find a use for this I'm listening.

HTTP Get
--------
This item will make a HTTP GET request to the given source url and display 
whatever it returns. You can give it any url but it's really only useful for 
returning a short plain text message such as getting your public ip or if you 
have a http server that provides information. There is no default, if you 
don't specify a url, it will return an error. 

Example:
  HTTPGET=active:1,interval:600,text:Public IP,source:http://plain-text-ip.com/
  
Here's a few other sites that return your public ip:
  https://ifconfig.co/ip
  http://ipecho.net/plain
  https://api.ipify.org/
  https://wtfismyip.com/text
  http://ident.me/
  https://myexternalip.com/raw
  http://plain-text-ip.com/

File Exists
-----------
This item will check if the given file exists and return true or false.  Use the
boolean formatting to make a nice display.

Example:
  FILEEXIST=active:1,interval:10,file:\glennisawesome.txt,text:Is Glenn Awesome?,display:%1[b:Absolutely!:Not!]
  
This tests for the file "\glennisawesome.txt". If it exists the display will be:
  "Is Glenn Awesome?           Absolutely!"
If the file doesn't exist, the display will be:
  "Is Glenn Awesome?           Not!"
  
File Contents
-------------
There are two items for displaying the contents of a text file:

  FILECONTENTS1			displays the file contents in the right column while the 
                        'text' property is displayed in the left column as a title
  FILECONTENTS2			displays the file contents across both columns
  
Set the file name in the 'file' property. Set the 'interval' if you want to 
update it at regular intervals.

Example:
  FILECONTENTS1=active:1,interval:3600,text:Lorem Ipsum,file:lorem ipsum.txt
  
Language File
-------------
The desktopinfo.ini file [options] section contains a "language" entry which 
points to a language configuration file. It's layout mirrors the 
desktopinfo.ini file; it contains an [options] section and an [items] section. 

The [options] section contains general language that may be used anywhere in
the program.

The [items] section contains the same list of items as is found in the 
desktopinfo.ini file. Each item is a name=value pair where the name matches 
either the item id or the item lid in the desktopinfo.ini file and the value 
is any text you want to use on the title display for that item. 

The NETWORKADAPTER and FIXEDDISK items may contain '%1' which will be replaced 
by each sub-item number.

So, when you create a new item such as a WMI query, simply give it a unique lid
value then go to the language file and create a new entry for that lid.

Example:
  WMI=active:1,lid:glenn_query_1,namespace:root\cimv2,query: .. . . ..  etc  ...
In the language file create:
  GLENN_QUERY_1=Glenn's amazing WMI query
  
Case is not sensitive, that's just today's standard.

You should ensure this text file is UTF-8 encoded for multi-byte compatability.

To change language all you have to do is disable the current language and enable
the new language file in the [options] of desktopinfo.ini.

Show Desktop
------------
The Show Desktop button on the Windows Quick Launch toolbar makes Desktop Info
invisible. Apparently Windows actually puts the desktop on top of everything.
There's nothing I can do about that. Instead, add a Desktop Info icon to your
Quick Launch toolbar. When you run it, Desktop Info will look to see if it's
running already. If it is, it will attempt to minimize enough applications to
make itself visible. This makes it sort of an alternative to Show Desktop.  The
obscuring windows may choose to ignore the minimize message or do other bizarre
things which are outside of my control.

Command Line Options
--------------------
The following command line options are available:

/a   Show all items regardless of ini file settings.

/f   Show a visible form. This tells Desktop Info to appear like a regular
     application allowing you to move it to the background or foreground and
     drag it around like any other application.

/ini Specify the full path and file name to an alternative desktopinfo.ini file.
     desktopinfo.exe /ini=mynewinifile.ini     
	 Don't forget the equals sign.

Context Menu
------------
To get the context menu to appear in transparent mode, you have to click on a 
visible pixel which may take a few tries. I like to keep the fixed disk bar 
chart on because it's easy to right click. The context menu can be disabled by 
setting the 'contextmenu' item in the 'options' section to '0'.

Show Desktop      In normal mode this minimises enough applications to make
                  Desktop Info visible. See above.
Refresh           This forces a refresh of the display and all items.
Configuration     Opens the desktopinfo.ini file with the default text editor.
                  When you edit and save this file, Desktop Info will detect the
                  change and load the new configuration.
Show Hidden Items Toggle the visibility of hidden items.
Read Me           Opens the readme.txt file with the default text editor.
Quit              Closes the Desktop Info application.

Screen Saver
------------
Desktop Info can be used as a screen saver. Make a copy of DesktopInfo.exe and
rename it to DesktopInfo.scr. Right click on this file and select Install. In
the ini file, the "ssfontsize" option controls the font size when running as a
screen saver. The size and position is preset. You can run the exe and the
screen saver at the same time.

Miscellaneous
-------------
The application is set to 'below normal priority' class which means that  
pretty much everything else will take priority but it won't necessarily wait 
until the cpu is idle. In previous versions it was set to 'idle priority' 
class but this makes it take too long to refresh. If some other application 
is going flat out 100% cpu, Desktop Info must wait and so the display may not 
update immediately or correctly.

The main CPU item shows percentage of all cpus in the system. This means it
will always show 0-100% regardless of how many cpus there are. The top process
cpu item shows the percentage per cpu. This means it may show more than 100%.

Top Process CPU can only show processes it has permissions to read. Running as
administrator or a member of the administrators group is enough for most
processes but not for some system processes. Desktop Info will attempt to
enable privileges to read system process information.

TOPPROCESSPF shows total page faults.

PAGEFAULTS shows both total and hard page faults. The hard page faults is
usually the one you're interested in. This shows page file activity which is
what kills system performance.

Some items may be denied access when retrieving data depending on the access
rights of the user running it on Vista, 7, 8, 10 and others.

Windows Platforms
-----------------
Desktop Info has been tested on the following Windows platforms:

XP Pro (32 bit) version 2002 service pack 2
XP Pro (32 bit) version 2002 service pack 3
XP Pro (64 bit) version 2003 service pack 2
Vista (32 bit) business service pack 1
Server 2000 (32 bit) service pack 4
Server 2003 (64 bit) service pack 2

Server 2008 (32 bit) standard service pack 1
Server 2008 (64 bit) standard service pack 1
Windows 7 Professional 64 bit
Windows 8
Windows 10 Home 1803
Windows 10 Pro 1803

The program basically works on Windows 2000 but some items won't work.

-------------------------------------------------------------------------------

Release Notes

Version v0.10
-------------
Limited distribution test release.

Version v0.11
-------------
Change 1: Fixed the nasty flicker some systems were getting.

Change 2: Fixed the odd characters after the domain name.

Change 3: Less full refreshes means less cpu time.

Change 4: Fixed disk figures for very small drives.

Version v0.20
-------------
Change 1: Added time zone info.

Change 2: Some optimisations.

Change 3: Added refresh intervals.

Change 4: Added domain controller info.

Change 5: Added event logs.

Version v0.21
-------------
Change 1: Added terminal server session count.

Change 2: Fixed some stuff in event logs.

Version v0.22
-------------
Change 1: Added DirectX version.

Change 2: Adjusted domain controller. I can't directly test this one.

Change 3: Added network packet stats and rates.

Change 4: Added network connection count.

Change 5: Added double click refresh.

Version v0.30
-------------
Change 1: Fixed a bunch of memory issues.

Change 2: Fixed Terminal Services sessions and added session list.

Change 3: Added auto font size.

Change 4: Added 'missing ini' default values.

Change 5: Implemented proper ini file monitoring.

Change 6: Added screen info.

Change 7: Fixed display for 256 color remote desktop.

Change 8: Added files monitor options.

Version v0.31
-------------
Change 1: Added Up Time.

Change 2: Added support for cpu times for Windows 2000.

Change 3: Fixed Domain Controller

Change 4: Fixed multiples of same file watch type bug.

Change 5: Fixed memory sizes over 2GB.

Version v0.40
-------------
Change 1: Added top process cpu time.

Change 2: Added top process memory usage.

Change 3: Added file version watch type.

Change 4: Added registry watch types.

Change 5: Added cpu count.

Change 6: Additional checking for terminal sessions.

Version v0.41
-------------
Change 1: Added unread mail.

Change 2: Added formright and formbottom options.

Version v0.42
-------------
Change 1: Increased fixed disks to eight.

Change 2: Added multiple ip addresses.

Change 3: Fixed problem with missing ini file.

Change 4: Split network gateway entries to separate lines.

Change 5: Added percentages to memory and disk displays.

Version v0.50
-------------
Change 1: I think I've nailed the show desktop thing.

Version v0.51
-------------
Change 1: Fixed problem with some USB drives.

Change 2: Solved refresh problem when removable drives come
and go.

Version v0.60
-------------
Change 1: Reworked the file monitoring so it works on local and remote
files and folders. You'll need to adjust your ini file entries as noted above.

Change 2: Reworked the registry monitoring to merge the two types. You'll need
to adjust your ini file entries as noted above.

Change 3: Added the /f command line option to show a visible, moveable form.

Change 4: Added the /a command line option to show all items regardless of the
ini file settings.

Change 5: Added right click context menu.

Change 6: The network entries are grouped so all information for each
adapter is together.

Change 7: Tested on a variety of Windows platforms. The results are noted above.

Version v0.70
-------------
Change 1: Added Disk IO on fixed logical drives.

Change 2: Added disk queue length.

Change 3: Changed ini file format as noted above. Will continue to read the old
format while the Intervals section exists.

Change 4: Added item colors.

Change 5: Fixed bug in Top Process Cpu

Change 6: Fixed bug in cpu times.

Change 7: Added charts.

Change 8: Added thresholds.

Change 9: Added exception handlers to process enumerators.

Version v0.71
-------------
Change 1: Fixed an access violation in the disk io routines.

Change 2: Fixed refresh when disks come and go.

Version v0.80
-------------
Change 1: Added colors to the file and registry monitors.

Change 2: Added option to disable the context menu.

Change 3: Added option to toggle the indents on disks/networks.

Change 4: Modified registry monitor to optionally show values.

Change 5: Registry item names are shown as found in the ini file.

Change 6: Added event log monitor and removed redundant event logs from
the items.

Version v0.81
-------------
Change 1: Improved disk change handling.

Change 2: Fixed file monitor where file/directory does not exist or
disappears or reappears.

Change 3: Fixed divide by zero error in fixed disks.

Version v0.90
-------------
Change 1: Refactored the chart display code to be more useful and added charts
to more items. See the charts section for more information.

Change 2: Refactored form display code. Options have changed accordingly. Auto
form width, auto font size and font color are gone. You should make sure every
item has the color set. See the options section for more information.

Change 3: Rewritten all the network adapter stuff. Added change handling.
Added filtering. See the options section for more information.

Change 4: Prevent form from resetting it's position after it is dragged.

Change 5: Rewrote the bar chart.

Change 6: Fixed problem with event log monitor thread not terminating correctly.

Change 7: Added the following items: printer, printerstatus, displaycontroller,
bios, motherboard, workgroup. Printers is work in progress.

Change 8: Added language file.

Change 9: Added screen saver option.

Change 10: Added msnstatus option.

Change 11: Changed method for retrieving service pack.

Version v1.00
-------------
Change 1: Added page faults and top process page faults.

Change 2: The order of displayed items now follows the order in the ini file.

Change 3: New ini file item format. This will make it easier to read and
easier for me to add new options. See the item section above for more details.

Change 4: Fixed the process name for all known varieties of Windows. If a
process name can't be retrieved for any reason, it will display <n/a> and maybe
an error message.

Change 5: Added cpu temperature from wmi. See the miscellaneous section above.

Change 6: Fixed line chart width in screen saver mode.

Change 7: Subdued some redundant refreshes.

Change 8: Some memory usage optimisations.

Change 9: Fixed display controller and bios on Windows 7 and hopefully haven't
broken it elsewhere.

Change 10: Added oeminfo. See miscellaneous section above.

Change 11: Added item font style.

Version v1.01
-------------
Change 1: Fixed fatal crash on startup as the result of an access denied problem
when retrieving OS info in limited access Windows account.

Version v1.10
-------------
Change 1: Added battery status.

Change 2: Added option to disable ClearType.

Change 3: Added header item. See ini file.

Change 4: Added cpu kernel time.

Change 5: Added inimonitortime to options. This is the number of seconds to
check the desktopinfo.ini file for changes.

Change 6: Added osbuild.

Change 7: Fixed a problem with reading process information for some system
processes.

Change 8: Removed DISKQUEUE item. It's included on the DISKIO item.

Change 9: Added filter option to FIXEDDISK item.

Version v1.11
-------------
Change 1: Changed the way the Windows architecture is determined.

Change 2: Fixed the transparency on 16 bit color display.

Version v1.12
-------------
Change 1: Forgot to switch off debug causing large log file, oops.

Version v1.20
-------------
Change 1: Fixed index out of bounds when battery chart type is 2.

Change 2: Added network PROXY item.

Change 3: Changed HEADER item into more general COMMENT item.

Change 4: COMMENT is ignored when calculating width of column 1 allowing it to
display over both columns.

Change 5: Added underline to style option.

Change 6: Changed FORMCOLOR in the main options section to a bgr type value to
keep it consistent with other colors. 000000 means transparent in normal mode
or black background in form mode.

Change 7: Converted file monitor into a regular item. Now you can put one or
more file monitor items anywhere in the items list.

Change 8: Converted registry monitor into a regular item. Now you can put one or
more registry monitor items anywhere in the items list.

Change 9: Fixed problem with monitoring registry on 64 bit Windows.

Change 10: Converted event log monitor into a regular item. Now you can put one
or more event log monitor items anywhere in the items list.

Change 11: Added AUDIOCONTROLLER item.

Change 12: Added logging option.

Change 13: Added /ini command line option.

Change 14: Added SERIALNUMBER item.

Change 15: Added multiple IP addresses per nic.

Change 16: Added option to allow/disallow dragging the form.

Change 17: Added offset property to network items.

Change 18: Added multi core cpu item, CPUUSAGE.

Change 19: Added activeonly property to NETWORKADAPTER.

Change 20: Added count property to control maximum number of multi items
displayed (CPUUSAGE, NETWORKADAPTER, FIXEDDISK, PRINTER.

Version v1.30
-------------
Change 1: Fixed critical error where USB drive is ejected but not
removed.

Change 2: Added SHORTDISPLAY option to PHYSICALRAM, VIRTUALMEMORY,
PAGEFILE and FIXEDDISK items.

Change 3: Added ENVVAR item.

Change 4: Added DEFAULTPRINTER item.

Change 5: Added SHORTDISPLAY option to the registry monitor.

Change 6: Added LOGONSESSION item.

Change 7: Moved network adapter filter to the item configuration and is
much more flexible with include and exclude options.

Version v1.40
-------------
Change 1: Added ALLIPADDRESS. This is a stand alone item to display all
active IP addresses without depending on the NETWORKADAPTER item.

Change 2: Fixed critical error where a network adapter has more than one
ip address sometimes causes an access violation.

Change 3: Improved response for changing network adapters, fixed disks and
screen resolution.

Change 4: Added hidden items. Set active to 2. Right click and select Show
Hidden Items. See above.

Change 5: Added OEMPRODUCT item. See above.

Change 6: Added SUBNETMASK item.

Change 7: Added csv option to items. See above.

Change 8: Fixed disk filter got lost during last version.

Change 9: Apparently fixed an obscure wmi bug.

Change 10: Fixed CPUTEMP charts.

Change 11: Added SERVICESTATE.

Change 12: Added TEXT.

Change 13: Added hook to Core Temp temperature reader.

Change 14: Added custom WMI item. See above for details. There's some examples
in the ini file. These may duplicate existing items. I'll leave the old items in
for this release and if all goes well they'll be removed next release.

Change 15: Adjusted screen saver display.

Version v1.50
-------------
Change 1: Fixed wmi line chart resetting when switching between hidden and not
hidden.

Change 2: Added volume to FIXEDDISK.

Change 3: There was a test item called PROCESSMEM which was hard wired to
DesktopInfo.exe. I've modified this so you can point it to any process name. The
result will be the sum of all processes by that name. 'ws' is Working Set, 'pf'
is Page File Usage or Commit Size.

Change 4: Added 'column1width' to global options.

Change 5: Added format option to WMI item.

Change 6: Added centerv and centerh to options.

Change 7: Removed following items as they can now be done with WMI: SERVICESTATE,
AUDIOCONTROLLER, SERIALNUMBER, WORKGROUP. The ini file has been updated as
appropriate.

Change 8: I don't know what I was thinking with LOGONSESSION.

Change 9: Added a global exception handler so maybe we won't see any more of
those cascading error messages.

Change 10: Added option to adjust background transparency.

Change 11: Cleaned up the display code and fixed a few little annoyances.

Change 12: Fixed IEVERSION to include svcversion updates.

Version v1.51
-------------
April 2014

Change 1: Fixed charts updating every second even though data is not updated.

Change 2: Fixed regression bug with COMMENT item.

Change 3: Fixed refresh ugliness and missing top lines.

Version v1.6
------------
August 2014

Change 1: Major refactor of the internal procedure calls.

Change 2: Reduced the display flickering some more.

Version v1.7
------------
August 2018
(Four years, that's not so bad is it?)

Change 1: Signing with digital code certificate. You can confirm this by right
clicking the DesktopInfo.exe, select Properties and the Digital Signatures tab.

Change 2: Removed secondary form from Windows task switcher.

Change 3: Removed MSN status option.

Change 4: Now correctly reads unicode language files. The language files must be
UTF-8 encoded.

Change 5: The language files are now collected in the "language" sub-directory.
Make sure you specify the sub-directory in the desktopinfo.ini file entry. Send
me your language files to be included in future releases.

Change 6: Doubled the size of item text so you can have longer comments.

Change 7: FIXEDDISK now correctly reads *only* local fixed and removable drives,
not remote, network, mapped or optical drives. No longer constantly polls drives
when the FIXEDDISK item is not active.

Change 8: UPTIME is no longer capped at 49 days.

Change 9: Added ShortDisplay to UPTIME.

Change 10: Added UTCTIME.  This seems to take a while to run so maybe set a
higher interval.

Change 11: Added full width underline style.

Change 12: I made a mistake with the TEXT item. The last field should be
'display' and not 'key'.  You should change your ini file to match.

Change 13: Added user variables. See the section above for details.

Change 14: Added csvdatatype option to items.  Data logging no longer outputs
the data in it's display form by default.  The default value of 0 outputs the
data in it's raw format. A value of 1 will output the data in the format it is
displayed. See data logging section above for more information.

Version v1.8
------------
September 2018

This version represents another not insignificant refactor which allows us to 
do a whole bunch of stuff we couldn't do previously. You should review the 
readme.txt, there's lots of new information there.

There may be things I've broken that I haven't discovered yet. Your current  
ini file will need modifications to bring it up to speed but it might be 
simpler to just start again with the new one. Let me know if something breaks 
that hasn't been mentioned here. 

Change 1: The first upshot of the big refactor is the addition of the 
'display' template property to every item.  This allows you to control how the 
data is displayed. See the items section above for details. This also means 
the 'shortdisplay' property is gone; you set your own display.

Change 2: The second upshot of the big refactor is that many items now offer
multiple values for display. You decide which values you want by using
replaceable parameters in the display template.  Not all items have fully 
implemented this yet, more to come in future releases.

Change 3: The third upshot of the big refactor is a whole new formatting 
system included with the display template. You now have much more control over 
numbers, dates, times, bytes, speeds and booleans.  See the Formatting 
sections above for much information.

Change 4: The custom WMI item has also undergone a major renovation and is 
much more useful now. The 'property' and 'format' options are gone and 
replaced with the 'display' template option. As with the other items, the WMI 
display template option allows you to specify the complete text you want to 
display including any and all returned wmi property values. You can add your 
own custom text as well as multiple values and formatting. See the Custom WMI 
section for details.

Change 5: The WMI item can now display multiple rows.  If your wmi query 
returns more than one row, additional rows will be added to the display.

Change 6: Added HTTPGET item. This item will make a simple HTTP GET request to 
the given source url and display whatever it returns. Useful for displaying 
your public ip for example. See the Http Get section for more information.

Change 7: Removed SCREEN and OSVERSION items. They are returning innaccurate
information so we'll use the WMI call instead.  See the ini file.

Change 8: Removed BIOS, OEMPRODUCT, MOTHERBOARD, PRINTER, PRINTERSTATUS, 
DEFAULTPRINTER, UTCTIME items. These are all wrappers for WMI calls so now 
we'll just use WMI directly with some nice formatting. See the ini file for 
the replacements.

Change 9: Fixed problem reading registry key with a comma in the name. A comma
in a registry key should be preceded by a backslash. See above for more
information.

Change 10: Added FILEEXIST item. Displays whether the given file exists. See 
the section above for details and the ini file for an example.

Change 11: Fixed column 1 auto width calculation.

Change 12: Added LOADTIME which is the time of day that Desktop Info was 
executed.

Change 13: Changed process priority from 'idle' to 'below normal'. I don't 
expect this to have any impact other than the display refreshes are a little 
smoother.

Change 14: Speaking of display refreshes, I've hopefully streamlined it some 
more to reduce unnecessary redraws.

Change 15: If an item color is not defined it will take on the color of the 
previous item.  In this way you set the color of the first item in a block and 
all successive items will be the same. 

Change 16: ALLIPADDRESS now puts one entry per line so if you have multiple IP 
addresses, there will be multiple lines. Might have found the bug where it 
crashes when a network interface goes away.

Change 17: Added FILECONTENTS1 and FILECONTENTS2 for displaying the contents of
a text file.

Change 18: Removed SUBNETMASK and MACADDRESS sub-items and added them as a 
second and fourth value (%2 and %4) to IPADDRESS.

Change 19: Added subnet class as a third value to IPADDRESS.

Change 20: Added subnet mask and class as second and third values to 
ALLIPADDRESS. 

Change 21: Now correctly resets it's position when the desktop size changes 
(maybe).

Change 22: Added 'noresults' option to the language files which is displayed 
when a query returns no rows, eg WMI.

Change 23: More improvement in language support. All 'text' has been moved out 
of the desktopinfo.ini file and into the language files. Each key in the 
language file is either an item id or a language id (lid) in the 
desktopinfo.ini file. See the section above for more information. Consider the
'text' option in the desktopinfo.ini file deprecated.


-------------------------------------------------------------------------------
