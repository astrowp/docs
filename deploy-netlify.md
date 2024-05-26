# Deploy to Netlify

Before you start, make sure you have a Netlify account. If you don't have one yet, you can create one for free at [netlify.com](https://netlify.com/).

## 1. Create a new project
   
After creating an account, you should see a prompt on the dashboard to create a new site from a Git repository. Click on the Import from Git button.

![image](https://github.com/astrowp/docs/assets/170225022/4229c64c-e29d-4bc5-9ac3-d2448de27efc)

## 2.Select your repository

If not already done, you will be asked to connect your Git provider account. After that, you can select the repository you want to deploy.

![image](https://github.com/astrowp/docs/assets/170225022/728f6825-7ec0-4238-a61e-37f15aefc5fc)

## 3. Configure the build

After selecting the repository, you will be promted to configure the build settings. Usually Netlify will detect the correct settings automatically. If not, you can configure them manually like in the screenshot below:

![image](https://github.com/astrowp/docs/assets/170225022/80c76c30-fabb-4467-a940-0186f3a2a589)

## 4. Deploy the site

Now click on the Deploy site button and wait for the deployment to finish. After that, you should be able to visit your freshly deployed SaaS.

💡 Tip: Select function region for better performance
After your site has been deployed, go to Site configuration -> Build & deploy -> Functions region and select the region closest region to where your database is hosted. This will reduce the loading time of your api functions and improve the overall performance of your SaaS.

Make sure to redeploy your site after changing the region by clicking the Trigger deploy button on the Deploys page of your project.

![image](https://github.com/astrowp/docs/assets/170225022/bc9fcb39-1f4c-41a7-acc9-9014aa9c5633)
