# Webhooks

Here, you will learn how to configure automatic deployment webhooks.

![what-is-deploy-webhook](https://github.com/astrowp/docs/assets/170225022/69bd358f-d1e7-4cda-b7fe-7f75809546ae)

Whenever you publish or update content on WordPress, **a webhook will trigger a deployment on Vercel/Netflify/DigitalOcean**, and the front end will be updated with the latest content updates and other saved changes you have made on your headless WordPress site.

> It's important to know that certain WordPress actions **will not** automatically trigger a deployment.

| Examples of actions that **WILL NOT** trigger a deployment | Examples of actions that **WILL** trigger a deployment |
| :-------- | :------- |
| - Creating a shortcode | - Publishing a post/page/custom post type |<tr></tr>
| - Activating/deactivating a plugin | - Updating a post/page/custom post type |<tr></tr>
| - Creating/deleting a new user | - Creating/deleting a category/tag/image to a post/page/custom post type |<tr></tr>
| - Creating an ACF metafield | - Creating/deleting SEO metadata for a post/page/custom post type |<tr></tr>

> If you want to "force" trigger a deployment on the front end, you will have to update a post/page/custom post type, and then the webhook will kick in to force a deployment.

## Configure webhooks

Go to Automator -> All Recipes.

![image](https://github.com/astrowp/docs/assets/170225022/e7aa54fd-3fd8-459f-aa6e-664c7ba8b566)

## Vercel and Netflify webhooks

Open the Vercel/Netlify webhook settings (the configuration is identical for Vercel and Netlify).

![image](https://github.com/astrowp/docs/assets/170225022/84f78ee7-3510-47e5-8bf7-aecc0621d0dc)

Click on the webhook.

<img src="https://github.com/astrowp/docs/assets/170225022/cc9e6b12-1697-4ac2-b609-27aad8cf093d" width="750" />

Configure the webhook.

<img src="https://github.com/astrowp/docs/assets/170225022/e4ebc18f-6d98-4ffa-b026-67af74f53c62" width="750" />

1. Paste in the Vercel/Netlify webhook URL.
2. Hit save.
3. Toggle the webhook to publish.

Learn how to get the [Vercel webhook URL](https://docs.astrowp.com/#/deploy?id=_5-create-an-auto-deploy-webhook) and the [Netflify webhook URL](https://docs.astrowp.com/#/deploy?id=_5-create-an-auto-deploy-webhook-1)

## DigitalOcean webhook

Open the DigitalOcean webhook settings (the configuration is very similar to Vercel and Netlify).

<img src="https://github.com/astrowp/docs/assets/170225022/a024afe2-70b6-4edc-b412-e8c901fddd86" width="750" />

1. Paste in the DigitalOcean webhook URL ([find out how to get it here](https://docs.astrowp.com/#/deploy?id=get-your-app-id-here)).
2. Paste in the DigitalOcean API token. ([find out how to get it here](https://docs.astrowp.com/#/deploy?id=get-your-api-token-here))).
3. Hit save.
4. Toggle the webhook to publish.
