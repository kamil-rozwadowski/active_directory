# Creating templates vm's
1. Creted template vm's for server purpose.


2. Creted template vm's for host purpose.
- Bypassing TMP protection for win11
   - Hit SHIFT + F10 to launch the command prompt. 
   - Type regedit and hit Enter to launch registry editor.
   - Navigate to HKEY_LOCAL_MACHINE\SYSTEM\Setup
   - Create a new registry key under Setup and name it LabConfig.
   - Within  LabConfig, create DWORDs values called BypassTPMCheck and BypassSecureBootCheck and set each to 1.
