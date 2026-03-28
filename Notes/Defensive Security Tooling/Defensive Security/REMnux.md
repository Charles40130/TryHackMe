---

---

---

`Oledump.py` : python tool that analyzes OLE2 files

OLE (Object Linking and Embedding) : technology developed by Microsoft, OLE2 files are used to store multiple data types , such as documents, spreadsheets and presentations within a single file 


---
#### INetSIM : Inter Services Simulation Suite



---
#### Volatility 3

1. `sudo su` : change the user to root
2. `cd /home/ubuntu/Desktop/tasks/Wcry_memory_image/` : navigate to this directory
3. `vol3 -f wcry.mem` : execute the plugin

We will see this parameters :
- windows.pstree.PsTree
- windows.pslist.PsList
- windows.cmdline.CmdLine
- windows.filescan.FileScan
- windows.dlllist.DllList
- windows.malfind.Malfind
- windows.psscan.PsScan

##### PSTree

```
vol3 -f wcry.mem windows.pstree.PsTree
```
lists processes in a tree based on their process ID

##### PSList
```
vol3 -f wcry.mem windows.pslist.PsList
```
lists all currently active processes in the machine

##### CmdLine
```
vol3 -f wcry.mem windows.cmdline.CmdLine
```
list process command line arguments

##### FileScan
```powershell
vol3 -f wcry.mem windows.filescan.FileScan
```
scans for file objects in a particular windows memory image

##### DllList
```powershell
vol3 -f wcry.mem windows.dlllist.DllList
```
lists the loaded modules in a particular Windows memory image.

##### PsScan
```powershell
vol3 -f wcry.mem windows.psscan.PsScan
```

scan for processes present in a particular Windows memory image.

##### Malfind
```powershell
vol3 -f wcry.mem windows.malfind.Malfind
```

```powershell
vol3 -f wcry.mem windows.malfind.Malfind
```