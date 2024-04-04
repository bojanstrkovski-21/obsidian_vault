---
cssclasses:
  - dashboard
banner: "![[home.jpg]]"
banner_x: 0.5
banner_y: 0
---
<div class="title" style="color:SkyBlue">LINUX_SCRIPT D A S H B O A R D</div>

# 🐧 Left-WM
```dataview
List from "Linux/09. Leftwm"
```
# 🐧 Rsync
```dataview
List from "Linux/10. Rsync tutorial"
```
# 🐧 10 Basic Linux Commands that everyone should know
```dataview
List from "Linux/11. 10 Linux basic commands that everyone should know"
```

# 🐧 Neovim
```dataview
list from "Linux/11. Neovim prepare and install"
```

# 🐧 How to logout from de
```dataview
list from "Linux/12. logout de"
```
# 🐧 SSH-GPG keys
```dataview
list from "Linux/13. ssh-gpg-keys"
```

# 🐧The easiest way to install dwm
```dataview
list from "Linux/14. The easiest way to install DWM - FAUN - Developer Community"
```

# 🐧Linux_Scripts_Other
🔹 Autostart in desktop environment
```dataview
List from "Linux/15. LINUX_SCRIPT/Autostart in desktop environment"
```

🔹Bluetooth
```dataview
list from "Linux/15. LINUX_SCRIPT/bluetooth"
```

🔹 Gtk_css_xfce4_panel
```dataview
list from "Linux/15. LINUX_SCRIPT/gtk_css_xfce4-panel"
```

🔹 NetStart
```dataview
list from "Linux/15. LINUX_SCRIPT/netstart"
```

🔹 Samba Config
```dataview
list from "Linux/15. LINUX_SCRIPT/SAMBA config"
```

🔹 SparkLines-Fish-Shell
```dataview
list from "Linux/15. LINUX_SCRIPT/Sparklines_fish"
```

🔹 Vbox
```dataview
list from "Linux/15. LINUX_SCRIPT/vbox"
```

🔹 Vim Commands
```dataview
list from "Linux/15. LINUX_SCRIPT/VIM commands"
```

🔹 Linux_Script_other...
```dataview
list from "Linux/15. LINUX_SCRIPT/"
where app 
```
# 🐧 Vault Info
- 🗄️ Recent file updates
 `$=dv.list(dv.pages('').sort(f=>f.file.mtime.ts,"desc").limit(4).file.link)`
- 🔖 Tagged:  favorite 
 `$=dv.list(dv.pages('#favorite').sort(f=>f.file.name,"desc").limit(4).file.link)`
- 〽️ Stats
	-  File Count: `$=dv.pages().length`
	-  Linux/Basics: `$=dv.pages('"Linux/01. Basics"').length`
	- Linux/Bash: `$=dv.pages('"Linux/02. Bash"').length`
	- Linux/Logging: `$=dv.pages('"Linux/03. Logging"').length`
	- Linux/Security: `$=dv.pages('"Linux/04. Security"').length`
	- Linux/Tips: `$=dv.pages('"Linux/05. Tips"').length`
	- Linux/Monitoring: `$=dv.pages('"Linux/06. Monitoring"').length`
	- Linux/Git_and_github: `$=dv.pages('"Linux/07. Git"').length`
	- Linux/Docker: `$=dv.pages('"Linux/08. Docker"').length`
	- Linux/Leftwm: `$=dv.pages('"Linux/09. Leftwm"').length`
	- Linux/Linux_Script: `$=dv.pages('"Linux/LINUX_SCRIPT"').length`