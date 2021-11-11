# Forcing RSAT installation when it fails

Disable Auto Update in Windows Update then reenable it [1]:

```powershell
Set-ItemProperty -path HKLM:\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate\AU -Name 'UseWUServer' -Value '0'
Restart-Service -Name wuauserv
Get-WindowsCapability -Name RSAT* -Online | Add-WindowsCapability -Online
Set-ItemProperty -path HKLM:\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate\AU -Name 'UseWUServer' -Value '1'
Restart-Service -Name wuauserv
```

[1](https://www.reddit.com/r/sysadmin/comments/ey98h1/unable_to_install_rsat_on_1909/)

    #rsat #powershell #windows

