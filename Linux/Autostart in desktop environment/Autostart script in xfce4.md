
1. Create the script and make it executable (open terminal in the folder where
the script is  and type **cmod +x autostart.sh** and hit enter)
use any text editor and create for example autostart.sh text file
open it with the text editor and at the begining add the shebang (**#!/usr/bin/env bash**)
than after this type youre stuf.
2. Create **.desktop** file in **~/.config ($HOME/.config)**
Folder might not exist by default. If not, create it.
The file can be named any as long as the extension is .desktop.

Its content should look like this:

[Desktop Entry]  
Version=1.0  
Encoding=UTF-8  
Name=Script  
Type=Application  
**Exec=/usr/local/share/scripts/autostart.sh**  
Terminal=false  
StartupNotify=false  
Hidden=false  
