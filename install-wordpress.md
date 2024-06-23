# Configure WordPress

## Install WordPress

After purchasing the AstroWP starter kit, you will receive ```.wpress``` files that you will use to import the themes Headless WordPress versions onto your favourite web host.

> **This .wpress file comes pre-configured with all the plugins and settings for your Headless WordPress site to work.**

You can use any web host you like, but I recommend using one of the these web hosts:

- [Hostinger](https://www.hostg.xyz/aff_c?offer_id=6&aff_id=1036&source=astrowp)
- [SiteGround](https://www.siteground.com/index.htm?afcode=cd053fc09a801013fd59695b1d137bbe)
- [InstaWP](https://app.instawp.io/register?ref=vPtVNfKldT)
- [DigitalOcean](https://www.digitalocean.com/pricing)

What's the *easiest* option? Personally, I find [InstaWP](https://app.instawp.io/register?ref=vPtVNfKldT) to be the easiest option for quickly spinning up a WordPress site.

What's the *cheapest* option? That's got to be [Hostinger](https://www.hostg.xyz/aff_c?offer_id=6&aff_id=1036&source=astrowp).

.. or you can host WordPress for free on your local machine using [LocalWP](https://localwp.com/help-docs/getting-started/installing-local/)

*If you decide to go with LocalWP, then keep in mind that when deploying the site, your WordPress site will need to be exposed to the Internet, i.e. deployed/hosted. This is something LocalWP isn't made to do - although if you are an advanced user, you can configure LocalWP to work with Ngrok or Cloudflare tunnels to be accessible on the web.*

### Step-by-Step Guide

1. Sign up for hosting.

 - You can use the temporary domain provided by most web hosts or connect a custom domain; either works fine as long as the URL is static and doesn't change.
 - You don't need to get flashy hosting :) Remember, WordPress is only for the backend; it's completely decoupled from the static front end.

2. Login to your web hosting company.

3. Go ahead and install a blank WordPress site.

4. In your WordPress dashboard, go to Plugins, and install and activate the free **All In One WP Migration plugin**. 

<img src="https://github.com/astrowp/docs/assets/170225022/b07713f5-81f9-40af-8d13-4ec087d94df7" width="750" />

5. Go to All In One WP Migration's import section and import the .wpress file (which you received when you signed up).

<img src="https://github.com/astrowp/docs/assets/170225022/9517e990-3d26-4990-babb-de9b28e5f47a" width="750" />

6. After the import, you will get logged out, so log back in again using *admin* and *password* as the login credentials.

![image](https://github.com/astrowp/docs/assets/170225022/8434f930-b504-4267-b819-a0a9b7803294)

> Login with **admin** and **password**

7. Create a new Administrator user and make a copy of the username and password .

<img src="https://github.com/astrowp/docs/assets/170225022/301d1b2e-94e3-4eb6-b52e-e0d7f3e9e48e" width="750" />

8. Log out and log back in again, as the new Admin user.

You should now delete the old admin user using *admin* and *password*.

9. Create an Application Password. Go to ```Users > Edit user > Application Password```. Make a copy of this password (this is important, you will need this later!).

<img src="https://github.com/astrowp/docs/assets/170225022/f2cceb34-0220-4eb2-ba14-1f6182124260" width="750" />

> Now, you should have three things to be able to move forward:

- a WordPress URL (of  your WordPress site) *e.g. https://my-astrowp-project.instawp.xyz*
- a WordPress Admin Username *e.g. Mathias*
- a WordPress Application Password *e.g. ABCD 1234 EFGH 5678*

Now it's time to connect your WordPress site to Astro.

## Edit .env.example

```
├── src/
|   └── .env.example
```

In your GitHub repository, navigate to the ``.env.example `` file in the root folder. Click on the Pencil icon and edit this file.

![Pasted image 20240517115903](https://github.com/astrowp/docs/assets/170225022/18e21dbd-ece5-423d-b471-44a53d6bceb1)

Rename the ```.env.example``` file to ```.env``` and add the required environment variables that you got in the earlier step.

For example:

```
WP_USERNAME=Mathias
WP_APPLICATION_PASSWORD=ABCD 1234 EFGH 5678
```

![Pasted image 20240517120236](https://github.com/astrowp/docs/assets/170225022/9ee3f484-7d8a-4cf0-b83c-c2a286ec14ac)

and then **Commit** the changes.

Alternatively, you can set up environment variables directly through the project settings in your deployment platform, such as Vercel, Netlify, or DigitalOcean.

## Edit config.json

In your GitHub repository, open the ```config.json``` file (in ```/src/config/config.json```). 

> In the Portfolio theme, the config file is located here ```src/config/config.ts```.

```
├── src/
|   └── config/
│       └── config.json
```

Edit this file, and replace **API_URL** with the WordPress server URL from the earlier step.

![Pasted image 20240517120623](https://github.com/astrowp/docs/assets/170225022/15ea9ec0-da2a-4b0e-a295-5c4080e92313)

(you can leave the URL variable empty for now; this is the URL for your [deployed site](deploy.md) (e.g. https<span>://</span>astrowp.com), if you don't know what your deployed site's URL is yet, then the URL for this variable can be added in later.)

and then **Commit** the changes.

That's it! Your WordPress site is now connected to Astro.
