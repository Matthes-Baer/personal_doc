# PowerShell

This section covers information about PowerShell.

## Useful Links
- [PowerShell 7 Tutorial](https://www.youtube.com/watch?v=NECE5CX69tk&list=PLnK11SQMNnE4vcvuAahz4KhNOS7zOfmB3)


## General Information
- It's best practice to use uppercase letters for each word in a PowerShell command, e.g., `Get-Process` instead of `get-process`.
- When using `Get-Help`, for example, you will see information about syntax, parameters, and more. When you see something like `[[-Name] <string[]>]` in the syntax section, it means that the `-Name` parameter is optional (thus the `[]` around `-Name`) and can accept multiple string values. When you see something like `[-DependentServices]` it means that this is a switch parameter, which does not require a value. If you use it, it will be set to `$true`, otherwise it will be `$false`. In the parameters section of the `Get-Help` cmdlet output, you can find more information about what to pass in for all the parameters.
- There are common parameters supported by most cmdlets, such as `-Verbose`, `-Debug`, `-ErrorAction` - [More Information](https://learn.microsoft.com/de-de/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7.5)


## Some Cmdlets
- `Get-Service` / `gsv` - Lists all services on the system
- `Start-Service` / `sasv` - Starts a service
- `Stop-Service` / `spsv` - Stops a service
- `Restart-Service` / `resv` - Restarts a service
- `Get-Process` / `gps` - Lists running processes
- `Stop-Process` / `spps` - Kills a process by ID or name

- `Get-Date` - Returns current date and time
- `Get-ComputerInfo` - Returns system info (OS, BIOS, etc.)
- `Get-Uptime` - Shows how long the system has been running

- `Get-ChildItem` / `gci` / `ls` / `dir` - Lists files and directories in a path (similar to `ls` in Unix)
- `Set-Location` / `cd` / `sl` - Changes the current directory (similar to `cd` in Unix)
- `Get-Content` / `gc` / `cat` - Reads content from a file
- `Set-Content` / `sc` - Writes content to a file
- `Add-Content` / `ac` - Appends content to a file
- `New-Item` / `ni` - Creates a new file or directory, or other item
- `Remove-Item` / `rm` / `del` / `erase` - Deletes a file or directory
- `Copy-Item` / `cp` / `copy` - Copies a file or directory
- `Move-Item` / `mv` / `move` - Moves a file or directory (or renames it)

- `$env:PATH` - Accesses environment variables, e.g., `$env:PATH` to get the system PATH variable
- `Write-Output` / `echo` / `write` - Writes output to the pipeline
- `Write-Host` - Writes output to the console, without pipeline (not recommended for scripts)
- `Read-Host` - Prompts for user input

- `Test-Connection` / `ping` - Pings a computer (like traditional `ping`)
- `Resolve-DnsName` - DNS lookup (replaces `nslookup`)
- `Get-NetIPAddress` - Shows IP config info

- `Get-Help` / `help` - Shows help for cmdlets (use `-Full`, `-Examples`) | e.g. 
- `Get-Command` / `gcm` - Finds cmdlets/functions/aliases/etc. -> this will reveal more shortcuts than listed here | this is the most important cmdlet since you can find all available cmdlets
- `Get-Alias` / `gal` - Lists aliases or resolves one
- `Get-Member` / `gm` - Shows properties/methods of objects


## Code Examples

### Get Full Information About a Cmdlet (including syntax etc.)

```powershell
Get-Help Get-Service -Full
```

### Find Commands with Noun in Name

Find all commands that have 'service' in their name:

```powershell
Get-Command -noun service
```
