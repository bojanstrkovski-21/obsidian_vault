
1. Create the script and make it executable 
use any text editor and create for example autostart.sh text file
open it with the text editor and at the begining add the shebang (#!/usr/bin/env bash)
than after this type youre stuf
2. Create .desktop file in ~/.config ($HOME/.config)
Folder might not exist by default. If not, create it.
The file can be named any as long as the extension is .desktop.
Its should look like this:
[Desktop Entry]  
Version=1.0  
Encoding=UTF-8  
Name=Script  
Type=Application  
**Exec=/usr/local/share/autostart.sh**  
Terminal=false  
StartupNotify=false  
Hidden=false  
