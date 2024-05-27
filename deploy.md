# Deployment

You can deploy your site to any hosting provider that supports Node.js, but for the best experience, I recommend using **Vercel**.

- [Vercel](https://vercel.com/home) - start on the free tier, , scale up to the $20/mo for more resources
- [DigitalOcean App Platform](https://www.digitalocean.com/pricing/app-platform) - start on the free tier, scale up to the $5/mo for more resources
- [Netlify](https://www.netlify.com/) - similar to Vercel, super-easy to get started with
- [Cloudflare Pages](https://pages.cloudflare.com/) - start on the free tier

## Deploy to Vercel 

Vercel is the easiest way to deploy.

### Setup a Vercel account

To host your project on Vercel, you first have to [create a free account](https://vercel.com/signup).

### Connect your git repository

![image](https://github.com/astrowp/docs/assets/170225022/01e00e82-2dcc-4d90-89a9-f35c4d577368)

After signing up, you will be prompted to import a GitHub repository. Select the **GitHub provider** for your project and connect your GitHub account with Vercel.

Now you will see a list of all your projects. Select the project you want to deploy and click on the **Import** button.

## Deploy to Netlify

Before you start, make sure you have a Netlify account. If you don't have one yet, you can create one for free at [netlify.com](https://netlify.com/).

![image](https://github.com/astrowp/docs/assets/170225022/4ed4bd37-de76-4ee6-98b9-6853a458e04a)

### 1. Create a new project
   
After creating an account, you should see a prompt on the dashboard to create a new site from a Git repository. Click on the Import from Git button.

![image](https://github.com/astrowp/docs/assets/170225022/6e5f0030-4dfd-49fb-a80a-5568cbb0db64)

### 2. Select your repository

If not already done, you will be asked to connect your Git provider account. After that, you can select the repository you want to deploy.

![image](https://github.com/astrowp/docs/assets/170225022/82e25e91-fc7d-4cad-ab4f-47282294f73d)

### 3. Configure the build

After selecting the repository, you will be promted to configure the build settings. I my experience, Netlify will auto-detect the correct settings automatically. If not, you can configure them manually like.

### 4. Deploy the site

Now click on the Deploy site button and wait for the deployment to finish.

![image](https://github.com/astrowp/docs/assets/170225022/c5a87c29-8adb-49a7-b8cc-56d0896629ac)

![image](https://github.com/astrowp/docs/assets/170225022/25f7dbce-394d-4aba-993b-d8a6843c0e5d)

### 5. Create an Auto-deploy webhook

You want to create a webhook that triggers a rebuild whenever your WordPress site is updated.

Go to **Site configuration -> Build & deploy -> Build hooks**

![image](https://github.com/astrowp/docs/assets/170225022/78a4317e-2b33-442e-9a96-f3b0a36900dc)

Give the webhook and name and save it.

Find out how to [configure the webhook in WordPress](webhooks.md)

### 6. Add a custom domain

Connect your custom domain, or you can continue using the temporary one given to you.

![image](https://github.com/astrowp/docs/assets/170225022/8424ccce-4f2d-433b-a34c-bde40d6e4af2)

### 7. Forms

With Netlify you can receive form submissions via Netlify in the dashboard. If you use Netlify, then you don't have to set up the contact form [as explained here](https://docs.astrowp.com/#/saas-theme?id=_7-contactjson).

![image](https://github.com/astrowp/docs/assets/170225022/62fb6f5e-6b27-45e8-8782-ade25833300c)

```
<form name="contact" method="POST" data-netlify="true">
```

Simply add the Netlify attribute in the ```<form>``` tag to enable form detection, and you'll automatically receive form submissions in your Netlify dashboard. [Learn more about Netlify forms here](https://docs.netlify.com/forms/setup/).

## Deploy to Digital Ocean App Platform

### 1. Create an account

Go to DigitalOcean and [sign up for an account](https://www.digitalocean.com/products/app-platform).

![image](https://github.com/astrowp/docs/assets/170225022/b45154ab-b4a8-4c8c-a5ab-a533251cf5d1)

### 2. Select your repository

Then, import the AstroWP GitHub repository.

![image](https://github.com/astrowp/docs/assets/170225022/c8e68d49-85ff-44e2-9eb8-7341966ff55f)

### 3. Configure the build

Go through the settings. DigitalOcean will auto-detect the correct settings automatically.

Give it a name, and choose the **Static Site** resource type.

![image](https://github.com/astrowp/docs/assets/170225022/16e091f5-e240-4f4b-8c5e-ad6171e35e56)

![image](https://github.com/astrowp/docs/assets/170225022/544e657e-8bf8-4dbc-820d-cd2b104c374f)

![image](https://github.com/astrowp/docs/assets/170225022/d2d34901-9b95-4a48-b56d-925cab2da37a)

and review the settings.

### 4. Deploy the site

Now click on the Deploy site button and wait for the deployment to finish.

![image](https://github.com/astrowp/docs/assets/170225022/710bf354-7f95-49de-96a9-de54d76ec1d4)

### 5. Add a domain

Connect your custom domain, or you can continue using the temporary one.

![image](https://github.com/astrowp/docs/assets/170225022/e56c5dc0-02ff-449c-bc36-8d27a0187d0b)

### 6. Create an Auto-deploy webhook

This webhook will trigger a deployment on DigitalOcean and update the frontend, whenever a post is created or updated in your WordPress dashboard.

Go to **Functions** in the left-side navigation, or visit [https://cloud.digitalocean.com/functions](https://cloud.digitalocean.com/functions)

Create a **Namespace** and **datacenter region**.

Create a **Function**, and give it a name.

![image](https://github.com/astrowp/docs/assets/170225022/2cfa6141-e1d3-48a5-83d8-fe179ea6c384)

In the **Source** window, paste in this function:

```
function main(args) {
  const https = require('https');
  const data = JSON.stringify({"force_build": true});
  const appId = 'YOUR-APP-ID-HERE'; // Replace with your App ID
  const token = 'YOUR-API-TOKEN-HERE'; // Replace with your DigitalOcean API token

  const options = {
    hostname: 'api.digitalocean.com',
    port: 443,
    path: '/v2/apps/' + appId + '/deployments',
    method: 'POST',
    headers: {
      'Authorization': 'Bearer ' + token,
      'Content-Type': 'application/json',
      'Content-Length': data.length
    }
  };

  const req = https.request(options, function(res) {
    console.log("statusCode: ", res.statusCode);
    console.log("headers: ", res.headers);

    res.on('data', function(d) {
      process.stdout.write(d);
    });
  });

  req.on('error', function(error) {
    console.error(error);
  });

  req.write(data); // Write the request body
  req.end();
}
```

Hit Save, and the hit Run.

> Make of copy of the API token and the Source URL (webhook URL)

![image](https://github.com/astrowp/docs/assets/170225022/03eab80a-eb4c-4c93-917c-96a735a7db78)

#### Get your APP ID here

Go to the overview page of your ape. Copy the App ID from the address bar.

![image](https://github.com/astrowp/docs/assets/170225022/02e57e6a-fc6a-4f0c-8b7b-0605ff0050be)

#### Get your API token here

In the left-side navigation, go to **Applications & API**, then generate a new Token.

![image](https://github.com/astrowp/docs/assets/170225022/d728cfe7-cf3a-4e9c-a3f0-34bb1efb6e19)

- Give the API token a name
- Set the expiry date (I use no expire)
- Choose Custom Scopes (for more granular permission levels)
  - Select app
- Click, Generate Token

Find out how to [configure the webhook in WordPress](webhooks.md)
