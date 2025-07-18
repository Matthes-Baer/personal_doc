# Personal Documentation for relevant topics and keywords

This personal documentation can be best used by using CTRL + F to search for specific keywords.

## General Commands

- Open `C:\Users\<user>\OneDrive\Documents` via a `cmd` terminal: `explorer $PROFILE`
- Run TypeScript file directly with Node ([since v22.6.0, and since v23.6.0 this is enabled by default](https://nodejs.org/en/learn/typescript/run-natively)): `node --experimental-strip-types example.ts`
- Select MySQL database: `USE database_name;`
- Connect to postgres database in container: `psql -h localhost -U postgres`
- Connect to PostgresSQL database: `\c database_name`
- Show tables of a MySQL database: `show tables;`
- Show tables of a PostgresSQL: `\dt`
- Bind a Next.js development server to all network interfaces, making it accessible for other devices/user on the same network: `pnpm run dev -H 0.0.0.0 -p PORT`
- Connect to a server via ssh: `ssh username@server_ip_or_hostname` (afterwards it will ask for password, unless SSH key is set up)
- Create a secret with python (e.g. for API Keys): `py -c "import secrets; print(secrets.token_hex(32))"` (this can be used in PowerShell, or use the code directly within a python session)
- Create a secret with just PowerShell: `-join ((48..57) + (65..90) + (97..122) | Get-Random -Count 64 | ForEach-Object {[char]$_})`
- Drop table in SQL and remove constraints (foreign keys) and dependent objects (views, indexes, sequences, triggers, ..): `DROP TABLE table_name CASCADE;`
- Automatically delete `node_modules` in project: `npx npkill`
- Execute prettier for all files in current directory (files in `.prettierignore` will be ignored): `npx prettier --write .`
- Execute eslint for all files in `/src` directory (with just `.` (whole current directory) it may load forever due to the amount of files): `npx eslint ./src`
- Execute eslint while automatically fixing all errors eslint can fix by itself in `./src` directory (like errors for import sorting): `npx eslint ./src --fix`
- Automatically delete node_modules in directory: `npx npkill`
- Perform a hard refresh to bypass the browser cache: `Ctrl + Shift + R`
- Create an empty file via terminal: `type nul > .env`
- Create a file with input via terminal: `echo DB_HOST=localhost > .env`
- Create new folder via terminal: `mkdir folder_name`
- Sending a ping to a domain / ip address: `ping example.com`
- Open IP Config: `ipconfig` & `ipconfig /all`
- On Current Cursor Position Import: `CTRL + .`
- Toggle Terminal in VS Code: `CTRL + J`
- Close all files in VS Code: `CTRL + K W`
- Select all entries of a word (while cursor is on it) and replace all of them in VS Code: `F2` 
- Show all currently running processes on the system: `tasklist`
- Terminate tasks by process ID or image name: `taskkill`
- Display detailed configuration information about a computer and its operating system: `systeminfo`
- Select all Occurrences of Current Word in VS Code: `Ctrl + F2`
- Select Next Occurrence of Current Word in VS Code: `Ctrl + D`
- Add Cursors to Line Ends in VS Code: `Ctrl + Alt + Down` / `Ctrl + Alt + Up`
- Add Cursor in VS Code: `Alt + Click`
- Change Terminal Background (`settings.json`): `%localappdata%\Packages\Microsoft.WindowsTerminal_8wekyb3d8bbwe\LocalState`
- Access experimental Chromium features (search for ...): `chrome://flags/`
- Create a new named migration file in Nest.js with MikroORM: `npm run migration:generate --name=migration_name`
- Migrate Database to most current version based on migration files (used after entities and migration files were added): `npm run migration:run`
- Start Next.js application on a different port (in package.json for port 8080): `"dev": "next dev -p 8080"`
- Start a simple HTTP server in the current directory: `python -m http.server`
- Delete .git in Windows Command Prompt: `rmdir /s /q .git`
- Forcefully update dependencies to fix vulnerabilities, potentially causing breaking changes: `npm audit fix --force`
- Prisma generate: `npx prisma generate`
- Prisma migrate: `npx prisma migrate dev --name init`
- Prisma migrate deploy: `npx prisma migrate deploy`
- Open command pallete in VS Code (for reloading the window, for example): `CTRL + Shift + P`#
- Programmatically reload page: `window.location.reload()`
- Open a CMD prompt from current file explore path (in a specific file explorer folder): `CTRL + L` -> Type in `cmd` or `powershell`
- Save without formatting in VS Code: `CTRL + P + >`, then `Save without formatting`
- Create a base64 string based on a string input in the console: `echo -n 'username:password' | base64`
- Get system information (including RAM): `wmic memorychip list full`
- Get information specifically for RAM: `Get-CimInstance win32_physicalmemory | Format-Table Manufacturer,Banklabel,Configuredclockspeed,Devicelocator,Capacity,Serialnumber -autosize`
- Add Basic Auth with base64 string: `'Authorization': 'Basic ' + (new Buffer.from(client_id + ':' + client_secret).toString('base64'))`
- Open command line in chrome developer tools (to disable/enable JavaScript, for example): `CTRL + SHIFT + p`
- Open PowerToys Selection for a file: `Shift + Rightlick`
- Open current folder via terminal in VS Code: `code .`
- Open File Explorer from current directory (on Windows via PowerShell): `start .`
- With Copilot in VS Code, open the Copilot chat: `CTRL + i`
- Open something with powertoys: `Shift + Rightclick`
- In here are the nvim configs (or should be placed if they are not there yet): `~/AppData/Local/nvim`
- View PATH variables with one entry per row: `$env:Path -split ";"`
- Use `theme()` and `@apply` to make use of Tailwind CSS within normal .css files / data attributes are another way to handle specific styling situations
- Create a zero-config setup for TypeScript libraries: `npx tsdx create library_name`
- Use wslcompact (https://github.com/okibcn/wslcompact): `wslcompact abc-data -c -y -d`

## Git commands

- Set git's global end of line config to lf: `git config --global core.autocrlf false`
- Set Global Git User Name: `git config --global user.name "Max Mustermann"`
- Set Global Git User Email: `git config --global user.email "example@gmail.com"`
- Push to Git stash with name: `git stash push -m "my_stash_name"`
- See all entries in Git stash: `git stash list`
- Pop the {n}th Git stash entry (this also drops the entry): `git stash pop "stash@{n}"`
- Apply the {n}th Git stash entry (this does not drop the entry): `git stash apply "stash@{n}"`
- Drop the {n}th Git stash entry (this deletes the entry without applying): `git stash drop "stash@{n}"`
- Clear the whole Git stash (this drops all entries): `git stash clear`
- Remove local references to remote branches that no longer exist: `git fetch --prune`
- Jump to a Commit in the Past (You have to Start a new branch from here if you want to build upon it): `git checkout <commit-hash>`
- Discard all not yet committed changes: `git restore .`
- Delete local Git branches: `git branch -d branchname`
- Delete Remote Repository connection (via GitLab etc.): `git push origin --delete branchname`
- Remove remote origin via Git: `git remote remove origin`
- Reset the current git user to log in with new credentials (have to push after this command): `git config --global credential.helper wincred`
- Reset all unstaged/staged local changes: `git reset --hard`
- Rename current branch (use -M if only the capitalization changes): `git branch -m <newname>`
- Rename a branch while pointed to any branch: `git branch -m <oldname> <newname>`
- Check the current remote repository URL: `git remote -v`
- Set a new remote repository URL: `git remote set-url origin https://neuerstandort.com/meinrepo.git`
- Unset the git user password (use push afterwards to enter new credentials): `git config --global --unset user.password`
- Change the casing for files via git (can't be done by just editing the files manually): `git mv -f current_file_name new_file_name`
- Start solving merge conflicts (while being on the branch to merge; use `git fetch` before): `git rebase origin/target_merge_branch`#
- Rebase current branch onto target branch (for example, feature branch as current branch and main branch as target_branch): `git rebase origin/target_branch`
- Add a git tag via command line (on commit which should be tagged): `git tag -a v1.0`, then `git push origin --tags` (use `git show` to see current commit)
- Unstage a staged file: `git reset file_path`
- Rename a file/folder recognized by git: `git mv source target_name`
- Git Add to stage with specific files excluded: `git add --all -- :!path/to/file1 :!path/to/file2 :!path/to/folder1/\* `

## pnpm/npm commands

- Install pnpm: `corepack enable pnpm` (if corepack is not installed, install it via `npm install -g corepack@latest`)
- Pin the version of pnpm used in a project: `corepack use pnpm@latest-10`
- Update pnpm itself: `pnpm self-update`
- Install other npm version: `npm install -g npm@11.1.0`
- Update all pnpm packages in project: `pnpm update --latest`
- Update only one specific package in project: `pnpm add package-name@latest`
- Show all versions of a specific package: `pnpm view package-name versions`
- Show all outdated pnpm packages in project: `pnpm outdated`
- See the pnpm config list: `pnpm config list`
- Set a pnpm config variable globally: `pnpm config set <key> <value> --global`
- Delete a pnpm config variable: `pnpm config delete <key>`
- Link your npm package: `pnpm link --global` (or `npm link`) | then link to it from your application's directory: `pnpm link your_package_name` (or `npm link your_package_name`) | do both commands but with `unlink` to unlink the package from the application and unlink it globally as well - this link process oftentimes doesn't really work
  - Alternatively, use `pnpm pack` to pack up your files in a .tgz archive format. Then, install this file from the application where you want to test it out. Use such procedure when testing out a library you are working on within an application, for example.
- Globally link a package (from package's directory; build package to have it updated for testing (like with rollup, for example)): `pnpm link --global`
- Link a globally linked package to an application (from application's directory; delete installed version of package before if necessary): `pnpm link --global linked_package`

## rg commands

- Searches for "mysearchword" inside all files under current folder: `rg mysearchword`
- Search for a phrase in all .txt files: `rg "hello world" --type txt`
- Ignore binary files (like images) (rg already does this by default): `rg "something" --binary-files=without-match`
- Search inside a specific directory: `rg error ./logs/`
- Show only filenames that match (`-l` = "list matching files"):`rg -l "needle"`
- Case-insensitive search: `rg -i "Error"`
- Show line numbers (default behavior but you can force it): `rg -n "searchterm"`
- Search using regular expressions (like find all numbers): `rg '[0-9]+'`
- Find files with one result per line which include the string "README" in their name: `rg --files --hidden | sort -u | rg "README"`

## fd commands

- Looks for files and folders matching "myfile" anywhere under the current directory: `fd myfile`
- Find only files (not directories): `fd myfile --type f`
- Find only directories (not files): `fd myfile --type d`
- Find files with a specific extension: `fd .py` / or more explicitly: `fd --extension py`
- Find files inside a specific folder: `fd myfile ./src`
- Exclude certain directories: `fd myfile --exclude node_modules`
- Run a command on found files (cat every .txt file found ( {} is replaced with each file)): `fd .txt --exec cat {}`
- Find files and folders with one result per line which include the string "readme" (ignoring case) in their name: `fd --hidden --ignore-case 'readme'`
- Find all .log files and search for "ERROR" inside them (`xargs` takes input from the previous command and builds new commands from it.): `fd --extension log | xargs rg "ERROR"`
  - Instead of using xargs, you can use fd's built-in --exec option to run a command directly on each found file: `fd --extension log --exec rg "ERROR" {}`
    - `fd` finds `.log` files
    - `--exec` means: "for every file you find, run this command"
    - `{}` is a placeholder for the filename
    - So it runs `rg "ERROR" filename.log` automatically for each file

## Linux & Unix-Based Commands
- Start WSL: `wsl`
- Check installed WSL distributions (from within Windows, not WSL): `wsl --list --verbose`
- Enter a specific WSL distribution (from within Windows, not WSL): `wsl -d <distribution_name>`
- Exit the current WSL terminal session: `exit`

- Show the path to the executable of a software (nvim in this example): `which nvim`
- In here are the nvim configs (or should be placed if not available yet): `~/.config/nvim`
- Show free memory: `df -h`
- Find Docker Volume sizes: `du -h --max-depth=1 /var/lib/docker/volumes/`
- See directory sizes: `df -h`
- See system hardware usage: `htop`
- Delete .git on Linux: `rm -rf .git`
- Remove a file (or multiple ones; with a pattern in this example (all files starting with "file")): `rm file*`
- Remove a folder: `rm -r folderName/`
- Search for files or directories containing the word "wget": `ls -laR . | grep wget` (`ls` lists the contents of directories, `-l` provides a detailed (long) listing of files, including permissions, owner, size, and modification date, `-a` includes hidden files (those starting with .), `-R` recursively lists the contents of all subdirectories within the current directory (. represents the current directory), The pipe takes the output of the first command `ls -laR .` and sends it as input to the second command `grep wget`, `grep` searches for lines containing the specified pattern `wget` in the input it receives - here, it filters the output of `ls -laR .` and displays only lines containing the word `wget`)
- Run any command as the root user (input the actual command for "..."): `sudo ...`
- Switch to the root account (if access to sudo is available): `sudo -i`
- Access the commandline package manager (lists the available commands with apt) - used with Debian-based linux distributions (like Ubuntu): `apt`
- Check the current position in the file system: `pwd`
- List the directories/files at the current file system position: `ls`
- List the directories/files at the current file system position with a long list (more details): `ls -l`
- List the directories/files at a different file system position (without having to move to that position with `cd`; swap "_path_" with the actual path to investigate): `ls _path_`
- Show files (also hidden ones) with their permissions: `ls -lah`
- Show size of directories: `du -sh *`
- Change the current directory (enter a relative or absolute path): `cd ...`
- Rename a file/folder: `mv source target_name`
- Create a new folder: `mkdir folderName`
- Create a new file: `touch fileName`
- Edit file with nano: `sudo nano /etc/resolv.conf`
- Save a file in nano: `Ctrl` + `o`
- Look into file on Linux (for small files): `cat /etc/resolv.conf`
- Look into a file (in an interactive way; for large files): `less /etc/resolv.conf`
- Search for words in a file (or multiple files with wildcard): `grep -i someWord file*`
- Show all files (including hidden ones): `ls -a`
- See all environment variables on the machine: `printenv` or `env`
- See environment variables for a particular variable (PATH in this example): `printenv PATH`
- Set an environment variable for only the current terminal session: `export ENV_NAME=ENV_NAME_VALUE`
- Check current processes: `ps`
- Kill a process (PID can be identified via `ps` command): `kill PID`
- Get to the home directory: `cd ~`
- `ipconfig` but for Linux: `ifconfig` (IP at `eth0`)
- Get OS infos: `cat /etc/os-release`
- Show infos for a file: `stat <file>`
- Recursive grep (searches through all subdirectories and the current directory for text matches): `grep -r "word_to_search" .`
- Install with apt (Debian/Ubuntu): `apt update && apt install -y curl`
- Install with apk (Alpine): `apk update && apk add curl`
- List all installed packages: `apk list --installed`
- View the 20 largest files/directories: `du -h | sort -rh | head -20`
- Look inside node_modules directory: `du -sh node_modules/*`
- Use an alias: `alias ll='ls -lah'`
- Show command history: `history | grep ssh`
- Show process monitoring: `top / htop`
- Scan open ports: `nc -zv host 1-1000`
- Delete all .log files: `find . -type f -iname "*.log" -delete`
- Run through each line: `xargs -n1 < file.txt`


## Neovim in VS Code & General VS Code

- Switch to terminal (actually toggle terminal): `CTRL + ö`
- Switch to main editor window: `CTRL + 1`
- Open external terminal with project's path: `CTRL + SHIFT + c`
- Open VS Code project's search bar: `CTRL + p`
- Open VS Code settings search bar: `CTRL + SHIFT + p`
- Switch between currently opened editor windows: `CTRL + Tab`
- Tab through side bar: `CTRL + q`
- Tab in Explorer Side Bar Tab (Use spacebar or enter to select/jump in file): `CTRL + Shift + e`
- Tab in Search Bar: `CTRL + Shift + f`
- Toggle Side Bar: `CTRL + b`
- Open new split windows or jump to the respective one: `CTRL + x` (2 for x, for example)
- Switch from one Split View to another: `CTRL + w`
- Select multiple lines with specific amount of columns (to remove multi-line comments, for example): `CTRL + v`
- Close all editors in other groups (requires keybind for `"workbench.action.closeEditorsInOtherGroups"`): `ALT + q`
- Move a block of code: select area to move and then `ALT + arrow_keys`
- Open new split view with current selected file (or close a split view): `CTRL + ALT + arrow_keys (left and right)`
- While having the cursor on a component, open the corresponding file: `F12`
- Comment out a selected area: `CTRL + #`
- Move from the search field (in the left sidebar) down to the file selection: `CTRL + arrow_down`
- Increase view width of current selected window (custom shortcut, see 'Keyboard Shortcuts (JSON)'): `CTRL + SHIFT + arrow_right`
- Decrease view width of current selected window (custom shortcut, see 'Keyboard Shortcuts (JSON)'): `CTRL + SHIFT + arrow_left`
- Close all but current selected window (custom shortcut, see 'Keyboard Shortcuts (JSON)'): `ALT + q`
- Switch current terminal (if multiple are available) in VS Code: `CTRL + PageDown/PageUp`
- Scroll up and down in current terminal in VS Code: `CTRL + ALT + PageDown/PageUp`
- Display error information while having the cursor on it (is not working in vim mode): `CTRL + k + i`
- Vertically increase terminal (custom shortcut for terminal resize): `CTRL + numpad_8`
- Vertically decrease terminal (custom shortcut for terminal resize): `CTRL + numpad_2`
- If VS Code Neovim with WSL is used, add this to the `init.lua` if it has trouble be recognized by VS Code: `If vim.g.vscode then ... else ... your_nvim_config ... End`
- Get to the "Problems" tab in VS Code (pick respective problem to jump there): `CTRL + SHIFT + m`


## General Information

- `git rebase` is a Git command that allows you to reapply your local commits on top of another branch, usually the updated remote branch. When you rebase, Git "moves" your local commits to the tip of the latest branch (like `main`), effectively rewriting history to make it look like your changes were made after the latest upstream changes. This results in a clean, linear commit history without merge commits, making the project history easier to read.
In contrast, when you pull (e.g., `git pull`), Git by default performs a merge, which brings in the latest changes from the remote branch and creates a merge commit if there are differences. This keeps the full history of how branches diverged but can lead to a messier commit log. Rebase is preferred for cleaner history and avoiding extra merge commits, while pull (with merge) is simpler and preserves the exact historical sequence of events.

- Deduplication is a technique used to avoid repeating the same operation or storing duplicate data by identifying and eliminating redundancy. In the context of React or web development, deduplication often refers to preventing multiple identical API calls or computations within a single server request or render cycle. For example, if a component requests the same data multiple times, deduplication ensures that only one actual fetch happens and the result is shared, improving performance and reducing server load.

- In React (especially with frameworks like Next.js 13/14+ using React Server Components), `cache()` is a special utility function used to memoize asynchronous functions on the server. `cache()` remembers the result of a function call based on its inputs (arguments). It prevents unnecessary re-fetching or recomputation on the server side. If you call the same cached function with the same arguments during the same server request lifecycle, React will return the cached result instead of re-running the function. You may use this for your "auth()" logic of nextAuth, for example: `export const { auth: uncachedAuth, handlers, signIn, signOut } = NextAuth({ ... }); ... export const auth = cache(uncachedAuth);`

- When you add types in a frontend application or somewhere else which refers to types of some other API, you normally only want the parts of the respective type you actually need to not leak too much information. Instead of having all properties for a customer type, for example, you might only need the `id`, `name`, and `email` properties. Thus, you can create a new type that only contains these properties. This way, you ensure that your frontend code only has access to the necessary information without exposing sensitive or unnecessary data.

- When working with Keycloak service accounts, you can check the clientId and preferred_username to have the "service-account-..." structure. This way you then know if the account is a service account or not. Service accounts are used for server-to-server communication, allowing applications to authenticate without user interaction. They are typically used in scenarios where an application needs to access resources on behalf of itself rather than on behalf of a user.

- A bucket is a common storage concept used by many object storage systems, such as AWS S3, MinIO, Google Cloud Storage, and others. It serves as a top-level container for storing data objects like files, images, videos, and documents. Buckets typically have a flat structure without directories in the traditional sense, but you can simulate folder-like organization using prefixes in object names (e.g., images/photo.jpg). To make objects like PDFs and images publicly accessible, you usually configure access policies at the bucket or object level. Most object storage systems provide policy-based access controls, allowing you to define who can read, write, or manage objects. Public access typically means enabling anonymous read permissions, so anyone with the URL can access the file. In systems like MinIO, this is handled through bucket policies or Access Control Lists (ACLs).

- Your public IP address is the address assigned to you by your Internet Service Provider (ISP) and is visible to websites and services on the internet; you can find it by searching “what is my IP” online. This address is how your entire network (like your home or office) appears to the outside world and is typically shared by all devices on the same network through a router. In contrast, your local IP address is used within your private network and is assigned by your router (often via DHCP) to identify each device individually; you can view it using the ipconfig command on Windows. Local IPs usually follow standard private ranges like 192.168.x.x, 10.x.x.x, or 172.16.x.x, and they allow devices to communicate internally while your router manages internet access through Network Address Translation (NAT). Public IPs can be static or dynamic, while local IPs often change when devices reconnect to the network.

- Bash is a shell (command-line interpreter). Bash runs on Linux, but many commands come from Linux system utilities, not Bash itself.

- Windows is an operating system built on the Windows NT kernel, and unlike Linux, it's developed and controlled entirely by Microsoft as a single, unified product. Linux, by contrast, is just a kernel, and various organizations build complete operating systems around it, called distributions (like Ubuntu or Fedora). There are alternatives to Windows, including Linux distributions, macOS (on Apple hardware), ChromeOS, and open-source systems like FreeBSD or ReactOS. Some tools like Wine or Proton let you run Windows applications on Linux. While Windows doesn't have "distributions" like Linux, it does come in editions (Home, Pro, etc.), which are more like variants than separate systems.

- When working with custom API routes in Next.js, don't just throw an error, instead use NextResponse to return a proper response. For example, if you want to return a 404 error, use `return NextResponse.json({ message: 'User not found', error: 'Not Found' }, { status: 404 })`. This way, the client can handle the response correctly and understand that the requested resource was not found. Thus, make use of try/catch and always return such NextResponse objects in your API routes to ensure proper error handling and response formatting.

- When working with server actions in Next.js, you can't return a NextResponse object directly since they only return data (or throw errors) instead of returning HTTP responses. Thus, for API routes use `NextResponse` for both success and error cases and for server actions throw errors for error cases and otherwise return the data you want to return. Server actions are designed to be used in the context of React components, allowing you to perform server-side logic and return data directly to the component without needing to handle HTTP responses explicitly.

- WASM stands for WebAssembly. It’s a binary instruction format designed to run code on the web (and elsewhere) with near-native performance. WASM lets you run code written in languages like C, C++, Rust, Go, etc. inside your browser (or other environments) — just like JavaScript — but faster and often more efficiently.
  - High performance: Runs at near-native speed by taking advantage of low-level bytecode execution.
  - Safe: Runs in a sandboxed environment (like JavaScript), with strict memory access rules.
  - Portable: Can run on any platform that supports WASM (not just in browsers — it's used in server-side apps too).
  - Language-agnostic: You write your code in a compiled language like Rust or C++, then compile it to .wasm.
You might use WASM if:
  - You're using a library or tool that was originally written in C/C++/Rust (like a PDF engine, graphics renderer, or math library).
  - You're doing something CPU-intensive and want a performance boost over JavaScript.
  - You're using frameworks that compile to WASM (e.g., Blazor for C#, Pyodide for Python, or Yew for Rust).
WebAssembly is not a replacement for Node.js or JavaScript — it’s more like a companion / performance booster for specific modules and requires a host (like a browser or Node.js). It’s a way to run compiled code (from C, C+, Rust, etc.) in:
  - The browser (client-side),
  - Or environments like Node.js (server-side).
Thus:
  - Node.js is a JavaScript runtime — it executes your JavaScript code, manages I/O (files, network), runs servers, etc.
  - WASM is a portable low-level format (kind of like bytecode) that runs inside a host environment — like a browser or Node.js.

- When getting some information about approving build after running a `pnpm install`, use `pnpm approve-builds` to approve the build. This is useful when you have a CI/CD pipeline that requires manual approval before proceeding with the deployment or further steps. It allows you to review and confirm the changes made by the installation process, ensuring that everything is as expected before moving forward.

- When working with Next.js or other similar frameworks where you can use a middleware, you may want to use path matchers to only apply the middleware to specific paths. This is done by defining a `matcher` property in the middleware's config which you have to export in the middleware file (in Next.js at least). For example, if you want to apply the middleware only to paths starting with `/api`, you can set `matcher: ['/api/:path*']`. This way, the middleware will only run for requests that match this pattern, allowing you to optimize performance and avoid unnecessary processing for other routes. A more common use case in a real world application would be some regex like this: `'/((?!api|_next/static|_next/image|favicon.ico).*)'`. This will match all paths except those starting with `/api`, `_next/static`, `_next/image`, and `favicon.ico`. This is useful for applying middleware to all routes except for API routes and static assets, which often don't require the same processing. If you work with authentication and have like custom login or logout routes, for example, this could be interesting as well - When working with next auth, for example, you might want to avoid processing logins to avoid infinite rerenders in some cases.

- If you're managing a single Keycloak access token in a simple Next.js app, using a shared file with plain variables and a function is perfectly fine and very straightforward. It works well because modules in Node.js are singletons by default, so the token state is preserved across imports. If your logic grows or you want more structure, a static class method offers a cleaner way to organize related code without needing to instantiate anything. For even more flexibility and better encapsulation, a singleton class instance gives you full control, similar to how services work in NestJS. However, it's a bit more setup and only really necessary if your auth needs become more complex. For most single-token use cases, the shared file or static class approach is ideal. Static fields are shared across all instances and even accessible without any instance at all.

- When you redeploy a Next.js app using Docker, the server-side cache and the .next build folder are reset, so any static pages or server-rendered content are regenerated. However, browser caches may still serve old assets unless filenames have changed or cache-control headers instruct revalidation. Next.js typically uses hashed filenames for static assets, which helps bypass stale browser caches. If you're using a CDN or reverse proxy like NGINX or Cloudflare, those layers may continue to serve cached content unless you explicitly purge or configure short cache lifetimes. To ensure users always get the latest version, it's important to manage cache headers correctly and consider automatic cache invalidation on redeploy.

- Using nodemailer, you are able to send an email in the name of some other email, as long as they are from the same domain and the email server configuration allows it. You may also adjust the replyTo option. In the end, you might use the email address `abc@test.com` but make it look like the email is from `xyz@test.com` and if you try to answer to that email you would also send an email to `xyz@test.com` instead of `abc@test.com`.
- `curl` uses low-level C networking libraries to send requests directly.
- `fetch` uses the Fetch API, built on modern browser internals, not XMLHttpRequest (this was for old browsers). In Node it's built on top of the low-level http/https modules.
- `axios` wraps XMLHttpRequest in browsers. On the server axios builds requests directly using Node's native http and https modules, just like node-fetch or built-in fetch in Node ≥ 18.

- `globalThis` refers to `window` in the browser and to `global` in Node.js. It provides a way to access the global scope in both environments without worrying about which one you're in. It's a standard way to refer to the global object across different JavaScript environments, ensuring compatibility and consistency.

- `navigator` is a built-in browser object that gives info about the user's browser and device (like browser name, version, OS, used language etc.). It’s only available in browsers because it’s part of the Web API — a set of tools browsers provide to interact with the web environment. It doesn’t exist in Node.js or server-side code.

- Additional built-in Web APIs (besides `navigator` (see above)):
  - `window` — controls the browser window, alerts, timers, etc.
  - `document` — lets you access and manipulate the webpage (DOM).
  - `fetch` — makes network requests (like AJAX) easily.
  - `localStorage / sessionStorage` — store data in the browser persistently or per session.
  - `Geolocation` — get the user’s location (with permission).
  - `Clipboard` — read/write from the clipboard.
  - `WebSocket` — real-time two-way communication.
  - `Notification` — show desktop/browser notifications.
  - `History` — manage browser history and URL without reloads.

- Sockets let two computers talk to each other directly over the internet or a network. They open a connection so data can flow back and forth. A WebSocket is a special type of socket used in web browsers that keeps a connection open between your browser and a server, allowing them to send messages instantly to each other without having to ask repeatedly.
  So basically:
  - Socket: A connection for two-way communication.
  - WebSocket: A socket made for real-time chatting between browser and server.

- Enums (short for "enumerations") are a way to define a set of named, constant values. They make code clearer and less error-prone, enforce a fixed set of allowed values, and help with type safety and auto-completion. They are used often for things like status codes, categories, or options where you want to limit the possible values to a predefined set.

- Why Not Use Auto-Sync in Production? Here’s why you use migrations in production instead of auto-sync (which you use in development):
  1. Unpredictable Changes - Auto-sync doesn’t know your intent. If you rename a column or field:
    - It might drop the old one and create a new one (💥 data loss).
    - It may not map it properly (e.g., changing string to number).
    - You need precise control over how changes are made.
  2. Data Loss Risk - Auto-sync might:
    - Drop columns or tables that it thinks are no longer used.
    - Fail silently or destructively on conflicts.
    - Not preserve existing data formats.
  3. No Audit Trail - With migrations:
    - You know exactly what schema changes occurred and when.
    - You can inspect the migration history.
    - You can roll back if needed.
    - Auto-sync is opaque — there’s no record of what changed unless you dig into the DB.
  4. Production Safety - Migrations let you:
    - Review and test schema changes before applying them.
    - Coordinate schema updates with code releases.
    - Run changes in a transactional and safe way.
    - Auto-sync can’t coordinate with CI/CD, pre-deployment tests, or rollback strategies.
  5. Versioning and Deployment Control - In production:
    - Multiple servers or instances may be running.
    - Schema changes must be done in a controlled way to avoid race conditions or downtime.
    - Teams need to synchronize changes via migrations, not by just pushing new code.

- In Payload CMS, the `payload run` command is a utility that sets up the Payload environment and executes scripts within the context of your application. It ensures that Payload's configuration, database connection, and other dependencies are properly initialized before running your script. Directly using `ts-node` might encounter errors if you didn't set up your `tsconfig.json` properly for this or if the environment isn't properly configured for Payload. The `payload run` command handles these configurations automatically, making it the preferred way to execute scripts that interact with Payload's features and APIs.

- When using custom scripts (for database seeding, for example), you may want to use `ts-node` or a more environment-specific approach (like `payload run` for Payload CMS applications). However, you could also compile the file yourself and then run it with `node`. You should also be able to run `.ts` files directly with `node` in a newer version of node (not sure about this). For compiling and then executing, you may use a command like this: `tsc ./src/scripts/db_seed_script.ts --outDir dist && node dist/scripts/db_seed_script.js`. However, for like Next.js or similar applications this approach might not be the best, since this command would use a `dist` directory which you don't have in those environments.

- `cross-env` is a utility that allows you to set environment variables in a way that works across different operating systems (e.g., Windows, macOS, Linux). This is particularly useful because setting environment variables differs between platforms. The command `cross-env NODE_OPTIONS=--no-deprecation` sets the `NODE_OPTIONS` environment variable to `--no-deprecation` before running the script. This tells Node.js to suppress deprecation warnings during execution, ensuring a cleaner output without warnings about deprecated features. You can put this before your package.json script commands (see how Payload CMS does it in their package.json).


- When you want to run some scripts in your project, install `ts-node` as dev dependency and add a command in your `package.json` to run the script. devDependencies are not installed in production, so you can use it for scripts that are only needed during development.
  - Example: `ts-node ./scripts/my-script.ts`
  - Add to package.json: `"scripts": { "my-script": "ts-node ./scripts/my-script.ts" }`
  - Run it with: `pnpm run my-script`

- When you run a file with `ts-node`, for example, all imports are resolved relative to the file being executed. Thus, you automatically have access to all required imports from other files and don't have to manually transpile those files as well.

- When you need access to environment variables, use the `dotenv` package (`dotenv.config()`). In Next.js environments, the environment variables are automatically loaded from `.env.local`, `.env.development`, and `.env.production` files, so you don't need to manually load them with `dotenv` (for server files, for client files you can use the `NEXT_PUBLIC_` prefix to expose them to the client side).

- Use a Relationship when:	
  - The related item is shared across many records
  - You update the related item independently
  - You want to enforce referential integrity
  - You're working with large or paginated related data
  - `post.author` -> Relationship (authors exist independently and are reused)
  - `post.tags` -> Could be either:
    - Relationship: if you reuse tags across many posts
    - Embedded: if tags are just strings or not managed separately

- Use a Join Field when:
  - The data is unique to this record
  - The data rarely changes or is tightly coupled
  - You prioritize read performance over normalization
  - You need everything loaded together in one document
  - `post.comments` -> Join Field/Embedded, unless comments are separate documents (e.g., for moderation, reuse, or scalability)

- When using Payload CMS you may encounter situations where you want to populate specific relationships in a collection (for example, if you use defaultPopulate false for some relationships by default). With like `populate[books][author]=true` (for REST API) you can reach out to like a customer entity that has a `books` property and inside that property you have `author` and you want to populate this specific field. Have in mind that it's not important how deep the relations are, you still only target the relation fields (books and author) and not anything in between.

- A request response can't be consumed multiple times. If you use `response.json()`, for example, you can't just return the original response later on.
  - If you want to use the response multiple times, you have to clone it first. Use [`response.clone()`](https://developer.mozilla.org/en-US/docs/Web/API/Response/clone) to create a copy of the response object. This allows you to consume the cloned response without affecting the original one.
  - Example:
    ```javascript
    const response = await fetch(url);
    const clonedResponse = response.clone();
    const data1 = await response.json(); // Consumes the original response
    const data2 = await clonedResponse.json(); // Consumes the cloned response
    ```

- When working with Payload CMS, have in mind that the transaction ID is not automatically set for custom endpoints. You have to create it yourself and pass the request object to all requests which should be combined in the same transaction. Within the corresponding hooks you will automatically have access to the transaction ID that will be the same as the transaction ID from the provided request object. If no request object was provided, it will generate a transaction ID for you.

- Axios uses `XMLHttpRequest (XHR)` under the hood and not the Fetch API. This means it has built-in support for older browsers that don't support Fetch, and it also provides some additional features like request cancellation and progress tracking that are not available in the Fetch API. If you have any trouble with the Fetch API, you can use Axios instead to avoid the Fetch API altogether.

- If you want to test something inside a node environment, use the `node` command in terminal and hit enter. Afterwards, you may use node/JavaScript.

- If using dynamic styles, you should use the style property for elements instead of className. Use it like `maxWidth: ${width}px` instead of having a tailwind className like `max-w-[${width}]`. 

- In software and ORMs, "dirty" is a common term meaning changed but not yet saved (from the concept of a "dirty write"). It's used in concepts like "dirty checking", where the system tracks which entities or properties are "dirty".

- A checksum is a small piece of data (usually a number or hash) calculated from a larger block of data (like a file, record, or row in a database). When you later want to verify the data hasn't changed, you recalculate the checksum and compare it to the original. If they differ, the data has been altered.

- `.gitlab-ci.yml` is a file used in GitLab to define the CI/CD pipeline for a project. It contains stages, jobs, and scripts that specify how the code should be built, tested, and deployed. The file is written in YAML format and has to be placed at the root of the repository. When changes are pushed to the repository, GitLab automatically triggers the pipeline defined in this file.

- `auto-deploy-values.yaml` might be placed in a `.gitlab` directory and is used to define values for automatic deployments in GitLab CI/CD. It allows you to specify environment variables, deployment configurations, and other settings that will be used during the deployment process. This file is particularly useful for managing different environments (like staging and production) and ensuring consistent deployment configurations across different branches or tags.

- Base64 is a way to encode binary data (like images, files, or buffers) into a string format using only printable ASCII characters (letters, numbers, +, /, and = for padding). This makes it: Safe to transmit in text-based formats (like JSON, HTML, or URLs) and easy to embed in things like data URIs or HTTP payloads. You might use it because many systems (like HTTP, email, or JSON) can only safely transmit text, Base64 is used to represent binary data as readable text. Image in email? Base64. File upload preview in JavaScript? Base64. Embedding images in CSS? Base64. Base64 increases size by ~33% compared to the original binary data. Why? Because you're representing 3 bytes (24 bits) using 4 characters (4 * 6 = 24 bits), but each ASCII character uses 8 bits, not 6 → inefficiency.
  - How Does Base64 Work?
    - It converts 3 bytes of binary data (24 bits) into 4 groups of 6 bits, then maps each 6-bit group to a printable character using a lookup table of 64 characters.
    For example:
    - Binary input: 01000001 01000010 01000011 (which is "ABC")
    - Break into 6-bit chunks: 010000 010100 001001 000011
    - Map to Base64: "Q" "U" "J" "D" → "QUJD"

- 192.168.x.x is a special reserved range of IP addresses used for private networks. These IPs are not routable on the public internet, and they're mainly used for local communication inside home or office networks. The range 192.168.0.0 to 192.168.255.255 is defined by RFC 1918 as private IP address space. Devices like routers, computers, smart TVs, and phones use these IPs when they're behind a router or firewall. Routers typically assign these IPs dynamically via DHCP (Dynamic Host Configuration Protocol). If you want to reach a device inside that network from the internet, you’d need port forwarding or a VPN. When a device with a private IP (like 192.168.1.42) accesses the internet, the router uses NAT (Network Address Translation) to map the private IP to its public IP address and it replies from the internet go to the router, and it routes them back to the correct device.
  - Common Real-Life Usage:
    - Home router IP: Often 192.168.0.1 or 192.168.1.1
    - Devices: Laptops, smart TVs, phones might be 192.168.0.10, 192.168.1.100, etc.
    - Subnet: Most routers use 192.168.1.0/24, giving you 254 usable IPs in that network.

- ODBC (Open Database Connectivity) is a standard that lets applications like Power BI talk to databases using a local driver installed on the same machine. It works by translating SQL queries into the database's native protocol and returning results in a standardized format.

- gRPC (Google Remote Procedure Call) is a fast, modern protocol that lets programs call functions on remote servers as if they were local, using Protocol Buffers for efficient data exchange over HTTP/2. It’s often used for high-performance communication between microservices or systems like Dremio.

- OpenSSL is a widely-used open-source cryptographic library that provides tools and implementations for:
  - Secure communication (like HTTPS using SSL/TLS)
  - Encryption and decryption
  - Digital signatures and certificates
  - Cryptographic hashing
  - Random number generation
  -> It's the engine behind much of the world's secure internet traffic. The `crypto` package from Node.js uses OpenSSL under the hood.
  - OpenSSL offers:
    - TLS/SSL protocols: For securing internet connections (e.g., HTTPS).
    - Command-line tools: For generating certificates, keys, etc.
    - Crypto algorithms: Hash functions (SHA, MD5), symmetric ciphers (AES, DES), asymmetric ciphers (RSA, ECC), etc.

- Why Can You Create the Same Hash from the Same Input, but Not Reverse It?
  - If you hash the same input, you'll get the same hash – but you cannot go backwards from the hash to the original input.
  That's because cryptographic hash functions are designed to be:
    - Deterministic: Same input → same output.
    - One-way: You cannot reverse the hash to get the original input.
    - Collision-resistant: It’s (very) hard to find two different inputs that produce the same hash.
  This is intentional, especially for sensitive uses like password hashing or data integrity.

- So-called arbitrary variants can be used in Tailwind CSS to have more style control. This can specifically be helpful in situations where you have to overwrite some styles from an external API (like @fullcalendar that uses custom classes you don't have full access to from the class name props and don't want to rely on an external css file to do  that). With the arbitrary variants you can use class name structures like `[&_.some-class-below]:text-white` in parent element to style all descendant elements with the corresponding custom class:
  - [] —> Tailwind's arbitrary variants syntax, used when you want to apply styles under custom selectors.
  - & —> Represents the current element Tailwind is generating styles for.
  - _ —> Represents a space in the final CSS selector (because spaces aren’t allowed inside [] directly).
  - .some-class-below —> A descendant class.
  - This would be like `& .some-class-below { color: white; }` in CSS
  - This only works with Tailwind 3+.

- With [parallel Routes in Next.js](https://nextjs.org/docs/app/building-your-application/routing/parallel-routes) you can have multiple directories and pages within a slot directory like `@modal`. All pages within that directory will be rendered at the same slot location.

- The btoa package (`pnpm add btoa`) in TypeScript (or JavaScript more generally) provides a way to encode a string in base64 format. It mimics the behavior of the browser-native btoa() function, which is not available in Node.js environments by default.
  - In browsers btoa(str) encodes a binary string into a base64-encoded ASCII string. It’s commonly used for encoding credentials or binary data for safe transmission over text-based protocols. In Node.js `btoa` is not available out of the box.


- The otplib package (pnpm add otplib) is a Node.js and browser-compatible library for implementing Two-Factor (2FA) and Multi-Factor Authentication (MFA) using both Time-based (TOTP) and HMAC-based (HOTP) One-Time Passwords, adhering to RFC 6238 and RFC 4226 standards. It is compatible with popular authenticator apps like Google Authenticator and Authy.

- MIME stands for Multipurpose Internet Mail Extensions. It's a standard that defines how to format and send different types of data over the internet, especially in emails and HTTP (like web pages). MIME tells a client (like a browser or email reader) what type of data it's receiving and how to handle it.
  - Common MIME types:
    | Type | MIME Type                | Description     |
    | ---- | ------------------------ | --------------- |
    | HTML | `text/html`              | Web page        |
    | CSS  | `text/css`               | Stylesheet      |
    | JS   | `application/javascript` | JavaScript file |
    | JSON | `application/json`       | JSON data       |
    | JPEG | `image/jpeg`             | Image file      |
    | PDF  | `application/pdf`        | PDF document    |

- In JavaScript/TypeScript, a constructor is a special method used to initialize an object when a class is instantiated. The `super` keyword is used to call the constructor of the parent class. `constructor` sets up the new object. `super(...)` is required in a subclass constructor to call the parent’s constructor before using this. In a subclass constructor, you must call super() first before accessing this, which includes using any properties or methods from the parent class.

- Virtual machines emulate entire operating systems, making them heavier and slower to start, but with stronger isolation. Docker containers share the host OS kernel, making them lightweight, fast, and ideal for running multiple apps efficiently on the same system. For docker container you need an image and volume (to have changes persist). The virtual machine basically acts as a separate computer with its own OS, so changes/installations automatically persist there.

- DNS is like the phonebook of the internet. It translates human-readable domain names (e.g., example.com) into IP addresses (e.g., 93.184.216.34) that computers use to find each other. You type google.com → DNS finds the IP → Your browser connects to that IP. It involves records like A, CNAME, MX, etc.

- SSL (Secure Sockets Layer) is a cryptographic protocol that was designed to: 
  - Encrypt data between a client and a server (e.g., browser and website)
  - Ensure privacy, integrity, and authenticity
  - SSL is old, it's vulnerable, and not used anymore (replaced by TLS)

- TLS (Transport Layer Security) is the modern cryptographic protocol that:
  - Encrypts data between two systems (e.g., browser ↔️ website)
  - Protects data from eavesdropping, tampering, or forgery
  - Is the successor to SSL (more secure and efficient) and the current standard

- Digital certificates (SSL/TLS) are used to secure web traffic (HTTPS). They:
  - Prove a website is authentic (issued by a trusted Certificate Authority like Let's Encrypt).
  - Enable encryption between your browser and the server using TLS.
  - Example: When you visit https://example.com, the site presents a certificate to prove it's really example.com, and then encrypts the connection.
  - 🔴 Without any certificate at all:
    - HTTPS won’t work at all.
    - The TLS handshake cannot even begin.
    - The server has nothing to present for encryption or identity.
    - The client (e.g., browser) will just refuse to connect over HTTPS.
  - 🟡 With a self-signed certificate:
    - HTTPS will work (the data is still encrypted).
    - BUT: Browsers will show a security warning like: `“Your connection is not private” NET::ERR_CERT_AUTHORITY_INVALID`
    - Users must manually bypass the warning (which is not recommended for public-facing sites).
  - 🟢 With a certificate signed by a trusted CA:
    - HTTPS works properly.
    - Browsers show the padlock icon and no warning.
    - The identity of your server is verified.
    - Ideal for all public sites.

- _SSL Certificate_: An SSL certificate is a digital certificate issued by a trusted Certificate Authority (CA). It contains the public key part of a key pair as well as identification information about the owner of the certificate (such as the domain name). When a web browser connects to a secure site, the site presents its SSL certificate for the browser's inspection. The SSL certificate serves two main purposes: 1. It provides the public key necessary to initiate a secure session. 2. It verifies that the server is the legitimate owner of the website and that the certificate is issued by a trusted authority, thus creating trust with the client.

- _SSL CA Bundle_: An SSL CA Bundle is a file that contains one or more root and intermediate certificates. The bundle helps client software (like web browsers) verify the chain of trust between the website's SSL certificate and the root certificate of the CA that issued it. When a web server presents its SSL certificate to a client, the client might not directly trust the certificate. The client will attempt to verify the certificate's authenticity by following the chain of certificates from the presented certificate up to a trusted root certificate. The CA bundle contains intermediate certificates that bridge the trust between the website's SSL certificate and a root certificate pre-installed in the client's certificate store.

- Typescript `Exclude<Type, ExcludedUnion>` removes union members from a union type: `type T = Exclude<"a" | "b" | "c", "a">;  // "b" | "c"`
- Typescript `Omit<Type, Keys>` removes keys from an object type.: `type T = Omit<{ a: number; b: string }, "a">;  // { b: string }`

- A JWT (JSON Web Token) is composed of three Base64-encoded parts, separated by periods (.): `<Header>.<Payload>.<Signature>`. By using `token.split(".").length === 3` you can check, whether the token is malformed or not. However, this does not guarantee that the token is valid or unexpired, that the signature is correct etc.

- When a browser makes an HTTP request (like when you visit a webpage), it automatically includes several default headers. These headers help the server understand the context of the request — who’s making it, from where, under what conditions, etc.
  - `User-Agent`: Identifies the browser and operating system.
    - e.g `User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/123.0.0.0 Safari/537.36`
    - Used for: Analytics, Adaptive content (e.g., mobile vs desktop), and Bot detection
  - `Accept`: Specifies the types of content the client can process (like HTML, JSON, etc.).
    - e.g. `Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8`
    - Used for: Content negotiation between client and server
  - `Accept-Language`: Indicates the preferred language for the response.
    - e.g. `Accept-Language: en-US,en;q=0.9`
    - Used for: Localizing website content
  - `Accept-Encoding`: Lists the content encodings (like gzip) that the client can handle.
    - e.g. `Accept-Encoding: gzip, deflate, br`
    - Used for: Helps reduce data size over the network.
  - `Connection`: Controls whether to keep the connection open after the request (like "keep-alive").
    - e.g. `Connection: keep-alive`
    - Used for: Performance (e.g., avoid reconnecting for each request)
  - `Host`: Specifies the domain name of the server (useful for virtual hosting).
    - e.g. `Host: example.com`
    - Used for: Routing requests to the correct server when multiple domains are hosted on the same IP address.
  - `Origin`: Indicates the scheme + hostname + port of the request’s origin.
    - e.g. `Origin: https://example.com`
    - Used for: CORS (Cross-Origin Resource Sharing) checks, and CSRF protection
    - Unlike `Referer`, this does not include the full path — only origin.
  - `Referer`: Indicates the URL of the page that linked to the resource being requested.
    - e.g `Referer: https://example.com/page1`
    - Used for: Analytics (e.g., where traffic is coming from), Security (e.g., validating same-origin requests), and Can be controlled/obscured with Referrer-Policy
  - `Referer-Policy`: Controls how much referrer information is passed along with requests.
    - e.g. `Referrer-Policy: no-referrer`
    - Used for: Privacy and security
  - `Cookie`: Sends stored cookies to the server
    - e.g. `Cookie: sessionid=abc123; theme=dark`
    - Used for: Sessions, authentication, preferences

- Ubuntu is one of the most popular Linux distributions (or "distros") designed with ease of use, stability, and wide hardware compatibility in mind. It’s based on Debian, another major Linux distribution, and it’s particularly well-suited for beginners due to its: Graphical installer, User-friendly desktop environments (like GNOME), Large software repositories, and Strong community support. Ubuntu also comes in variants like Ubuntu Server (for headless server environments), and flavors like Kubuntu, Xubuntu, and Ubuntu MATE, which offer different desktop environments. Common Alternatives to Ubuntu are:
  - Debian – Ubuntu's parent, known for its rock-solid stability. Great for servers, but with less cutting-edge software.
  - Fedora – Sponsored by Red Hat. More cutting-edge than Ubuntu, great for developers.
  - Arch Linux – A minimal and rolling-release distro focused on user control and customization (more on this below).
  - Manjaro – Based on Arch, but user-friendlier. Ideal if you want Arch’s power without all the complexity.
  - Linux Mint – Based on Ubuntu. Known for ease of use and a traditional desktop experience.
  - openSUSE – Offers both stable (Leap) and rolling (Tumbleweed) versions; good for power users.
  - Pop!_OS – Made by System76, based on Ubuntu. Popular with creators and gamers for its hardware support and tiling window manager.

- Arch Linux is a lightweight, flexible, and minimalist Linux distribution aimed at experienced users. It follows the KISS principle ("Keep It Simple, Stupid") and provides a rolling release model, meaning updates are continuous and there are no major version jumps. Key features:
  - You build your system from the ground up (minimal install, then add what you need).
  - Uses the Pacman package manager.
  - Extensive and up-to-date Arch User Repository (AUR).
  - A famous Arch Wiki that’s one of the best Linux documentation sources.
  - Not beginner-friendly: requires command line use and manual configuration.

- *eslint*: The standard ESLint CLI tool. Every time it runs, it loads the config, parses the code, and analyzes it. This makes it slower, especially on large projects or with frequent use (like during formatting or linting on save).
- *eslint_d*: A daemonized version of ESLint. It runs a background process that keeps ESLint preloaded between runs. This results in significantly faster performance for repeated linting operations. Think of eslint_d as a performance optimization layer on top of eslint.
- *prettier*: The standard CLI for Prettier. Like ESLint, it loads everything from scratch each time you run it.
- *prettier_d*: A daemon for Prettier. It runs a background process to cache configuration and reduce startup overhead, making it much faster for repeated formatting.

- A daemon (pronounced DEE-muhn) is a background process that runs continuously, without being directly tied to a user’s terminal session. When a tool is daemonized, it means, it starts once and stays running in the background; it waits for commands (like formatting a file or linting code); it reuses cached data (like your config files or project structure), which avoids reloading everything every time; it typically responds much faster than a normal command-line tool that starts from scratch each time.

- A .dll file stands for Dynamic Link Library. It’s a type of file in Windows that contains code, data, and resources (like images or functions) that multiple programs can use at the same time. Instead of each program copying that code into itself, they all "link" to the .dll file, saving memory and storage space. Think of a .dll like a shared toolbox: instead of every worker needing their own set of tools, they all pull the tools they need from one shared set.

  - Programs can call functions from a .dll when they need them.
  - This makes programs smaller and more efficient.
  - It also makes it easier to update or fix bugs — you can just update the .dll instead of every program individually.
  - However, if a .dll file is missing or corrupted, programs relying on it may not work properly.

- If you block specific IPs via nginx, you would get `403` errors as the caller using such a blocked IP.

- In `C:\Windows\System32\drivers\etc` you can find a `hosts` file. This file is used to map hostnames (DNS names) to IP addresses manually, before any request is made to a DNS server. It's one of the first places your OS checks when resolving a domain name. It allows you to: Override DNS resolution (e.g., redirect a domain to a different IP); Block domains (e.g., set a domain to 127.0.0.1 or 0.0.0.0 to effectively null-route it); Set custom domain names for local development (e.g., map myapp.local to 127.0.0.1). You can list multiple hostnames (aliases) for the same IP on the same line. IPv6 entries are allowed too (e.g., ::1 localhost).

- Types don't exist during runtime.

- The `middleware.ts` in Next.js (or in other frameworks as well) runs on the server.

- An "upsert" would be something like `INSERT INTO ... ON CONFLICT ... DO UPDATE ...` in SQL.

- If you need to make some API call on initial render of a web page and it's not about fetching/getting data (where you would use useQuery) and have access to running code on the server (via server components in Next.js, for example), you should run this logic directly in the server component. If you have like a `/unsubscribe` route for a newsletter unsubscribe feature, the user shouldn't have to wait for rendering/hydration to make the call, instead the post/patch/put/etc. request should happen on the server and then you just display a corresponding result or make a redirect to some other route if you want to show the result on there. The code in your server component will run only once. In a client component you would have to add some checks to avoid calling the same api call multiple times due to component re-renders and you also don't have to wait for hydration with a server component.

- React Client Component Lifecycle (on hydration): 1. Render phase — React renders the component (e.g., evaluates useState, useSearchParams, etc.) | 2. Commit phase — React compares the virtual DOM to the existing server-rendered DOM and updates only if needed | 3. Effect phase — useLayoutEffect runs synchronously before paint; useEffect runs after paint | This entire process is hydration for that component. Hydration attaches interactivity to already-rendered HTML.

- With `any` you may do everything without any error risk from the compiler since you neglect any type safety. With `unknown` you have type safety since you have to explicitly tell what type the underlying value actually has before you may use it. This can be used, if you have like data from any source where the type can't be known but you may know for specific situations where you use the values - in those situations you can explicitly tell what type it is. With `never` you can declare that something will never have a return value (like a function that only throws an exception). `never` will also come into play for unreachable code / exhaustive checks.

- You don't add setters in dependency arrays in React, even though eslint might ask you to do so. This can lead to infinite rerenders in some situation and would just break the application. Ignore the warnings in such situations.

- With next-intl you can set up a provider, getLocale, getMessages in the main layout, while having a specific folder structure (`/src/i18n/messages/...`) where the messages are automatically received from. In client components you can use `useTranslations()`

- To allow specific IP ranges, you can set this up via a proxy (nginx, with like `allow xxx.xxx.x.x/24; ... deny all`), or directly in an API.

- Polymorphic relationships in Payload CMS: "You cannot query on any field values within the related document. Since we are referencing multiple collections, the field you are querying on may not exist and break the query." (from the official docs)

- When updating an existing database with documents with updated tables, check what fields you edit in detail. Let's say you add a new field that is required (like a id to reference to some other table's data) and don't add a default value, this field would disturb the current still existing data in the database since it still has the old data structure. In such a case, the migration would fail since the old data would have null values for the required field. To fix this, you may create multiple migrations: The first one with a default value for the added required field and the second one with the default value removed again, for example. Or, you could delete all the affected data (which might not work in already productively running environments).

- APT (Advanced Package Tool)

  - Used in: Debian-based Linux distributions (e.g., Ubuntu, Debian, Linux Mint). a
  - Purpose: Manages software packages, allowing users to install, update, and remove software easily.
  - Common Commands:
    - apt update – Updates package lists.
    - apt upgrade – Installs available updates.
    - apt install <package> – Installs a package.
    - apt remove <package> – Removes a package.
  - File Format: .deb (Debian package format).

- `~` represents the home directory.

- In Linux systems, `/usr` (Unix System Resources) is a system directory that contains user-related system files like binaries, libraries, documentation, and shared resources:

  - `/usr/bin/` –> Contains essential user programs (e.g., ls, grep, vim).
  - `/usr/sbin/` –> Contains system administration commands (e.g., iptables, fdisk).
  - `/usr/lib/` –> Stores shared libraries required by applications.
  - `/usr/local/bin/` -> Could be used for for a `entrypoint.sh` file (commonly used in Docker containers or system startup scripts)
    - in Dockerfile:
      ```Dockerfile
      COPY entrypoint.sh /usr/local/bin/
      # add execute permission to the file (-x would remove the execute permission) -> this adds the permission for owner, group, and others
      # could be restricted with like u+x (execute permission only for the owner), ug+x (execute permission for owner and group)
      RUN chmod +x /usr/local/bin/entrypoint.sh
      ENTRYPOINT ["/usr/local/bin/entrypoint.sh"]
      ```

- In Linux systems, the `/etc` directory is used to store system-wide configuration files:

  - Configuration files for system services (`/etc/ssh/sshd_config` for SSH).
  - User account information (`/etc/passwd`, `/etc/shadow`).
  - System initialization scripts (`/etc/init.d/` or `/etc/systemd/`).
  - Application configuration files (e.g., `/etc/nginx/nginx.conf` for the Nginx web server).
  - If you need to implement a system-wide crontab (cron table) you could do so in `/etc/crontab` (System-wide cron jobs are also stored in /etc/cron.d/ as individual files)
    - Scripts placed in these directories will run at the specified intervals automatically (no separate cron schedule needed (like `* * * * * root /path/to/script.sh`), just place the scripts directly in here; to find out at what time they run, look at the system-wide crontab file in `/etc/`):
      - /etc/cron.hourly/
      - /etc/cron.daily/
      - /etc/cron.weekly/
      - /etc/cron.monthly/

- In Linux systems, you may encounter file permission strings like `-rw-r-x---`:

  - First character (`-`): Indicates the file type.
    - `-` = Regular file
    - `d` = Directory
    - `l` = Symbolic link
    - `c` = Character device (hardware-related)
    - `b` = Block device (disk-related)
  - Next 9 characters (`rw-r-x---`): Represent file permissions in three groups of three:
    - `rw-` (Owner): The file owner can read (r) and write (w), but not execute (-).
    - `r-x` (Group): Users in the file’s group can read (r) and execute (x), but not write (-).
    - `---` (Others): Other users have no permissions.

- Generally speaking, you don't really need test databases. Especially, if you just work with Unit Tests, it's more recommended to mock any database action (just create a variable where you store the created results in and pass that variable to other tests which need to read from the "database" data). Such procedure can be used for testing access control in Payload projects, for example, that has some logic intensity and should be automatically tested to avoid a lot of manual testing later on - however, you don't need to check if the underlying actions actually were able to reach out to a working database or not; just test the access control itself in such situations.
- useQuery in Tanstack React Query is the standard way to fetch data; it needs explicit handling of loading (isLoading) and error (isError) states.
- useSuspenseQuery in Tanstack React Query is a suspense-enabled version of useQuery; loading and error states are handled by React Suspense and Error Boundaries.
- `./**/*.entity.js`: This is a glob pattern. The `**` part means "any directory" (recursively, zero or more subdirectories), and `*.entity.js` means "any file that ends with `.entity.js`". So, this pattern will match all files ending with `.entity.js` in any subdirectory of the current directory.
- (Based on Payload CMS): The `relationship` type for a field defines a relational connection between tables and can use database schema changes (e.g. foreign keys - thus, this will actually edit the table you apply this relationship field to (like adding a company ID the document in the table is associated to). The `join` type for a field executes a runtime query to fetch related data from another table based on matching IDs (without modifying the schema). Based on the prior example, you would use this field type on the company table that is associated with other documents of the other table.
- With [nuqs](https://www.npmjs.com/package/nuqs) you can state manage search params for React frameworks. It's basically like `useState` but directly connected with the url query string. With using `useQueryState` like you would use `useState` the current state is also written to the url query string. This is e.g. helpful when working with tables (like tanstack table) where your table state should rely on the url query string (to have it efficiently persist on reloads when fetching with the url query string from your backend, for example). In such cases you might want to read the url query string, parse it to have it properly configured for the table state and when the table state changes, parse the changes which are put in the url query string in a way your backend can handle them.
- In Tailwind CSS you can select all child div elements of the element the class is applied on with `sm:[&>div]:text-red-500`, for example. This is just an example to show that you have access to such `&>` etc. operators with tailwind.
- X-Forwarded-Host (XFH) is an HTTP header that proxies set to indicate the original Host requested by the client. It’s useful for handling reverse proxies (ensure the app sees the correct original domain), load balancers, and multi-tenant applications (route requests based on subdomains).
- When using Windows environment variables, you can use `$env:ENV_NAME` in PowerShell to resolve them. For `npm`, `node`, and other programs they are automatically resolved (for example in the `.npmrc` file or in your npm/pnpm config).
- Normally, throwing an exception (e.g., `throw new Error("Something went wrong")`) would crash the application if not caught.
  - But Nest.js, Payload and other libraries/frameworks automatically catch exceptions and convert them into structured HTTP responses instead of crashing the server. This behavior is very similar to returning `Err(...)` in Rust, where errors are handled explicitly instead of throwing exceptions.
- A tar file is a tape archive file, commonly used in Unix-like systems to combine multiple files and directories into a single archive file. The .tar extension indicates it’s an uncompressed archive. A .tgz file is a tar archive that has been compressed using gzip. It's essentially a .tar.gz file, where the .tar portion represents the archive format the .gz portion indicates that the archive has been compressed with gzip.
- Custom headers should follow the X- naming convention (e.g., `X-API-KEY`, `X-Custom-Header`).
  - this way you could still use the reserved headers in combination with your custom headers (like for using Authorization with a bearer token and also allow the `X-API-KEY` to be set for further authorization methods)
- Cookies are stored inside the `Set-Cookie` (if server sets cookie) and `Cookie` (if set via Javascript `document.cookie`) header.
- If I make a request from the client/frontend, does it take all the browser cookies automatically? Yes, if you make a request from the browser, cookies are automatically included — but only same-origin cookies (cookies tied to your site's domain). If you fetch a different domain (like an external API), cookies won't be automatically included unless you explicitly set credentials: "include" in your fetch(). In a server action or in other server-side logic, you have no automatic cookie context. You need to manually read the cookies in the server environment (using cookies() from next/headers for example).
- In the client, when using Next.js, you might want to use [cookies-next](https://www.npmjs.com/package/cookies-next) for easier handling the parsing that has to be done. The library is both for server and client-side usage, so you can use it in both places. It provides a simple API to get, set, and delete cookies without worrying about the underlying implementation details.
- In Next.js, it's not recommended to use server actions for GET requests/fetches. Instead, use custom Next.js endpoints for this. Those endpoints are public by default. If you have no session for authentication but only like API Keys in the endpoint itself, be aware that these endpoints might be called from other people directly (rate limits etc. recommended).
- From within the WSL you have access to all the data you have on your drives.
  - WSL mounts your Windows drives under the /mnt/ directory, e.g. -> /mnt/c/...
  - In there you have links/mount points to the actual drives of your windows PC
  - Therefore, you could technically access all the data via those links
  - However, it's generally a better idea to install necessary software (linke some compiler etc.) directly in the WSL if you need those for software within the WSL
    - When you install something in the WSL: WSL 2 uses a virtualized Linux file system inside a virtual disk. The data is stored in a .vhdx file located at: `C:\Users\<YourUsername>\AppData\Local\Packages\<DistroName>\LocalState\ext4.vhdx`
- The PATH environment variable is a single string that contains multiple directory paths, separated by semicolons (;) on Windows.
  - running `$env:PATH` could output something like this: `C:\Windows\system32;C:\Windows;C:\Program Files\Git\bin;C:\Users\YourUser\AppData\Local\Microsoft\WindowsApps`
  - Since it's just a string, you could split it to reach each item in it: `$pathArray = $env:PATH -split ";"` and then `$pathArray[0]  # First directory`
  - If you need variables that actually just store one value (like ohmyposh uses with `$env:POSH_THEMES_PATH`), you can create whole new environment variables in Windows
- grep (Global Regular Expression Print) is a command-line tool used in Unix and Linux systems for searching text using patterns. It allows you to find specific lines in files that match a given pattern.
  - Supports regular expressions for pattern matching.
  - Can search recursively through directories using (-r) - example: `grep -r "TODO" .  # Searches for "TODO" in all files in the current directory`
  - Supports case-insensitive searches (-i) - example: `grep -i "warning" logfile.txt  # Case-insensitive search`
  - Can display line numbers (-n)
  - Allows inverted matching (-v) to find lines that do not match a pattern - example: `grep -v "success" logfile.txt  # Shows lines that do NOT contain "success"`
- Ripgrep (rg) is a modern alternative to grep that is much faster and more user-friendly. It is designed for speed and efficiency, making it ideal for searching large codebases.

  - `rg "error"  # Searches for "error" in all files recursively`
  - `rg -i "warning"  # Case-insensitive search`
  - `rg --no-ignore "TODO"  # Searches all files, including ignored ones`
  - `rg -t python "import"  # Searches only Python files`
  - `rg "def .+\(" --multiline  # Searches for function definitions across multiple lines`

- Concurrency means executing multiple tasks independently but not necessarily at the same time. It helps efficiently manage multiple operations without waiting for one to finish before starting another. Rust with Actix Web is quite strong in terms of concurrency, for example.

- For the neovim setup you'll probably need this structure or similar (on Windows):

```
C:\Program Files\Neovim\share\nvim
├── init.lua
├── lua\
│   ├── plugins\
│   |   ├── dsp.lua
│   |   ├── lsp.lua
│   |   ├── git.lua
│   |   ├── rust.lua
│   |   ├── general.lua
│   ├── config\
│   |   ├── autocmds.lua
│   |   ├── keymaps.lua
│   |   ├── lazy.lua
│   |   ├── options.lua
```

- When you have Windows environment variables defined, you could use them in your project with `process.env.VARIABLE_NAME` or in other files which are able to resolve environment variables (like in a `.npmrc` file).

- When you store environment variables in GitLab CI/CD, they are not stored in your project files directly. Instead, GitLab keeps them securely in its CI/CD settings, and they are injected into the runner's environment at runtime.

  - GitLab encrypts and stores the environment variables in its settings.
  - These variables are only accessible during pipeline execution (when running jobs).
  - They are not committed to the repository or stored in the project files.
  - When a job runs in a GitLab pipeline, the defined environment variables are passed to the container or script execution context.
  - This ensures secrets (e.g., API keys, database passwords) are not stored in the repository but are available when needed.
  - You can set variables as protected, meaning they are only available in protected branches or tags.
  - You can also restrict access based on environment scopes (e.g., only available for staging or production).

- `CI_JOB_TOKEN` is used for internal authorization in the same GitLab instance (for GitLab pipelines).

- `CI_PROJECT_ID` includes the project's/repository's id (for GitLab pipelines).

- You can add a `.npmrc` file in a project which will be used for npm specifiy commands inside that project's directory and can be utilized for authorization when installing a private registry's package, for example.

- The `LF` End of Line Sequence is `\n` while `CRLF` is `\r\n`. `LF` is expected by Linux systems (if `LF` is not used on a Linux-based system, this might create trouble).

- By default, containers are part of the bridge network unless specified otherwise. Therefore, multiple containers can communicate with each other, by default. To make this work with other networks you have to make sure that the respective containers are on the same custom network. Then, you may use their Internal IP or their container names to let them communicate with each other (for example an API container reaching out to a database container on the same network).

- `process.env` can basically be used in any kind of application (that includes `process`) since it reaches out to the `.env` file in the application where it's ultimately used. Using this in a library that will always be included in another project instead of being standalone will work as soon as you include the respective environment variables needed for the library in your application where you use this library.

- If you have an import in a file that has the same name as an argument of a function in that same file, the argument of the function takes precedence within the function's scope.

- If you declare some variable in a file in the most outer scope of that file (not inside any function or similar), and using that variable in the functions of that file, it will cache the variable's value if you use this file from any place inside your application (it won't re-declare and re-initialize such variables).

- If you have a React component that includes some functionality you would like to have access to in the component's child components, you may use React Context to create the context, pass down the respective values with the context provider wrapper in that component, and export a hook from that component that reaches out to that context - use that hook in any child component of that original component - (create context, context provider as wrapper, hook to read values from contenxt)

- Files within the public folder for Nest.js or Next.js, for example, can be accessed with the corresponding path, like `api_url/images/my_image.png` -> thus, one use case can be, that you could save the correspinding paths and use them in your frontend application, for example, to fetch/access them with the proper paths of the backend api where the images are saved.

- The "home directory" `~` is the current user's directory.

- When adding a new personal access token for GitLab, a re-login is required. Use `git push` within a repository to open the login mask and enter the new credentials there.

- When working with migrations, it's helpful to have a seperate database which can be deleted or altered in any way to test out the new migrations. This way, the actual development database's data remains untouched.

- _Buffer (in JavaScript specifically)_: A Buffer is a global class in Node.js (since it’s part of its core API) that provides a way to work with raw binary data directly. It is essentially an array of bytes and is fixed in size. They allow you to handle binary data efficiently, which is crucial when dealing with things like file I/O, network protocols, or binary encoding formats.

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

- CORS (Cross-Origin Resource Sharing) is a security feature implemented in web browsers to restrict how resources on a web page can be requested from another domain. When a script on a web page tries to request resources from a different domain, CORS policy comes into play. This is done to prevent malicious websites from making requests on behalf of a user without their consent, a security issue known as Cross-Site Request Forgery (CSRF). For example, if your JavaScript code running on https://domain-a.com tries to fetch data from https://domain-b.com/data.json, it would be considered a cross-origin request. By default, browsers block such requests unless the server at https://domain-b.com explicitly permits it by sending the right CORS headers. To add CORS headers, you would typically modify your server's response headers to include headers like Access-Control-Allow-Origin, that specifies which domains are allowed to make requests to your server. See the code example "Handle URL Rewrites in middleware (Next.js) - Solving potential CORS Errors" for an approach to handle corresponding problems within Next.js (if you want to make requests from the browser, not from the server via server components/server actions). CORS configuration does not fully secure your API, it only acts for requests made from web browsers. In fact, CORS is not designed to protect your API at all, it's about protecting users and their browsers. Otherwise, there might be a website where in the background an API call to some sensitive API is done (to your banking API or whatever (just an example)). If not CORS would exist, this request just could get through. With CORS in place, the API would deny access since it doesn't recognize the domain this request comes from (potentially a malicious website). Therefore, with Postman, curl or via server-side functions (server actions/server components in Next.js - those don't run in the browser but in the server) etc. you can just get through since there is no users's browser that has to be protected by CORS. To actually protect your API, you have to use API Keys or other authorization and security measures. A lot of APIs might allow all origins (they basically don't care about the origin) but require an API Key (for example, an API you pay for to get an API Key). This way, it basically secures the user's browser as well as the API from invalid fetches/calls since if you have no API Key, the request won't get through.

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


- _Bit_ & _Byte_: 8 Bits equal 1 Byte (50 Mbit/s equals 6.25 Megabyte/s).

- _Volumes_: In the context of software and systems engineering, a "volume" generally refers to a designated storage area that is used to hold data. This concept is integral to various computing environments, including operating systems, virtualization platforms, and containerization technologies. The purpose and functionality of a volume can vary widely depending on the context, but the core idea revolves around data management and persistence. Volumes are designed to persist data beyond the lifecycle of the process or instance using them. This means that the data stored in a volume remains available even after the process ends or the instance is terminated. Volumes can provide a way to isolate data for specific applications or services, ensuring that the data is accessible only to those components that need it, which enhances security and organization. In many systems, volumes can be shared among multiple processes or instances, allowing for efficient data exchange and collaboration without the need for data duplication. Volumes can offer a way to easily move data between different environments or systems. By detaching a volume from one instance and attaching it to another, the data becomes instantly available to the new instance. The underlying physical storage of volumes can vary, ranging from local disk storage on a single machine to distributed file systems across a network or cloud-based storage solutions. This flexibility allows volumes to be tailored to specific storage needs and performance requirements.

- _Performance API_: The Performance API, part of the Web Performance APIs suite, provides a way to measure the performance of web applications by giving access to performance-related information in the browser. It's a standardized API available in modern web browsers that allows developers to collect detailed performance metrics in a fine-grained and precise manner. The Performance API is particularly useful for understanding the real-world performance of web applications, diagnosing slow performance, and identifying bottlenecks.

- _dependencies and devDependencies_: `dependencies` are packages required by your application at runtime and build time for development and production. This includes libraries that your application imports and uses when it's running, like React (react), Redux (redux or @reduxjs/toolkit), UI libraries, utility libraries, and any other code that is part of the production bundle that gets executed in the user's browser or on the server in the case of SSR (Server-Side Rendering) applications like Next.js. `devDependencies` are packages that are only needed during the development's runtime and the build process (for development and production). Thus, they are not available during production runtime. This includes compilers/transpilers (like Babel, TypeScript), build tools (Webpack, Rollup), CSS preprocessors (Sass, Less), testing libraries (Jest, Mocha), linters (ESLint, Prettier), and other tools that help in the development of the application but are not needed for the application to run in production. For example, you wouldn't need your testing framework or linter in your production environment. Both `dependencies` and `devDependencies` can be involved in the build process. However, only the output (usually a set of static files, JS bundles, CSS, etc.) of this process is used in production.

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

- _Fiddler_: You have access to all requests that go through the target system (own system but also smartphone for example via a proxy). This way you can, for example, find endpoints online games and/or websites are using for their actions when the client requests data from the respective server. In order to follow this procedure for apps, a proxy can be established on the smartphone which basically forwards the requests in a proper form to the Fiddler client application on the computer. In theory, it would be also possible to use android emulators, for example, but setting this up seemed to be quite a hassle. Therefore, if possible, it's strongly recommended to just use the respective app on a smartphone device and follow the "remote devices" instruction on Fiddler to set up the connection which works perfectly fine.

### KeyCloak

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

### Understanding SSL (Secure Sockets Layer)

SSL, or Secure Sockets Layer, is a standard security technology for establishing an encrypted link between a server and a client—typically a web server (website) and a browser, or a mail server and a mail client (e.g., Outlook).

SSL allows sensitive information such as login credentials, credit card numbers, or personal details to be transmitted securely. Normally, data sent between browsers and web servers is sent in plain text, which can leave you vulnerable to eavesdropping. If an attacker is able to intercept all data being sent between a browser and a web server, they can see and use that information.

- How SSL Works
  _SSL Handshake_: Initially, when a client connects to an SSL-secured server, they perform an "SSL handshake". During this handshake, the client and server establish which encryption algorithm they will use, and the server provides its SSL certificate as proof of identity.

_Encryption of Data_: Once the handshake is complete, the data transmitted between the server and the client is encrypted according to the agreed-upon encryption algorithm. This means that even if the data is intercepted, it would be unreadable without the encryption key.

_Data Integrity_: In addition to encryption, SSL also ensures that the data sent is unchanged and authentic through a message authentication code (MAC).

### Blob Storage

Blob storage, short for Binary Large Object storage, is a solution for storing large amounts of unstructured binary data, such as images, audio, video, or documents. It's commonly used in cloud storage services like AWS S3, Azure Blob Storage, or Google Cloud Storage. Here's how it works and how you use it in conjunction with a database:

1. Storing Data: Blob storage is designed to store large binary files. It's optimized for storing massive amounts of unstructured data, providing high availability, reliability, and scalability.

2. Access: You typically interact with blob storage through APIs provided by the cloud service. These APIs allow you to upload, download, and manage your blobs (files).

#### Keeping References in the Database

1. Upload to Blob Storage: Instead of storing the actual image file in your database, you upload the image to a blob storage service. After uploading, you receive a unique URL or identifier for the stored image.

2. Store Reference in Database: You then store this URL or identifier in your database, not the image itself. This reference is used to access the image when needed.

3. Retrieval: When you need the image, you use the stored reference to fetch it directly from the blob storage. Your application or users can access the image via the URL or through an API call that retrieves the blob data using its identifier.

#### Advantages

1. Efficiency: Storing large files in a database can be inefficient and costly. Blob storage is a more cost-effective and performance-optimized solution.
2. Scalability: Blob storage services are built to handle large amounts of data and traffic, making them ideal for scalable applications.
3. Separation of Concerns: This approach keeps your database lean and focused on structured data, while blob storage handles the unstructured data.
4. Security and Management: Cloud-based blob storage services offer robust security, backup, and data management features.

#### Example Scenario

Let's say you have a web application where users can upload profile pictures. Instead of storing these images directly in your SQL database:

1. The images are uploaded to an AWS S3 bucket (blob storage).
2. Each image gets a unique URL or key.
3. In your user table in the database, you store this URL or key in a column, say profile_picture_url.
4. When you need to display a user's profile picture, your application fetches the image using the URL from the S3 bucket.

In summary, blob storage is used for efficient, scalable storage of large binary files, while your database holds references to these files, offering a more optimized and manageable data storage architecture.

### CRON

CRON is a time-based job scheduling system commonly used in Unix-like operating systems. It enables users to schedule scripts, commands, or software applications to run at specified times, dates, or intervals. Here's a brief overview:

- Cronjobs: These are the scheduled tasks that you want to run automatically at specified intervals. Each task is defined in a line of a "crontab" (cron table) file.

- Crontab: This is the configuration file where cronjobs are specified. Each line in a crontab file represents a separate job and consists of a CRON expression (indicating when the job should be executed) and the command to execute.

- CRON Expression: A CRON expression is a string of fields separated by spaces, representing a set of times for when a job should be executed. The fields typically represent minute, hour, day of the month, month, day of the week, and optionally year.

- Usage: CRON is widely used for automating system maintenance tasks, backups, monitoring scripts, and other recurring tasks that need to be run at regular intervals.

By setting up cronjobs, you can automate repetitive tasks and maintain your system efficiently without manual intervention.

### Darkmode in Tailwind CSS

If the parent element has the "dark" class, all child elements can make use of "dark:..." to apply styles for this state of darkmode.
Normally, you may use a cookie for the theme or some similar name. In the layout (speaking of Next.js), you then can apply this cookie on the html class name with "dark" or "light", for example. This will enable the darkmode Tailwind CSS feature in your application.

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

### How Are Passwords Saved

Passwords aren't saved directly in databases due to security risks. Instead, they are transformed into a form that's difficult to reverse-engineer using a process called hashing. Let me break down the common process:

- Hashing the Password:
  When a user sets or changes their password, it’s hashed using a cryptographic hash function (e.g., bcrypt, Argon2, or PBKDF2). Hashing turns the password into a fixed-length string of characters that doesn’t reveal the original password and can’t be reversed to reveal it.

- Adding a Salt:
  To make each hash unique, a random value called a salt is added to the password before hashing. This prevents attackers from using precomputed "rainbow tables" to guess passwords, as the same password will produce different hashes with different salts.

- Storing Only the Hash and Salt:
  Only the hash and salt are stored in the database. When a user logs in, the application hashes the entered password with the stored salt and compares it to the saved hash to check if they match.

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

## Packages

- [react-use - collection of utils](https://www.npmjs.com/package/react-use)
- [animejs - lightweight JavaScript animation library](https://www.npmjs.com/package/animejs)
- [gsap-quicktools - my animation quicktools package](https://www.npmjs.com/package/gsap-quicktools)
- [react-hammerjs - mobile device touch event support](https://www.npmjs.com/package/react-hammerjs)
- [sharp - converting images for better efficiency](https://www.npmjs.com/package/sharp)
- [react-intersection-observer - monitor the visibility of different sections on a webpage and dynamically execute actions](https://www.npmjs.com/package/react-intersection-observer)

## Potential Fixes

- If you work with docker and have a Dockerfile that can use both npm and pnpm, make sure to have only one lockfile (for npm OR pnpm). If you have a mix (npm lockfile but installed with pnpm etc.), this will break most likely.

- If you work with icons or images and they seem to act weird (don't react to all style changes and/or are really big and so on), then you might want to delete the `.next` folder (when working with Next.js), restart the application, or maybe just open the application in an incognito window. This is a common issue with Next.js and its caching mechanism, which can sometimes lead to unexpected behavior with static assets.

- When getting some weird error that you cannot do some in the server that comes from the client, you may work with some sort of server action which you call from the client-side while passing in some data that can't be created in client-side and then passed to server-side. An example for this is a class instance that was created in the client-side (like a createDTO), if you pass that to the server-side, you will get such error in a server action (server actions are features of Next.js).

- When having type problems with Formik, make sure to pass a generic type argument to the `Formik` component like this: `<Formik<ValuesInterface> ... >`.

- If you use [`cva`](https://www.npmjs.com/package/class-variance-authority) with Tailwind CSS, and you encounter weird style issues, you might want to add a space character before the applied cva class names. This is a work around for such situations.

- If you have issues with TypeScript when using `[number]` for a type inside an array, consider using `NonNullable` for that type.

- When working with Next.js you may encounter issues with caching or static page generation. For example, if you want to resolve an environment variable in a page (server component), make sure it's dynamic and not static since for static pages, the environment variables are resolved at build time, not at runtime. If you need to access environment variables in a server component, make use of the `dynamic` export to force a dynamic page generation (https://nextjs.org/docs/app/api-reference/file-conventions/route-segment-config#dynamic). Using `revalidate` would not help in this case, since it is only used for revalidating static pages after a certain time. You won't have your env resolved directly at start.

- If the `pnpm-workspace.yaml` file is present in a repository, make sure you use pnpm version 10.8.0 or higher. If you are using an older version of pnpm, you may encounter issues.

- When you try to import like an enum that was defined in a backend (like in a Payload CMS collection) into a frontend file, you might get an error like "Module not found: Can't resolve '...'". This is because the enum is not available in the frontend context. To fix this, you can create a separate file that exports the enum and import it in both the backend and frontend files. This way, you ensure that the enum is accessible in both contexts. For the Payload CMS example this is the reason: Payload CMS collection files (like `src/collections/Users.ts`) are server-side Node.js code, and they implicitly or explicitly depend on Node modules, including fs. Even if you only export an enum, the entire file gets processed during the frontend build when you try to import from it — so your frontend build tries to bundle server-only code, hits fs, and fails because fs doesn't exist in the browser.

- When working in Payload CMS with a postgres database with a collection that has a relationship to another document of the same collection as itself, remember to make use of `depth=0` when creating such a collection's document (this is also how the admin panel does it). Otherwise, you will get a database error due to wrong type since the relationship will be resolved at some point instead of being an integer (the id) which is not working for the database. This situation might occur when you are not creating the document via the admin panel but directly via the Payload API.

- When having a type error like "TypeError: Converting circular structure to JSON", it could be that you are trying to stringify an object that contains a circular reference. This can happen when an object references itself directly or indirectly. To fix this, you can use a library like `flatted` or `circular-json` to handle circular references when stringifying the object. You can also use `inspect()` which comes out of the box from node.js.

- If you are using Payload CMS and have relationships and joins where collections are referencing each other again, make use of defaultPopulate to deactivate the defaultPopulate of respective fields to avoid circular references. This fix helps for errors like "id is ambigious" when querying with the id that is available multiple times due to the circular references.

- If you have trouble with migrations where it's trying to change types of fields which are connected with some constraint, you may have to manually drop the related constraints (`ALTER TABLE ... DROP CONSTRAINT IF EXISTS ...`), change the types afterwards (`ALTER TABLE ... ALTER COLUMN ... SET DATA TYPE ...`) and then add the constraints again manually in the migration file (`ALTER TABLE ... ADD CONSTRAINT ... FOREIGN KEY ... REFERENCES ... ON DELETE CASCADE`). This might happen with an early version of drizzle (ORM for typescript/javascript applications). This orm is used with the payload cms, for example. Have in mind, that this might break the downwards compatibility with the corresponding migration file if you manually adjust it (might be worth to delete all migrations and basically fully reset at that point).

- If you have trouble with some packages installed by pnpm within the node_modules, try `pnpm install --shamefully-hoist`. Normally, pnpm keeps dependencies in a content-addressable store and uses symlinks to ensure module isolation. The `--shamefully-hoist` flag forces pnpm to behave more like npm or yarn by hoisting dependencies into the root node_modules, making them more accessible (which can help with some legacy packages that expect dependencies to be in a flat node_modules structure). If you encounter dependency resolution issues where packages cannot find required dependencies, this command might help.

- Next.js executes top-level code at build time. This means, if you have logic which accesses env variables etc. in top-level code, it could not resolve them correctly since they may not be present at build-time. The code within the (server) components is only executed at runtime where you will have access to such env variables.

- If you have trouble with pnpm not automatically running install-scripts, [check this out](https://github.com/pnpm/pnpm/releases/tag/v10.0.0) (since major version 10).

- When working with a `.npmrc` file, you have to make sure, it fully resolves when you build a package that relies on that file (for private libraries, for example). As soon as one value can't be resolved (like a specific environment variable), a 404 could appear pointing to a different line in the file (not the line that did cause the error). Similar errors could appear if all values were resolved successfully but just are the wrong ones (like an API token with insufficient permissions for installing a private library).

- If having trouble with pages which lack CSS, try to import the main globals css file for the respective layout again + the fortawesome config and the corresponding styles if that is used

- If trouble with GPG secrets/keys arises, try to delete the `.password-store` (with the docker-credentials-helper) and/or the whole `.docker` folder to reset the settings, then use `pass init GPG_FINGERPRINT` to initialize the process with the GPG secret.

- Git Error based on wrong user and password: `Windows-Anmeldeinformationen verwalten` -> In here, the proper user has to be configured for the corresponding git platform, so that the user operating in Git is the same user mentioned in the `Windows-Anmeldeinformationen`.

- To make a keycloak client work, a role has to be configured (like a "user" role).

- When using Next.js the error.tsx client component only works for server-side errors. If you want to get to this separate client component from a client component, you have to set up a state (errorState, for example) set it to true whenever the error might occur (in the catch block of an asynchronous action, for example) and check for true of this errorState to then throw an error which will lead you to the designated error.tsx client component.

- Fetch requests might fail with 400 (Bad Request) or 500 statuses which are valid HTTP responses (4xx and 5xx error status codes). However, these are not catched by the catch block which are for network errors, for example, (if the browser is unable to make the request at all). To catch those 4xx and 5xx error status codes you have to check with `response.ok` in the try block and throw an error manually to get to the corresponding catch block.

- For old browsers there might be a error in terms of "globalThis is not defined". To polyfill this issue you might use `<script src="https://polyfill.io/v3/polyfill.min.js?features=globalThis"></script>` or `<script dangerouslySetInnerHTML={{ __html: 'window.globalThis = window', }} type="text/javascript" />` or also `<script src="https://unpkg.com/@ungap/global-this@0.4.4/min.js" noModule async></script>` ([First & Second approach](https://github.com/vercel/next.js/pull/45592)[Third approach](https://github.com/vercel/next.js/discussions/49771))

- If animations are implemented which make use of `x` or `y` or similar movements, some sort of flickering might appear, affecting fonts and elements in general while the respective animation takes place. With the help of `backface-visibility: hidden` and `transform: translateZ(0)` this bug can be fixed. However, this fix might cause a small decline in quality for the fonts/texts - [source](https://discourse.webflow.com/t/a-fix-for-when-your-elements-move-up-and-or-blur-during-animations-interactions-on-chrome/11629)

- Add a focus on a label to focus the input element within that label.

- If you can't properly import a database export, check the collation/s of the import query (for example, change `utf8mb4_0900_ai_ci` to `utf8mb4_general_ci` to make it work in this specific case)


- If Tailwind CSS classes are not properly working, check if the file they are used in, is included in the bundle path of the tailwind config file

- When having trouble with migrations which won't get created, for example, removing the snapshot might help.

- When dealing with circular dependency errors in Nest.js, remember to make use of `forwardRef()` in the respective modules to import the circular dependency modules. Also make use of `@Inject(forwardRef() => Some_Module)` within the respective service files if those also have circular dependency.

- When trying to link a local library to another project, try `npm link` and `npm link project_name` if `pnpm` won't work.

- When trying to import the `package.json` try to set `esModuleInterop` and `resolveJsonModule` both to `true` in your `tsconfig.json`

## Code Examples

### How WASM and Node.js can work together

You can use Node.js to:
  - Run your main server app (e.g., in JavaScript/TypeScript),
  - And load a WASM module to do something fast (like encryption, image resizing, parsing a PDF, etc.).

```ts
const fs = require('fs');
const wasmCode = fs.readFileSync('./my_module.wasm');
const wasmModule = await WebAssembly.instantiate(wasmCode);
```

### Generic React component

```ts
type MyComponentProps<T> = {
  items: T[];
};

function MyComponent<T>({ items }: MyComponentProps<T>) {
  return <div>{items.length} items</div>;
}

...

<MyComponent<string> items={['a', 'b', 'c']} />
```

### Displaying PDF base64 strings

- Make sure the Base64 string does not include a prefix like data:application/pdf;base64, — if your API only gives you the raw Base64 string, you need to manually add that prefix before using it.
- If your PDF is large, using a Blob is better than a data: URL to avoid memory issues.

_View the PDF (in a new tab or <iframe>) without blob_

```ts
// Example Base64 PDF string from your API (without the data: prefix)
const base64PDF = "JVBERi0xLjQKJc..."; // Just the raw base64 string

// Create a data URL for the PDF
const dataUrl = `data:application/pdf;base64,${base64PDF}`;

// Open it in a new tab
window.open(dataUrl, '_blank');
```

_Or show it inside your page using an <iframe> without blob_

```ts
<iframe src="data:application/pdf;base64,JVBERi0xLjQKJc..." width="100%" height="600px"></iframe>
```

_View PDF (open in new tab) using Blob_

```ts
function base64ToBlob(base64, mime = 'application/pdf') {
  const binary = atob(base64);
  const bytes = Uint8Array.from(binary, char => char.charCodeAt(0));
  return new Blob([bytes], { type: mime });
}

function openPDFInNewTab(base64PDF) {
  const blob = base64ToBlob(base64PDF);
  const url = URL.createObjectURL(blob);
  window.open(url, '_blank');

  // Optional: revoke the object URL after a delay to free memory
  setTimeout(() => URL.revokeObjectURL(url), 10000);
}

...

// Use case
openPDFInNewTab(yourBase64PDFString);
```

_Embed PDF in page with Blob URL (for <iframe>)_

```ts
function embedPDF(base64PDF, iframeElement) {
  const blob = base64ToBlob(base64PDF);
  const url = URL.createObjectURL(blob);
  iframeElement.src = url;

  // Remember to revoke URL when iframe is removed or page unloads
  window.addEventListener('unload', () => URL.revokeObjectURL(url));
}

// Use case
const iframe = document.querySelector('#pdf-frame');
embedPDF(yourBase64PDFString, iframe);
```

_Download PDF (on button click) using Blob_

```ts
function downloadPDF(base64PDF, filename = 'file.pdf') {
  const blob = base64ToBlob(base64PDF);
  const url = URL.createObjectURL(blob);

  const a = document.createElement('a');
  a.href = url;
  a.download = filename;
  document.body.appendChild(a);
  a.click();
  document.body.removeChild(a);

  URL.revokeObjectURL(url);
}

// Use case
downloadPDF(yourBase64PDFString, 'my-document.pdf');
```

_Full helper function base64ToBlob_

```ts
function base64ToBlob(base64, mime = 'application/pdf') {
  const binary = atob(base64);
  const bytes = Uint8Array.from(binary, char => char.charCodeAt(0));
  return new Blob([bytes], { type: mime });
}
```

_React hook example for downloading a PDF Blob_

```ts
import { useCallback } from 'react';

export function useDownloadPDF() {
  const downloadPDF = useCallback((base64PDF, filename = 'file.pdf') => {

    // This would be the base64ToBlob helper function from above
    const binary = atob(base64PDF);
    const bytes = Uint8Array.from(binary, c => c.charCodeAt(0));
    const blob = new Blob([bytes], { type: 'application/pdf' });

    // URL.createObjectURL(blob) creates a temporary, unique URL that points to the Blob data inside your browser's memory. This URL can be used as a source (for example, in an <iframe>, <img>, or <a> tag) to access the Blob content.
    const url = URL.createObjectURL(blob);

    const a = document.createElement('a');
    a.href = url;
    a.download = filename;
    document.body.appendChild(a);
    a.click();
    document.body.removeChild(a);

    // URL.revokeObjectURL(url) tells the browser to release and clean up the memory and resources associated with that URL, making it no longer valid or accessible.
    // If you don’t call revokeObjectURL after you’re done with the Blob URL, the browser keeps the Blob data in memory, which can cause memory leaks, especially if you create many URLs over time.
    URL.revokeObjectURL(url);
  }, []);

  return downloadPDF;
}
```


### Buffer (in JavaScript for Node.js)

Buffer is a Node.js class for handling raw binary data. You use it to easily encode and decode Base64.
If you need similar logic within a website's browser, you can't use Buffers since these are a Node.js feature. You can use `atob` / `bota` for such cases.

_Encode to Base64_
```ts
const buf = Buffer.from('Hello world');     // Create buffer from string
const base64 = buf.toString('base64');      // Encode to base64
console.log(base64); // Outputs: SGVsbG8gd29ybGQ=
```

_Decode from Base64_
```ts
const decoded = Buffer.from(base64, 'base64').toString(); // Back to string
console.log(decoded); // Outputs: Hello world
```

_For binary files_
```ts
const fs = require('fs');

// Read image into buffer
const imageBuffer = fs.readFileSync('image.png');

// Convert to base64 string (e.g., for embedding)
const base64Image = imageBuffer.toString('base64');

// Later, you can restore the binary
const originalBuffer = Buffer.from(base64Image, 'base64');
fs.writeFileSync('copy.png', originalBuffer);
```

### btoa & atob (in Javascript for Browsers)

- btoa() - Binary to ASCII → encodes a string to Base64	- “binary to aSCII”
- atob() - ASCII to Binary → decodes a Base64 string back	- “aSCII to binary”

```ts
// Encode string to Base64
const encoded = btoa('Hello world');
console.log(encoded); // "SGVsbG8gd29ybGQ="

// Decode Base64 back to string
const decoded = atob(encoded);
console.log(decoded); // "Hello world"
```

❌ Only work with ASCII/Latin1 strings — if you pass Unicode or emoji, they may break or give incorrect results.
❌ Not available in Node.js — these are browser-only functions.

If you need to handle full Unicode (e.g., emoji, non-English characters), wrap your input/output with encodeURIComponent and decodeURIComponent:

```ts
// Encode Unicode string safely
const safeBase64 = btoa(encodeURIComponent('✓ é 🚀'));

// Decode safely
const decoded = decodeURIComponent(atob(safeBase64));

console.log(decoded); // ✓ é 🚀
```

Or use the more modern Web APIs (in newer environments): 

```ts
// Encode safely using Web APIs (e.g. in browsers or Deno)
const base64 = btoa(new TextEncoder().encode('✓ é 🚀'));
```


### Crypto package

Node.js comes with a built-in module called crypto, which works seamlessly in TypeScript too. You use it to do things like hashing, HMACs, encryption, and generating random values.

```ts
// Creating a Hash

import { createHash } from 'crypto';

const data = 'Hello world';
const hash = createHash('sha256').update(data).digest('hex');

console.log(hash); // e.g., "64ec88ca00b268e5..."
```

- `createHash('sha256')`: Choose the hashing algorithm (e.g., sha256, md5, sha512).
- `.update(data)`: Provide the input data.
- `.digest('hex')`: Output the hash as a hexadecimal string.

If you hash the same input again, you’ll get the same result:

```ts
const sameHash = createHash('sha256').update('Hello world').digest('hex');
console.log(sameHash === hash); // true
```

*Why Can’t You Reverse the Hash?*
Hash functions produce a fixed-size output (e.g., 256 bits for SHA-256) from inputs that can be any size. This means:
  - Many different inputs could theoretically map to the same hash (though good hash functions make this very rare).
  - There is no practical way to know what input produced a given hash without guessing (brute-forcing).
  - The hashing process discards information, so reversing it is mathematically infeasible.


Besides hashing, `crypto` offers:
  - randomBytes: for generating secure random data
  - createHmac: for creating keyed-hash messages (HMAC)
  - pbkdf2: for secure password-based key derivation
  - createCipheriv / createDecipheriv: for encryption/decryption

It’s a secure and well-maintained module, using OpenSSL behind the scenes.


### Using authenticator package

```ts
import { authenticator } from 'otplib';

// Generate a 32-character (160-bit) base32 key
const formattedKey = authenticator.generateSecret();
console.log('Key:', formattedKey);

// Generate a 6-digit time-based token
const formattedToken = authenticator.generate(formattedKey);
console.log('Token:', formattedToken);

// Verify the token
const verification = authenticator.check(formattedToken, formattedKey);
console.log('Verification:', verification);

// Manually generate an otpauth URI
const uri = `otpauth://totp/ACME%20Co:john.doe@example.com?secret=${formattedKey}&issuer=ACME%20Co&algorithm=SHA1&digits=6&period=30`;
console.log('otpauth URI:', uri);

```

To facilitate user setup in authenticator apps, you can generate a QR code from the otpauth:// URI. This can be done using libraries like qrcode in Node.js or qrcode.js in the browser


### Using btoa package

*Encode string to base64*

```ts
import btoa from 'btoa';

const encoded = btoa('Hello world');
console.log(encoded); // Outputs: SGVsbG8gd29ybGQ=
```

*Decode from base64 to original string*

```ts
import atob from 'atob';

const decoded = atob('SGVsbG8gd29ybGQ=');
console.log(decoded); // Outputs: Hello world
```

Or directly decode with using `Buffer`:

```ts
const decoded = Buffer.from('SGVsbG8gd29ybGQ=', 'base64').toString('utf-8');
console.log(decoded); // Hello world
```


### Add certificate to nginx web server

You can buy certificates or get them free by Let's Encrypt, for example.
You can use `Certbot` to automate the whole process for your server.

If you're using a web server (like Nginx or Apache) you'll typically need:
- A certificate file (.crt)
- A private key file (.key)
- Possibly an intermediate bundle

```nginx
server {
    listen 443 ssl;
    server_name yourdomain.com;

    ssl_certificate     /etc/ssl/certs/yourdomain.crt;
    ssl_certificate_key /etc/ssl/private/yourdomain.key;
}
```

If you're using a platform (like Netlify, Vercel, Heroku):
  - These platforms often auto-manage HTTPS for you using Let's Encrypt.
  - You usually just add your custom domain, and HTTPS is enabled automatically.


### clsxm (clsx + tailwind merge)

This is also a good help when trying to overwrite already existing classes.

```ts
import clsx, { ClassValue } from "clsx";
import { twMerge } from "tailwind-merge";

/**
  * Merge Tailwind classes with clsx
  */
const clsxm = (...classes: ClassValue[]) => twMerge(clsx(...classes));

export default clsxm;
```

### Get Type from a Component

This can be useful if you want to create a custom component that builds on top of an already existing component and you want to be able to pass down all the original component's props to your custom component (or at least some of them).

```ts
pagination?: boolean | Omit<ComponentProps<typeof Pagination>, "page" | "setPage">;

...

export interface PropTypes extends Omit<ComponentProps<"input">, "id" | "size"> { ... }


...

ComponentProps<typeof Carousel>
```

### Catch different Error cases (in Payload)

```ts
try {
  ...
} catch (error) {
  if (error instanceof Error) {
    throw new APIError(`... ${error.message}`, 500);
  } else {
    throw new APIError(`... ${error}`, 500);
  }
}
```

### Make a request with passing current cookies

If code is executed from the server (like in a server component in Next.js), the cookies are not automatically available. If your backend depends on getting some cookies, pass them manually with the fetch request. With the payload cms framework this is needed, for example. If you want to make Postman request, you would also have to pass the cookies through. Look at a previous request from your frontend, and copy the whole Cookie from the request header there to pass as a `Cookie` header in your Postman request.

```ts
...

const cookieStore = await cookies();

const response = await fetch(url,
  {
    method: "GET",
    headers: {
      Cookie: cookieStore.toString(),
    },
  });
```

### $and, $in, and $exists

```ts
$and: [
  { id: some_id },
  {
    $or: [
      {
        // If at least one item of some_array has one of the both states, this will catch it
        some_array: {
          state: {
            $in: [EntityState.Waiting, EntityState.Rejected],
          },
        },
      },
      { some_array: { $exists: false } }, // if some_array is empty, this will catch it
    ],
  },
];
```

### Zod Basic Example

```ts
import { z } from "zod";

const UserSchema = z.object({
  name: z.string().min(2, "Name must be at least 2 characters"),
  age: z.number().min(18, "Age must be at least 18"),
  email: z.string().email("Invalid email format"),
});

const invalidUser = {
  name: "J", // Too short
  age: 16, // Too young
  email: "not-an-email", // Invalid format
};

try {
  const user = UserSchema.parse(invalidUser);
  console.log("Valid user:", user);
} catch (error) {
  console.error("Validation failed:", error.errors);
}
```

_Error Output:_

```ts
Validation failed: [
  { message: 'Name must be at least 2 characters', path: ['name'], ... },
  { message: 'Age must be at least 18', path: ['age'], ... },
  { message: 'Invalid email format', path: ['email'], ... }
]
```

### Use an Indexed Access Type in TypeScript

```ts
type Test = {
  logger: { log: (msg: string) => void };
  user: { name: string; age: number };
};

// Access the type structure of logger or user inside the Test type without them being used directly (especially helpful if working with libraries, for example)
const test: Test["logger"];
```

### Check for differences in two objects

```ts
JSON.stringify(object1) === JSON.stringify(object2); // order of key-value pairs is important since a different order would also trigger a detected change

// or map through one object with Object.keys(object1), for example and check for differences for each key-value pair of both objects (if object1 has less key-value pairs this might produce wrong results)
```

### tsconfig.json & package.json setup for library/sdk with tsc

First steps: Initialize project with `npm init`, install Typescript as dev dependency with `npm install typescript --save-dev`, generate tsconfig.json by running `npx tsc --init`

_tsconfig.json:_

```json
{
  "compilerOptions": {
    "target": "ESNext",
    "module": "ESNext",
    "rootDir": ".",
    "moduleResolution": "Node",
    "declaration": true,
    "emitDeclarationOnly": false,
    "sourceMap": true,
    "outDir": "dist",
    "declarationDir": "dist/types",
    "allowSyntheticDefaultImports": true,
    "esModuleInterop": true,
    "forceConsistentCasingInFileNames": true,
    "strict": true
  },
  "include": ["src/**/*.ts"],
  "exclude": ["dist", "dist/types"]
}
```

_package.json:_

```json
{
  "name": "...",
  "version": "0.0.1",
  packageManager: "pnpm@9.15.4",
  "description": "...",
  "repository": {
    "url": "...",
    "type": "git"
  },
  "main": "dist/src/index.js",
  "types": "dist/types/src/index.d.ts",
  "exports": {
    ".": {
      "types": "./dist/types/src/index.d.ts",
      "import": "./dist/src/index.js",
      "default": "./dist/src/index.js"
    }
  },
  "files": ["dist"],
  "type": "module"
  "scripts": {
  "build": "tsc",
  "test": "jest --passWithNoTests",
  "lint": "eslint"
  },
  "author": "...",
  "devDependencies": {
    "@jest/globals": "...",
    "@types/jest": "...",
    "@types/node": "...",
    "axios": "...",
    "axios-mock-adapter": "...",
    "globals": "...",
    "jest": "...",
    "prettier": "...",
    "ts-jest": "...",
    "typescript": "...",
    "eslint": "...",
    "...": "..."
  },
  "peerDependencies": {
    "axios": "...",
    "...": "..."
  }
}
```

### Useful Jest Test features

```ts

jest.useFakeTimers()

...

afterEach(() => {
  mock.reset()
  jest.clearAllMocks();
  jest.clearAllTimers();
});

...

const mock = new MockAdapter(axios);
const mockResponse = { ... }

mock.onPost("some_url").reply(200, mockResponse);
// then access parts of this, like mock.history.post.length or do stuff like this:
const postData = JSON.parse(mock.history.post[0].data);
expect(postData.method).toBe("...");
expect(postData.params.ABC).toBe("...");

...

const someMock = jest.fn()

const renderComponent = () => render(
  <SomeComponent onClick={someMock} />
)

...

renderComponent()
fireEvent.click(screen.getByText("..."))
expect(someMock).toHaveBeenCalledTimes(1);

...

act(() => {
  jest.advanceTimersByTime(500);
})

...

expect(() => {
  renderHook(() => useTestHook());
}).toThrowError("useTestHook must be used within ABC context");
```

### React Portal

```tsx
const Modal = ({ children, onClose }) => {
  return ReactDOM.createPortal(
    <div style={styles.overlay}>
      <div style={styles.modal}>
        <button style={styles.closeButton} onClick={onClose}>
          Close
        </button>
        {children}
      </div>
    </div>,
    document.getElementById("modal-root"), // Portal's target DOM node
  );
};
```

_Somewhere in the application_

```html
<div id="modal-root"></div>
<!-- Here the React Portal from above would be applied to -->
```

_If multiple portals are rendered at the same time:_

- All the portal contents will coexist within the same `#modal-root` element.

### Cronjob via Next.js and via dockerfile

#### In crons file:

```sh
0 * * * * * curl -s -f http://localhost:${PORT}/ENDPOINT_PATH
0 * * * * * curl -X DELETE -s -f http://localhost:${PORT}/DELETE_ENDPOINT_PATH # -X does not work in PowerShell, use "-Method" there
... more cronjobs ...
```

-s = silent mode
→ It makes curl not show progress meters or error messages (basically, no output unless you specifically print it).

-f = fail silently on server errors
→ If the HTTP response code is 400 or higher (like 404 or 500), curl won't print the HTML error page — it will just exit with an error code, cleanly and quietly.

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
- The cron file can only be access as root user.

### Style scroll bar in CSS

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

### Convert (png) image to base64

```ts
const emailLogoPath = path.resolve(process.cwd(), "public/email/logo.png");
const emailLogoBuffer = fs.readFileSync(emailLogoPath);
const base64EmailLogo = emailLogoBuffer.toString("base64");
const emailLogoSrc = `data:image/png;base64,${base64EmailLogo}`;
```

If dealing with rapid quality loss, consider using a larger sized image.

### Handle URL Rewrites in middleware (Next.js) - Solving potential CORS Errors (via Spoofing)

CORS only becomes an issue when the browser makes a request directly to a different domain and the backend (the other domain) doesn't allow the requesting origin. However, since the following Next.js middleware rewrites the request internally, the browser only sees a request to the Next.js domain, and CORS never gets triggered. This approach basically acts as an internal proxy. This makes use of "Spoofing", basically faking the origin the request actually comes from by rewriting it to the same domain of the api. Spoofing works like this in middlewares but also via curls like `curl -H "Origin: https://trusted-site.com https://api.your-service.com`. You just rewrite the origin header that is automatically sent by the browser to the same domain of the API and make the API think "oh, this comes from the same domain, I allow it".

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
  if (n <= 2) return 1;

  memo[n] = fibo(n - 1, memo) + fibo(n - 2, memo);
  return memo[n];
};
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
  R extends ValidResourcesForClient<T>,
> = ClientResourceScopes[T][R];

interface PermissionScopesGrantedArguments<
  T extends keyof ClientResourceScopes,
  R extends ValidResourcesForClient<T>,
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

const AppContext = createContext<ContextType | undefined>(undefined);

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

## Nest.js

This section includes relevant information for Nest.js (Node.js framework).

- _Identity Map_: A pattern that ensures each entity is loaded only once per request. MikroORM keeps a map of all fetched entities, so multiple queries for the same record (same ID) return the same object instance. This prevents duplication and helps with consistency (e.g., updates don't conflict).
- _Unit of Work_: A transactional pattern that tracks all changes (create, update, delete) to entities. MikroORM collects these changes and flushes them in one batch (usually at the end of a request). It ensures atomic writes and reduces DB roundtrips. This enables the fact that you don't have to persist, the changes made are all tracked automatically and at flush they all get applied on database level. You might fetch like a customer entity record (this fetched record will be inside the Identity Map), afterward you might change like `customer.name = "new_name"` (this change is tracked by the Unit of Work) and if you then flush, all similar changes made from the current request context will be applied to the database. You only need to persist if you created a new entity (not fetched from existing ones).
- _Changeset_: A Changeset in MikroORM is an internal snapshot of the differences between the current and original state of an entity. When you modify an entity (e.g., user.name = 'New Name'), MikroORM uses the Identity Map to know it’s tracking that entity, and the Unit of Work then creates a Changeset to record what exactly was changed. This Changeset is what the ORM later uses to generate the correct SQL query (e.g., UPDATE users SET name = 'New Name' WHERE id = ...). Unlike the Identity Map (which prevents duplication) and the Unit of Work (which tracks that a change occurred), the Changeset captures what specifically changed. It’s part of the Unit of Work internals and is generated during the flush process. You don't usually interact with Changesets directly, but understanding them helps clarify how MikroORM knows exactly what to persist during a flush — it's the reason updates are efficient and minimal, and it plays a central role in ensuring the consistency and correctness of writes.
- _Request Context_: A per-request "sandbox" that holds the Identity Map and Unit of Work. It's created at the beginning of a request (e.g., via middleware), and passed down automatically. It keeps operations isolated between requests, important for parallelism and correctness. Every incoming HTTP request (like a controller method) gets its own RequestContext. But, MikroORM won’t automatically set up a RequestContext for Cron jobs, Message queues (e.g. Bull, Kafka), CLI scripts, Websockets, anything outside normal HTTP flow. When you create a cron job, for example, you have to manually introduce a Request Context for that specific cron job, to have like persisting and all needed features work. RequestContext uses AsyncLocalStorage under the hood (similar to thread-local storage in other languages). Each HTTP request creates its own AsyncLocalStorage context → MikroORM binds a unique EntityManager to that. When you run a cronjob (or queue handler, etc.), it runs outside that scope — no AsyncLocalStorage is active → no context → MikroORM won't know what to do. You won't “accidentally share” a context. The real issue is absence, not conflict.
- When [using custom repositories](https://docs.nestjs.com/recipes/mikroorm#using-custom-repositories), and you follow the proper naming convention, you don't need the `@InjectRepository()` decorator anymore.
- When people say "Nest.js DI" or "Nest.js DI container", they mean: DI = Dependency Injection | DI container = a system inside Nest.js that automatically creates, manages, and gives you instances of your classes or services when you need them.
- If you need to add like the current user to the entity manager context to reach out to that in a EventSubscriber, you can user a Nest.js Interceptor and make use of `em.setLoggerContext()`. An interceptor is not the same as middleware. Middleware is basically more low-level.
- If no actual changes were made to an entity on an update, the change set will remain empty 
- Your guards will run before any interceptor will. If you have role guards, for example, you will have the user with their roles in an interceptor. You don't have to manually parse the JWT in there.
- When throwing an exception in Nest.js, it interrupts the current flow (like throwing any error in JavasScript/TypeScript), and it triggers the exception filters, which transform the error into an HTTP response with statusCode, message, error.


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

## esbuild, tsc, rollup, and tsup

| Feature               | **esbuild** 🚀                | **tsc** 🎯                    | **rollup** 📦                      | **tsup** ⚡              |
| --------------------- | ----------------------------- | ----------------------------- | ---------------------------------- | ------------------------ |
| **Primary Purpose**   | Fast bundling & transpilation | Type checking & transpilation | Bundling (optimized for libraries) | Easy TypeScript bundling |
| **Performance**       | ⚡ Extremely fast             | 🐢 Slow (TypeScript-based)    | 🐢 Slow (tree-shaking overhead)    | ⚡ Fast (uses `esbuild`) |
| **Type Checking**     | ❌ No                         | ✅ Yes                        | ❌ No                              | ✅ (Optional)            |
| **Bundling**          | ✅ Yes                        | ❌ No (only transpiles)       | ✅ Yes                             | ✅ Yes                   |
| **Tree Shaking**      | ✅ Yes                        | ❌ No                         | ✅ Yes (better than esbuild)       | ✅ Yes                   |
| **Minification**      | ✅ Yes                        | ❌ No                         | ✅ Yes                             | ✅ Yes                   |
| **Output Formats**    | ESM, CJS, IIFE                | JS (ESNext, ES6, etc.)        | ESM, CJS, IIFE                     | ESM, CJS, IIFE           |
| **Config Simplicity** | 🔥 Simple                     | ❌ Complex (`tsconfig.json`)  | ❌ Complex (`rollup.config.js`)    | ✅ Simple                |
| **Best For**          | Fast dev builds               | Type safety                   | Libraries (optimized output)       | Easiest TS bundling      |
| **Used With**         | Vite, Webpack                 | Standalone, Linting           | Libraries (React, Vue, etc.)       | Modern TS projects       |

### **When to Use Each?**

- **`tsc`** → If you need **type checking**.
- **`esbuild`** → If you need **super-fast builds**.
- **`rollup`** → If you’re **building libraries** (optimized, tree-shaken output).
- **`tsup`** → If you want **a simple way to bundle TypeScript** with minimal config. -> This is a good way to set up libraries where you need both cjs and mjs compilation.
