# Deployment

You can deploy your site to any hosting provider that supports Node.js, but for the best experience, I recommend using **Vercel**.

- [Vercel](https://vercel.com/home)
- [Netlify](https://www.netlify.com/)
- [DigitalOcean](https://www.digitalocean.com/pricing/app-platform)
- [Cloudflare Pages](https://pages.cloudflare.com/)

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

Now click on the Deploy site button and wait for the deployment to finish. After that, you should be able to visit your freshly deployed SaaS.

![image](https://github.com/astrowp/docs/assets/170225022/c5a87c29-8adb-49a7-b8cc-56d0896629ac)

![image](https://github.com/astrowp/docs/assets/170225022/25f7dbce-394d-4aba-993b-d8a6843c0e5d)

### 5. Auto-deploy webhook

You want to create a webhook that triggers a re-build whenever your WordPress site is updated.

Go to **Site configuration -> Build & deploy -> Build hooks**

![image](https://github.com/astrowp/docs/assets/170225022/78a4317e-2b33-442e-9a96-f3b0a36900dc)

Give the webhook and name and save it.

### 6. Add a custom domain

Connect your custom domain, or you can continue using the temporary

![image](https://github.com/astrowp/docs/assets/170225022/8424ccce-4f2d-433b-a34c-bde40d6e4af2)

### 7. Forms

With Netlify you can receive form submissions via Netlify in the dashboard. If you use Netlify, then you don't have to set up the contact form [as explained here](https://docs.astrowp.com/#/saas-theme?id=_7-contactjson).

![image](https://github.com/astrowp/docs/assets/170225022/62fb6f5e-6b27-45e8-8782-ade25833300c)

```
<form name="contact" method="POST" data-netlify="true">
```

Simply add the Netlify attribute in the <form> tag to enable form detection, and you’ll automatically receive form submissions in your Netlify dashboard. 

[Learn more here](https://docs.netlify.com/forms/setup/).


