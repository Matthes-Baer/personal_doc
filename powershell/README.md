# PowerShell

This section covers information about PowerShell.

## Useful Links
- [PowerShell 7 Tutorial](https://www.youtube.com/watch?v=NECE5CX69tk&list=PLnK11SQMNnE4vcvuAahz4KhNOS7zOfmB3)


## General Information
- It's best practice to use uppercase letters for each word in a PowerShell command, e.g., `Get-Process` instead of `get-process`.
- When using `Get-Help`, for example, you will see information about syntax, parameters, and more. When you see something like `[[-Name] <string[]>]` in the syntax section, it means that the `-Name` parameter is optional (thus the `[]` around `-Name`) and can accept multiple string values. When you see something like `[-DependentServices]` it means that this is a switch parameter, which does not require a value. If you use it, it will be set to `$true`, otherwise it will be `$false`. In the parameters section of the `Get-Help` cmdlet output, you can find more information about what to pass in for all the parameters.
- There are common parameters supported by most cmdlets, such as `-Verbose`, `-Debug`, `-ErrorAction` - [More Information](https://learn.microsoft.com/de-de/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7.5)
- File ending for PowerShell scripts is `.ps1`, for modules it is `.psm1`, and for module manifest files it is `.psd1`.
- Arrays are not optimized for large datasets (like size > 100) because they have a fixed size (see code example below), so if you need to work with large datasets or need dynamic storage, consider using `System.Collections.Generic.List` or `System.Collections.ArrayList` instead.


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

- `Measure-Command` - Measures the time it takes to run a script or command


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

### Declare and Initialize a Variable

```powershell
$testVariable = "Hello, World!"
$anotherTestVariable = Get-Date

$testVariable
```

With the `$testVariable` in the end of a script, the value will be printed to the console.

### Set Strict Mode On/Off

Set it on:

```powershell
Set-StrictMode -Version Latest
```

With the strict mode enabled, PowerShell will enforce stricter rules for variable declaration and usage, which can help catch errors early in your scripts. Let's say you try to use a variable that has not been declared, it will throw an error. Also trying to access an item in an array that does not exist will throw an error (out of bounce) with the strict mode enabled.

Set it off:

```powershell
Set-StrictMode -Off
```

### Measure Execution Time of a Command

```powershell
$testArrayList = New-Object System.Collections.ArrayList

Measure-Command -Expression { $testArrayList.AddRange(@(0..10000)) }
```

### Basic Arrays

Arrays have a fixed size, so if you need to work with large datasets, consider using `System.Collections.Generic.List` or `System.Collections.ArrayList` instead.

```powershell
# Declare and initialize an array
$myArray = @("Item1", "Item2", "Item3")

# Add some item to the array (it's fixed size, so `Add` method won't work)
$myArray += "Item4"

# Remove an item from the array (array is still fixed size, so `RemoveAt` won't work)
$myArray = $myArray -ne "Item2"
```

### ArrayList

Basically dynamic arrays, so you can add and remove items without worrying about the size.

```powershell
# Create a new ArrayList
$myArrayList = New-Object System.Collections.ArrayList

# Add items to the ArrayList without logging output (the index would be logged to console)
$myArrayList.Add("Item1") | Out-Null

# Remove an item from the ArrayList without logging output
# Alternatively, you can use `RemoveAt` to remove by index or use `RemoveRange` to remove multiple items
$myArrayList.Remove("Item1") | Out-Null

# Add multiple items at once without logging output
$myArrayList.AddRange(@("Item2", "Item3", "Item4")) | Out-Null
```
