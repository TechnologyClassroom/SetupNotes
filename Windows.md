# Windows

This file will always be incomplete.  Use free, libre, and open source operating
systems if you value privacy.

When installing a Windows system, it comes with terrible defaults that do not
always have your best interests in mind.  Be very careful when installing for
the first time.  As a rule of thumb, turn everything off unless you are sure
that you need it.

## Troubleshooting

Problem: Motherboard is set to UTC time for GNU/Linux distributions.  Windows 7
has the incorrect time.
Solution: Add a Windows registry key to use UTC time.

- Run regedit.exe as Administrator.
- Navigate to HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\TimeZoneInformation
- Add a new DWORD entry titled: RealTimeIsUniversal
- Set the value of RealTimeIsUniversal to 1.
- Reboot

From http://crashmag.net/configuring-windows-7-support-for-utc-bios-time

Problem: MSN opens a browser when logging in.
Solution: Change the registry.
From http://www.troublefixing.in/solved-windows-launch-msn-or-bing-page-on-starup/345/
regedit Run As Administrator
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\NlaSvc\Parameters\Internet\
On right side pane you will find a EnableActiveProbing value, just double click
on it and change its value from 1 to 0.

Problem: Users start multiple instances of a program causing nothing to work.
Solution: Create a batch script in a text file using this line and save it as
like KSPLaunch.bat in the directory with the process.  Replace KSP.exe with your
process name.  Replace shortcuts with a shortcut to the batch script.  Replace
shortcut icons with the original icons.

```
tasklist /nh /fi "imagename eq KSP.exe" | find /i "KSP.exe" > nul || (start KSP.exe)
```

From http://superuser.com/questions/654088

Problem: Password expiration notice appears and the machine's password should
not expire.
Solution: Disable Password Expiration for a User in Windows 8.1/8/7

- Run lusrmgr.msc as Administrator.
- Click on ```Users``` in the left pane.
- Right click on the username to be modified.
- Click on ```Properties```.
- CHECK ```Password never expires```.
- Click ```OK```.
- Exit lusrmgr.

Based on https://www.windowspasswordsrecovery.com/articles/password/enable-or-disable-password-expiration-for-a-user-in-windows-8-7.html


## How to search for literal strings in Explorer

From Kustardking on
https://answers.microsoft.com/en-us/windows/forum/windows_7-files/how-do-i-search-for-parenthesis/ff8982f2-7a65-4569-a3f1-0373d0763ad8

name:~"*(2)*"
(2) can be changed to other literal strings.
