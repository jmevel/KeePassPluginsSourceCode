## Synopsis

This code automatically extracts KeePass plugins' source code from the PLGX files. 
In order to make it work you have to compile your own keepass.exe

Works with KeePass v2.35

## Motivation

I've been using KeePass for years and always had some concerns about plugins' security issues. How to ensure the plugins you install don't steal all your emails and passwords?

There is no other way than reviewing the source code by yourself. 
The problem is that some plugins are open source, others are not. Moreover you can't be sure the PLGX file you downloaded really correspond to the open source code you reviewed.

Therefore I decided to modify a tiny part of the KeePass source code in order to get the REAL code executed by the plugins.

## Installation

1) Download the KeePass 2.35 source code at http://keepass.info/download.html
2) Replace the file **/KeePass-2.35-Source/KeePass/Plugins/PlgxCsprojLoader.cs** by the one in this repository
3) Copy the file **NewDatabase.kdbx** at the root folder of your KeePass source code (*KeePass-2.35-Source*) 
   (You should NOT load the plugins with your personal KeePass database until you reviewed their codes)
4) Open the solution with Visual Studio and build the project
5) If you have issues with the signed keys import you can simply disable it:
	- Right-click the project in the solution explorer and select "Properties".
	- Click on the "Signing" tab and uncheck the "Sign the assembly" checkbox
6) If you built the project in Debug mode then navigate to the **/KeePass-2.35-Source/KeePass/obj/Debug** directory
7) Create a folder named **Plugins** and put in it any PLGX files you want
8) Open a Windows command line and go to your Debug directory
9) Execute the command `keePass.exe ./../../../EmptyDatabase.kdbx -pw:123`

All the plugins' source codes are now in the **/KeePass-2.35-Source/KeePass/obj/Debug/Plugins** directory

## License

*KeePass Password Safe - The Open-Source Password Manager*
*Copyright (C) 2003-2017 Dominik Reichl <dominik.reichl@t-online.de>*

*This program is free software; you can redistribute it and/or modify*
*it under the terms of the GNU General Public License as published by*
*the Free Software Foundation; either version 2 of the License, or*
*(at your option) any later version.*

*This program is distributed in the hope that it will be useful,*
*but WITHOUT ANY WARRANTY; without even the implied warranty of*
*MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the*
*GNU General Public License for more details.*

*You should have received a copy of the GNU General Public License*
*along with this program; if not, write to the Free Software*
*Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA  02110-1301  USA*
