# Run AstroWP Locally

> You don't have to run AstroWP locally, you could

BUT

The benefit of XX is that you can preview changes before deploying

## Prerequisites

- **Node.js** version 20.3.0 or higher installed on your local machine. You can download Node [here](https://nodejs.org/en/download/package-manager).
- **GitHub Desktop**. [GitHub Desktop](https://desktop.github.com/) has a graphical user interface that simplifies commands and helps you visualize changes.
- **Text editor** - I recommend VS Code with the [Official Astro extension](https://marketplace.visualstudio.com/items?itemName=astro-build.astro-vscode), but any text editor works.
- **Terminal** - Astro is accessed through its command-line interface (CLI).

## Installation Guide

In your terminal, run the following commands to clone, install dependencies and run AstroWP on your local machine:

1. First, create a new empty directory (for example a directory/folder on the [desktop directory](https://youtu.be/B1IxcK6V-Vc?si=aQpY4HTEBR2Cwitb)) with the name of your project *(rename my-astrowp-project to whatever you like)*.

```
mkdir my-astrowp-project
```

2. Then navigate into it.

```
cd my-astrowp-project
```

3. Now clone the private repository to the directory you just created.

```
git clone https://github.com/astrowp/headlesswp-saas-theme.git .
```

*(Note: The dot . at the end ensures the repository is cloned into the current directory, avoiding the creation of a nested directory.)*

4. Install dependencies.

```npm install
npm install
```

5. Then fire up the local server.

```npm run dev
npm run dev
```

> If it all goes well, the project should now be up and working on http://localhost:4321/ *(it might be a different port to 4321)*
