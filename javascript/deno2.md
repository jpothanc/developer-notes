# Node to Deno: More Than a Name Flip

Have you ever reopened an old project or application you once built and thought, If I were to build this today, I'd do it so differently? With time comes experience, new tools, and a shift in perspective that redefines how we approach challenges.
Ryan Dahl, the creator of Node.js back in 2009, must have had a similar realization when he introduced Deno in 2018. It wasn't It was not just shuffling of letters around no-de(de-no) - it was a deliberate effort to overcome its limitations and design something better. While the vision was forward-thinking, the early adoption of Deno came with skepticism, particularly for production use.
Now, with the release of Deno 2 in October 2024, the narrative has changed. Deno has matured, and it's not just an evolution - it feels like a revolution, a true game-changer.
So, Javascript developers, and Node.js lovers, you should look at Deno!! 
How to set up a simple Deno project

```bash
# install deno in windows, run below in powershell
irm https://deno.land/install.ps1 | iex

C:\Projects>deno -v
deno 2.1.7

C:\Projects\deno>mkdir deno2-test

C:\Projects\deno>cd deno2-test
# Initialize the workspace, for intellisense you will need this
C:\Projects\deno\deno2-test>deno init
✅ Project initialized

Run these commands to get started

  # Run the program
  deno run main.ts

  # Run the program and watch for file changes
  deno task dev

  # Run the tests
  deno test

# Open vs code
C:\Projects\deno\deno2-test>code .
```

## Native TypeScript support

Deno supports TypeScript natively for both execution and for type checking. It can run TypeScript files directly without needing additional setup or tools like the TypeScript compiler (tsc) or Babel.

```typescript
export function add(a: number, b: number): number {
  return a + b;
}t

console.log("Add 2 + 3 =", add(2, 3));

// Run using deno run command
deno run main.ts
Add 2 + 3 = 5
import { assertEquals } from "@std/assert";
import { add } from "./main.ts";

Deno.test(function addTest() {
  assertEquals(add(2, 3), 5);
});

// Run using deno test command
deno test

Check file:///C:/Projects/deno/deno2-test/main_test.ts
running 1 test from ./main_test.ts
addTest ... ok (0ms)

ok | 1 passed | 0 failed (4ms)
```

## Secure by Default

Deno is designed to be secure by default, which means it runs scripts in a sandbox with no access to the file system, network, or environment variables unless explicitly granted by the user.
Explicit Permissions: When running a script, you must grant explicit permissions (e.g., - allow-net, - allow-read). This security model is in contrast to Node.js, which does not restrict access by default. So, stop worrying about npm modules introducing unexpected vulnerabilities. Deno restricts access to the file system, network, and system environment by default, so code can access only what you allow

```bash
$ node random.js
Executing random.js...
🚨 File system compromised!

$ deno random.js
⚠️ Deno requests write access
Allow? [y/n/A]
$ n
❌ Denied write access
Exited
```

```typescript
// You can eliminate these prompts when you provide the approriate
// flags while # running the application

// Allows reading from the file system (e.g., reading files)
deno run --allow-read main.ts
// Shorthand for --allow-read
deno run -R main.ts

// Allows writing to the file system (e.g., creating or modifying files)
deno run --allow-write main.ts
// Shorthand for --allow-write
deno run -W main.ts

// Allows network access (e.g., making HTTP requests or opening sockets)
deno run --allow-net main.ts
// Shorthand for --allow-net
deno run -N main.ts

// Allows environment variable access
deno run --allow-env main.ts
// Shorthand for --allow-env
deno run -E main.ts
```

## Built on web standards

Deno provides web-standard APIs that are built into the runtime, just like those you would find in the browser. This means that Deno uses the same standard JavaScript APIs that you're familiar with from the browser environment, which helps make server-side code more uniform with client-side code.

```typescript
// Example of Web APIs: fetch for HTTP requests.
// In Deno, fetch() works exactly the same way as it does in the browser,
// making it simpler to transition between client-side and server-side code.

const response = await fetch("https://jsonplaceholder.typicode.com/posts/1");
const data = await response.json();
console.log(data);

// Run Deno
PS C:\Projects\deno\deno2-test> deno run --allow-net .\fetch.ts
{
  userId: 1,
  id: 1,
  title: "sunt aut facere repellat provident occaecati excepturi optio reprehenderit",
  body: "quia et suscipit\n" +
    "suscipit recusandae consequuntur expedita et cum\n" +
    "reprehenderit molestiae ut ut quas totam\n" +
    "nostrum rerum est autem sunt rem eveniet architecto"
}
```

## All-in-one Batteries included toolchain

Deno 2 continues to build on its "batteries included" philosophy, providing built-in tools that streamline development. These tools cover a wide range of needs, including formatting, linting, testing, bundling, and compiling.

