## Configure WordPress

### Install HeadLess WordPress

After purchasing the AstroWP starter kit you will get an ```.wpress``` file that you will use to import the Headless WordPress version on to your favorite web host.

> **This .wpress file comes pre-configured with all the plugins and settings for your Headless WordPress site to work.**

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

4. Go to All In One WP Migration's Import, and import the .wpress file.

5. You will be logged out, so log back in again using *username* and *password* as the login credentials.

6. Create a new Administrator user (afterwards, you should delete the old admin user using *username* and *password*).

<img src="https://github.com/astrowp/docs/assets/170225022/301d1b2e-94e3-4eb6-b52e-e0d7f3e9e48e" width="750" />

7. Create an Application Password. Go to ```Users > Edit user > Application Password```. Make a copy of this password (this is important!).

<img src="https://github.com/astrowp/docs/assets/170225022/f2cceb34-0220-4eb2-ba14-1f6182124260" width="750" />

> Now, you should have three things for moving forward:

- a WordPress Server URL e.g. https://my-astrowp-project.instawp.xyz
- a WordPress Username e.g. Mathias
- a WordPress Application Password e.g. ABCD 1234 EFGH 5678

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
