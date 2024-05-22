## Getting Started with AstroWP

> First things first, if you haven't already, go and create a free [GitHub account](https://github.com/).

## Fork the repository

After purchasing **AstroWP** you will receive an invite to the private GitHub repository.

![Pasted image 20240519171746](https://github.com/astrowp/docs/assets/170225022/31433aa9-2625-4039-a396-dc203fc7ca42)

Click on the "View invitation" link in the email, and accept the invitation and go ahead and fork the repository.

***Are you getting a 404 error?** Make sure you’re signed in to your GitHub account.
**Will the forked repository be private or public?** When you fork the AstroWP private repository, GitHub will create a copy of that repository under your account, and it will inherit the private status of the original repository.

## Configure WordPress

After purchasing the AstroWP boilerplate you will get an ```.wpress``` file that you'll use to import the headless WordPress version on to your favorite web host.

You can use any web host you, I recommend the following web hosts:

Hostinger afflink https://www.hostg.xyz/aff_c?offer_id=6&aff_id=1036&source=astrowp
SiteGround afflink
Cloudways afflink
InstaWP afflink https://app.instawp.io/register?ref=vPtVNfKldT

or you can host WordPress locally using [LocalWP](https://localwp.com/help-docs/getting-started/installing-local/)* 

*Keep in mind that when deploying the site your WordPress server will need to be exposed to the Internet i.e. deployed/hosted, this is something LocalWP isn't made to do - although if you are an advanced user you can configure LocalWP to work with Ngrok or Cloudflare tunnels.*

1. Sign up for hosting, 
	- You can use a temporary domain provided by the web host, or you can connect a custom domain, either works.
	- You don't need fancy hosting :) Remember, WordPress will only be the back-end, it's completely decoupled from the front-end.
2. Install a blank WordPress site on your preferred web host.
3. Go to Plugins, and install the free **All In One WP Migration plugin** from the WordPress repository. 
4. Go to All In One WP Migration, and import the ```.wpress``` file.
5. Log back in again using *username* and *password*.
6. Create a new Administrator user (afterwards you can delete the old admin user).

![Pasted image 20240517114704](https://github.com/astrowp/docs/assets/170225022/301d1b2e-94e3-4eb6-b52e-e0d7f3e9e48e)

7. Create an Application Password. Go to Users > Edit user > Application Password. Make a copy of this password.

![Pasted image 20240517114618](https://github.com/astrowp/docs/assets/170225022/f2cceb34-0220-4eb2-ba14-1f6182124260)

Things you need for moving forward:

```
WordPress Server URL e.g. https://my-astrowp-project.instawp.xyz
WordPress Username e.g. Mathias
WordPress Application Password e.g. ABCD 1234 EFGH 5678
```

## Setup webhooks

You can use webhooks and GitHub Actions to create a re-build process for the Astro site for a particular change(s) made in the WordPress backend.

### GitHub Configuration

1. First, create a [GitHub personal access token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens). This token will be used in the webhook request to authenticate with GitHub.
2. Give it a name, and repository access to your Astro site repo.
3. Under "Repository permissions", set Contents to `Contents: Read and Write`. The final repository permissions should be "Read access to metadata" and "Read and Write access to code".
4. Copy the token on the following page to use for the next steps.
5. In the GitHub repository, go to Settings > Actions > General, and enable `Read and write permissions` under "Workflow permissions".

### WordPress Configuration

1. Install the [Uncanny Automator](https://wordpress.org/plugins/uncanny-automator/) plugin.
2. Create a recipe (Logged-in users or Everyone depending on the trigger) and choose WordPress for the Trigger.
3. Choose Webhooks > Send data to a webhook for the Action by clicking "Add action".
4. Select the events you want to use to trigger a re-build e.g. when a post is created.
5. Give the webhook a name and add the URL using your repository in the format of:

```
https://api.github.com/repos/{owner}/{repo}/dispatches
```

6. Under Request method, choose "POST" (the default).
7. Under Data format, choose "JSON".
8. In the Authorization field, paste your GitHub token in the format of:

```
Bearer github_pat_*********
```

9. Under Body, click "Add pair" and add:

```
event_type Text webhook
```

10. Click Save, and then click on "a webhook" to open up the settings again. Click "Send test" to see if everything works - a 204 response should be received and the action should be triggered - you can check the "Actions" tab in the GitHub repo.

11. To test the webhook itself, set the Trigger (WordPress) and Action (Webhooks) to "Live". You also need to set the recipe itself to "Live" (under the Recipe section on the right). Then you can create a post or whatever trigger you selected, to see if the action occurred.

The "published.txt" file in the repository will be created/updated with the current date, which will trigger a re-build with the hosting platform.

### Edit .env.example

In your GitHub repository, navigate and go to the ```.env.example``` file. Click on the Pencil icon to edit this file.

![Pasted image 20240517115903](https://github.com/astrowp/docs/assets/170225022/18e21dbd-ece5-423d-b471-44a53d6bceb1)

Rename the ```.env.example``` file to ```.env``` and add the required environment variables from the earlier step.

For example:

```
WP_USERNAME=Mathias
WP_APPLICATION_PASSWORD=ABCD 1234 EFGH 5678
```

![Pasted image 20240517120236](https://github.com/astrowp/docs/assets/170225022/9ee3f484-7d8a-4cf0-b83c-c2a286ec14ac)

and then Commit the changes.

### Edit config.json

Open the ```config.json``` file (/src/config/config.json)

```
├── src/
│   └── pages/
│   │   └── ...
|   └── config/
│       └── config.json
```

and replace **API_URL** with the WordPress server URL, from the earlier step.

![Pasted image 20240517120623](https://github.com/astrowp/docs/assets/170225022/15ea9ec0-da2a-4b0e-a295-5c4080e92313)

and then Commit the changes.

## Run AstroWP locally

**Prerequisites**

- **Node.js** version 20.3.0 or higher. You can download Node [here](https://nodejs.org/en/download/package-manager).
- **GitHub Desktop**. [GitHub Desktop](https://desktop.github.com/) has a graphical user interface that simplifies commands and helps you visualize changes.
- **Text editor** - I recommend VS Code with the [Official Astro extension](https://marketplace.visualstudio.com/items?itemName=astro-build.astro-vscode), but any text editor works.
- **Terminal** - Astro is accessed through its command-line interface (CLI).

**Step-by-step**

In your terminal, run the following commands to clone, install dependencies and run AstroWP on your local machine:

1. First, create a new empty directory (for example a directory in your [Desktop](https://youtu.be/B1IxcK6V-Vc?si=aQpY4HTEBR2Cwitb) location) with the name of your project *(rename my-astrowp-project to whatever you like)*.

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

If it all goes well, the My Astro Project should now be working on http://localhost:4321/
### Deploy AstroWP

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
