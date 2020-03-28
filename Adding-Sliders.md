## Introduction
This page provide programmers information on adding another slider to WLED. This information is not yet complete, as it doesn't yet deal with icons, EEPROM or IR.

## Updating html_ui.h
This file is compressed and is taken from data\index.htm. Please see Aircoookie's page on 'adding your own effect':

https://github.com/Aircoookie/WLED/wiki/Add-own-functionality

To serve your changes by the internal webserver, you will need to follow these or similar steps to gzip compress the index.html file:

1. Gzip compress the file. I use this online converter, use setting Compress this file, output – gz
1. Rename file to xxx.gz.png (change file type to image)
1. Convert it to a C-style byte/char array. I use this converter, intended for image sprites. Therefore, the previous step of changing the file format was neccessary. Select Raw as Color format.
1. Open the downloaded .c file in a text editor, e. g. Notepad++. Select the contents of the array and replace the array contents in html_ui.h with them.
1. Update PAGE_index_L to the binary size stated in the bottom of the downloaded .c file
Recompile and flash WLED!


