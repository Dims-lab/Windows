# Windows Forensic Commands

## Network Discovery
- `net view /all`
- `net view`
- `net view \\HOSTNAME`
- `net share`
- `net session`
- `wmic volume list brief`
- `wmic share get`
- `wmic logicladisk get`

## Scan Commands
- `nbtstat -A [ip_address]`
- `for /L %I in (1,1,254) do ping -w 30 -n 1 192.168.1.%I | find "Reply" >> [output_file].txt`
- `nbtstat -c`
- `for /L %I in (1,1,254) do nbtstat -An 192.168.1.%I`

## Wi-Fi Connections
- `netsh wlan show profile`
- `netsh wlan show profile [profile_name] key=clear`

## Network Information
- `netstat -e`
- `netstat -nr`
- `netstat -naob`
- `netstst -S`
- `netstat -vb`
- `route print`
- `arp -a`
- `ipconfig /all`
- `netsh wlan show interfaces`
- `netsh wlan show all`

## Firewall Management
- `netsh advfirewall show rule name=all`
- `netsh advfirewall set allprofile state off`
- `netsh advfirewall set allprofile state on`
- `netsh advfirewall set publicprofile state on`
- `netsh advfirewall set privateprofile state on`
- `netsh advfirewall set domainprofile state on`
- `netsh advfirewall firewall add rule name="Open Port 80" dir=in action=allow protocol=TCP localport=80`
- `netsh advfirewall firewall add rule name="My Application" dir=in action=allow program="C:\\MyApp\\MyApp.exe" enable=yes`

## User Management
- Create user: `net user /add [username] [password]`
- Add to administrators: `net localgroup administrators [username] /add`
- View user details: `net user [username]`
- Change password: `net user [username] [new_password]`
- Other user commands:
  - `net users`
  - `net localgroup administrators`
  - `net group administrators`

## WMI Commands
- `wmic rdtoggle list`
- `wmic useraccount list`
- `wmic group list`
- `wmic netlogin get name,lastlogin,badpasswordcount`
- `wmic netclient list brief`
- `wmic nicconfig get`
- `wmic netuse get`

## File Operations
- Show content of a file: `type [file.txt]`

## Service Management
- `at`
- `tasklist`
- `tasklist /svc`
- `schtask`
- `net start`
- `sc query`
- `wmic service list brief | findstr "Running"`
- `wmic service list brief | findstr "Stopped"`
- `wmic service list config`
- `wmic service list brief`
- `wmic service list status`
- `wmic service list memory`
- `wmic job list brief`
- Start/Stop service:
  - `sc config "[service_name]" start= disable`
  - `sc stop "[service_name]"`
  - `wmic service where name='[service_name]' call ChangeStartMode Disabled`

## Autorun and Autoload
- `wmic startup list full`
- `wmic ntdomain list brief`

## Registry Operations
- Read registry entries: `reg query "HKCU\\Control Panel\\Desktop"`
- Enable/Disable Remote Desktop:
  - Enable: `reg add "HKEY_LOCAL_MACHINE\\SYSTEM\\CurrentControlSet\\Control\\Terminal Server" /v fDenyTSConnections /t REG_DWORD /d 0 /f`
  - Disable: `reg add "HKEY_LOCAL_MACHINE\\SYSTEM\\CurrentControlSet\\Control\\Terminal Server" /v fDenyTSConnections /t REG_DWORD /d 1 /f`
- Enable remote assistance: `reg add "HKEY_LOCAL_MACHINE\\SYSTEM\\CurrentControlSet\\Control\\Terminal Server" /v fAllowToGetHelp /t REG_DWORD /d 1 /f`

## Shadow Copies
- `vssadmin List ShadowStorage`
- `vssadmin List Shadow`
- `net start VSS`

## Policy and Patch Management
- `set`
- `gpresult /r`
- `systeminfo`
- `wmic qfe`

## Reboot Command
- `shutdown.exe /r`

## Security Log and Audit Policies
- Check security log settings: `wevtutil gl Security`
- Check audit policies: `auditpol /get /category:*`

## System Information
- `echo %DATE% %TIME%`
- `hostname`
- `systeminfo`
- `wmic csproduct get name`
- `wmic bios get serialnumber`
- `wmic computersystem list brief`