```typescript
// deno fmt: Automatically formats your TypeScript or JavaScript code
// according to a standard style. This eliminates the need for external
// tools like Prettier.
deno fmt your_file.ts

// deno lint: Deno's linter helps to identify issues in your code, such as
// stylistic problems, bugs, or potential errors.
deno lint your_file.ts

// deno test : Provides a simple, built-in framework for writing and
// running tests in Deno.
deno test test.ts

// deno bundle:Bundles your Deno project into a single file for distribution,
// reducing the number of dependencies that need to be imported at runtime.
deno bundle your_file.ts output.js

// deno compile: Deno can compile TypeScript and JavaScript code into
// standalone executables, which doesn't require Deno to be installed on the
// target machine
deno compile --output myApp main.ts
```

## Backward compatibility with Node.js

Deno 2 introduces backward compatibility with Node.js, bridging the gap between Deno and the extensive Node.js ecosystem.
Deno can natively import NPM packages without requiring a package.json or node_modules folder. 
Deno understands package.json and can work with node_modules when needed, enabling smooth integration with existing workflows.
Deno can run existing Node.js applications written in ESM (ECMAScript Modules) with minimal changes.

```typescript
import chalk from "npm:chalk";
console.log(chalk.green("Hello, Deno with NPM!"));
```

## Package Management

Deno 2 makes package management easy with commands like deno install, deno add, and deno remove. 
It now introduces the JSR (JavaScript Registry), a new system for publishing TypeScript and JavaScript modules. JSR supports only ECMAScript modules (not CommonJS) and works with NPM, allowing JSR modules to use NPM packages. It's designed for use across platforms like Node.js, Deno, Bun, Cloudflare Workers, and browsers. Publishing to JSR is simpler than NPM, with no need to compile TypeScript, and it also generates documentation automatically
The code snippet below shows how you can import from JSR and npm

```typescript
import { walk } from "jsr:std/fs@1";
import { relative } from "node:path";

async function listFilesWithRelativePaths(directory: string): Promise<void> {
  console.log(`Files in directory: ${directory}\n`);
  for await (const entry of walk(directory)) {
    if (entry.isFile) {
      const relativePath: string = relative(directory, entry.path);
      console.log(relativePath);
    }
  }
}

const targetDirectory: string = "./programs";
listFilesWithRelativePaths(targetDirectory).catch((error) =>
  console.error("Error:", error)
);
```

## Executables

Deno allows developers to create standalone executables from their TypeScript or JavaScript code. These executables can be run on systems without requiring Deno to be installed. This feature is useful for distributing applications or scripts as self-contained binaries.

```typescript
deno compile --output hello ./hello.ts
// Optional Flags for Compilation:
// --allow-*: Include permissions for the executable (e.g., --allow-read, --allow-net).
// --target: Specify the target platform (x86_64-unknown-linux-gnu, x86_64-pc-windows-msvc, etc.).
// --output: Define the name of the executa

// Cross compile for Apple Silicon
deno compile --target aarch64-apple-darwin main.ts

// Cross compile for Windows with an icon
deno compile --target x86_64-pc-windows-msvc --icon ./icon.ico main.ts
```

## Long Term Support

Deno now has LTS (Long Term Support), providing a stable and reliable version for production use. LTS versions focus on maintaining API stability, regular security updates, and critical bug fixes, ensuring long-term reliability. These versions are supported for an extended period, typically 12–18 months, allowing developers to build and maintain applications with confidence.

## Jupiter Notebook Support

Deno 2 now supports Jupyter Notebooks, enabling developers to run and interact with Deno code directly within a notebook environment. This integration makes it easier to write, test, and demonstrate Deno scripts in an interactive and visual format. Developers can use Jupyter to explore Deno's features, perform data analysis, or prototype applications while leveraging the notebook's rich output and visualization capabilities.

```bash
🚀 **Deno Built-in Tools & Commands** 🚀

🛠 **Development & Code Quality**
✅ `deno fmt`      → Format code
✅ `deno lint`     → Lint code
✅ `deno test`     → Run tests
✅ `deno bench`    → Run benchmarks
✅ `deno doc`      → Generate documentation

📦 **Module & Dependency Management**
✅ `deno info`     → Inspect dependencies
✅ `deno cache`    → Cache modules
✅ `deno vendor`   → Vendor dependencies
✅ `deno lock`     → Manage lockfile

🖥 **Execution & Compilation**
✅ `deno run`      → Run a script
✅ `deno task`     → Run task scripts
✅ `deno repl`     → Open interactive REPL
✅ `deno compile`  → Compile script into an executable

🌍 **Security & Permissions**
✅ `deno check`    → Type-check code
✅ `deno permissions` → Inspect/set runtime permissions

🚀 **Deployment & Debugging**
✅ `deno bundle`   → Bundle files into one
✅ `deno install`  → Install scripts as CLI tools
✅ `deno uninstall` → Remove installed scripts
✅ `deno upgrade`  → Upgrade Deno to the latest version

🔍 **System & Environment**
✅ `deno version`  → Show Deno version
✅ `deno help`     → Show help for commands
✅ `deno completions` → Generate shell completions
✅ `deno upgrade`  → Upgrade to latest version

🔋 **All-in-One, No External Dependencies Needed!** 🔋

```
