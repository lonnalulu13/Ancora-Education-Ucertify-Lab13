# Ancora-Education-Ucertify-Lab13
# Performing IDS Configuration with Snort

> **Original Lab Source**
> This lab was available through:
> [https://ancoraeducation.ucertify.com/app/?func=navigate_items&item_sequence=4]

## Objective of the Lab
In this lab, you will learn to perform IDS (Intrusion Detection System) configuration with Snort. Snort is an open-source intrusion prevention system capable of real-time traffic analysis and packet logging.

## Instructions
### STEP 1
From the bottom-left bar, click the WIN16 tab, and then click On/Connect to power on the machine.

### STEP 2
on the taskbar, click the file explorer icon

### STEP 3
Navigate to Local Disk (C:)>Snort>etc.

### STEP 4
In the etc window, right-click snort.conf and select Edit with Notepad++

**CAUTION**

If the Notepad++update prompt appears, click No.

### STEP 6
In the file, change the following things:

**CAUTION**

For comments, use # at the beginning of the specific line. You can uncomment a line in a configuration file by removing the # at the start of the line.

a. Comment out the line 99.

b. In the line 104, to set RULE_PATH, replace . . / rules with C:\Snort\rules

c. Comment out the line 105.

d. In the line 106, to set PREPROC_RULE_PATH, replace . . / preproc_rules with 
C:\Snort\preproc_rules

e. In the line 113, to set WHITE_LIST_PATH, replace . . / rules with C:\Snort\rules

f. In the line 114, to set BLACK_LIST_PATH, replace . . / rules with C:\Snort\rules

g. Uncomment the line 186 and set config logdir: as C:\Snort\log

h. In the line 247, to set dynamicpreprocessor directory, replace /usr/local/lib/snort_dynamicpreprocessor/ with C:\Snort\lib\snort_dynamicpreprocessor

i. In the line 250, to set dynamicengine, replace /usr/local/lib/snort_dynamicengine/libsf_engine.so with C:\Snort\lib\snort_dynamicengine\sf_engine.dll

j. Comment out the lines 253, 265, 266, 267, 268, 269, and 335.

k. Uncomment the line 418.

l. In the line 511, to set whitelist, replace $WHITE_LIST_PATH/white_list.rules, \ with $WHITE_LIST_PATH\white.list, \

m. In the line 512, to set blacklist, replace $BLACK_LIST_PATH/black_list.rules with $BLACK_LIST_PATH\black.list

n. On the icon based toolbar, select the Replace () icon to open the Replace window.

o. To replace all / with \, in the Replace window, in the Find what text box, type /, in the Replace with text box, type \, and click Replace All.

p. Close the Replace dialog box.

### STEP 7
From the menu, navigate to File>Save to save all the changes.

### STEP 8
Click the Start menu and open Windows PowerShell.

### STEP 9
In the Windows PowerShell window, execute the following commands (Note: Execute one command at a time.):
```bash
cd \snort\bin
```
```bash
.\snort.exe -V -i 0
```
### STEP 10
In the File Explorer window, navigate to Local Disk (C:) > Snort > rules.

### STEP 11
In the rules folder, right-click local.rules, and select Edit with Notepad++.

### STEP 12
Add the following signatures rules in the line 22 of the file local.rules (Note: Execute one command at a time.):
```bash
alert icmp any any -> any any (msg: "Ping packets detected"; sid: 1000001; )
```
```bash
alert tcp any any -> any any (msg: "TCP packets detected"; sid: 1000002; )
```
```bash
alert udp any any -> any any (msg: "UDP packets detected"; sid: 1000003; )
```
### STEP 13
From the menu, navigate to File > Save to save all the changes.

### STEP 14
Go back to Windows PowerShell window.

### STEP 15
In the Windows PowerShell window, execute the following command:
```bash
.\snort.exe -i 0 -c C:\Snort\etc\snort.conf -T
```

**CAUTION**

Wait for 5-6 minutes to complete the execution of the command.

## Disclaimer

This repository is for **educational and personal learning purposes only**.  

The original lab content belongs to **uCertify / Ancora Education** and remains their copyrighted material.  
This repository is not affiliated with, endorsed by, or sponsored by uCertify or Ancora Education.  

No copyright infringement is intended.  
Use of any tools or techniques mentioned here should only be performed in authorized, legal environments.







