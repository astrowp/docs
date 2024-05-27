# Webhooks

Here you'll learn how to configure the webhook. Whenever you publish or update content on WordPress, this webhook will trigger a deployment on Vercel/Netflify/DigitalOcean, and the frontend will be updated with the latest content updates, and other savings you have made on the WordPress site.

> It's important to know that certain actions **will not** trigger a deployment.

| Examples of actions that **WON'T** trigger a deployment | Examples of actions that **WILL** trigger a deployment |
| -------- | ------- |
| - Creating a shortcode | - Publishing a post/page/custom post type |
| - Activating/deactivating a plugin | - Updating a post/page/custom post type |
| - Creating/deleting a new user | - Creating/deleting a category/tag/image to a post/page/custom post type |
| - Creating an ACF metafield | - Creating/deleting SEO metadata for a post/page/custom post type |

> If you want to trigger a deployment on the frontend, you will have to update a post/page/custom post type, and then the webhook will kick in to force a deployment.

## Configure webhooks

Go to Automator -> All Recipes.

![image](https://github.com/astrowp/docs/assets/170225022/e7aa54fd-3fd8-459f-aa6e-664c7ba8b566)

## Vercel and Netflify webhooks

Open the Vercel/Netlify webhook settings (the configuration is identical for Vercel and Netlify).

![image](https://github.com/astrowp/docs/assets/170225022/84f78ee7-3510-47e5-8bf7-aecc0621d0dc)

Click on the webhook.

![image](https://github.com/astrowp/docs/assets/170225022/cc9e6b12-1697-4ac2-b609-27aad8cf093d)

Configure the webhook.

![image](https://github.com/astrowp/docs/assets/170225022/e4ebc18f-6d98-4ffa-b026-67af74f53c62)

1. Paste in the Vercel/Netlify webhook URL.
2. Hit save.
3. Toggle the webhook to publish.

## DigitalOcean webhook

Open the DigitalOcean webhook settings (the configuration is very similar to Vercel and Netlify).

![image](https://github.com/astrowp/docs/assets/170225022/a024afe2-70b6-4edc-b412-e8c901fddd86)

1. Paste in the DigitalOcean webhook URL ([find out how to get it here](https://docs.astrowp.com/#/deploy?id=get-your-app-id-here)).
2. Paste in the DigitalOcean API token. ([find out how to get it here](https://docs.astrowp.com/#/deploy?id=get-your-api-token-here))).
3. Hit save.
4. Toggle the webhook to publish.
