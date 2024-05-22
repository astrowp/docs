# Get Started with AstroWP

> First things first, if you haven't already, go and create a free [GitHub account](https://github.com/).

## Fork the Repository

After you have purchased **AstroWP**, you will receive an invite to AstroWP's GitHub repository.

![Pasted image 20240519171746](https://github.com/astrowp/docs/assets/170225022/31433aa9-2625-4039-a396-dc203fc7ca42)

**Click on the "View invitation" link in the email, and accept the invitation.**

*Are you getting a 404 error when trying to accept the invitation? Then make sure you’re actually signed in to your GitHub account. Will the forked repository be private or public? When you fork the AstroWP private repository, GitHub will create a copy of that repository under your account, and it will inherit the private status of the original repository.*

1. In the top-right corner of the repository page, click on **FORK**.

![image](https://github.com/astrowp/docs/assets/170225022/ba9bcbc3-507f-4498-ae33-8d7c5f1cb1ee)

2. This will give you a couple of settings to configure.

![image](https://github.com/astrowp/docs/assets/170225022/39dbee45-e727-4ea1-b410-70df3dbbd7b3)

3. Under "Owner," select the dropdown menu and select yourself as the owner of the forked repository.

4. By default, forks are named the same as their upstream repositories. To distinguish your fork, you can type a different name in the "Repository name" field. (You can also change this later in the Settings).

5. Optionally, in the "Description" field, type a description of your fork. (You can also change this later in the Settings).

6. Select Copy the **MAIN** branch only, as you only need to copy the default branch.

7. Click **Create fork**, and you are done. AstroWP's repository is now yours!

If you are confused about forking and need more help, check out this [GitHub tutorial](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo#forking-a-repository).

## Configure Headless WordPress

### Install WordPress

After purchasing the AstroWP starter kit you will get an ```.wpress``` file that you will use to import the Headless WordPress version on to your favorite web host.

> **This ```.wpress``` file comes pre-configured with all the plugins and settings for your Headless WordPress site.**

You can use any web host you like, I recommend the following web hosts:

- [Hostinger](https://www.hostg.xyz/aff_c?offer_id=6&aff_id=1036&source=astrowp)
- SiteGround afflink
- Cloudways afflink
- [InstaWP](https://app.instawp.io/register?ref=vPtVNfKldT)

or you can host WordPress locally using [LocalWP](https://localwp.com/help-docs/getting-started/installing-local/)

*If you use LocalWP, then keep in mind that when deploying the site, your WordPress site will need to be exposed to the Internet i.e. deployed/hosted. This is something LocalWP isn't made to do - although if you are an advanced user, you can configure LocalWP to work with Ngrok or Cloudflare tunnels.*

1. Sign up for hosting.

 - You can use a temporary domain provided by the web host, or you can connect a custom domain, either works fine.
 - You don't need fancy hosting :) Remember, WordPress is only for the back-end; it's completely decoupled from the front-end.

2. Install a blank WordPress site on your preferred web host.

3. In your WordPress dashboard, go to Plugins, and install and activate the free **All In One WP Migration plugin**. 

4. Go to All In One WP Migration's Import, and import the ```.wpress``` file.

5. You will be logged out, so log back in again using *username* and *password* as the login credentials.

6. Create a new Administrator user (afterwards, you should delete the old admin user using *username* and *password*).

![Pasted image 20240517114704](https://github.com/astrowp/docs/assets/170225022/301d1b2e-94e3-4eb6-b52e-e0d7f3e9e48e)

7. Create an Application Password. Go to ```Users > Edit user > Application Password```. Make a copy of this password (this is important!).

![Pasted image 20240517114618](https://github.com/astrowp/docs/assets/170225022/f2cceb34-0220-4eb2-ba14-1f6182124260)

Now, you should have three things for moving forward:

```
a WordPress Server URL e.g. https://my-astrowp-project.instawp.xyz
a WordPress Username e.g. Mathias
a WordPress Application Password e.g. ABCD 1234 EFGH 5678
```

## Configure WordPress

### Set Up Webhooks

You can use webhooks and GitHub Actions to create a re-build process for the Astro site for a particular change(s) made in the WordPress backend.

### Configure GitHub

1. First, create a [GitHub personal access token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens). This token will be used in the webhook request to authenticate with GitHub.

2. Give it a name, and repository access to your Astro site repo.

3. Under "Repository permissions", set Contents to `Contents: Read and Write`. The final repository permissions should be "Read access to metadata" and "Read and Write access to code".

4. Copy the token on the following page to use for the next steps.

5. In the GitHub repository, go to Settings > Actions > General, and enable `Read and write permissions` under "Workflow permissions".

### Configure WordPress


### Edit .env.example

In your GitHub repository, navigate and go to the ```.env.example``` file in the root folder. Click on the **Pencil** icon to edit this file.

![Pasted image 20240517115903](https://github.com/astrowp/docs/assets/170225022/18e21dbd-ece5-423d-b471-44a53d6bceb1)

Rename the ```.env.example``` file to ```.env``` and add the required environment variables from the earlier step.

For example:

```
WP_USERNAME=Mathias
WP_APPLICATION_PASSWORD=ABCD 1234 EFGH 5678
```

![Pasted image 20240517120236](https://github.com/astrowp/docs/assets/170225022/9ee3f484-7d8a-4cf0-b83c-c2a286ec14ac)

and then **Commit** the changes.

### Edit config.json

Open the ```config.json``` file (in /src/config/config.json)

```
├── src/
│   └── pages/
│   │   └── ...
|   └── config/
│       └── config.json
```

Edit this file, and replace **API_URL** with the WordPress server URL, from the earlier step.

![Pasted image 20240517120623](https://github.com/astrowp/docs/assets/170225022/15ea9ec0-da2a-4b0e-a295-5c4080e92313)

(you can leave the URL variable empty for now, this is the URL for your deployed site e.g. https://astrowp.com), if you don't know what your deployed site's URL is then the URL for this variable can be added in later.)

and then **Commit** the changes.

## Run AstroWP Locally

### Prerequisites

- **Node.js** version 20.3.0 or higher. You can download Node [here](https://nodejs.org/en/download/package-manager).
- **GitHub Desktop**. [GitHub Desktop](https://desktop.github.com/) has a graphical user interface that simplifies commands and helps you visualize changes.
- **Text editor** - I recommend VS Code with the [Official Astro extension](https://marketplace.visualstudio.com/items?itemName=astro-build.astro-vscode), but any text editor works.
- **Terminal** - Astro is accessed through its command-line interface (CLI).

### Installation Guide

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

4. Then install the dependencies.

```npm install
npm install
```

5. Then fire up the local server.

```npm run dev
npm run dev
```

> If it all goes well, the project should now be up and working on http://localhost:4321/ *(it might be a different port to 4321)*

## Deploy AstroWP

Commit your code and push to your repository on GitHub.

Use your favorite hosting provider (Vercel for me) to create a new project based on the GitHub repository.

Deployment
In general you can deploy the application to any hosting provider that supports Node.js, but we recommend using Vercel for the best experience.

Read further deployment guides on our blog:

Render
Fly.io
Netlify
Docker image

Deploying to Vercel
Vercel is the easiest way to deploy Next.js apps. It's the company behind Next.js and has first-class support for Next.js.

Setup vercel account
To host your project on Vercel you first have to create an account.

Connect your git repository
After signing up you will be promted to import a git repository. Select the git provider of your project and connect your git account with Vercel.

Vercel welcome screen

Now you will see a list of all your projects. Select the project you want to deploy and click on the Import button.

In the Configure Project view expand the Enviornment Variables section and add the following variables one by one (you can copy them from the .env file in your projects root too):

NEXT_PUBLIC_SITE_URL=<YOUR_SITE_URL>
DATABASE_URL=<YOUR_DATABASE_URL>

The NEXT_PUBLIC_SITE_URL is the main url of your site, e.g. https://your-app.com.

Vercel project configuration

Then click the Deploy button and your project will be deployed.
