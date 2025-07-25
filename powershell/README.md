# PowerShell

This section covers information about PowerShell.

## Useful Links
- [PowerShell 7 Beginners Tutorial](https://www.youtube.com/watch?v=NECE5CX69tk&list=PLnK11SQMNnE4vcvuAahz4KhNOS7zOfmB3)
- [PowerShell 7 Intermediates Tutorial](https://www.youtube.com/watch?v=DNbfCMywWeI&list=PLnK11SQMNnE4cjIZlhK3N7K9V92tLM6wf&index=1)
- [PowerShell Gallery](https://www.powershellgallery.com/)


## General Information
- It's best practice to use uppercase letters for each word in a PowerShell command, e.g., `Get-Process` instead of `get-process`.
- When using `Get-Help`, for example, you will see information about syntax, parameters, and more. When you see something like `[[-Name] <string[]>]` in the syntax section, it means that the `-Name` parameter is optional (thus the `[]` around `-Name`) and can accept multiple string values. When you see something like `[-DependentServices]` it means that this is a switch parameter, which does not require a value. If you use it, it will be set to `$true`, otherwise it will be `$false`. In the parameters section of the `Get-Help` cmdlet output, you can find more information about what to pass in for all the parameters.
- There are common parameters supported by most cmdlets, such as `-Verbose`, `-Debug`, `-ErrorAction` - [More Information](https://learn.microsoft.com/de-de/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7.5)
- File ending for PowerShell scripts is `.ps1`, for modules it is `.psm1`, and for module manifest files it is `.psd1`.
- Arrays are not optimized for large datasets (like size > 100) because they have a fixed size (see code example below), so if you need to work with large datasets or need dynamic storage, consider using `System.Collections.Generic.List` or `System.Collections.ArrayList` instead.
- To log a variable to the console, you can simply put the variable name at the end of a script or use `Write-Output` or `echo`. However, `Write-Host` is not recommended for scripts as it writes directly to the console and does not return output to the pipeline.
- `$PROFILE` is a special variable that contains the path to the current user's PowerShell profile script, which runs every time you start PowerShell. You can use it to set up your environment, like adding custom module paths or aliases. Such variables like `$PROFILE` are PowerShell automatic variables, which are predefined and available in every PowerShell session. These are no environment variables, (envirnonment variables would need this structure: `$env:COMPUTERNAME`).
- To reset the default Microsoft Powershell path: `%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe`
- To have tests for your PowerShell modules, you may use the PowerShell Pester module, which is a testing framework for PowerShell. It allows you to write unit tests for your PowerShell scripts and modules. You can install it from the PowerShell Gallery using `Install-Module -Name Pester`.


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


## Some helpful envs
- Current logged-in user: `$env:USERNAME`
- Local machine name (Windows): `$env:COMPUTERNAME`
- Domain or workgroup name: `$env:USERDOMAIN`
- Paths PowerShell uses to find modules: `$env:PSModulePath`
- System path (locations for executables): `$env:PATH`
- Location for temp files: `$env:TEMP` / `$env:TMP`
- User profile path relative to drive: `$env:HOMEPATH`
- Full path to user profile (`C:\Users\YourName`): `$env:USERPROFILE`
- Roaming application data (e.g., configs): `$env:APPDATA`
- Local (non-roaming) app data: `$env:LOCALAPPDATA`
- Windows system directory (`C:\Windows`): `$env:SystemRoot`
- Program Files path (`C:\Program Files`): `$env:ProgramFiles`
- 32-bit Program Files on 64-bit OS: `$env:ProgramFiles(x86)`
- AMD64, ARM64, or x86 (CPU architecture): `$env:PROCESSOR_ARCHITECTURE`
- CPU cores count: `$env:NUMBER_OF_PROCESSORS`
- OS identifier (e.g., Windows_NT): `$env:OS`
- Shows detailed PowerShell version info: `$PSVersionTable`
- Current working directory: `$env:PWD`
- Parent shell information: `$env:SHELL`

-> Helper (list all environment variables): `Get-ChildItem Env:`

## Some PowerShell Commands

- Check whether some package is included in the package json file of your project/s (helpful when checking if a specific version of a package is installed in all your projects): `Get-ChildItem -Path . -Filter package-lock.json -Recurse | Select-String -Pattern "<package-name>@1.0.0"`
- Open the PowerShell profile file from a PowerShell terminal: `explorer $PROFILE`
- Create a new file path: `New-Item -ItemType File -Path "filename.txt"`
- Create a new file with directory path and name: `New-Item -Path "c:\temp" -Name "test01.txt" -ItemType File -Force`
- Remove directory folder: `Remove-Item $env:LOCALAPPDATA\nvim\.git -Recurse -Force`
- Find the path of some file: `Get-ChildItem -Path C:\ -Recurse -Filter "de.utf-8.spl" -ErrorAction SilentlyContinue`
- Set an environment variable locally for the current terminal session in PowerShell: `$env:ENV_NAME = "0"`
- Make a web request, to download some file, for example: `Invoke-WebRequest -Uri "https://ftp.nluug.nl/vim/runtime/spell/de.utf-8.spl" -OutFile "$env:LOCALAPPDATA\nvim\spell\de.utf-8.spl"`
  - The `LOCALAPPDATA` env is special and exists by default. It's a process-level environment variable, meaning it is not stored permanently in the registry like PATH. Instead, Windows dynamically sets it for each user session. It points to `C:\Users\YourUsername\AppData\Local`
- Find all processes running on a specific port (`a` for showing all active connections and listening ports / `n` for displaying addresses and port numbers in numerical form (instead of resolving host names) / `o` for showing the process ID (PID) associated with each connection): `netstat -ano | findstr :PORT`
- Kill a process with specific PID: `taskkill /PID <PID> /F` Based on my configs: `CTRL + R` for back-i-search (reverse incremental search mode, which lets you search backward through your command history)
- Based on my configs: `Tab` for auto-completion in current work directory (also works with git branches)
- List all available commands in PowerShell: `Get-Command`
- Show all running processes in PowerShell: `Get-Process`
- Show all installed services in PowerShell: `Get-Service`
- Get detailed information about a specific service in PowerShell: `Get-Help <cmdlet> -Full`
- Allow scripts to run in PowerShell (if you get an error about execution policy): `Set-ExecutionPolicy RemoteSigned` (or `Unrestricted` if you want to allow all scripts)
- Show PowerShell version: `$PSVersionTable`
- Show PowerShell path: `$PSHOME`
- Show PowerShell profile path: `$PROFILE`
- Show content of file: `Get-Content file.txt`
- Find big files: `Get-ChildItem -Recurse -File | Where-Object { $_.Length -gt 10MB }`
- Measure runtime: `Measure-Command { <command> }`
- Start background job: `Start-Job { Get-EventLog System }`
- See if it's still running or already finished: `Get-Job`
- Once the job is in the Completed state: `Receive-Job -Id <JobId>`
- You can run Receive-Job multiple times only if you use -Keep. Otherwise, the data is cleared after the first read: `Receive-Job -Id <JobId> -Keep`
- Remove a job to clean up: `Remove-Job -Id <JobId>`
- Remove all jobs: `Get-Job | Remove-Job`
- Wait for a job to be done: `Wait-Job -Id <JobId>`
- Adjust/Create the Powershell profile: `notepad $PROFILE` - add `. path_to_script` in there to make the powershell script globally available in all sessions



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

### HashTable

HashTables are key-value pairs, similar to dictionaries in other programming languages. They are useful for storing related data. They are not ordered, so the order of items is not guaranteed.

```powershell
# Create a new HashTable
$myHashTable = @{
    key1 = "Value1"
    key2 = "Value2"
}

# Get a value by key (check if existing with .ContainsKey)
$myHashTable["key1"]

# Add a new key-value pair
$myHashTable.Add("key3", "Value3")
$myHashTable["key3"] = "Value3" # Alternative way to add or update

# Remove a key-value pair
$myHashTable.Remove("key3")
```

### Custom Objects

Custom objects allow you to create structured data with properties and methods. 
They are useful for organizing data in a more readable way.

```powershell
# Create a custom object with properties
# It basically casts a HashTable to a PSCustomObject
$Employee1 = [PSCustomObject]@{
    Name = "John Doe"
    Age = 30
    Position = "Developer"
}

# This above was a shorthand way to create a custom object.
# You may also do it all manually like this, for example:
$Employee2 = New-Object -TypeName PSCustomObject 
Add-Member -InputObject $Employee2 -MemberType NoteProperty -Name "Name" -Value "Jane Smith"
Add-Member -InputObject $Employee2 -MemberType NoteProperty -Name "Age" -Value 28
Add-Member -InputObject $Employee2 -MemberType NoteProperty -Name "Position" -Value "Designer"
```

### Pipelines

Pipelines allow you to pass the output of one command as input to another command.

- Each command passes objects, not plain text, to the next command.
- You filter (Where-Object), sort (Sort-Object), select (Select-Object), and act on these objects downstream.
- This object-based pipeline is what makes PowerShell so flexible compared to traditional shells like Bash.

```powershell
# Get all running processes, filter by CPU usage, sort by CPU usage, and select the top 5
Get-Process | Where-Object { $_.CPU -gt 100 } | Sort-Object CPU -Descending | Select-Object -First 5

# List Top 10 Largest Files in a Folder
Get-ChildItem -Path "C:\Logs" -Recurse |
    Where-Object { -not $_.PSIsContainer } |
    Sort-Object Length -Descending |
    Select-Object FullName, Length -First 10

# Find all services that are stopped and start them
Get-Service |
    Where-Object { $_.Status -eq 'Stopped' } |
    Start-Service

# Kill chrome processes
Get-Process chrome |
    Stop-Process -Force

# Export all running services to a CSV file
Get-Service |
    Where-Object { $_.Status -eq 'Running' } |
    Select-Object Name, Status |
    Export-Csv -Path "C:\running-services.csv" -NoTypeInformation

# Extract event logs and filter by keyword
Get-EventLog -LogName Application -Newest 1000 |
    Where-Object { $_.Message -like "*error*" } |
    Select-Object TimeGenerated, Source, Message |
    Out-GridView
```

### Some Comparison Operators

```powershell
1 -eq 1       # Equals -> True
1 -ne 2       # Not Equals -> True
1 -lt 2       # Less than -> True
2 -le 2       # Less than or equal -> True
3 -gt 2       # Greater than -> True
2 -ge 2       # Greater than or equal -> True
```

### Some Array Membership Operators

```powershell
@(1, 2, 3) -contains 2       # True (case-insensitive for strings)
@(1, 2, 3) -ccontains 2      # True (ccontains is case-sensitive, works the same for numbers)

@('Test', 'test') -contains 'test'      # True (case-insensitive)
@('Test', 'test') -ccontains 'test'     # True
@('Test', 'test') -ccontains 'Test'     # True
@('Test', 'test') -ccontains 'TeSt'     # False (case-sensitive)
```

### Some String Matching Operators

```powershell
"PowerShell" -like "*Shell"             # True (wildcard, case-insensitive)
"PowerShell" -clike "*Shell"            # True (case-sensitive)
"PowerShell" -clike "*shell"            # False (case-sensitive)

"PowerShell" -notlike "*bash*"          # True

"PowerShell123" -match "\d+"            # True (regex match)
"PowerShell" -notmatch "\d+"            # True (no digits)

# Regex Replace
"abc123" -replace "\d+", "XYZ"          # "abcXYZ"
```

### Some Logical Operators

```powershell
(1 -eq 1) -and (2 -eq 2)                # True
(1 -eq 1) -or (2 -eq 3)                 # True
-not (1 -eq 2)                          # True
!(1 -eq 2)                              # True (shortcut for -not)
```

### Some Type Operators

```powershell
"hello" -is [string]                    # True
123 -is [int]                           # True
"123" -isnot [int]                      # True
```

### Escaping

```powershell
Write-Output "This is a double quote: `"`"  # Escaping double quotes
```

### Switch Statement

```powershell
# Base example
switch ($variable) {
    "Value1" { 
      Write-Output "Matched Value1" 
      break
    }
    "Value2" { 
      Write-Output "Matched Value2" 
      break 
    }
    default { 
      Write-Output "No match found" 
      break
    }
}

# Example with dynamic conditions without breaks
switch ($variable) {
    { $_ -is [int] } { Write-Output "It's an integer" }
    { $_ -is [string] } { Write-Output "It's a string" }
    { $_ -is [bool] } { Write-Output "It's a boolean" }
    { $_ -is [array] } { Write-Output "It's an array" }
    { $_ -is [hashtable] } { Write-Output "It's a hashtable" }
    { $_ -is [PSCustomObject] } { Write-Output "It's a custom object" }
    { $_ -is [System.Collections.ArrayList] } { Write-Output "It's an ArrayList" }
    { $_ -is [System.Collections.Generic.List] } { Write-Output "It's a List" }
    { $_ -lt 2 } { Write-Output "It's less than 2" }
    { $_ -gt 2 } { Write-Output "It's greater than 2" }
    { $_ -eq 2 } { Write-Output "It's equal to 2" }
    { $_ -ne 2 } { Write-Output "It's not equal to 2" }
    { $_ -in (0..9) } { Write-Output "It's in the list 1, 2, 3" }
    { $_ -notin 4, 5, 6 } { Write-Output "It's not in the list 4, 5, 6" }
    { $_ -like "*test*" } { Write-Output "It matches the pattern *test*" }
    { $_ -clike "*test*" } { Write-Output "It matches the case-sensitive pattern *test*" }
    { $_ -notlike "*test*" } { Write-Output "It does not match the pattern *test*" }
    { $_ -notclike "*test*" } { Write-Output "It does not match the case-sensitive pattern *test*" }
    { $_ -match "\d+" } { Write-Output "It matches the regex \d+" }
    { $_ -notmatch "\d+" } { Write-Output "It does not match the regex \d+" }
    { $_ -like "*test*" } { Write-Output "It matches the pattern *test*" }
    { $_ -notlike "*test*" } { Write-Output "It does not match the pattern *test*" }
    default { Write-Output "Unknown" }
}
```

### Loops

```powershell
# For loop
for ($i = 1; $i -le 5; $i++) {
    Write-Output "Number: $i"
}

# Foreach loop (array iteration) - can also be used like $array.ForEach({ $_ })
$items = @("Apple", "Banana", "Cherry")
foreach ($item in $items) {
    Write-Output "Fruit: $item"
}

# While loop
$count = 0
while ($count -lt 3) {
    Write-Output "Count is $count"
    $count++
}

# Do-While loop (runs at least once)
$counter = 0
do {
    Write-Output "Do count: $counter"
    $counter++
} while ($counter -lt 3)

# Do-Until loop (runs until condition is true)
$n = 0
do {
    Write-Output "Until loop iteration $n"
    $n++
} until ($n -ge 3)

# Foreach-Object (pipelined loop)
1..5 | ForEach-Object {
    Write-Output "Piped number: $_"
}
```

### Try Catch Finally

This is used for error handling in PowerShell scripts.

```powershell
# Basic Try-Catch
try {
    # Intentionally causing an error (division by zero)
    $result = 10 / 0
    Write-Output "Result: $result"
}
catch {
    Write-Output "An error occurred: $($_.Exception.Message)"
}

# Try-Catch-Finally (with cleanup step)
try {
    Write-Output "Trying risky operation..."
    # Simulating error
    Get-Item "C:\This\Does\Not\Exist.txt"
}
catch {
    Write-Output "Caught Error: $($_.Exception.Message)"
}
finally {
    Write-Output "This runs no matter what (cleanup code)."
}

# Specific Exception Type (optional)
try {
    [int]::Parse("NotANumber")  # Causes FormatException
}
catch [System.FormatException] {
    Write-Output "Caught FormatException: $($_.Exception.Message)"
}
catch {
    Write-Output "Caught a general exception: $($_.Exception.Message)"
}

# Multiple Catch Blocks
try {
    # Choose your error:
    # Throw "general error"
    [int]::Parse("abc")
}
catch [System.FormatException] {
    Write-Output "Caught a FormatException."
}
catch {
    Write-Output "Caught a general exception."
}

# Throwing Custom Exceptions
try {
    throw "Custom error message from script"
}
catch {
    Write-Output "Caught custom error: $($_.Exception.Message)"
}

# Stop process with -ErrorAction
# By default, many PowerShell errors are non-terminating (they print but don't stop execution).
# You can promote them to terminating errors:
try {
    Get-Item "C:\DoesNotExist.txt" -ErrorAction Stop
}
catch {
    Write-Output "Error occurred, script will stop."
}

Write-Output "This will not run after throw."

# Alternatively, you can also declare the global behavior for the whole script (at the top of the current script file):
$ErrorActionPreference = 'Stop'


# Show the most recent error message in the current session
$Error[0] | Format-List -Force
```

### Modules

- A module is a package of PowerShell functions, cmdlets, variables, and scripts you can import and use.
- Helps organize reusable code (like libraries in programming languages).

```powershell
# Check where PowerShell looks for modules
$env:PSModulePath -split ';'
```

This shows a list of folders, like:
- For current user: C:\Users\<User>\Documents\PowerShell\Modules
- System-wide: C:\Program Files\PowerShell\Modules
You can place your custom modules in these folders. 
Only modules in these folders will be automatically loaded/recognized when you use their commands.

However, you may also add custom paths to `$PROFILE` which is a script (a variable path to a script) that runs every time you start PowerShell, so you can add custom module paths there:

```powershell
# Within $PROFILE
$env:PSModulePath += ";C:\Users\YourUser\Documents\powershell_customs"
```

```powershell
# List installed modules
Get-Module -ListAvailable
```

```powershell
# Install Module from PowerShell Gallery
Install-Module -Name Az -Scope CurrentUser
```

```powershell
# Import a module
Import-Module Az

# List commands from a module
Get-Command -Module Az

# Use a command
Get-AzSubscription
```

```powershell
# Create a custom module (.psm1 in e.g. C:\Path\To\MyTools)
function Get-Greeting {
    param(
        [string]$Name = "World"
    )
    "Hello, $Name!"
}

# Create a module manifest for the custom module (.psd1 in e.g. C:\Path\To\MyTools)
# This cmdlet will create a module manifest file that describes the module, its version, author, and other metadata
New-ModuleManifest -Path "C:\Path\To\MyTools\MyTools.psd1" `
                   -RootModule "MyTools.psm1" `
                   -Author "Your Name" `
                   -Description "Example custom PowerShell module" `
                   -ModuleVersion "1.0.0"

# You can import this module in another script or session like this:
Import-Module MyTools
Get-Greeting -Name "Alex"

# You may also export only specific functions
Export-ModuleMember -Function Get-Greeting, Other-Function

# Import a custom module from a specific path (needed, if the path is not part of $env:PSModulePath)
Import-Module "C:\Path\To\MyTools\MyTools.psm1"
```


### Functions

_Rule of Thumb:_
- Without pipeline input? → Skip `process {}`.
- With pipeline input? → Use `process {}`.
- Complex multi-stage processing? → You can also use `begin {}`, `process {}`, and `end {}` together.

The `CmdletBinding()` attribute is used to define a function as a cmdlet, which allows you to use advanced features like parameter validation, pipeline input, and more.

```powershell
# Basic Function
function Get-Greeting {
    param (
        [string]$Name = "World"
    )
    Write-Output "Hello, $Name!"
}

# Usage
Get-Greeting -Name "Alice"


# Function with pipeline input
# process() is needed to process each input item individually (when accepting pipeline input via [Parameter(ValueFromPipeline=$true)]).
function Get-SquaredNumber {
    [CmdletBinding()]
    param (
        [Parameter(ValueFromPipeline = $true)]
        [int]$Number
    )

    process {
        $result = $Number * $Number
        Write-Output $result
    }
}

# Usage with pipeline
1, 2, 3, 4 | Get-SquaredNumber


# Function with multiple parameters and Verb-Noun naming
function Set-UserStatus {
    [CmdletBinding()]
    param (
        [Parameter(Mandatory=$true)]
        [string]$Username,

        [Parameter(Mandatory=$true)]
        [ValidateSet("Active", "Inactive")]
        [string]$Status
    )

    process {
        Write-Output "Setting status of $Username to $Status."
    }
}

# Usage
Set-UserStatus -Username "jdoe" -Status "Active"


# Summing Numbers from Pipeline
function Get-Sum {
    [CmdletBinding()]
    param (
        [Parameter(ValueFromPipeline = $true, Mandatory = $true)]
        [int]$Number
    )

    # Runs once before any pipeline input is processed
    begin {
        $sum = 0
        Write-Verbose "Starting sum calculation..."
    }

    # Runs once per pipeline input
    process {
        Write-Verbose "Adding $Number to total sum."
        $sum += $Number
    }

    # Runs once after all pipeline input has been processed
    end {
        Write-Output "Total sum: $sum"
    }
}

# Example usage with pipeline
1, 2, 3, 4, 5 | Get-Sum -Verbose
```

### Remoting

Remoting refers to the ability to run commands or scripts on remote computers — securely and efficiently.

Enable PowerShell Remoting (on the remote machine): `Enable-PSRemoting -Force`
This sets up WinRM (Windows Remote Management), configures listeners, and allows remote connections.

_Notes:_
- Windows Firewall must allow WinRM.
- Trusted hosts may need configuration for workgroups (`Set-Item WSMan:\localhost\Client\TrustedHosts -Value 'machine_name,machine_ip_address'`).
- Linux/macOS: You can use SSH-based remoting (PowerShell 7+).

```powershell
# Start interactive session
# Prompts you for credentials
# You get an interactive remote shell on RemotePC
# Type exit to leave the session
Enter-PSSession -ComputerName "RemotePC" -Credential (Get-Credential)

# Invoke Command on Remote Machine (One-Off Commands)
# Runs Get-Process on RemotePC and returns the result locally.
Invoke-Command -ComputerName "RemotePC" -Credential (Get-Credential) -ScriptBlock {
    Get-Process
}

# Remoting to Multiple Machines (Parallel Execution)
# Runs Get-Date on all servers and collects output
# $computers would have the ip addresses of the remote machines
$computers = @("Server01", "Server02", "Server03")

Invoke-Command -ComputerName $computers -Credential (Get-Credential) -ScriptBlock {
    Get-Date
}

# Persistent Session (Reuse Connection)
# New-PSSession creates a reusable connection, reducing authentication overhead
$session = New-PSSession -ComputerName "RemotePC" -Credential (Get-Credential)

# Run multiple commands using the same session
Invoke-Command -Session $session -ScriptBlock { Get-Service }

# Clean up
Remove-PSSession $session
```

### Pester 

You will need to have Pester installed: `Install-Module -Name Pester -Force`

```powershell
# Some example function
function Get-Greeting {
    param([string]$Name)
    "Hello, $Name!"
}

# Within a test file (e.g. MyModule.Tests.ps1)
# Import the module you're testing
Import-Module "$PSScriptRoot\MyModule.psm1"

Describe "Get-Greeting Tests" {
    It "Should return a greeting with the provided name" {
        $result = Get-Greeting -Name "Alice"
        $result | Should -Be "Hello, Alice!"
    }

    It "Should not return an empty string" {
        $result = Get-Greeting -Name "Bob"
        $result | Should -Not -BeEmpty
    }
}

# Run the test
Invoke-Pester -Path .\MyModule.Tests.ps1
```

### Import CSV file
```powershell
# Example CSV file content:
# Name;Age;City
# Alice;30;New York
# Bob;25;Los Angeles
# Charlie;35;Chicago

# Import CSV with semicolon delimiter
$data = Import-Csv -Path "C:\Path\To\data.csv" -Delimiter ';'

# Display all imported data
$data

# Example: Format output to show only Name and City in a table
$data | Format-Table Name, City -AutoSize

# Example: Filter where Age > 28
$data | Where-Object { [int]$_.Age -gt 28 } | Format-Table -AutoSize

# Export Modified Data Back to CSV with a Different Delimiter
$data | Where-Object { [int]$_.Age -gt 28 } | Export-Csv -Path "C:\Path\To\filtered.csv" -Delimiter ',' -NoTypeInformation
```

### Read JSON from a file

```powershell
# Read JSON file content as string
$jsonString = Get-Content -Path "C:\Path\To\data.json" -Raw

# Convert JSON string to PowerShell object
$data = $jsonString | ConvertFrom-Json

# Access properties
$data.Name           # Outputs: Alice
$data.Age            # Outputs: 30
$data.Skills[0]      # Outputs: PowerShell
$data.Address.City   # Outputs: New York

# Add a new property
$data.Location = "USA"

# Convert back to JSON (pretty formatted)
$jsonOutput = $data | ConvertTo-Json -Depth 3

# Save modified JSON to a new file
$jsonOutput | Set-Content -Path "C:\Path\To\modified_data.json"
```

### Sending POST request with JSON formatted data

```powershell
# Create body as a PowerShell hashtable
$jsonBody = @{
    Name = "Alice"
    Age = 30
    Skills = @("PowerShell", "C#", "Azure")
    Address = @{
        City = "New York"
        Zip = "10001"
    }
}

# Convert to JSON string
$jsonString = $jsonBody | ConvertTo-Json -Depth 3

# POST JSON to API endpoint
$response = Invoke-RestMethod -Uri "https://api.example.com/users" `
                              -Method Post `
                              -Body $jsonString `
                              -ContentType "application/json"

# Display response data
$response | Format-List
```
