# PowerShell ExecutionPolicy configurator

![GitHub repo size](https://img.shields.io/github/repo-size/niklasrast/Windows-10-PowerShell-ExecutionPolicy-Configurator)

![GitHub issues](https://img.shields.io/github/issues-raw/niklasrast/Windows-10-PowerShell-ExecutionPolicy-Configurator)

![GitHub last commit](https://img.shields.io/github/last-commit/niklasrast/Windows-10-PowerShell-ExecutionPolicy-Configurator)

This repo contains an powershell scripts to configure the execution policy for powershell on any windows 10 client.

## Install:
```powershell
#Call via software deployment with -ExecutionPolicy Bypass
PowerShell.exe -ExecutionPolicy Bypass -Command .\Invoke-ExecutionPolicyChange.ps1 -policy AllSigned
PowerShell.exe -ExecutionPolicy Bypass -Command .\Invoke-ExecutionPolicyChange.ps1 -policy Bypass
PowerShell.exe -ExecutionPolicy Bypass -Command .\Invoke-ExecutionPolicyChange.ps1 -policy Default
PowerShell.exe -ExecutionPolicy Bypass -Command .\Invoke-ExecutionPolicyChange.ps1 -policy RemoteSigned
PowerShell.exe -ExecutionPolicy Bypass -Command .\Invoke-ExecutionPolicyChange.ps1 -policy Restricted
PowerShell.exe -ExecutionPolicy Bypass -Command .\Invoke-ExecutionPolicyChange.ps1 -policy Undefined
PowerShell.exe -ExecutionPolicy Bypass -Command .\Invoke-ExecutionPolicyChange.ps1 -policy Unrestricted

#Call trough an exe file
ExecutionPolicyConfigurator.exe -policy AllSigned
ExecutionPolicyConfigurator.exe -policy Bypass
ExecutionPolicyConfigurator.exe -policy Default
ExecutionPolicyConfigurator.exe -policy RemoteSigned
ExecutionPolicyConfigurator.exe -policy Restricted
ExecutionPolicyConfigurator.exe -policy Undefined
ExecutionPolicyConfigurator.exe -policy Unrestricted
```

## Configuration:
```powershell 
#Create RegKeys for the execution policy based on the value of the parameter -policy
$registryPath = "HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell"
$Name = "ExecutionPolicy"

New-ItemProperty -Path $registryPath -Name $name -Value $policy -PropertyType String -Force
```

## Logfiles:
The scripts create a logfile with the name of the .ps1 script in the folder C:\Windows\Logs.

## Requirements:
- PowerShell 5.0
- Windows 10
- Local admin privileges

# Feature requests
If you have an idea for a new feature in this repo, send me an issue with the subject Feature request and write your suggestion in the text. I will then check the feature and implement it if necessary.

Created by @niklasrast 