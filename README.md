# Personal Documentation for relevant topics and keywords

This personal documentation can be best used by using CTRL + F to search for specific keywords.

## General Commands

- Perform a hard refresh to bypass the browser cache: `Ctrl + Shift + R`
- Create an empty file via terminal: `type nul > .env`
- Create a file with input via terminal: `echo DB_HOST=localhost > .env`
- Create new folder via terminal: `mkdir folder_name`
- Sending a ping to a domain / ip address: `ping example.com`
- Open IP Config: `ipconfig` & `ipconfig /all`
- Set Global Git User Name: `git config --global user.name "Max Mustermann"`
- Set Global Git User Email: `git config --global user.email "example@gmail.com"`
- On Current Cursor Position Import: _CTRL + ._
- Toggle Terminal in VS Code: _CTRL + J_
- Show all currently running processes on the system: `tasklist`
- Terminate tasks by process ID or image name: `taskkill`
- Display detailed configuration information about a computer and its operating system: `systeminfo`
- Select all Occurrences of Current Word in VS Code: `Ctrl + F2`
- Select Next Occurrence of Current Word in VS Code: `Ctrl + D`
- Add Cursors to Line Ends in VS Code: `Ctrl + Alt + Down` / `Ctrl + Alt + Up`
- Add Cursor in VS Code: `Alt + Click`
- Remove local references to remote branches that no longer exist: `git fetch --prune`
- Delete local Git branches: `git branch -d branchname`
- Delete Remote Repository connection (via GitLab etc.): `git push origin --delete branchname`
- Remove remote origin via Git: `git remote remove origin`
- Change Terminal Background (`settings.json`): `%localappdata%\Packages\Microsoft.WindowsTerminal_8wekyb3d8bbwe\LocalState`
- Access experimental Chromium features (search for ...): `chrome://flags/`
- Jump to a Commit in the Past (You have to Start a new branch from here if you want to build upon it): `git checkout <commit-hash>`
- Discard all not yet committed changes: `git restore .`
- Create a new named migration file: `npm run migration:generate -- -n init`
- Migrate Database to most current version based on migration files (used after entities and migration files were added): `npm run migration:run`
- Start Next.js application on a different port (in package.json for port 8080): `"dev": "next dev -p 8080"`
- Start a simple HTTP server in the current directory: `python -m http.server`
- Delete .git in PowerShell (Visual Studio Code): `Remove-Item -Path .git -Recurse -Force`
- Delete .git in Windows Command Prompt: `rmdir /s /q .git`
- Reset the current git user to log in with new credentials (have to push after this command): `git config --global credential.helper wincred`
- Reset all unstaged/staged local changes: `git reset --hard`
- Forcefully update dependencies to fix vulnerabilities, potentially causing breaking changes: `npm audit fix --force`
- Rename current branch (use -M if only the capitalization changes): `git branch -m <newname>`
- Rename a branch while pointed to any branch: `git branch -m <oldname> <newname>`
- Check the current remote repository URL: `git remote -v`
- Set a new remote repository URL: `git remote set-url origin https://neuerstandort.com/meinrepo.git`
- Unset the git user password (use push afterwards to enter new credentials): `git config --global --unset user.password`
- Change the casing for files via git (can't be done by just editing the files manually): `git mv -f current_file_name new_file_name`
- Start solving merge conflicts (while being on the branch to merge; use `git fetch` before): `git rebase origin/target_merge_branch`#
- Prisma generate: `npx prisma generate`
- Prisma migrate: `npx prisma migrate dev --name init`
- Prisma migrate deploy: `npx prisma migrate deploy`
- Open command pallete in VS Code (for reloading the window, for example): `CTRL + Shift + P`#
- Programmatically reload page: `window.location.reload()`
- Open a CMD prompt from current file explore path (in a specific file explorer folder): `CTRL + L` -> Type in `cmd` or `powershell`
- Add a git tag via command line (on commit which should be tagged): `git tag -a v1.0`, then `git push origin --tags` (use `git show` to see current commit)
- Save without formatting in VS Code: `CTRL + P + >`, then `Save without formatting`
- Create a base64 string based on a string input in the console: `echo -n 'username:password' | base64`
- Set an environment variable locally for the current terminal session in powershell: `$env:ENV_NAME = "0"`
- Link your npm package: `pnpm link --global` | then link to it from your application's directory: `pnpm link your-package-name` | do both commands but with `unlink` to unlink the package from the application and unlink it globally as well
- Adjust/Create the Powershell profile: `notepad $PROFILE` - add `. path_to_script` in there to make the powershell script globally available in all sessions
- Unstage a staged file: `git reset file_path`
- rebase current branch onto target branch (for example, feature branch as current branch and main branch as target_branch): `git rebase origin/target_branch`
- Get system information (including RAM): `wmic memorychip list full`
- Get information specifically for RAM: `Get-CimInstance win32_physicalmemory | Format-Table Manufacturer,Banklabel,Configuredclockspeed,Devicelocator,Capacity,Serialnumber -autosize`
- Add Basic Auth with base64 string: `'Authorization': 'Basic ' + (new Buffer.from(client_id + ':' + client_secret).toString('base64'))`
- Open command line in chrome developer tools (to disable/enable JavaScript, for example): `CTRL + SHIFT + p`
- Rename a file/folder recognized by git: `git mv source target_name`
- Open PowerToys Selection for a file: `Shift + Rightlick`
- Open current folder via terminal in VS Code: `code .`
- Open File Explorer from current directory (on Windows via PowerShell): `start .`
- With Copilot in VS Code, open the Copilot chat: `CTRL + i`
- Open something with powertoys: `Shift + Rightclick`
- In here are the nvim configs (or should be placed if they are not there yet): `~/AppData/Local/nvim`
- Globally link a package (from package's directory; build package to have it updated for testing (like with rollup, for example)): `pnpm link --global`
- Link a globally linked package to an application (from application's directory; delete installed version of package before if necessary): `pnpm link --global linked_package`
- View PATH variables with one entry per row: `$env:Path -split ";"`
- Use `theme()` and `@apply` to make use of Tailwind CSS within normal .css files / data attributes are another way to handle specific styling situations
- Git Add to stage with specific files excluded: git add --all -- :!path/to/file1 :!path/to/file2 :!path/to/folder1/\*

## Linux Commands

- Start WSL: `wsl`
- Delete .git on Linux: `rm -rf .git`
- Search for files or directories containing the word "wget": `ls -laR . | grep wget` (`ls` lists the contents of directories, `-l` provides a detailed (long) listing of files, including permissions, owner, size, and modification date, `-a` includes hidden files (those starting with .), `-R` recursively lists the contents of all subdirectories within the current directory (. represents the current directory), The pipe takes the output of the first command `ls -laR .` and sends it as input to the second command `grep wget`, `grep` searches for lines containing the specified pattern `wget` in the input it receives - here, it filters the output of `ls -laR .` and displays only lines containing the word `wget`)
- Exit the current terminal session: `exit`
- Run any command as the root user (input the actual command for "..."): `sudo ...`
- Switch to the root account (if access to sudo is available): `sudo -i`
- Access the commandline package manager (lists the available commands with apt) - used with Debian-based linux distributions (like Ubuntu): `apt`
- Check the current position in the file system: `pwd`
- List the directories/files at the current file system position: `ls`
- List the directories/files at the current file system position with a long list (more details): `ls -l`
- List the directories/files at a different file system position (without having to move to that position with `cd`; swap "_path_" with the actual path to investigate): `ls _path_`
- Change the current directory (enter a relative or absolute path): `cd ...`
- Get to the home directory: `cd ~`
- Rename a file/folder: `mv source target_name`
- Create a new folder: `mkdir folderName`
- Create a new file: `touch fileName`
- Remove a file (or multiple ones; with a pattern in this example (all files starting with "file")): `rm file*`
- Remove a folder: `rm -r folderName/`
- Edit file on Linux (with nano): `sudo nano /etc/resolv.conf`
- Save a file in nano: `Ctrl` + `o`
- Look into file on Linux (for small files): `cat /etc/resolv.conf`
- Look into a file (in an interactive way; for large files): `less /etc/resolv.conf`
- Search for words in a file (or multiple files with wildcard): `grep -i someWord file*`
- Show all files (including hidden ones): `ls -a`
- See all environment variables on the machine: `printenv`
- See environment variables for a particular variable (PATH in this example): `printenv PATH`
- Set an environment variable for only the current terminal session: `export ENV_NAME=ENV_NAME_VALUE`
- Check current processes: `ps`
- Kill a process (PID can be identified via `ps` command): `kill PID`
- Get to the home directory: `cd ~`
- `ipconfig` but for linux: `ifconfig` (at `eth0`)
- Show the path to the executable of a software (nvim in this example): `which nvim`
- In here are the nvim configs (or should be placed if not available yet): `~/.config/nvim`
- Find Docker Volume sizes: `du -h --max-depth=1 /var/lib/docker/volumes/`
- See directory sizes: `df -h`
- See system hardware usage: `htop`

## Powershell Commands

- Create a new file path: `New-Item -ItemType File -Path "filename.txt"`
- Create a new file with path for the directory and name: `New-Item -Path "c:\temp" -Name "test01.txt" -ItemType File -Force`

## Docker & Inside a Container Commands

- Enter a mariadb shell (with Docker Desktop you already have the shell accessible): `docker exec -it container_name -u root -p`
- Build an image with a set variable by adding `ARG SOME_VAR` and then afterwards you can use it like `RUN npm config set -- //npm.fontawesome.com/:_authToken="${SOME_VAR}"` (within the Dockerfile) if you run a command like: `docker buildx build --build-arg SOME_VAR=123123 -t my_application .`
- Create a custom volume (to be able to name it): `docker volume create named_volume`
- Stop a Container: `docker stop container_name_or_id`
- Remove a Container: `docker rm container_name_or_id`
- Run a container with a specific name and volume: `docker run --name my-mariadb-container -p 3306:3306 -v <volume_name>:/var/lib/mysql -e MARIADB_ROOT_PASSWORD=my-secret-pw -d mariadb` (potentially add `--bind-address=0.0.0.0`)
- When using Docker Desktop, assign a volume like this: `Host Path: /var/lib/docker/volumes/<volume-name>/_data` and `Container Path: /var/lib/mysql`

- Select MySQL database: `USE database_name;`
- Connect to PostgresSQL database: `\c database_name`
- Show tables of a MySQL database: `show tables;`
- Show tables of a PostgresSQL: `\dt`

## General Neovim & Neovim in VS Code & general VS Code

- Access Package Manger: `:Lazy`
- Access Neotree: `:Neotree`
- Open a terminal at the bottom: `:belowright split | terminal`
- Copy the full path to the clipboard: `:let @+=expand('%:p')`
- Resize a window (8 lines as example): `:resize 8`
- Resize a window vertically: `:vertical resize 30`
- Move backwards: `b`
- Normal Yank: `y`
- Yank to use outside of the editor: `"+y`
- Switch to terminal (actually toggle terminal): `CTRL + ö`
- Switch to main editor window: `CTRL + 1`
- Open external terminal with project's path: `CTRL + SHIFT + c`
- Open VS Code project's search bar: `CTRL + p`
- Open VS Code settings search bar: `CTRL + SHIFT + p`
- Switch between currently opened editor windows: `CTRL + Tab`
- Search in a file: `/ + search_phrase`
- Multiline comments: `s/^/\/\/`
- Replace anything in selected area: `s/replace/replace_with`
- Tab through side bar: `CTRL + q`
- Tab in Explorer Side Bar Tab (Use spacebar or enter to select/jump in file): `CTRL + Shift + e`
- Tab in Search Bar: `CTRL + Shift + f`
- Toggle Side Bar (can't be used with Neovim): `CTRL + b`
- Open new split windows or jump to the respective one: `CTRL + x` (2 for x, for example)
- Switch from one Split View to another: `CTRL + w`
- Select multiple lines with specific amount of columns (to remove multi-line comments, for example): `CTRL + v`
- Close all editors in other groups (requires keybind for `"workbench.action.closeEditorsInOtherGroups"`): `ALT + q`
- Add text via command line (for multi-select): `normal a` or `normal i`
- Move a block of code: select area to move and then `ALT + arrow_keys`
- Open new split view with current selected file (or close a split view): `CTRL + ALT + arrow_keys (left and right)`
- While having the cursor on a component, open the corresponding file: `F12`
- Comment out a selected area: `CTRL + #`
- Move from the search field (in the left sidebar) down to the file selection: `CTRL + arrow_down`
- Increase view width of current selected window (custom shortcut, see 'Keyboard Shortcuts (JSON)'): `CTRL + SHIFT + arrow_right`
- Decrease view width of current selected window (custom shortcut, see 'Keyboard Shortcuts (JSON)'): `CTRL + SHIFT + arrow_left`
- Close all but current selected window (custom shortcut, see 'Keyboard Shortcuts (JSON)'): `ALT + q`
- With cursor on an opening or closing bracket, jump to the respective opening or closing bracket: `SHIFT + 5`
- Delete current word: `d + w`
- Search for next occurence of a character in the current line (backwards with uppercase): `f + search_for`
- Search for next occurence of a character in the current line but place the cursor to the preceding position (backwards with uppercase): `t + search_for`
- Repeat the preceding change: `.`
- Enter a register (register_key can be a-z): `q{register_key} + commands + q` -> use it with `@register_key`
- Switch current terminal (if multiple are available) in VS Code: `CTRL + PageDown/PageUp`
- Scroll up and down in current terminal in VS Code: `CTRL + ALT + PageDown/PageUp`
- Display error information while having the cursor on it (is not working in vim mode): `CTRL + k + i`
- Vertically increase terminal (custom shortcut for terminal resize): `CTRL + numpad_8`
- Vertically decrease terminal (custom shortcut for terminal resize): `CTRL + numpad_2`
- Add/remove spaces at the start of a line (like `Tab` or `Shift + Tab`) (also works with multiple lines selected): Open Command line with `:`, then use `normal <<` or `normal >>`
- If VS Code Neovim with WSL is used, add this to the `init.lua` if it has trouble be recognized by VS Code: `If vim.g.vscode then ... else ... your_nvim_config ... End`
- Get to the "Problems" tab in VS Code (pick respective problem to jump there): `CTRL + SHIFT + m`

## Packages

- [react-use - collection of utils](https://www.npmjs.com/package/react-use)
- [animejs - lightweight JavaScript animation library](https://www.npmjs.com/package/animejs)
- [gsap-quicktools - my animation quicktools package](https://www.npmjs.com/package/gsap-quicktools)
- [react-hammerjs - mobile device touch event support](https://www.npmjs.com/package/react-hammerjs)
- [sharp - converting images for better efficiency](https://www.npmjs.com/package/sharp)
- [react-intersection-observer - monitor the visibility of different sections on a webpage and dynamically execute actions](https://www.npmjs.com/package/react-intersection-observer)

## Common Terms

- _extends_: It's used for class inheritance. When you use extends, the class you are defining inherits properties and methods from the base class. Inheritance is a way to create a new class from an existing class. The new class (child class) gets access to the properties and methods of the existing class (parent class), allowing for code reuse and maintaining a hierarchical class structure.

- _implements_: It's used when a class intends to fulfill the contract provided by an interface. An interface in TypeScript is a structure that defines a contract in your application. It defines the syntax for classes to follow. Classes that implement an interface must provide an implementation for all the properties and methods defined in the interface.

- _Universally Unique Identifier (UUID)_: A UUID is a 128-bit value used to uniquely identify an object or entity on the internet. Depending on the specific mechanisms used, a UUID is either guaranteed to be different or is, at least, extremely likely to be different from any other UUID generated until A.D. 3400.

- _SCRUM_: SCRUM is an agile development methodology used primarily for managing software development projects. It aims to improve team collaboration and speed up the development process. The process starts with planning, where the team selects tasks from the backlog to complete during the sprint (a set period during which specific work must be completed). At the end of the sprint, the team reviews the work and reflects on improvements for the next sprint.

- _static_: The static keyword in programming languages, including Dart, JavaScript, C#, (for Python you would use `@staticmethod`), is used to declare class-level variables and methods, meaning they belong to the class itself rather than any individual instance of the class. When you declare a variable or method as static, it exists independently of any object instances. You can access these static members using the class name instead of a specific instance. Static variables and methods are stored in memory differently than instance variables and methods. There's only one copy of a static member, shared by all instances of the class, which can be more memory efficient. Static variables are initialized when the class is loaded into memory, not when instances of the class are created. Static methods can only directly access other static members. They cannot access non-static members (instance variables or methods) directly because they are not associated with any instance of the class. Often, static methods are used as utility functions that perform a task not dependent on the state of an instance.

- _Proxy Server_: A proxy server, in the context of web development and networking, acts as an intermediary between a client (such as a web browser) and a server (like a web service). It sits between end users and the services they want to access. When a client makes a request, the proxy server forwards it to the appropriate server, gets the response, and sends it back to the client. Proxy servers are used for various purposes, including improving performance through caching, filtering requests for security, and circumventing geographic restrictions.

- _Document Object_: When an HTML document is loaded into a web browser, it becomes a document object. The document object is the root node of the HTML document. The document object is a property of the window object. The document object is accessed with: `window.document` or just `document`.

- _Parsing_: Parsing is the process of converting formatted text into a data structure. A data structure type can be any suitable representation of the information engraved in the source text.

- _Watch Mode (--watch flag)_: The --watch flag is commonly used in various command-line tools and development environments to enable a "watch mode." When you run a command with the --watch flag, the tool keeps running and continuously monitors specified files or directories for changes. If any changes are detected, the tool automatically re-runs a specific part of its operation related to those changes. This feature is particularly useful in software development for various purposes:

- _WSDL_ [Link](https://www.w3schools.com/XML/xml_wsdl.asp): WSDL stands for Web Services Description Language. WSDL is used to describe web services. WSDL is written in XML. An WSDL document describes a web service. It specifies the location of the service, and the methods of the service.

- _SOAP_ [Link](https://www.w3schools.com/XML/xml_soap.asp): SOAP stands for Simple Object Access Protocol. SOAP is an application communication protocol. SOAP is a format for sending and receiving messages. SOAP is platform independent. SOAP is based on XML. SOAP provides a way to communicate between applications running on different operating systems, with different technologies and programming languages.

- _Serialization_: Serialization involves converting an object into a format that can be easily stored or transmitted. For example, in a web application, you might serialize a data object into JSON format before sending it over the network to a client or saving it to a database. The primary purpose of serialization is to save or transmit data in a form that can be easily transported and reconstructed later. It's particularly useful in distributed systems, where data must be transferred across different network nodes. Common serialization formats include JSON, XML, and binary formats. The choice of format depends on the requirements for readability, size, and compatibility.

- _Deserialization_: Deserialization is the reverse process of serialization. It involves taking data structured from a simple format (like a JSON string) and rebuilding it into an object or data structure suitable for use in computer programs. Deserialization is used to reconstruct data received over a network or read from a persistent storage into usable objects or data structures. A key challenge with deserialization is ensuring that the data is accurately and securely reconstructed. Incorrect or maliciously crafted data can lead to errors or security vulnerabilities (like injection attacks).

- _Adding DNS to resolv.conf_: Adding a DNS (Domain Name System) server to the resolv.conf file on your computer means specifying which DNS servers your computer should use to translate domain names (like www.example.com) into IP addresses. The resolv.conf file is a configuration file for DNS resolution, typically found on Unix-like operating systems, including Linux and macOS. When your computer needs to find the IP address associated with a domain name, it refers to this file to determine which DNS servers to query. Important files for this process are `/etc/resolv.conf` and `/etc/wsl.conf`

- _Execution Policies for Windows Computers_: An execution policy is part of the PowerShell security strategy. Execution policies determine whether you can load configuration files, such as your PowerShell profile, or run scripts. And, whether scripts must be digitally signed before they are run - [Set-ExecutionPolicy](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.security/set-executionpolicy?view=powershell-7.4)

- _`sudo` & `cat` on Linux_: `sudo` is a command that you use to obtain root privileges. `cat` is used to read a file - [More Information](https://askubuntu.com/questions/429944/difference-between-cat-and-sudo-cat)

- _CORS_: CORS (Cross-Origin Resource Sharing) is a security feature implemented in web browsers to restrict how resources on a web page can be requested from another domain. When a script on a web page tries to request resources from a different domain, CORS policy comes into play. This is done to prevent malicious websites from making requests on behalf of a user without their consent, a security issue known as Cross-Site Request Forgery (CSRF). For example, if your JavaScript code running on https://domain-a.com tries to fetch data from https://domain-b.com/data.json, it would be considered a cross-origin request. By default, browsers block such requests unless the server at https://domain-b.com explicitly permits it by sending the right CORS headers. To handle CORS in a Node.js Express application, you can manually add CORS headers to your responses or use the cors middleware package for Express. This middleware simplifies the process by automatically handling the necessary CORS headers for your API responses, allowing you to specify which origins can access your resources. To add CORS headers manually, you would typically modify your server's response headers to include headers like Access-Control-Allow-Origin, which specifies which domains are allowed to make requests to your server. For more dynamic and configurable setups, the cors middleware package allows you to specify various options such as which domains are allowed, which HTTP methods are permitted, and whether credentials like cookies can be included in the requests.

- _Mono Repository_: Mono repositories (mono repos) are a development strategy where the code for many projects is stored in a single repository. This can include several independent applications, libraries and services that may use different technologies but are still closely linked. This strategy encourages code reuse, facilitates dependency sharing and improves team collaboration. Mono repos are successfully used by large technology companies such as Google, Facebook and Twitter.

- _Garbage Collector (GC)_: The Garbage Collector in programming languages is a form of automatic memory management. The garbage collector attempts to reclaim memory occupied by objects that are no longer in use by the program. It helps in preventing memory leaks by automatically freeing up memory that is no longer needed, which otherwise would have been difficult and error-prone if done manually by the programmer. In JavaScript, garbage collection is implemented as a part of the JavaScript engine, such as V8 (used by Chrome and Node.js) or SpiderMonkey (used by Firefox). JavaScript's garbage collector operates on the principle of reachability, meaning that any object that is reachable (accessible in some way from the root) is considered alive, and everything else is considered garbage and can be collected. The most common algorithm used is "mark-and-sweep", where the collector marks all reachable objects and then sweeps through the memory to collect unmarked objects. Rust, on the other hand, takes a different approach to memory management and does not have a garbage collector like JavaScript. Rust uses a system of ownership with a set of rules that the compiler checks at compile time. Each value in Rust has a variable that’s called its owner, and there can only be one owner at a time. When the owner goes out of scope, the value will be dropped. Rust also uses borrowing and references, allowing multiple access to data without taking ownership, ensuring memory safety and preventing data races without needing a garbage collector. This makes Rust programs efficient and safe in terms of memory management, at the cost of a steeper learning curve due to its ownership rules.

- _Overhead_: Overhead refers to the additional time, memory, or other resources required to perform a task beyond the minimal necessary amount. Overhead can be introduced by the programming language, its runtime environment, or the abstractions and features it provides. Examples of overhead include memory overhead (extra memory used by data structures or runtime environments. For example, an object-oriented language might use more memory per data item due to the storage of metadata and pointers to methods), time overhead/execution overhead (additional time taken to execute a program due to language features or abstractions. For instance, dynamic typing in languages like Python or JavaScript can introduce overhead because types must be checked at runtime), abstraction overhead (higher-level abstractions, while improving developer productivity and code readability, can introduce overhead by adding layers of computation or by being less efficient than lower-level code. For example, using a high-level function for sorting might be less efficient than a custom-tailored sorting algorithm written specifically for the task at hand), garbage collection overhead (languages that use automatic memory management (garbage collection) incur overhead in periodically checking and freeing unused memory, which can affect performance predictably).

- _Browserlist_: The browserslist configuration ([in package.json for Next.js](https://nextjs.org/docs/architecture/supported-browsers)) specifies the range of browser versions that your application supports. It's used by various tools, like Babel, PostCSS, and Autoprefixer, to ensure the generated code and styles are compatible with the specified browsers. In your case, the list means that your application targets specifically these versions of browsers. However, tools like Babel and Autoprefixer can use this information to apply necessary polyfills or prefixes to support features in browsers newer than those listed but with the same compatibility needs. For more details, you can refer to the official Browserslist documentation. Newer browsers will still work with your application even if they are not explicitly listed in your browserslist configuration. The browserslist is primarily used to ensure that the generated code and styles are compatible with older browsers you specify. It doesn't prevent newer browsers from using your application; instead, it helps tools like Babel and Autoprefixer understand which browser versions they need to ensure compatibility for, typically by adding necessary polyfills or CSS prefixes. This means your app will be accessible to users on both older browsers listed in your browserslist and newer versions.

- _Polyfill_: A [polyfill](https://developer.mozilla.org/en-US/docs/Glossary/Polyfill) is a piece of code (usually JavaScript on the Web) used to provide modern functionality on older browsers that do not natively support it. For example, a polyfill could be used to mimic the functionality of a text-shadow in IE7 using proprietary IE filters, or mimic rem units or media queries by using JavaScript to dynamically adjust the styling as appropriate, or whatever else you require.

- _Chromium_: Chromium serves as the foundational project for several well-known browsers, including Google Chrome, Microsoft Edge, Opera, Brave, and Vivaldi, among others​​. These browsers have built upon Chromium's open-source codebase, incorporating their unique features and enhancements while maintaining core aspects of the Chromium architecture. Regarding running Chromium itself, it is indeed a standalone browser that can be used directly. While it shares much of its code with Google Chrome, there are notable differences, especially in terms of features like automatic updates, certain API keys for Google services, and proprietary codecs which are present in Chrome but not in Chromium. Chromium is more of a raw version of the browser that developers and more advanced users might use for various reasons, including development testing or a preference for open-source software​​. To run an older version of Chromium or any Chromium-based browser, you would generally need to find the specific version's installer or source code and install it on your system. Keep in mind that using significantly older versions of browsers can expose you to security risks, as they may lack important updates and patches that have been introduced in later versions.

- _Babel_: Babel is a widely used, open-source JavaScript compiler that allows developers to write next-generation JavaScript today. It transforms modern JavaScript (ES6+) code into backwards compatible versions of JavaScript that can run in older browsers or environments. This includes converting new JavaScript syntax, features, and APIs into a form that older JavaScript engines can understand, ensuring broad compatibility and enabling developers to use the latest language features without waiting for client environments to catch up.

- _Nullish Coalescing Assignment_: The [Nullish Coalescing Assignment operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Nullish_coalescing_assignment) (??=) in JavaScript is a logical assignment operator that assigns the right-hand value to the left-hand variable only if the left-hand variable is null or undefined. It is useful for setting default values while avoiding unintended overwrites by falsy values like 0, '', or false, which are considered valid by the more common logical OR assignment (||=). This makes ??= particularly handy for assignments where you want to preserve falsy values except for null or undefined.

- _CMDB (Configuration Management Database)_: A Configuration Management Database (CMDB) is a repository that acts as a data warehouse for information technology (IT) installations. It contains details of the IT infrastructure components in an organization and the relationships between those components. CMDBs are used to keep track of the state of assets such as the versions of hardware, software, systems, networking equipment, and so on, and the relationships among them. This information is used for various IT services management processes, including incident management, problem management, change management, and more.

- _Nginx_: Nginx (pronounced as "Engine-X") is a high-performance web server, reverse proxy, and HTTP cache. It is known for its high efficiency, stability, rich feature set, simple configuration, and low resource consumption. Nginx is used for serving web content, proxying requests to other servers, handling load balancing, and more. It's a popular choice for high-traffic websites because of its ability to efficiently handle multiple connections at once.

- _Load Balancer_: Within the context of Nginx, a load balancer is a method of distributing incoming network traffic across multiple servers to ensure no single server bears too much demand. By spreading the requests, load balancers improve the responsiveness and availability of applications, websites, or databases. Nginx can be configured as a load balancer to manage the traffic to your web servers and optimize performance.

- _Matomo_: Matomo (formerly known as Piwik) is an open-source web analytics platform that provides detailed reports on your website and its visitors, including the search engines and keywords they used, the language they speak, which pages they like, the files they download, and much more. It's a privacy-friendly alternative to Google Analytics and allows organizations to host their analytics, giving them full control over their data.

- _SSL Key_: An SSL key is a private key that is used in the SSL/TLS encryption process. It is a secret key that is kept on the server and is used to decrypt information encrypted with the corresponding public key. In SSL/TLS, public and private keys are used to establish a secure connection through a process known as a handshake. The private key is used in conjunction with a public key to create a secure connection. The private key should be kept secure and not shared, as it is used to decrypt data sent to the server.

- _SSL Certificate_: An SSL certificate is a digital certificate issued by a trusted Certificate Authority (CA). It contains the public key part of a key pair as well as identification information about the owner of the certificate (such as the domain name). When a web browser connects to a secure site, the site presents its SSL certificate for the browser's inspection. The SSL certificate serves two main purposes: 1. It provides the public key necessary to initiate a secure session. 2. It verifies that the server is the legitimate owner of the website and that the certificate is issued by a trusted authority, thus creating trust with the client.

- _SSL CA Bundle_: An SSL CA Bundle is a file that contains one or more root and intermediate certificates. The bundle helps client software (like web browsers) verify the chain of trust between the website's SSL certificate and the root certificate of the CA that issued it. When a web server presents its SSL certificate to a client, the client might not directly trust the certificate. The client will attempt to verify the certificate's authenticity by following the chain of certificates from the presented certificate up to a trusted root certificate. The CA bundle contains intermediate certificates that bridge the trust between the website's SSL certificate and a root certificate pre-installed in the client's certificate store.

- _Bit_ & _Byte_: 8 Bits equal 1 Byte (50 Mbit/s equals 6.25 Megabyte/s).

- _Volumes_: In the context of software and systems engineering, a "volume" generally refers to a designated storage area that is used to hold data. This concept is integral to various computing environments, including operating systems, virtualization platforms, and containerization technologies. The purpose and functionality of a volume can vary widely depending on the context, but the core idea revolves around data management and persistence. Volumes are designed to persist data beyond the lifecycle of the process or instance using them. This means that the data stored in a volume remains available even after the process ends or the instance is terminated. Volumes can provide a way to isolate data for specific applications or services, ensuring that the data is accessible only to those components that need it, which enhances security and organization. In many systems, volumes can be shared among multiple processes or instances, allowing for efficient data exchange and collaboration without the need for data duplication. Volumes can offer a way to easily move data between different environments or systems. By detaching a volume from one instance and attaching it to another, the data becomes instantly available to the new instance. The underlying physical storage of volumes can vary, ranging from local disk storage on a single machine to distributed file systems across a network or cloud-based storage solutions. This flexibility allows volumes to be tailored to specific storage needs and performance requirements.

- _Performance API_: The Performance API, part of the Web Performance APIs suite, provides a way to measure the performance of web applications by giving access to performance-related information in the browser. It's a standardized API available in modern web browsers that allows developers to collect detailed performance metrics in a fine-grained and precise manner. The Performance API is particularly useful for understanding the real-world performance of web applications, diagnosing slow performance, and identifying bottlenecks.

- _dependencies and devDependencies_: `dependencies` are packages required by your application at runtime. This includes libraries that your application imports and uses when it's running, like React (react), Redux (redux or @reduxjs/toolkit), UI libraries, utility libraries, and any other code that is part of the production bundle that gets executed in the user's browser or on the server in the case of SSR (Server-Side Rendering) applications like Next.js. `devDependencies` are packages that are only needed during development and the build process. This includes compilers/transpilers (like Babel, TypeScript), build tools (Webpack, Rollup), CSS preprocessors (Sass, Less), testing libraries (Jest, Mocha), linters (ESLint, Prettier), and other tools that help in the development of the application but are not needed for the application to run in production. For example, you wouldn't need your testing framework or linter in your production environment. Both `dependencies` and `devDependencies` can be involved in the build process. However, only the output (usually a set of static files, JS bundles, CSS, etc.) of this process is used in production. Only the packages that are part of your final, built application code `dependencies` are needed at runtime.

- _Constructor_: A function that creates an instance.

- _Destructor_: A function that cleans up an instance.

- _Memory Leak_: Memory that is never cleaned up.

- _TOTP_: TOTP (Time-based One-Time Password) is a secure method for generating temporary, one-time passcodes that are valid for a short period, usually 30 seconds. It combines a secret key (shared between the user and the service) with the current time to create a unique code. This code changes periodically, making it difficult for attackers to reuse intercepted codes. TOTP is commonly used in two-factor authentication (2FA) to enhance security by requiring both something the user knows (password) and something the user has (the TOTP code).

- _SSH_: SSH (Secure Shell) is a network protocol that provides a secure way to access and manage network devices and servers remotely. It encrypts all data transmitted between the client and the server, ensuring confidentiality and integrity. SSH is widely used for secure login, command execution, file transfers (using protocols like SCP or SFTP), and creating encrypted tunnels for other network services. It replaces older, insecure protocols like Telnet and FTP, offering stronger security through encryption and authentication mechanisms.

- _127.0.0.1_: Also known as Loopback address or localhost. It is used to refer to the local machine, allowing a computer to communicate with itself. Commonly used for testing and development purposes to ensure that network services are functioning on the local machine without needing external network access.

- _0.0.0.0_: It is a non-routable meta-address used to designate an invalid, unknown, or non-applicable target. In the context of servers, it means "all IPv4 addresses on the local machine." When a service listens on 0.0.0.0, it means it will accept connections on any of the machine's IP addresses. For example, a web server configured to listen on 0.0.0.0 will respond to requests on any of its network interfaces.

- _Deserialization_: Deserialization is the process of converting data from a format like JSON, XML, or binary into a data structure. For example, deserializing JSON data into a Rust struct.

- _\* (Asterisk)_:Represents any number of any characters in a single level of the directory structure. Example: \*.txt matches all .txt files in the current directory. Example: data/\* matches all files and directories directly inside the data directory.

- _\*\* (Double Asterisk)_: Represents any number of any characters across multiple levels of the directory structure. Often used in combination with / to indicate any number of subdirectories. Example: data/\*\*/\*.txt matches all .txt files in the data directory and all its subdirectories, regardless of their depth.

- _Rebasing_: Rebasing takes the changes from the branch you’re rebasing onto (branch-a) and then re-applies your changes on top of it. It rewrites your branch’s history to include the latest changes from branch-a, making it appear as though you built your changes directly on top of the latest version of branch-a. Rebasing is useful when you want to incorporate upstream changes into your branch cleanly, without the need for a merge commit. See corresponding command in general commands section.

## General Information

- Files within the public folder for Nest.js or Next.js, for example, can be accessed with the corresponding path, like `api_url/images/my_image.png` -> thus, one use case can be, that you could save the correspinding paths and use them in your frontend application, for example, to fetch/access them with the proper paths of the backend api where the images are saved.

## Helpful Links

- [What is idempotency in HTTP methods?](https://stackoverflow.com/questions/45016234/what-is-idempotency-in-http-methods)
- [How To Format Code with Prettier Extension in Visual Studio Code](https://www.digitalocean.com/community/tutorials/how-to-format-code-with-prettier-in-visual-studio-code)
- [Running Promises In Parallel: A Visual Guide (Promise.all(), Promise.allSettled(), Promise.race(), Promise.any())](https://julesblom.com/writing/running-promises-in-parallel)
- [Understanding JWTs](https://dev.to/philip-ainberger/understanding-jwts-a-simple-guide-for-beginners-aba)
- [API Integration Patterns – The Difference between REST, RPC, GraphQL, Polling, WebSockets and WebHooks](https://www.freecodecamp.org/news/api-integration-patterns/)
- [Common mistakes with the Next.js App Router and how to fix them](https://vercel.com/blog/common-mistakes-with-the-next-js-app-router-and-how-to-fix-them)
- [Shared browser compatibility config for popular JavaScript tools](https://browsersl.ist/)
- [Babel Presets](https://babeljs.io/docs/presets)
- [Can I Use ...](https://caniuse.com/)
- [Chromium All Old Stable Versions](https://github.com/Bugazelle/chromium-all-old-stable-versions)
- [Types of Network Protocols Explained](https://www.computernetworkingnotes.com/networking-tutorials/types-of-network-protocols-explained-with-functions.html)
- [Install C Compiler for Windows](https://www.scaler.com/topics/c/c-compiler-for-windows/)
- [Rust: Vector API Documentation](https://doc.rust-lang.org/std/vec/struct.Vec.html)
- [Optimizing JavaScript](https://romgrk.com/posts/optimizing-javascript?utm_source=tldrwebdev#10-data-structures)
- [What You Need to Know about Modern CSS (Spring 2024 Edition)](https://frontendmasters.com/blog/what-you-need-to-know-about-modern-css-spring-2024-edition/?utm_source=tldrwebdev)
- [Mocking Asynchronous Functions with Jest](https://www.youtube.com/watch?v=gA-uNj2FgdM)
- [Removing .env file from Git history](https://git.wtf/removing-env-file-from-git-history/)
- [Pagination on TanStack table under NEXT.JS](https://tocalai.medium.com/pagination-on-tanstack-table-under-next-js-787ed03198a3)
- [The NGINX Handbook – Learn NGINX for Beginners](https://www.freecodecamp.org/news/the-nginx-handbook/)
- [Cursor Based Pagination](https://www.sitepoint.com/paginating-real-time-data-cursor-based-pagination/)

## Potential Fixes

- If trouble with GPG secrets/keys arises, try to delete the `.password-store` (with the docker-credentials-helper) and/or the whole `.docker` folder to reset the settings, then use `pass init GPG_FINGERPRINT` to initialize the process with the GPG secret.

- Git Error based on wrong user and password: `Windows-Anmeldeinformationen verwalten` -> In here, the proper user has to be configured for the corresponding git platform, so that the user operating in Git is the same user mentioned in the `Windows-Anmeldeinformationen`.

- To make a keycloak client work, a role has to be configured (like a "user" role).

- When using Next.js the error.tsx client component only works for server-side errors. If you want to get to this separate client component from a client component, you have to set up a state (errorState, for example) set it to true whenever the error might occur (in the catch block of an asynchronous action, for example) and check for true of this errorState to then throw an error which will lead you to the designated error.tsx client component.

- Fetch requests might fail with 400 (Bad Request) or 500 statuses which are valid HTTP responses (4xx and 5xx error status codes). However, these are not catched by the catch block which are for network errors, for example, (if the browser is unable to make the request at all). To catch those 4xx and 5xx error status codes you have to check with `response.ok` in the try block and throw an error manually to get to the corresponding catch block.

- For old browsers there might be a error in terms of "globalThis is not defined". To polyfill this issue you might use `<script src="https://polyfill.io/v3/polyfill.min.js?features=globalThis"></script>` or `<script dangerouslySetInnerHTML={{ __html: 'window.globalThis = window', }} type="text/javascript" />` or also `<script src="https://unpkg.com/@ungap/global-this@0.4.4/min.js" noModule async></script>` ([First & Second approach](https://github.com/vercel/next.js/pull/45592)[Third approach](https://github.com/vercel/next.js/discussions/49771))

- If animations are implemented which make use of `x` or `y` or similar movements, some sort of flickering might appear, affecting fonts and elements in general while the respective animation takes place. With the help of `backface-visibility: hidden` and `transform: translateZ(0)` this bug can be fixed. However, this fix might cause a small decline in quality for the fonts/texts - [source](https://discourse.webflow.com/t/a-fix-for-when-your-elements-move-up-and-or-blur-during-animations-interactions-on-chrome/11629)

- Add a focus on a label to focus the input element within that label.

- If you can't properly import a database export, check the collation/s of the import query (for example, change `utf8mb4_0900_ai_ci` to `utf8mb4_general_ci` to make it work in this specific case)

- To reset the default Microsoft Powershell path: `%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe`

- If Tailwind CSS classes are not properly working, check if the file they are used in, is included in the bundle path of the tailwind config file

## How Are Passwords Saved

Passwords aren't saved directly in databases due to security risks. Instead, they are transformed into a form that's difficult to reverse-engineer using a process called hashing. Let me break down the common process:

- Hashing the Password:
  When a user sets or changes their password, it’s hashed using a cryptographic hash function (e.g., bcrypt, Argon2, or PBKDF2). Hashing turns the password into a fixed-length string of characters that doesn’t reveal the original password and can’t be reversed to reveal it.

- Adding a Salt:
  To make each hash unique, a random value called a salt is added to the password before hashing. This prevents attackers from using precomputed "rainbow tables" to guess passwords, as the same password will produce different hashes with different salts.

- Storing Only the Hash and Salt:
  Only the hash and salt are stored in the database. When a user logs in, the application hashes the entered password with the stored salt and compares it to the saved hash to check if they match.

## Fiddler

Using Fiddler, you have access to all requests that go through the target system (own system but also smartphone for example via a proxy). This way you can, for example, find endpoints online games and/or websites are using for their actions when the client requests data from the respective server. In order to follow this procedure for apps, a proxy can be established on the smartphone which basically forwards the requests in a proper form to the Fiddler client application on the computer. In theory, it would be also possible to use android emulators, for example, but setting this up seemed to be quite a hassle. Therefore, if possible, it's strongly recommended to just use the respective app on a smartphone device and follow the "remote devices" instruction on Fiddler to set up the connection which works perfectly fine.

## Next.js & React.js Features

This section covers some important Next.js and React.js features.

- `server-only` is to poison a module, so that if a client module, imports from it, the application crashes. An error is raised.
- `use server` is used to mark code as executable server side:

### Contexts

Example Context setup file:

```js
"use client";

import React, { createContext, useReducer, useContext } from "react";

type Variant = "success" | "error" | "warning" | "info" | "confirm";

interface Alert {
  title: string;
  variant?: Variant;
  primaryButtonText: string;
  onPrimary: () => void;
  onClose: () => void;
}

export type State = {
  activated: boolean,
  title: string,
  variant: Variant,
  primaryButtonText: string,
  onPrimary: () => void,
  onClose: () => void,
};

export type ContextType = {
  alertState: State,
  alertDispatch: React.Dispatch<Action>,
};

export type Action =
  | { type: "activate", alert: Alert }
  | { type: "deactivate" };

const initialState: State = {
  activated: false,
  title: "",
  variant: "error",
  primaryButtonText: "",
  onPrimary: () => {},
  onClose: () => {},
};

// Reducer function
const reducer = (state: State, action: Action): State => {
  switch (action.type) {
    case "activate":
      return {
        ...state,
        ...action.alert,
        activated: true,
        variant: action.alert.variant ?? "error",
      };
    case "deactivate":
      return { ...initialState, activated: false };
    default:
      return state;
  }
};

`const AppContext = createContext<ContextType | undefined>(undefined);`;

export const AppProvider = ({ children }: { children: React.ReactNode }) => {
  const [alertState, alertDispatch] = useReducer(reducer, initialState);

  return (
    <AppContext.Provider value={{ alertState, alertDispatch }}>
      {children}
    </AppContext.Provider>
  );
};

// Hook to use the context
export const useAppContext = (): ContextType => {
  const context = useContext(AppContext);
  if (context === undefined) {
    throw new Error("useAppContext must be used within an AppProvider");
  }
  return context;
};
```

Use `const { alertState, alertDispatch } = useAppContext();` within a component that is wrapped by this context to access the actual context. Wrap the respective components with `<AppProvider>{stuff}</AppProvider>`

### `Use()` Hook

The `use()` hook can be utilized to resolve the data from promises (for example by a async fetch function).

Since the pages and components itself shouldn't be declared as `async` in Next.js, directly using the `await` keyword in such a component or page in order to resolve a promise isn't a valid option.
You rather should use the `useEffect()` hook on the client-side in this case (you can still declare the fetch funcion itsel for the server-side and import it on the client-side or create the function directly on the corresponding page component and pass it down as a prop to the component) -> Remember that you can't make the `useEffect()` hook's callback itself `async`, instead you have to create a separate `async` function and call it inside the `useEffect()` hook to set the state of a variable (in the following example `data` is the passed down promise function from the page component):

```js
useEffect(() => {
  const fetchData = async () => {
    const cur = await data;
    setInput(cur);
  };

  fetchData();
}, []);
```

Instead of doing all this, you may also use the [`use()` hook](https://react.dev/reference/react/use) which basically resolves the promise and makes the data available without having to mark the parent component/page as `async` and therefore you are able to fetch the actual data directly on the server without a client-side workaround (without a loading screen in this case; `getData()` is the `async` promise fetch function):

```js
import ComponentTest from "./componentTest";
import getData from "./serveronlyfunctions";
import { use } from "react";

export default function Home() {
  const data = use(getData());

  return (
    <main className="flex min-h-screen flex-col items-center justify-between p-24">
      <ComponentTest data={data} />
    </main>
  );
}
```

### `forwardRef` & `useImperativeHandle`

Both are used for passing a ref from a parent component to a child component. This can be used when you want to handle a animation's logic (by gsap, for example) in the parent component while actually using the animation in a child component.

Example to apply forwardRef on the child component (the parent component would pass a `ref` prop to the child component):

```js
const KeyboardErrors: ForwardRefRenderFunction<
  HTMLDivElement,
  PropsInterface
> = (props, ref) => {
  const internalRef = useRef();

  // If this does not work, just return the ref.current.
  useImperativeHandle(ref, () => ({
    focus: () => {
      internalRef.current.focus();
    },
  }));

  // Make sure to attach the `ref` to a DOM element, for example:
  return <div ref={internalRef}>{/* Your component's content */}</div>;
};

export default forwardRef(KeyboardErrors);
```

## Bearer Token

A "Bearer" token is a type of access token used in OAuth 2.0, which is a protocol for authorization. In the context of HTTP authentication, "Bearer" tokens are a type of access token that are typically used to gain access to a protected resource.

Here's a breakdown of the concept:

1. Bearer Token: The term "Bearer" is essentially an authorization type. In this context, it indicates that the person or system presenting the token is authorized to access the resource. The word "Bearer" signifies that the bearer of the token has been granted access.

2. Usage: When used in HTTP authentication headers, a Bearer token is usually presented like this: Authorization: Bearer [token]. This header is added to HTTP requests to prove that the sender is allowed to access the resource.

3. Security: Bearer tokens must be protected to ensure that they are not intercepted by unauthorized parties. If someone else obtains the token, they can use it to gain access to the protected resources.

4. OAuth 2.0 and OpenID Connect: Bearer tokens are commonly used in OAuth 2.0 and OpenID Connect for granting access to resources without sharing the resource owner's credentials. They are usually provided after an authentication and authorization process.

5. Token Properties: Typically, a Bearer token is a cryptographically secure string, often generated by the server in response to a login request. The token itself is opaque to the client.

6. Statelessness: In many implementations, Bearer tokens are stateless. The server doesn't need to remember the token after it's issued, as all necessary information to validate the token is contained within it.

In summary, a Bearer token is a form of access token that grants the bearer (the one who presents the token) access to a protected resource, commonly used in modern web APIs and online services for authentication and authorization purposes.

## General Testing

This section covers relevant information about testing in general.

### Mocks

A mock is an object that replaces a real component within your system during testing. Mocks are pre-programmed with expectations and responses, mimicking the behavior of the actual object they are replacing. They are primarily used to:

1. Simulate complex behavior: Mocks can replicate the functionality of real objects that might be difficult or impractical to incorporate into a unit test (like a database or an external service).

2. Verify interactions: You can check whether the system under test interacts with the mock in the expected way, such as calling certain methods with specific arguments.

3. Control test environment: By using mocks, you can create predictable and controlled test scenarios, ensuring your tests are reliable and repeatable.

4. Isolate the system under test: Mocks help in isolating the part of the system you want to test from its dependencies, ensuring that test outcomes are solely based on the behavior of the system under test.

### Spies (and 'spyOn')

A spy is a function that records some information about its usage, such as how many times it was called and what arguments were passed to it. Unlike mocks, spies are generally used to wrap real implementations of functions, so the actual behavior is executed, but additional tracking is performed.

The spyOn function is commonly used in testing frameworks like Jasmine or Jest. It replaces the specified function with a spy. Key aspects of spies include:

1. Observation without interference: Spies allow you to observe the behavior of a function (such as whether it was called and with what arguments) without modifying its actual implementation.

2. Call tracking: They keep track of how and when they are called, which is useful for verifying that your system under test interacts correctly with other parts of your application.

3. Return value control: Spies can be configured to return specific values, throw errors, or call through to the real implementation.

4. Integration testing: Spies are particularly useful in integration testing where you want to test the integration of components but still need to verify certain interactions or prevent certain actions (like network calls).

### Examples

#### Mocking a module with a spy

```js
// Mocking a module
jest.mock("./someModule", () => {
  return {
    someMethod: jest.fn().mockReturnValue("mocked value"),
  };
});

// Using a spy
const myObject = {
  myMethod: () => "real value",
};

jest.spyOn(myObject, "myMethod").mockReturnValue("spied value");

// In a test
expect(myObject.myMethod()).toBe("spied value"); // using the spy
expect(someModule.someMethod()).toBe("mocked value"); // using the mock
```

#### stopPropagation Spy

```js
  ...

  const trigger = getByTestId("trigger");

  const triggerClickEvent = createEvent.click(trigger);
  triggerClickEvent.stopPropagation = jest.fn();

  fireEvent(trigger, triggerClickEvent);

  expect(triggerClickEvent.stopPropagation).toHaveBeenCalled();

  ...
```

## Understanding SSL (Secure Sockets Layer)

SSL, or Secure Sockets Layer, is a standard security technology for establishing an encrypted link between a server and a client—typically a web server (website) and a browser, or a mail server and a mail client (e.g., Outlook).

SSL allows sensitive information such as login credentials, credit card numbers, or personal details to be transmitted securely. Normally, data sent between browsers and web servers is sent in plain text, which can leave you vulnerable to eavesdropping. If an attacker is able to intercept all data being sent between a browser and a web server, they can see and use that information.

- How SSL Works
  _SSL Handshake_: Initially, when a client connects to an SSL-secured server, they perform an "SSL handshake". During this handshake, the client and server establish which encryption algorithm they will use, and the server provides its SSL certificate as proof of identity.

_Encryption of Data_: Once the handshake is complete, the data transmitted between the server and the client is encrypted according to the agreed-upon encryption algorithm. This means that even if the data is intercepted, it would be unreadable without the encryption key.

_Data Integrity_: In addition to encryption, SSL also ensures that the data sent is unchanged and authentic through a message authentication code (MAC).

## Nest.js

This section includes relevant information for Nest.js (Node.js framework).

### Commands

- Install Nest.js CLI: `npm i -g @nestjs/cli`
- Install Nest.js application in the current directory (without creating a new folder): `nest new .`
- Create module / controller / provider / : `nest g module name` / `nest g controller name` / `nest g provider name`
- Get Nest CLI overview: `nest`
- Start the server: `npm run start:dev`
- Used for PartialType for DTOs (see corresponding section): `npm i @nestjs/mapped-types -D`
- Used for decorator-based validation: `npm i --save class-validator class-transformer`

### `ConfigModule.forRoot()` to make environment variables work

1. Install the Nest.js config module `npm i --save @nestjs/config`. It relies on dotenv.
2. Create an `.env` file in the root folder and add the key/value pairs e.g. `DATABASE_USER=myusername`.
3. Open `app.module.ts` and import the config module: `import { ConfigModule } from '@nestjs/config';`
4. Add `ConfigModule.forRoot()` to the imports section of `app.module.ts`. It will load the contents of the `.env` file automatically.
5. Then you can begin to use the environment variables with `process.env.<variable_name>` in the database config section e.g.

### Authentication

In `app.module.ts`:

```ts
...
  providers: [
    AppService,
    // This adds a global level authentication guard,
    // you can also have it scoped
    // if you like.
    //
    // Will return a 401 unauthorized when it is unable to
    // verify the JWT token or Bearer header is missing.
    {
      provide: APP_GUARD,
      useClass: AuthGuard,
    },
    // This adds a global level resource guard, which is permissive.
    // Only controllers annotated with @Resource and
    // methods with @Scopes
    // are handled by this guard.
    {
      provide: APP_GUARD,
      useClass: ResourceGuard,
    },
    // New in 1.1.0
    // This adds a global level role guard, which is permissive.
    // Used by `@Roles` decorator with the
    // optional `@AllowAnyRole` decorator for allowing any
    // specified role passed.
    {
      provide: APP_GUARD,
      useClass: RoleGuard,
    },
  ],
...
```

### Migrations in Mikro ORM

MicroORM migrations are a powerful tool for version control of your database. They allow you to systematically manage, track and undo changes to your database structure. Here is a detailed explanation of the commands and concepts:

_`mikro-orm migration:create`_:

- This command is used to create a new migration file.
- MikroORM analyses your entities and the current database structure to determine which changes need to be made (e.g. adding/removing tables or columns).
- The generated migration file contains two main methods: `up()` and `down()`.
- The `up()` method contains SQL statements or JavaScript code required to apply the changes to the database (e.g. add a table, change a column).
- The `down()` method contains SQL statements or JavaScript code to undo these changes (e.g. remove an added table, reset a changed column). This is useful if you need to revert to a previous database schema.

_`mikro-orm migration:up`_:

- This command applies the migrations that have not yet been executed to your database.
- MikroORM runs through the migration files in the order in which they were created and executes the up() method of each migration that has not yet been applied.
- After a migration has been successfully applied, an entry is added to a special migration table (`_migrations` by default) in your database. This entry is used to track which migrations have already been performed.

_`Initial migration file (e.g. Migration123412431_init.ts)`_:

- This file is normally generated automatically when you set up MikroORM for the first time in a project that already has an existing database structure.
- It represents the initial state of your database at the time of MikroORM integration.
- The file is generated by MikroORM comparing the structure of your entities with the current database structure and generating the necessary SQL statements to bring your database to the state required by your entities.
- This file is usually created once and should not be changed unless you understand exactly what you are doing and why. Future changes to your database should be managed through new migration files.
- This file should not be manually edited. For new changes to the database schema, such as adding a new field to a table, you should instead execute a new migration command (`mikro-orm migration:create`). This command generates a new migration file with `up()` and `down()` methods that contain the necessary steps to apply or undo the change. By recording each change in a new migration file, you can keep the history of your database changes traceable and organised.

### Soft Delete

In a soft delete approach, records are not physically removed from the database; instead, they are marked as deleted, typically with a boolean flag or a timestamp. This allows for data recovery and auditing.
The following code example is a filter which can be used to implement a soft delete logic:

```js
import { Filter } from "@mikro-orm/core";

export const SoftDeletedFilter = () =>
  Filter<{ deleted?: boolean }>({
    default: true,
    name: "softDeleted",
    cond: { deleted: null },
  });
```

_Filter Decorator:_ The Filter decorator from MikroORM is used to create a custom filter.
_Filter Configuration:_

- default: true means this filter is enabled by default for all queries.
- name: "softDeleted" sets the name of the filter.
- cond: { deleted: null } specifies the condition for the filter. In this case, it filters out records where the deleted field is null, implying that only records that have not been marked as deleted will be retrieved.

To use this filter in a service, you first need to apply it to your entities. This is typically done by decorating your entity class with the @Filter() decorator:

```js
import { Entity, Filter } from "@mikro-orm/core";
import { SoftDeletedFilter } from "./SoftDeletedFilter";

@Filter(SoftDeletedFilter())
@Entity()
export class YourEntity {
  // ... entity fields
}
```

In a service, you can then use this filter in your queries. Here's an example:

```js
import { EntityRepository, MikroORM } from '@mikro-orm/core';
import { Injectable } from '@nestjs/common';
import { YourEntity } from './your-entity.entity';

@Injectable()
export class YourService {
  constructor(
    private readonly orm: MikroORM,
    private readonly repository: EntityRepository<YourEntity>,
  ) {}

  async findNonDeleted() {
    // This will automatically apply the softDeleted filter
    return this.repository.findAll();
  }

  async findAllIncludingDeleted() {
    // Temporarily disable the filter for this query
    return this.repository.find({}, { filters: { softDeleted: false } });
  }
}
```

In `findNonDeleted`, the `softDeleted` filter will be applied by default, so it will return only the entities that are not marked as deleted. In `findAllIncludingDeleted`, the filter is disabled for that specific query, so it will return all entities, including those marked as deleted.

#### CustomEntityRepository

```js
import { EntityRepository } from "@mikro-orm/mariadb";

export class CustomEntityRepository<T extends object> extends EntityRepository<T> {
  /**
   * Soft delete an entity
   * @param entity
   */
  softRemove(entity: T) {
    entity["deleted"] = new Date();

    this.getEntityManager().flush();
  }

  /**
   * Restore a soft deleted entity
   * @param entity
   */
  restore(entity: T) {
    entity["deleted"] = null;

    this.getEntityManager().flush();
  }
```

This `CustomEntityRepository` is a custom repository in MikroORM, specifically tailored to handle soft delete and restore operations for entities. Let's break down its usage and how it integrates with your entity:

This repository extends EntityRepository, allowing it to perform all standard repository operations while adding two custom methods:

1. `softRemove(entity: T)`:

- Marks an entity as 'soft deleted' by setting its `deleted` property to the current date.
- Calls `flush()` to persist the change to the database.
- Assumes that the entity has a `deleted` property of date type or similar.

2. `restore(entity: T)`:

- Reverses a soft delete operation by setting the `deleted` property back to `null`.
- Calls `flush()` to persist this change.

When you annotate an entity with `@Entity({ repository: () => CustomEntityRepository })`, you're telling MikroORM to use `CustomEntityRepository` as the repository for instances of that entity. This means you can perform soft delete and restore operations on instances of that entity using the custom methods you've defined.

Assuming you have an entity class `Abc`:

```js
@Entity({ repository: () => CustomEntityRepository })
export class Abc {
  // ... your entity properties, including a 'deleted' property
  @Property({ nullable: true })
  deleted: Date | null;
}
```

You can then use `CustomEntityRepository` in your services like this:

```js
@Injectable()
export class AbcService {
  constructor(
    @InjectRepository(Abc)
    private readonly abcRepository: CustomEntityRepository<Abc>,
  ) {}

  async softDeleteAbc(entity: Abc) {
    this.abcRepository.softRemove(entity);
  }

  async restoreAbc(entity: Abc) {
    this.abcRepository.restore(entity);
  }
}
```

`softDeleteAbc` uses `softRemove` to soft delete an `Abc` entity. `restoreAbc` uses `restore` to undo the soft delete.

By using a custom repository, you can encapsulate specific data manipulation logic (like soft deleting) in a reusable way across your application. This makes your code more modular and maintainable. Just ensure that all entities using this repository have a `deleted` field or a field with similar functionality.

### EntityRepositories & EntitiyManager & orm

Entity Repositories are thin layers on top of EntityManager. They act as an extension point, so we can add custom methods, or even alter the existing ones. The default, EntityRepository implementation just forwards the calls to underlying EntityManager instance - [click for more information](https://mikro-orm.io/docs/repositories)

To make use of the EntityRepositories in the modules, you would have to implement `MikroOrmModule.forFeature([entity_name])`. To make use of the `orm` class you would have implement `MikroOrmModule` as a provider (I think).

### findOneOrFail() vs getReference()

If a property is created via a @ManyToOne relation in an entity, you would store the whole related object in this situation:

```js
export class Something {
@ManyToOne(() => SomeOtherTableObject)
  someOtherTableObject?: SomeOtherTableObject;
  }
```

However, in the actual database you would have a column for the id (the Foreign Key), like `SomeOtherTableObject_id`. If you insert a new object into this table, the database will automatically will store the corresponding id and basically will have a reference to it (The typical SQL relation behaviour).

If you don't provide the id (you would use to find the related object from the other table) as a Query Param, for example, you could also insert it into the Body of the Request via the corresponding creating DTO.

In ORMs like MikroORM, which is used in Nest.js, getReference is a method that allows you to create a reference to an entity for which you have the ID, without actually fetching it from the database. This can be particularly useful for setting up relationships or for operations where you don't need the full entity data. Let's break down its usage and compare it with findOneOrFail.

- getReference
  _Usage_: getReference is used when you need a reference to an entity but don't need to load its data from the database. This is
  efficient for performance, especially in cases where you only need to establish a relationship or perform an operation that doesn't require the actual entity data.

_Example_: In your code, this.couponGroupRepository.getReference(createVoucherDto.couponGroupId) creates a reference to a CouponGroup entity using the provided couponGroupId. This reference can then be used to set up a relationship with the Voucher entity being created, without the overhead of fetching the CouponGroup entity from the database.

- findOneOrFail
  _Usage_: findOneOrFail is used when you need to retrieve the full data of an entity from the database. It fetches the entity based on the given criteria, and if the entity is not found, it throws an error.

_When to Use_: Use findOneOrFail when you need to work with the actual data of the related entity. For example, if you need to validate some data, check permissions, or use any specific information from the related entity before proceeding.

- Comparison and Use Cases

_getReference_:
Best for setting foreign key relations when you already have the ID.
More performant for large objects or when you don't need the actual data from the related entity.
Doesn't ensure the existence of the related entity (no database hit).

_findOneOrFail_:
Best for scenarios where you need to access or manipulate the actual data of the related entity.
Ensures that the related entity exists (throws an error if not).

Involves a database query, hence more resource-intensive.

- Conclusion
  In summary, choose getReference when you only need to associate entities
  based on their IDs and do not require loading the entire entity data from the database. This is particularly useful for improving performance and efficiency. On the other hand, use findOneOrFail when you need to work with the actual content of the entity, such as performing validations or operations that depend on the entity's data. This ensures the entity exists and allows you to access its properties, but with the added cost of a database query.

### Error Handling

Make use of HttpException instead of `throw new Error()` in order to create relevant errors with easier access to a corresponding body with message and status.

```js
getSingleUserWithID(id: string): IUSERDATA {
    const IDNumber: number = parseInt(id);

    if (isNaN(IDNumber)) {
      throw new HttpException(
        'Invalid ID format, number format required.',
        HttpStatus.BAD_REQUEST,
      );
    }

    const user = USERDATA.find((ele: IUSERDATA) => ele.id === IDNumber);

    if (user) {
      return user;
    } else {
      throw new HttpException(
        'User not found for this ID.',
        HttpStatus.NOT_FOUND,
      );
    }
  }
```

### Creating a Global Module

In this example I'm using the SOAP client to make a global Soap Module I was able to use anywhere without importing anything in the corresponding modules (just import the Global module in the service itself). This could be an example of how you would be able to create global modules for other third-party clients as well if needed.

1. Create a Global SoapModule:

```js
// soap.module.ts
import { Module, Global, DynamicModule } from "@nestjs/common";
import { SoapModule as NestSoapModule } from "nestjs-soap";
import soapConfig from "./config/soap-config";

@Global()
@Module({})
export class SoapModule {
  static forRoot(): DynamicModule {
    return {
      module: SoapModule,
      imports: [NestSoapModule.forRootAsync(soapConfig)],
      exports: [NestSoapModule],
    };
  }
}
```

2. Update AppModule

```js
// app.module.ts
import { Module } from "@nestjs/common";
import { SoapModule } from "./soap.module";
import { AppController } from "./app.controller";
import { AppService } from "./app.service";
// ... other imports

@Module({
  imports: [
    SoapModule.forRoot(),
    // ... other imports
  ],
  controllers: [AppController],
  providers: [AppService],
})
export class AppModule {}
```

3. Use SOAP Client in Other Modules
   Now, in any other module where you need to use the SOAP client, you can simply inject it without needing to import the SoapModule.

_Explanation_

- The @Global() decorator makes the module global-scoped. Modules that are global-scoped do not need to be imported into other modules; instead, once imported into the root module (AppModule), they are available everywhere.
- SoapModule.forRoot() is a pattern used for configuring modules dynamically. It's useful for modules that need to perform some setup before they can be used, such as connecting to a SOAP service.
- The forRoot() method in SoapModule returns a dynamic module that imports the nestjs-soap module configured with your settings.

### Pipes

[Pipes on Nest.js docs](https://docs.nestjs.com/pipes)
Middleware for transformation and validation of the request data

```js
@Get(':id')
  getSingleUserWithID(
    @Param('id', ParseIntPipe) id: number,
  ): IUSERDATA | undefined {
    return this.usersService.getSingleUserWithID(id);
  }
```

### DTO (Data Transfer Object) Schemas

[DTO Schemas on Nest.js docs](https://docs.nestjs.com/controllers#request-payloads)
A DTO is an object that defines how the data will be sent over the network. Use classes instead of TypeScript interfaces.

```js
// in /users/dto/create-user.dto.ts
export class CreateUserDto {
  name: string;
  email: string;
  role: "INTERN" | "ENGINEER" | "ADMIN";
}
```

```js
// in /users/dto/update-user.dto.ts
import { CreateUserDto } from "./create-user.dto";
import { PartialType } from "@nestjs/mapped-types";

// Makes CreateUserDto fields optional (not everything has to be updated with each request)
export class UpdateUserDto extends PartialType(CreateUserDto) {}
```

### Decorator-based validation

[Validation decorators](https://github.com/typestack/class-validator#validation-decorators)

```js
import { IsEmail, IsEnum, IsNotEmpty, IsString } from "class-validator";

export class CreateUserDto {
  @IsString()
  @IsNotEmpty()
  name: string;

  @IsEmail()
  email: string;

  @IsEnum(["INTERN", "ENGINEER", "ADMIN"], {
    message: "Valid role required.",
  })
  role: "INTERN" | "ENGINEER" | "ADMIN";
}
```

```js
// ValidationPipe has to be included, otherwise the validation won't work.
@Post() // POST /users
  create(@Body(ValidationPipe) createUserDto: CreateUserDto) {
    return createUserDto;
  }
```

### @Query & @Param

[Click for more information](https://stackoverflow.com/questions/54958244/how-to-use-query-parameters-in-nest-js)

If you have you a parameter as part of an url `/articles/${articleId}/details`, you would use @Param:

```js
@Get('/articles/:ARTICLE_ID/details')
async getDetails(
    @Param('ARTICLE_ID') articleId: string
): Promise<any> {
  ...
  }
```

If you want to provide query parameters `/article/findByFilter/bug?google=1&baidu=2`, you would use @Query:

```js
@Get('/article/findByFilter/bug?')
async find(
    @Query('google') google: number,
    @Query('baidu') baidu: number,
): Promise<any> {
  ...
  }
```

### Rate Limits

Too limit the amount of incoming requests you can use `npm i @nestjs/throttler` and make the corresponding changes in the module file (See [Nest.js REST API with CORS, Rate Limits, Server Logs, & Exception Filter](https://www.youtube.com/watch?v=hQTtioSw4Zo&list=PL0Zuz27SZ-6MexSAh5x1R3rU6Mg2zYBVr&index=7) for some examples). You could also add specific throttle logic for single routes in the controller (Takes precedence over the throttle logic in the module file) with `@Throttle({ short: {ttl: 1000, limit: 1 }})`, for example.

```js
// This is in app.module.ts
import { Module } from "@nestjs/common";
import { AppController } from "./app.controller";
import { AppService } from "./app.service";
import { UsersModule } from "./users/users.module";
import { ThrottlerModule, ThrottlerGuard } from "@nestjs/throttler";
import { APP_GUARD } from "@nestjs/core";

@Module({
  imports: [
    UsersModule,
    ThrottlerModule.forRoot([
      {
        name: "short",
        ttl: 5000,
        limit: 3,
      },
      {
        name: "long",
        ttl: 60000,
        limit: 100,
      },
    ]),
  ],
  controllers: [AppController],
  providers: [AppService, { provide: APP_GUARD, useClass: ThrottlerGuard }],
})
export class AppModule {}
```

### @ValidateNested()

In case a DTO is based on another DTO (like in the following example), you have to use the `@ValidateNested()` decorator as well as the `@Type()` decorator. Otherwise, the input safety checks won't work.

```js
import { Type } from 'class-transformer';
import { ValidateNested, IsArray, IsInt, ArrayNotEmpty } from 'class-validator';

export class ParentDto {
  @ValidateNested({ each: true })
  @Type(() => createChildDto)
  @IsArray()
  create: createChildDto[];

  @ValidateNested({ each: true })
  @Type(() => updateChildDto)
  @IsArray()
  update: updateChildDto[];
```

The `{ each: true }` option for the `@ValidateNested()` decorator is used since the `createChildDto` is an array in this case (otherwise you would not need the `{ each: true }` option).

### Testing in Nest.js

This is a test file for the corresponding controller. Remember to include all relevant controllers and services. A potential source of error could be incorrect or missing asynchronous logic in the controller.

```js
import { Test, TestingModule } from '@nestjs/testing';
import { UsersController } from './users.controller';
import { IUSERDATA, UsersService } from './users.service';

describe('UsersController', () => {
  let controller: UsersController;
  let service: UsersService;

  beforeEach(async () => {
    const module: TestingModule = await Test.createTestingModule({
      controllers: [UsersController],
      providers: [UsersService],
    }).compile();

    controller = module.get<UsersController>(UsersController);
    service = module.get<UsersService>(UsersService);
  });

  describe('/users', () => {
    it('should return users with a specific role', async () => {
      const role = 'ADMIN'; // Change this to the role you want to test

      const mockUsers: IUSERDATA[] = [
        {
          id: 1,
          name: 'Bub Bilbo',
          email: 'Bub.Bilbo@Bilbo.com',
          role: 'INTERN',
        },
        {
          id: 2,
          name: 'Kamin Ka',
          email: 'disposableEmail@temporary.com',
          role: 'INTERN',
        },
        { id: 3, name: 'Hajin', email: 'Hajin.Ma@gmx.de', role: 'ADMIN' },
      ] as IUSERDATA[];

      jest.spyOn(service, 'getUsers').mockResolvedValue(mockUsers);

      const result = await controller.getUsers(role);

      expect(result).toEqual(mockUsers);
    });
  });

  describe('update', () => {
    it('should correctly update a user with the given id and return updated user data', () => {
      const id = '1';
      const updateUserDto = {
        name: 'Updated Name',
        email: 'updated.email@example.com',
      };

      const result = controller.update(id, updateUserDto);

      expect(result).toEqual({ id, ...updateUserDto });
    });
  });

  describe('getSingleUserWithID', () => {
    it('should return a user with the specified ID', async () => {
      const user: IUSERDATA = {
        id: 1,
        name: 'Bub Bilbo',
        email: 'Bub.Bilbo@Bilbo.com',
        role: 'INTERN',
      };

      jest.spyOn(service, 'getSingleUserWithID').mockImplementation(() => user);

      const result = controller.getSingleUserWithID(1);

      expect(result).toEqual(user);
    });

    it('should handle the case where a user with the given ID does not exist', async () => {
      const userId = 999; // Non-existent user ID

      jest
        .spyOn(service, 'getSingleUserWithID')
        .mockImplementation(() => undefined);

      const result = controller.getSingleUserWithID(userId);

      expect(result).toBeUndefined();
    });
  });
});
```

### @Req and @Res

In Nest.js, @Req and @Res are decorators used to inject the request and response objects of the underlying HTTP library (like Express or Fastify) into your route handling methods.

1. @Req: The @Req decorator is used to inject the request object into your method. It allows you to access the request data (like body, query parameters, HTTP headers, etc.).

2. @Res: The @Res decorator injects the response object. It is used to send a response back to the client. This includes setting the response status, headers, and sending the response body.

### MikroORM in Nest.js

Install relevant dependencies: `npm i -s @mikro-orm/core @mikro-orm/nestjs @mikro-orm/mariadb` (for mariadb) - [click for more information](https://mikro-orm.io/docs/usage-with-nestjs)

MikroORM requires a configuration file. This file specifies how MikroORM connects to your MariaDB database and manages entities. Create a file named `mikro-orm.config.ts` in your project's root directory with the following content:

```js
import { MariaDbDriver, Options } from '@mikro-orm/mariadb';

@Module({
  imports: [MikroOrmModule.forRoot({
  dbName: 'your_database_name',
  type: 'mariadb',
  host: 'localhost',
  port: 3306,
  user: 'your_username',
  password: 'your_password',
  entities: ['dist/**/*.entity.js'],  // Production
  entitiesTs: ['src/**/*.entity.ts'], // Development (TypeScript)
  driver: MariaDbDriver,
  }),
  // ... other imports,
  ]
  providers: [PhotoService],
  controllers: [PhotoController],
})
```

To integrate MikroORM with Nest.js, you have to set up a module. You can either use the MikroOrmModule.forRoot() method for root configuration or MikroOrmModule.forRootAsync() for asynchronous configuration.

In your main application module (usually app.module.ts), add the following:

```js
import { Module } from "@nestjs/common";
import { MikroOrmModule } from "@mikro-orm/nestjs";
import mikroOrmConfig from "./mikro-orm.config";

@Module({
  imports: [MikroOrmModule.forRoot(mikroOrmConfig)],
  // ... other configurations
})
export class AppModule {}
```

#### Entities

Entities in MikroORM are like models representing your database tables. Create a directory for your entities (e.g., entities) and define your entities there. Here's a simple example:

```js
import { Entity, PrimaryKey, Property } from '@mikro-orm/core';

@Entity()
export class User {
  @PrimaryKey()
  id!: number;

  @Property()
  name!: string;

  // ... other properties
}
```

Now, you can inject the EntityManager from MikroORM into your services or controllers to interact with the database.

```js
import { Injectable } from '@nestjs/common';
import { EntityManager } from '@mikro-orm/mariadb';
import { User } from './entities/user.entity';

@Injectable()
export class UserService {
  constructor(private readonly entityManager: EntityManager) {}

  async findAll(): Promise<User[]> {
    return await this.entityManager.find(User, {});
  }

  // ... other methods
}
```

#### The `dist` Folder

The dist folder, short for "distribution", is a common naming convention used in many software projects, especially those involving JavaScript and TypeScript. It serves as the output directory where the compiled, built, or transpiled code is placed. This folder is what you typically deploy to your production environment, as it contains the optimized and runnable version of your application code.

#### Glob Pattern

**/\*.entity.js: This is a glob pattern. The ** part means "any directory", and \*.entity.js means "any file that ends with .entity.js". So, this pattern will match all JavaScript files ending with .entity.js in any subdirectory of dist.

#### HeidiSQL vs. MikroORM

HeidiSQL is a popular database management tool that provides a graphical user interface (GUI) to interact with various types of SQL databases, including MariaDB. Here are some common uses for HeidiSQL in your development workflow:

- Database Administration: HeidiSQL allows you to perform administrative tasks like creating databases, modifying tables, managing indexes, and setting up foreign key relationships.
- Data Visualization and Editing: It provides an easy-to-use interface for viewing, adding, editing, and deleting data in your database tables.
- Query Execution: You can write and execute SQL queries directly, which is helpful for testing queries, exploring data, or performing complex database operations that might not be straightforward through an ORM.
- Database Debugging and Optimization: HeidiSQL can be used to analyze and optimize SQL queries, view query execution plans, and diagnose performance issues.
- Exporting and Importing Data: It offers tools for exporting data (e.g., to SQL dumps, CSV files) and importing data from various sources.

MikroORM, on the other hand, is an Object-Relational Mapping (ORM) tool used within your Nest.js application. Its roles include:

- Entity Management: MikroORM lets you define entities in your codebase, which map to tables in your MariaDB database.
- Database Interactions in Code: It abstracts the database interactions, allowing you to write database queries using JavaScript or TypeScript, without writing raw SQL.
- Data Manipulation and Retrieval: You can use MikroORM to create, read, update, and delete records in your database through your application's code.
- Migrations: MikroORM can handle database migrations, which are useful for managing changes to your database schema over time.

In a typical development workflow:

- Use HeidiSQL for direct database interactions, schema creation, data visualization, and manual querying. It's particularly useful during the initial stages of database design or when you need to perform complex operations that are easier to handle with a GUI.
- Use MikroORM within your Nest.js application for all database interactions that your application needs to perform programmatically. This includes CRUD operations, business logic implementation, and handling relational data through entities.

#### Inserting Data into the Database

1. Creating an Entity: In MikroORM, you first create an entity instance with the data you want to insert into your database. This is usually done using the create method on your entity repository or by simply creating a new instance of the entity class and setting its properties.

2. Persisting the Entity: The persist function is used to make MikroORM aware of the entity instance you wish to save to the database. It doesn't immediately execute a database insert operation. Instead, it tells MikroORM to "track" this entity as something that will need to be saved to the database. You can think of this as a way to prepare or stage your data for insertion.

3. Flushing the Changes: The flush function is what actually triggers the communication with the database. When you call flush, MikroORM looks at all the entities it has been told to track (through persist) and performs the necessary insert, update, or delete operations on the database. This is the point where your data is actually saved to the database.

The reason for this two-step process (persist, then flush) is to allow for more efficient database operations. By collecting several changes and then applying them all at once in a single flush, MikroORM can optimize database access, reduce the number of individual transactions, and maintain transactional integrity.

#### Naming Convention for Entities

In MikroORM when using it with Nest.js (or in any other context), the entity name and the database table name don't necessarily have to match exactly, but there needs to be a clear association between them. The convention in many ORM frameworks, including MikroORM, is to name entities in singular form (e.g., Coupon) and tables in plural form (e.g., coupons). However, this convention is not a strict requirement, and you can configure MikroORM to map entity names to specific table names as needed.

In MikroORM, as with many ORM (Object-Relational Mapping) frameworks, there's a common convention to use snake_case for database column names, especially when working with certain databases like PostgreSQL or MySQL. This convention is not a strict rule, but it is widely adopted due to its readability and compatibility with SQL standards.

Here's how the process typically works:

1. Entity Class Definition: You define an entity class (e.g., Coupon) in your application code. This class represents a table in your database (e.g., coupons).

2. Table Mapping: By default, MikroORM will try to map your entity class to a table in the database by converting the class name from singular to plural and by following specific naming conventions (like camelCase to snake_case). However, if your table name doesn't follow these conventions, you need to explicitly specify the table name.

3. Explicit Table Naming: You can use the @Entity decorator to explicitly define the table name associated with an entity. For example, if your entity is named Coupon but your table is named coupons, you can specify this like so:

```js
@Entity({ tableName: "coupons" })
export class Coupon {
  // ... entity properties ...
}
```

This tells MikroORM exactly which table this entity corresponds to, regardless of the naming convention.

4. Repository and Database Interaction: When you interact with the database through a repository, MikroORM uses the mapping information from your entity class to know which table to query or modify. The entity class acts as a blueprint for how the data should be structured and how it relates to the database schema.

If you want to use the singular form Coupon and still map it to the coupons table, you should explicitly set the tableName in the @Entity decorator as shown above.

Automatic vs. Manual Mapping: By default, MikroORM will try to automatically convert camelCase property names in your entities to snake_case column names in the database. However, if your database schema doesn't follow this convention, or if you prefer a different naming style, you might encounter issues. In such cases, you have to explicitly specify the column names using decorators, like so:

```js
@Entity()
export class User {
  @Property({ columnType: "int", fieldName: "user_id" })
  userId: number;

  @Property({ columnType: "varchar", fieldName: "user_name" })
  userName: string;
  // ...
}
```

In the above example, userId and userName are camelCase properties in your entity, but they are explicitly mapped to user_id and user_name in the database.

#### DTO & Entity Usage in a POST Request (Example)

_1. User Entity (User.ts):_
This is a basic user entity that corresponds to your users table in the database.

```js
import { Entity, PrimaryKey, Property } from "@mikro-orm/core";

@Entity()
export class User {
  @PrimaryKey()
  @SerializedPrimaryKey()  // This decorator is useful when using non-numeric primary keys like UUIDs
  id!: number;  // '!' is used to tell TypeScript that this field will be populated automatically

  @Property()
  username: string;

  @Property()
  email: string;

  // ... other properties like password, etc.
}
```

_2. DTO for Creating User (create-user.dto.ts):_
This DTO will be used to receive data from the POST request.

```js
export class CreateUserDto {
    readonly username: string;
    readonly email: string;
    // ... other relevant properties
}
```

_3. User Service (user.service.ts):_
This service handles the business logic, including interacting with the database using MikroORM.

```js
import { Injectable } from '@nestjs/common';
import { User } from './entities/user.entity';
import { CreateUserDto } from './dto/create-user.dto';
import { EntityRepository } from '@mikro-orm/core';

@Injectable()
export class UserService {
    constructor(
        @InjectRepository(User)
        private readonly userRepository: EntityRepository<User>,
    ) {}

    async createUser(createUserDto: CreateUserDto): Promise<User> {
        const user = this.userRepository.create(createUserDto);
        await this.userRepository.persistAndFlush(user);
        return user;
    }
}
```

_4. User Controller (user.controller.ts):_
The controller handles the HTTP requests. The POST route uses the CreateUserDto.

```js
import { Controller, Post, Body } from '@nestjs/common';
import { CreateUserDto } from './dto/create-user.dto';
import { User } from './entities/user.entity';
import { UserService } from './user.service';

@Controller('users')
export class UserController {
    constructor(private readonly userService: UserService) {}

    @Post()
    async createUser(@Body() createUserDto: CreateUserDto): Promise<User> {
        return this.userService.createUser(createUserDto);
    }
}
```

_Summary_

- The CreateUserDto is used in the controller to define the shape of the data received from the client.
- The service receives the CreateUserDto, uses it to create a new User entity instance, and then persists this instance to the database.
- The entity User represents the structure of your database table and is used for database operations.
- This separation ensures that the input data is validated and transformed as needed before being used to create a new entity in the database.

#### Steps to Use UUIDs in MikroORM

If you're using a database that doesn't natively generate UUIDs, you might need to use an external package like uuid to generate them. Install it via npm if needed (`npm install uuid`).

Example:

```js
import { Entity, PrimaryKey, Property } from "@mikro-orm/core";
import { v4 as uuidv4 } from "uuid";

@Entity()
export class User {
  @PrimaryKey({ type: "uuid" })
  id: string = uuidv4();

  @Property()
  username: string;

  @Property()
  email: string;

  // ... other properties ...
}
```

When you create a new user in your service, MikroORM will handle the UUID generation (no extra steps required at this point).

#### Populating in MikroORM

"Populating" in MikroORM refers to the process of automatically loading related entities (or relations) when you fetch an entity from the database. This is similar to "eager loading" in other ORMs.

When you define a relationship in MikroORM (like @ManyToOne or @OneToMany), the related entities are not loaded by default. To load them, you use the populate option in your query.
Populating ensures that when you retrieve an entity, its related entities are also fetched and available for use, which is helpful in resolving relationships in a single query.

#### ManyToOne and OneToMany Relationships

These are types of entity relationships in MikroORM (and ORMs in general) that define how entities are related to each other in the database.

##### ManyToOne()

1. ManyToOne: This relationship means that many instances of an entity can be associated with one instance of another entity. For example, in a blog application, many Comment entities might be related to one Post entity. In MikroORM, you would define this in the Comment entity class with the @ManyToOne decorator.

The following code example establishes a Many-to-One relationship between the current entity and the Supplier entity. It means that many instances of the current entity can be related to one instance of the Supplier entity. The arrow function () => Supplier is used to defer the evaluation of the Supplier entity and avoid circular dependency issues.

```js
@ManyToOne(() => Supplier, {
    nullable: false,
    eager: true,
    cascade: [Cascade.ALL],
  })
```

1. nullable: `false`

- This specifies that the foreign key column in the database cannot be null. In other words, every instance of this entity must be associated with a Supplier entity. It enforces a mandatory relationship.

2. eager: `true`

- Eager loading means that whenever you load instances of this entity, the related Supplier entity will be automatically loaded along with it.
- This is opposed to lazy loading, where the related entity would only be loaded when specifically accessed. Eager loading can be useful for relationships where you almost always need the related data, but it can lead to performance issues if not used judiciously due to the potential for loading large amounts of data.

3. cascade: `[Cascade.ALL]`

- Cascading options define how database operations should be cascaded from the parent entity to the child entity.
- Cascade.ALL means that all operations (like persisting, removing, etc.) performed on the current entity will be cascaded to the associated Supplier entity.
- This can be powerful, but it should be used carefully as it can lead to unintended updates or deletions in your database.

##### OneToMany()

2. OneToMany: This is the inverse of ManyToOne. One instance of an entity is associated with many instances of another entity. In the blog example, one Post has many Comments. In MikroORM, this would be defined in the Post entity class with the @OneToMany decorator.

These relationships are crucial for modeling how data is structured and related in your application's database. They also dictate how you can query related data using MikroORM.

#### PK & FK

- Primary Key (PK): A unique identifier for each record in a database table, ensuring that no two rows have the same primary key.

Foreign Key (FK): A field in one table that links to the primary key in another table, establishing a relationship between the two tables.

Relation: Foreign keys in a table point to primary keys in another, creating connections across tables, essential for relational databases to maintain data integrity and enable complex queries.

## Tailwind CSS

This section includes relevant information for Tailwind CSS (CSS framework).

### Skeleton Loader (Pulse Effect)

Uses `animate-pulse` to create the typical skeleton pulse effect ([source](https://tailwindcss.com/docs/animation)).

```js
<div class="border border-blue-300 shadow rounded-md p-4 max-w-sm w-full mx-auto">
  <div class="animate-pulse flex space-x-4">
    <div class="rounded-full bg-slate-700 h-10 w-10"></div>
    <div class="flex-1 space-y-6 py-1">
      <div class="h-2 bg-slate-700 rounded"></div>
      <div class="space-y-3">
        <div class="grid grid-cols-3 gap-4">
          <div class="h-2 bg-slate-700 rounded col-span-2"></div>
          <div class="h-2 bg-slate-700 rounded col-span-1"></div>
        </div>
        <div class="h-2 bg-slate-700 rounded"></div>
      </div>
    </div>
  </div>
</div>
```

## KeyCloak

Keycloak is an open-source identity and access management solution which is part of the JBoss family, a project overseen by Red Hat. It offers a comprehensive set of features to implement secure authentication and authorization mechanisms in applications. Here's a breakdown of its various aspects:

_What is Keycloak?_
Keycloak is designed to manage identities and access in modern applications and services. It centralizes the login functionality for different types of applications (web, mobile, services) and provides features like Single Sign-On (SSO), two-factor authentication, identity brokering, and social login.

_What Does it Do?_

- User Authentication and Authorization: It handles user login and ensures that users are who they claim to be. It also manages what access each user has.

- Single Sign-On (SSO): Enables users to log in once and gain access to multiple applications without re-authenticating.

- Identity Brokering: Connects with external identity providers (like Google, Facebook, or enterprise identity systems) to support social logins or to use an existing identity source.

- User Federation: Integrates with existing user directories (like LDAP or Active Directory) to manage user identities.

- Token-based Security: Uses OpenID Connect and OAuth 2.0 protocols to secure applications and services with tokens.

_Why Use Keycloak?_

- Security: Offers robust security features out of the box, reducing the risk of security flaws in custom implementations.

- Ease of Integration: Easily integrates with various platforms and technologies.

- Customization: Highly customizable to fit different requirements.

- Community Support: Being open-source, it has strong community support and continuous updates.

_How Do You Use It_?

- Installation and Setup: Install Keycloak on a server or use a cloud instance. Configure realms, clients, and roles.

- Integration: Integrate Keycloak with your applications using adapters or standard protocols like OpenID Connect or SAML.

- User Management: Manage users, roles, and permissions within Keycloak.

_Realms, Clients, Roles and Tenants_

- Realms: A realm in Keycloak is a way to manage a set of users, credentials, roles, and groups. Each realm is a separate namespace and does not share data with other realms. It's like a container of data.

- Clients: In Keycloak, a "client" represents an application or service that wants to use Keycloak for authentication and authorization purposes. This is a broad concept and can include various types of applications. Each client within Keycloak is configured with specific settings that determine how it interacts with the Keycloak server.

- Roles in Keycloak are a way to define permissions and access levels for users or clients. They are used to control what actions a user can perform or what resources they can access. Roles can be assigned to users directly, or they can be mapped through groups or composite roles (a role that combines multiple other roles). When a user or a client is authenticated, Keycloak issues a token (like a JWT token) that includes the roles assigned to them. This token is then used to determine their access rights in different applications or services.

- Tenants: In a multi-tenancy setup, each tenant (usually representing a different business or organizational unit) can have its own realm. This allows for segregation of user spaces and customized authentication flows.

Keycloak's flexibility and range of features make it a popular choice for managing identity and access, especially in scenarios requiring high security and efficient user management. It's suitable for a wide range of applications, from small projects to large enterprise systems.

## Docker

This section covers relevant information about Docker.

### Additional Information

- For all containers it is important to use a exposed port.
- When creating a new mariaDB container in portainer, you have to add a MARIADB_ROOT_PASSWORD env variable. The username is automatically set to "root" in this case. This way you are able to connect to this container with HeidiSQL.
- When creating a new postgreSQL container in portainer, you have to add a POSTGRES_PASSWORD env variable. The username is automatically set to "postgres " in this case. This way you are able to connect to this container with HeidiSQL. A new PostgreSQL database can be picked from the connection window in HeidiSQL, the tables are placed within the public schema. To create a custom schema use `CREATE SCHEMA my_schema AUTHORIZATION postgres;` via SQL.
- If a Docker container needs to be connected to another docker container, they need to be in the same bridge network (I think) and they need to use the container's IP while you on your local machine may be able to just use localhost, for example.
- Docker Compose makes it possible to use containers name to connect to each other instead of IPs
- Docker Desktop enables the use of docker within Windows (doesn't have to be done through wsl terminal)

### Docker & WSL

- Overview of docker disk usage: `docker system df`
- View all docker images on the machine: `docker images`
- Build a docker image (in the same directory as the application): `docker buildx build -t IMAGE_NAME:TAG .`
- View all current running and stopped processes: `docker ps -a`
- Start a container with .env file in project (Port to reach it:Port the application was exposed to through dockerfile): `docker run -p 3000:5000 --env-file .env APP_NAME:latest`
- Remove a docker image: `docker rmi IMAGE_NAME:TAG`
- Stop a container: `docker stop CONTAINER_NAME_OR_ID`
- Remove a stopped container: `docker rm CONTAINER_NAME_OR_ID`
- Delete all non-used and hanging images: `docker image prune -a`
- Delete the builder cache: `docker builder prune`
- Delete the volumes: `docker volume prune`
- Delete stopped containers: `docker container prune`
- View the layers of the corresponding docker image: `docker history IMAGE_NAME:TAG`
- Run the docker-compose.yml file: `docker-compose up`
- Stop the docker compose applications: `docker-compose down`
- Rebuild the containers from the docker compose: `docker-compose up --build`
- View the docker compose logs: `docker-compose logs -f`
- WSL Shutdown (after exiting the WSL): `wsl --shutdown`

When logging in with docker (general login or login for specific registries), you may want to encrypt/hide your password: Use `sudo apt-get install pass` to install `pass`, download [docker-credential-helpers](https://github.com/docker/docker-credential-helpers), afterwards make the binary executable with `sudo chmod +x /usr/local/bin/docker-credential-pass` and put the binary into the path directoy with `move C:\Users\USERNAME\Desktop\docker-credential-pass.exe "C:\Program Files\Docker\docker-credential-pass.exe"` (on Windows) and use `gpg --gen-key`, use `gpg --list-keys` to find the gpg id, and use `pass init GPG_ID`, add `"credsStore": "pass"` to the docker config in `/home/your_username/.docker/config.json` - remember to store the gpg passphrase somewhere safe that will be cached at first.

### Commands Within Container

- List all installed packages: `apk list --installed`
- View the 20 largest files/directories: `du -h | sort -rh | head -20`
- Look inside node_modules directory: `du -sh node_modules/*`

### Dockerfile in an Application

1. What It Is: A Dockerfile is a text document that contains all the commands a user could call on the command line to assemble an image. In the context of a React.js or Nest.js application, it typically includes instructions to build a complete and executable version of your application in a Docker container.

2. Purpose:

- Consistency: It ensures that your application runs the same way in different environments (development, staging, production) by specifying the exact operating system, dependencies, environment variables, and file locations.
- Dependencies: It explicitly defines all the dependencies and their versions, so there are no discrepancies between development and production environments.
- Configuration: It can include various configuration steps like installing necessary packages, setting up environments, and executing build scripts.

### Docker Image

1. What It Is: A Docker image is a lightweight, standalone, executable package that includes everything needed to run a piece of software, including the code, a runtime, libraries, environment variables, and config files.

2. Purpose:

- Portability: Once an image is created, it can be run on any machine that has Docker installed, regardless of the underlying infrastructure.
- Version Control: Images can be versioned, allowing easy rollbacks to previous states and ensuring that everyone on a team is using the same environment.
- Isolation: Docker images can run in isolation, preventing conflicts between different projects or parts of a project.

### Docker in React.js or Nest.js Applications

1. Development & Deployment: Docker simplifies the development and deployment process. For instance, a React.js front-end and a Nest.js back-end can each have their Docker containers. They can be developed, tested, and deployed independently yet work together seamlessly in production.

2. Microservices Architecture: Particularly for complex applications, Docker supports a microservices architecture by allowing each service (like a Nest.js API) to run in its own container, ensuring isolation and ease of scalability.

3. Environment Standardization: Docker ensures that everyone working on the project, from developers to QA testers, has the same environment. This "it works on my machine" problem is significantly reduced.

4. CI/CD Integration: Docker works well with continuous integration and continuous deployment pipelines. Automated tools can use Docker images to create consistent testing and deployment environments.

5. Cloud Compatibility: Docker containers can be easily deployed to cloud platforms, offering high compatibility with cloud services.

## WSL

WSL stands for Windows Subsystem for Linux. It's a feature provided by Microsoft for Windows 10 and Windows 11 operating systems, enabling users to run a Linux environment directly on Windows, without the need for a traditional virtual machine or dual-boot setup.

### Key Features and Benefits of WSL:

1. Run Linux Natively on Windows: WSL allows you to run a GNU/Linux environment, including most command-line tools, utilities, and applications, directly on Windows.

2. Multiple Linux Distributions: You can install different Linux distributions from the Microsoft Store, such as Ubuntu, Debian, Fedora, and others.

3. Integration with Windows: WSL provides seamless integration between Windows and the Linux subsystem. For example, you can access Windows files from within the Linux environment and vice versa.

4. Development and Testing: WSL is particularly useful for development, especially when you're developing applications that will be deployed on a Linux server or using tools and technologies that are native to Linux. It's also beneficial for testing scripts and running Linux-based services.

5. No Overhead of a Full Virtual Machine: Unlike running a full Linux virtual machine, WSL does not require a significant amount of additional system resources. It's a lightweight solution that directly leverages the Windows kernel.

### Versions: WSL 1 vs WSL 2

There are two versions of WSL:

- WSL 1: The first iteration, offering translation of Linux system calls into Windows system calls. It's known for better compatibility with Windows but with some performance limitations.

- WSL 2: The newer version uses a real Linux kernel in a lightweight virtual machine. It provides significantly improved performance, especially for file system operations, and better system call compatibility. WSL 2 is recommended for most users.

### Setting Up WSL

Setting up WSL typically involves enabling the feature through Windows Features or using PowerShell commands, and then installing a Linux distribution of your choice from the Microsoft Store.

WSL has become a popular tool among developers who use Windows but need or prefer a Linux environment for certain tasks. It exemplifies the growing cross-platform compatibility in modern development environments.

## Blob Storage

Blob storage, short for Binary Large Object storage, is a solution for storing large amounts of unstructured binary data, such as images, audio, video, or documents. It's commonly used in cloud storage services like AWS S3, Azure Blob Storage, or Google Cloud Storage. Here's how it works and how you use it in conjunction with a database:

1. Storing Data: Blob storage is designed to store large binary files. It's optimized for storing massive amounts of unstructured data, providing high availability, reliability, and scalability.

2. Access: You typically interact with blob storage through APIs provided by the cloud service. These APIs allow you to upload, download, and manage your blobs (files).

### Keeping References in the Database

1. Upload to Blob Storage: Instead of storing the actual image file in your database, you upload the image to a blob storage service. After uploading, you receive a unique URL or identifier for the stored image.

2. Store Reference in Database: You then store this URL or identifier in your database, not the image itself. This reference is used to access the image when needed.

3. Retrieval: When you need the image, you use the stored reference to fetch it directly from the blob storage. Your application or users can access the image via the URL or through an API call that retrieves the blob data using its identifier.

### Advantages

1. Efficiency: Storing large files in a database can be inefficient and costly. Blob storage is a more cost-effective and performance-optimized solution.
2. Scalability: Blob storage services are built to handle large amounts of data and traffic, making them ideal for scalable applications.
3. Separation of Concerns: This approach keeps your database lean and focused on structured data, while blob storage handles the unstructured data.
4. Security and Management: Cloud-based blob storage services offer robust security, backup, and data management features.

### Example Scenario

Let's say you have a web application where users can upload profile pictures. Instead of storing these images directly in your SQL database:

1. The images are uploaded to an AWS S3 bucket (blob storage).
2. Each image gets a unique URL or key.
3. In your user table in the database, you store this URL or key in a column, say profile_picture_url.
4. When you need to display a user's profile picture, your application fetches the image using the URL from the S3 bucket.

In summary, blob storage is used for efficient, scalable storage of large binary files, while your database holds references to these files, offering a more optimized and manageable data storage architecture.

## CRON

CRON is a time-based job scheduling system commonly used in Unix-like operating systems. It enables users to schedule scripts, commands, or software applications to run at specified times, dates, or intervals. Here's a brief overview:

- Cronjobs: These are the scheduled tasks that you want to run automatically at specified intervals. Each task is defined in a line of a "crontab" (cron table) file.

- Crontab: This is the configuration file where cronjobs are specified. Each line in a crontab file represents a separate job and consists of a CRON expression (indicating when the job should be executed) and the command to execute.

- CRON Expression: A CRON expression is a string of fields separated by spaces, representing a set of times for when a job should be executed. The fields typically represent minute, hour, day of the month, month, day of the week, and optionally year.

- Usage: CRON is widely used for automating system maintenance tasks, backups, monitoring scripts, and other recurring tasks that need to be run at regular intervals.

By setting up cronjobs, you can automate repetitive tasks and maintain your system efficiently without manual intervention.

### Cronjob via Next.js and via dockerfile

#### In crons file:

```
0 * * * * * curl -s -f http://localhost:${PORT}/ENDPOINT_PATH
... more cronjobs ...
```

#### In custom-entrypoint.sh (look out for LF or CRLF)

```sh
#!/bin/sh

# Start cron service in background
echo "STARTING CRON SERVICE..."
crontab -l
crond -l 0

# Run command provided by the dockerfile
exec "$@"

```

1. #!/bin/sh: This is called a shebang. It tells the system that this script should be run with the sh shell.

2. echo "STARTING CRON SERVICE...": This command prints the message "STARTING CRON SERVICE..." to the console. It's useful for logging and debugging to know what the script is doing.

3. crontab -l: This command lists the current user's cron jobs. It's likely used here to show the current cron jobs for debugging or logging purposes.

4. crond -l 0: This command starts the cron daemon (crond) in the background. The -l 0 flag sets the log level to 0, which means the cron daemon will log all messages. Starting the cron service ensures that any scheduled jobs specified in the cron table will be executed.

5. exec "$@": This command replaces the shell with the command provided as arguments to the script. The "$@" variable holds all the arguments passed to the script. This is typically used in entrypoint scripts to allow the container to run the command specified in the Dockerfile's CMD instruction or as provided in the docker run command. It ensures that the main process runs as PID 1 in the container, which is important for proper signal handling and termination of the container.

#### In Dockerfile:

```
...
COPY crons /etc/crontabs/root

COPY ./custom-entrypoint.sh /usr/local/bin/custom-entrypoint.sh
RUN chmod +x /usr/local/bin/custom-entrypoint.sh
...

ENV PORT 5000
ENV HOSTNAME 0.0.0.0
EXPOSE 5000

...

ENTRYPOINT ["custom-entrypoint.sh"]

...
```

- `chmod +x` is a Unix command that changes the file permissions to make the file executable.

## CSS

This section covers some CSS information.

### Style scroll bar

There are multiple ways to style the scrollbar. With CSS you basically have the most control over it:

```js
*::-webkit-scrollbar {
  width: 15px;
}

*::-webkit-scrollbar-track {
  background: #eea842;
}

*::-webkit-scrollbar-thumb {
  background-color: #252525;
}
```

### Tailwind CSS

#### Darkmode

If the parent element has the "dark" class, all child elements can make use of "dark:..." to apply styles for this state of darkmode.
Normally, you may use a cookie for the theme or some similar name. In the layout (speaking of Next.js), you then can apply this cookie on the html class name with "dark" or "light", for example. This will enable the darkmode Tailwind CSS feature in your application.

## Code Examples

### Convert (png) image to base64

```ts
const emailLogoPath = path.resolve(process.cwd(), "public/email/logo.png");
const emailLogoBuffer = fs.readFileSync(emailLogoPath);
const base64EmailLogo = emailLogoBuffer.toString("base64");
const emailLogoSrc = `data:image/png;base64,${base64EmailLogo}`;
```

If dealing with rapid quality loss, consider using a larger sized image.

### Handle URL Rewrites in middleware (Next.js) - Solving potential CORS Errors

```ts
import { withAuth } from "next-auth/middleware";
import { NextRequest, NextResponse } from "next/server"

const rewriteURL = (request: NextRequest, replace: RegExp, replaceWith: string) => {
  return NextResponse.rewrite(
    request.nextUrl.pathname.replace(replace, replaceWith) + request.nextUrl.search,
  );
};

export default withAuth(async (request: NextRequest) => {
  if (request.nextUrl.pathname.startsWith("/api/your_api_service")) {
    return rewriteURL(request, /^\/api/your_api_service/, "your_api_service_api_url");
  } else if (...) {
    ...
  }
});

export const config = {
  matcher: ["/((?!_next/static|_next/image|favicon.ico).*)"],
}
```

### Fibonacci with Memo

```js
const fibo = (n, memo = {}) => {
  if (n in memo) return memo[n];
  if (n === 0) return 0;
  if (n <= 2) returnb 1;

  memo[n] = fibo(n - 1, memo) + fibo(n - 2, memo);
  return memo[n];
}
```

### Fibonacci with Dynamic Programming

```js
const fibo = (n) => {
  if (n === 0) return 0;

  const dp = new Array(n);
  dp[0] = 0;
  dp[1] = 1;

  for (let i = 2; i <= n; i++) {
    dp[i] = dp[i - 1] + dp[i - 2];
  }

  return dp.at(n);
};
```

### isServer

```ts
const isServer = typeof window === "undefined" || "Deno" in globalThis;
```

## Network Information

### Common/Important Ports

Port numbers are integral to networking, as they help identify specific services and applications on a network. Here are some of the most important port numbers, along with the services they are commonly associated with:

1. Port 22 - SSH (Secure Shell)

- Service: Secure Shell (SSH)
- Purpose: Used for securely logging into remote systems, executing commands remotely, and transferring files securely using tools like SCP (Secure Copy) and SFTP (Secure File Transfer Protocol).

2. Port 443 - HTTPS (Hypertext Transfer Protocol Secure)

- Service: HTTPS
- Purpose: Used for secure web traffic, ensuring data transmitted between a web server and a browser is encrypted.

3. Port 80 - HTTP (Hypertext Transfer Protocol)

- Service: HTTP
- Purpose: Used for standard, unsecured web traffic. HTTP is the foundation of any data exchange on the Web.

4. Port 25 - SMTP (Simple Mail Transfer Protocol)

- Service: SMTP
- Purpose: Used for sending emails from a client to a server or between email servers.

5. Port 110 - POP3 (Post Office Protocol version 3)

- Service: POP3
- Purpose: Used by email clients to retrieve messages from a mail server. Unlike IMAP, it downloads the emails and typically deletes them from the server.

6. Port 143 - IMAP (Internet Message Access Protocol)

- Service: IMAP
- Purpose: Used by email clients to retrieve messages from a mail server, allowing the management of emails directly on the server without downloading them.

7. Port 53 - DNS (Domain Name System)

- Service: DNS
- Purpose: Used to translate domain names into IP addresses, enabling browsers to load websites.

8. Port 23 - Telnet

- Service: Telnet
- Purpose: Used for remote access to servers and networking devices. It is insecure as data, including passwords, are transmitted in plain text.

9. Port 21 - FTP (File Transfer Protocol)

- Service: FTP
- Purpose: Used for transferring files between a client and a server. It is not secure, so secure alternatives like SFTP (SSH File Transfer Protocol) are often preferred.

10. Port 3389 - RDP (Remote Desktop Protocol)

- Service: RDP
- Purpose: Used by Windows for remote desktop access, allowing users to connect to another computer over a network connection.

11. Port 445 - SMB (Server Message Block)

- Service: SMB
- Purpose: Used for sharing files, printers, and serial ports among computers on a network.

12. Port 389 - LDAP (Lightweight Directory Access Protocol)

- Service: LDAP
- Purpose: Used to access and maintain distributed directory information services, such as managing user and group information in a network.

13. Port 3306 - MySQL

- Service: MySQL Database Service
- Purpose: Used by the MySQL database management system for database connections.

14. Port 137-139 - NetBIOS

- Service: NetBIOS
- Purpose: Used for file and printer sharing over a network in older Windows systems.

15. Port 161/162 - SNMP (Simple Network Management Protocol)

- Service: SNMP
- Purpose: Used for managing and monitoring network devices like routers, switches, and servers.

16. Port 514 - Syslog

- Service: Syslog
- Purpose: Used for system logging on Unix and Linux systems.

17. Port 8080 - HTTP Alternative

- Service: HTTP Alternative
- Purpose: Often used as an alternative to HTTP port 80, typically for web servers running on non-standard configurations.

These ports represent a mixture of essential services for secure communication, file transfer, email exchange, and network management. Understanding these ports and their associated services is crucial for network configuration, security management, and troubleshooting.

### Layers of the OSI (Open Systems Interconnection) Model

1. Physical Layer
   _Function_: Deals with the physical connection between devices, including the transmission of raw binary data over a physical medium (like cables, radio waves).
   _Examples_: Ethernet cables, fiber optics, wireless signals, network adapters.

2. Data Link Layer
   _Function_: Responsible for node-to-node data transfer, error detection and correction, and MAC (Media Access Control) addressing.
   _Examples_: Switches, MAC addresses, Ethernet, PPP (Point-to-Point Protocol).

3. Network Layer
   _Function_: Manages data routing, forwarding, and addressing to ensure that data is sent from the source to the correct destination.
   _Examples_: Routers, IP addressing (IPv4, IPv6), ICMP (Internet Control Message Protocol).

4. Transport Layer
   _Function_: Ensures complete data transfer, manages error detection and correction, flow control, and reassembly of data packets.
   _Examples_: TCP (Transmission Control Protocol), UDP (User Datagram Protocol), port numbers.

5. Session Layer
   _Function_: Manages sessions between applications, handling connections and sessions (e.g., establishing, maintaining, and terminating connections).
   _Examples_: APIs, session management, SSL/TLS for establishing sessions.

6. Presentation Layer
   _Function_: Translates data between the application layer and the network, handling data encryption, compression, and formatting.
   _Examples_: Data encryption (like SSL/TLS), data compression, character encoding (like ASCII, EBCDIC).

7. Application Layer
   _Function_: Closest to the end user, it provides network services directly to applications, such as email, file transfer, and web browsing.
   _Examples_: HTTP, FTP, SMTP, DNS, Telnet, web browsers.

## Typescript

### Generics examples

```ts
type ClientResourceScopes = {
  "a-controller": {
    A: "view" | "edit";
    B: "create" | "delete";
  };
  "b-controller": {
    C: "start" | "stop";
    D: "create" | "complete";
  };
};

type ValidResourcesForClient<T extends keyof ClientResourceScopes> =
  keyof ClientResourceScopes[T];

type ValidScopesForClientResource<
  T extends keyof ClientResourceScopes,
  R extends ValidResourcesForClient<T>
> = ClientResourceScopes[T][R];

interface PermissionScopesGrantedArguments<
  T extends keyof ClientResourceScopes,
  R extends ValidResourcesForClient<T>
> {
  client: T;
  resource: R;
  scopes: ValidScopesForClientResource<T, R>;
}
```

### Type Guards

A type guard in TypeScript is a function that allows you to narrow down the type of a variable within a conditional block. It uses type predicates to assert that a value has a specific type. Type guards are particularly useful when working with union types, where you need to distinguish between different types within a union.

```ts
// Union type
type StringOrNumber = string | number;

// Type guard function to check if the value is a string
function isString(value: StringOrNumber): value is string {
  return typeof value === "string";
}

// Type guard function to check if the value is a number
function isNumber(value: StringOrNumber): value is number {
  return typeof value === "number";
}

// Usage example
function printValue(value: StringOrNumber) {
  if (isString(value)) {
    // TypeScript now knows `value` is a string
    console.log(`The string is: ${value.toUpperCase()}`);
  } else if (isNumber(value)) {
    // TypeScript now knows `value` is a number
    console.log(`The number is: ${value.toFixed(2)}`);
  }
}
```

## Other Examples

### Session Provider with Context

_Attention:_
This is just an example. With Next-Auth you don't need to use this since useSession() already makes use of a context. This is not an optimization in terms of requests amount.

```ts
"use client";

import {
  SessionProvider as NextAuthSessionProvider,
  useSession,
  Session,
} from "next-auth/react";
import React, {
  createContext,
  useContext,
  useState,
  useEffect,
  ReactNode,
  Dispatch,
  SetStateAction,
} from "react";

interface CustomSessionContextType {
  data: Session | null;
  status: "loading" | "authenticated" | "unauthenticated";
  update: (data?: any) => Promise<void>;
}

interface SessionContextProviderProps {
  setCustomSession: Dispatch<SetStateAction<CustomSessionContextType>>;
  children: ReactNode;
}

const CustomSessionContext = createContext<CustomSessionContextType | null>(
  null
);

export const useCustomSession = () => {
  const context = useContext(CustomSessionContext);
  if (!context) {
    throw new Error(
      "useCustomSession must be used within a SessionProviderWrapper"
    );
  }
  return context;
};

export const SessionProviderWrapper = ({
  children,
}: {
  children: ReactNode;
}) => {
  const [customSession, setCustomSession] = useState<CustomSessionContextType>({
    data: null,
    status: "loading",
    update: async () => {},
  });

  return (
    <NextAuthSessionProvider>
      <SessionContextProvider setCustomSession={setCustomSession}>
        <CustomSessionContext.Provider value={customSession}>
          {children}
        </CustomSessionContext.Provider>
      </SessionContextProvider>
    </NextAuthSessionProvider>
  );
};

// SessionContextProvider Component
const SessionContextProvider: React.FC<SessionContextProviderProps> = ({
  setCustomSession,
  children,
}) => {
  const { data: session, status, update } = useSession();

  useEffect(() => {
    setCustomSession({ data: session, status, update });
  }, [session, status, update, setCustomSession]);

  return <>{children}</>;
};
```

## Kubernetes (https://www.boot.dev/lessons/85d0acd6-b0ac-4afe-a061-a7f9effc1d3c)

Kubernetes orchestrates and manages collections of containers (often those created by Docker). It takes care of scaling, distribution, and connectivity among these containers. Think of it as a system to manage many containers and the infrastructure they run on.
For example, you could install Docker on a single server, and route traffic directly to it. That's fairly simple to set up, but what if you want 10 instances of that server? What about 1000 instances? What if you want to deploy many different services, each scaling up with more instances depending on load? Those are the problems that Kubernetes solves.
The Kubernetes command-line tool, kubectl, allows you to run commands against Kubernetes clusters. It's a client that communicates with a Kubernetes API server.
