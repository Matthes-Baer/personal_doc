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

## Linux Commands

- Start WSL: `wsl`
- Delete .git on Linux: `rm -rf .git`
- Exit the current terminal session: `exit`
- Run any command as the root user (input the actual command for "..."): `sudo ...`
- Switch to the root account (if access to sudo is available): `sudo -i`
- Access the commandline package manager (lists the available commands with apt): `apt`
- Check the current position in the file system: `pwd`
- List the directories/files at the current file system position: `ls`
- List the directories/files at the current file system position with a long list (more details): `ls -l`
- List the directories/files at a different file system position (without having to move to that position with `cd`; swap "_path_" with the actual path to investigate): `ls _path_`
- Change the current directory (enter a relative or absolute path): `cd ...`
- Get to the home directory: `cd ~`
- Rename a file/folder: `mv source targetName`
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

## Neovim & Corresponding Plugins Commands

- Access Package Manger: `:Lazy`
- Access Neotree: `:Neotree`
- Open a terminal at the bottom: `:belowright split | terminal`
- Copy the full path to the clipboard: `:let @+=expand('%:p')`
- Resize a window (8 lines as example): `:resize 8`
- Resize a window vertically: `:vertical resize 30`

## Packages

- (react-use - collection of utils)[https://www.npmjs.com/package/react-use]
- (gsap-quicktools - my animation quicktools package)[https://www.npmjs.com/package/gsap-quicktools]
- (react-hammerjs - mobile device touch event support)[https://www.npmjs.com/package/react-hammerjs]
- (sharp - converting images for better efficiency)[https://www.npmjs.com/package/sharp]

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

## Potential Fixes

- Git Error based on wrong user and password: `Windows-Anmeldeinformationen verwalten` -> In here, the proper user has to be configured for the corresponding git platform, so that the user operating in Git is the same user mentioned in the `Windows-Anmeldeinformationen`.

- To make a keycloak client work, a role has to be configured (like a "user" role).

- When using Next.js the error.tsx client component only works for server-side errors. If you want to get to this separate client component from a client component, you have to set up a state (errorState, for example) set it to true whenever the error might occur (in the catch block of an asynchronous action, for example) and check for true of this errorState to then throw an error which will lead you to the designated error.tsx client component.

- Fetch requests might fail with 400 (Bad Request) or 500 statuses which are valid HTTP responses (4xx and 5xx error status codes). However, these are not catched by the catch block which are for network errors, for example, (if the browser is unable to make the request at all). To catch those 4xx and 5xx error status codes you have to check with `response.ok` in the try block and throw an error manually to get to the corresponding catch block.

- For old browsers there might be a error in terms of "globalThis is not defined". To polyfill this issue you might use `<script src="https://polyfill.io/v3/polyfill.min.js?features=globalThis"></script>` or `<script dangerouslySetInnerHTML={{ __html: 'window.globalThis = window', }} type="text/javascript" />` or also `<script src="https://unpkg.com/@ungap/global-this@0.4.4/min.js" noModule async></script>` ([First & Second approach](https://github.com/vercel/next.js/pull/45592)[Third approach](https://github.com/vercel/next.js/discussions/49771))

- If animations are implemented which make use of `x` or `y` or similar movements, some sort of flickering might appear, affecting fonts and elements in general while the respective animation takes place. With the help of `backface-visibility: hidden` and `transform: translateZ(0)` this bug can be fixed. However, this fix might cause a small decline in quality for the fonts/texts - [source](https://discourse.webflow.com/t/a-fix-for-when-your-elements-move-up-and-or-blur-during-animations-interactions-on-chrome/11629)

## Next.js & React.js Features

This section covers some important Next.js and React.js features.

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

### Example

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

## Rust

This section covers information about the programming language Rust.

### Ownership

Ownership is a set of rules that govern how a Rust program manages memory.

- Each value in Rust has an owner.
- There can only be one owner at a time.
- When the owner goes out of scope, the value will be dropped.

### The Stack and the Heap

Both the stack and the heap are parts of memory available to your code to use at runtime, but they are structured in different ways. The stack stores values in the order it gets them and removes the values in the opposite order. This is referred to as last in, first out. Think of a stack of plates: when you add more plates, you put them on top of the pile, and when you need a plate, you take one off the top. Adding or removing plates from the middle or bottom wouldn’t work as well! Adding data is called pushing onto the stack, and removing data is called popping off the stack. All data stored on the stack must have a known, fixed size. Data with an unknown size at compile time or a size that might change must be stored on the heap instead.

The heap is less organized: when you put data on the heap, you request a certain amount of space. The memory allocator finds an empty spot in the heap that is big enough, marks it as being in use, and returns a pointer, which is the address of that location. This process is called allocating on the heap and is sometimes abbreviated as just allocating (pushing values onto the stack is not considered allocating). Because the pointer to the heap is a known, fixed size, you can store the pointer on the stack, but when you want the actual data, you must follow the pointer. Think of being seated at a restaurant. When you enter, you state the number of people in your group, and the host finds an empty table that fits everyone and leads you there. If someone in your group comes late, they can ask where you’ve been seated to find you.

The heap is used for dynamic memory allocation, where the size of the data might not be known at compile time or can change at runtime. Complex types such as String, vectors (Vec<T>), and other types that can grow or shrink at runtime are stored on the heap. When you use such types in Rust, what's actually stored on the stack is a pointer (or multiple pointers) to the data on the heap. This pointer contains the memory address of the actual data.

Pushing to the stack is faster than allocating on the heap because the allocator never has to search for a place to store new data; that location is always at the top of the stack. Comparatively, allocating space on the heap requires more work because the allocator must first find a big enough space to hold the data and then perform bookkeeping to prepare for the next allocation.

Accessing data in the heap is slower than accessing data on the stack because you have to follow a pointer to get there. Contemporary processors are faster if they jump around less in memory. Continuing the analogy, consider a server at a restaurant taking orders from many tables. It’s most efficient to get all the orders at one table before moving on to the next table. Taking an order from table A, then an order from table B, then one from A again, and then one from B again would be a much slower process. By the same token, a processor can do its job better if it works on data that’s close to other data (as it is on the stack) rather than farther away (as it can be on the heap).

When your code calls a function, the values passed into the function (including, potentially, pointers to data on the heap) and the function’s local variables get pushed onto the stack. When the function is over, those values get popped off the stack.

Keeping track of what parts of code are using what data on the heap, minimizing the amount of duplicate data on the heap, and cleaning up unused data on the heap so you don’t run out of space are all problems that ownership addresses. Once you understand ownership, you won’t need to think about the stack and the heap very often, but knowing that the main purpose of ownership is to manage heap data can help explain why it works the way it does.

#### Example

Consider a String type in Rust. When you create a String, the struct that represents the String (which includes the pointer, length, and capacity) is stored on the stack. The actual contents of the string, however, are stored on the heap. The pointer in the String struct points to this heap-allocated memory where the characters of the string are stored.

```js
let s = String::from("hello");
```

In this example, s is a variable on the stack that contains a String struct. This struct contains a pointer to the heap where the actual "hello" string is stored. The String struct itself might contain more than just a pointer (like length and capacity), but the crucial part for this discussion is that the character data is on the heap, and s on the stack points to it.

### `struct`

In Rust, a struct (short for "structure") is a custom data type that lets you name and package together multiple related values that make up a meaningful group. It's similar to a record, struct in C, or a class in other object-oriented languages (without the methods). Structs are a fundamental concept in Rust, used to create custom types.

### The `&` Symbol in Rust

The following information is based on this example:

```rust
use ferris_says::say;
use std::io::{stdout, BufWriter};

fn main() {
    let message: String = String::from("Hello fellow Rustaceans!");
    let width: usize = message.chars().count();

    let mut writer = BufWriter::new(stdout());
    say(&message, width, &mut writer).unwrap();
}
```

The `&` symbol is used for referencing in Rust. It creates a reference to a value without taking ownership of it. In Rust, every value has a single owner, and when the owner goes out of scope, the value is dropped. References allow you to refer to a value without owning it.

In the context of `&message`: Here, `&message` creates a reference to the `message` variable. The say function doesn't take ownership of `message`; it only needs to read the data. By passing a reference, you allow say to use `message` without taking ownership, so `message` can be used later in your function if needed.

In the context of `&mut`: When you see `&mut`, it signifies a mutable reference. This means that not only is the function referencing the variable, but it also needs to modify it. Mutable references allow you to change the data the reference points to. In `&mut` writer, it indicates that the say function might modify the writer.

### Understanding `mut` in Rust

mut stands for mutable. It's used to declare that a variable can be modified after its initial declaration. In Rust, variables are immutable by default, meaning once a value is bound to a name, you can’t change that value. To allow a variable to be mutable, you prepend it with mut.

### Moving and Borrowing

The following information is based on this example:

```rust
use ferris_says::say;
use std::io::{stdout, BufWriter};

fn main() {
    let message: String = String::from("Hello fellow Rustaceans!");
    let width: usize = message.chars().count();

    let mut writer = BufWriter::new(stdout());
    say(&message, width, &mut writer).unwrap();
}
```

In Rust, values can be passed to functions either by moving or by borrowing. These are key concepts in Rust's ownership system:

- Moving: When you pass a value to a function without a reference (e.g., just `message`), Rust assumes a move of ownership. After the move, you can't use the original variable unless the ownership is returned. This ensures memory safety but can be restrictive if you want to use the variable again after the function call.

- Borrowing: By passing a reference (`&message`), you borrow the value without transferring ownership. The function can use the value, but the original owner (in this case, the main function) retains ownership and can continue to use it after the function call. This is a non-destructive way to pass values to functions.

In your example, `say` needs to read `message` but doesn't need to own it. Using a reference (`&message`) is more efficient as it avoids unnecessary data copying and maintains the ability to use `message` later in the main function.

### Vec<T>

[Vector API Documentation](https://doc.rust-lang.org/std/vec/struct.Vec.html)

```rs
let mut v = vec![1, 2, 3, 4, 5];

let first = &v[0];

v.push(6);

println!("The first element is: {first}");
```

The code look like it should work: why should a reference to the first element care about changes at the end of the vector? This error is due to the way vectors work: because vectors put the values next to each other in memory, adding a new element onto the end of the vector might require allocating new memory and copying the old elements to the new space, if there isn’t enough room to put all the elements next to each other where the vector is currently stored. In that case, the reference to the first element would be pointing to deallocated memory. The borrowing rules prevent programs from ending up in that situation.

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
