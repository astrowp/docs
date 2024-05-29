# Run AstroWP Locally

> You don't *have to* clone the AstroWP repository to your local machine. Technically, you could edit files and make commits directly on GitHub.

**OR** you could use VS Code with the [GitHub Repositories extension](https://marketplace.visualstudio.com/items?itemName=GitHub.remotehub). This extension lets you [edit and commit](https://www.youtube.com/watch?v=uCDKpsIRLPc) to the GitHub repository directly from GitHub — no cloning or local repository required.

**BUT** I recommend that you clone the repo and run it locally. *Why?* Because cloning the repository to your local computer makes it easier to add or remove files, and push combined commits, AND it lets you preview the site on localhost instead of having to deploy.

### Prerequisites

- **Node.js** version 20.3.0 or higher installed on your local machine. You can download Node [here](https://nodejs.org/en/download/package-manager).
- **Text editor / IDE** - I recommend using [VS Code](https://code.visualstudio.com/download) with the official Astro and GitHub Repositories extensions, but any text editor works.

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

> If it all goes well, the project should now be up and working on http<span>://</span>localhost:4321/ *(it might be a different port to 4321)*

## VSCode

<img src="https://github.com/astrowp/docs/assets/170225022/e7fec34c-87f9-4fd9-bdb8-247418e9a896" width="750px" />

[Download VS Code here](https://code.visualstudio.com/download)

Of course, you can use any IDE you like with this starter kit, but when used with Visual Studio Code and the suggested extensions, it will give you the best possible experience customizing your project.

These are the extensions I recommend:

[Astro](https://marketplace.visualstudio.com/items?itemName=astro-build.astro-vscode)
It provides language support for .astro files. This extension is powered by the Astro language server.

[GitHub Repositories](https://marketplace.visualstudio.com/items?itemName=GitHub.remotehub)
It allows you to quickly browse, search, edit, and commit to any remote GitHub repository directly from within Visual Studio Code. You can open any GitHub repository directly from GitHub — no cloning or local repository required.

[Tailwind CSS IntelliSense](https://marketplace.visualstudio.com/items?itemName=bradlc.vscode-tailwindcss)
It enhances the Tailwind development experience by providing Visual Studio Code users with advanced features such as autocomplete, syntax highlighting, and linting.
