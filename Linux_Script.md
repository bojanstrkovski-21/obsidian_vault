---
cssclasses:
  - dashboard
banner: "![[home.jpg]]"
banner_x: 0.5
banner_y: 0
---
<div class="title" style="color:SkyBlue">LINUX_SCRIPT D A S H B O A R D</div>

# 🐧 Linux Basics
```dataview
List from "Linux/01. Basics"
```
# 🐧 Bash, Logging, Security
🔹 Bash
```dataview
List from "Linux/02. Bash"
```

🔹 Loging
```dataview
List from "Linux/03. Logging"
```
🔹 Security
```dataview
List from "Linux/04. Security"
```

🔹 Monitoring
- Grafana
 ```dataview
 List from "Linux/06. Monitoring/01. Grafana"
```

- Influxdb
```dataview
List from "Linux/06. Monitoring/02. Influxdb"
```
- Kibana
```dataview
List from "Linux/06. Monitoring/04. Prometheus"
```
# 🐧 Tips
```dataview
List from "Linux/05. Tips"
```

# 🐧 Git
```dataview
list from "Linux/07. Git"
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