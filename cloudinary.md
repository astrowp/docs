# Cloudinary

Cloudinary comes pre-installed with your WordPress site. Although you are not required to use it, I recommend it, as Cloudinary is designed to optimize your WordPress site's media file performance. 

Here is how you configure Cloudinary.

## Sign up for a free Cloudinary account

[Go to cloudinary.com](https://cloudinary.com/users/register_free) and sign up for a free account.

The free plan gives you 25 monthly credits, which translates to either 25,000 transformations, 25 GB of storage, or 25 GB of managed bandwidth.

## Start the setup wizard

Go to the plugin and start the 3-step setup wizard.

![image](https://github.com/astrowp/docs/assets/170225022/43df47a2-6cb2-4902-acdc-90db27258a5b)

## Get your API key

Go to your Cloudinary dashboard, get your API key, and paste it in.

![image](https://github.com/astrowp/docs/assets/170225022/4ead7293-6bdc-4698-bb82-8f2dfac761f6)

## Configure media library sync settings

The plugin is ready out of the box, and the only consideration you should really make is whether you want to store media in WordPress, Cloudinary, or both (I recommend both).

![image](https://github.com/astrowp/docs/assets/170225022/fd84d059-3f85-47be-bbc9-fd3b5c660fd8)

By default, all your media assets are stored in both WordPress and Cloudinary, which allows us to keep all assets in sync. If you're looking to reduce the size of your WordPress storage, you can adjust your storage settings accordingly. You'll find this setting under General Settings > Media Library Sync Settings from the plugin menu. At minimum, assets must be stored with Cloudinary to be delivered with all the benefits Cloudinary offers.

The three options you can select are:

1. **Cloudinary and WordPress**. This setting stores all assets in both Cloudinary and WordPress local storage. With this setting, if there are any issues with your Cloudinary account, or you choose to deactivate the Cloudinary plugin, your assets will be delivered directly from WordPress storage with no issues, ensuring a more robust fallback mechanism.

2. **Cloudinary and WordPress (low resolution)**. This setting stores the original full-resolution assets with Cloudinary and a lower-resolution compressed version in WordPress, saving space in your local storage. If you deactivate the Cloudinary plugin, your assets will be delivered at a much lower resolution directly from WordPress storage. This setting provides a limited fallback mechanism.

3. **Cloudinary only**. This setting stores all assets in Cloudinary only. Any existing assets stored in WordPress will be removed to save space in your local storage. With this setting enabled, you need to manually sync your media back to WordPress before deactivating the plugin. Before setting to Cloudinary only, we recommend creating a full backup of your WordPress site.

For more information, check out this [help article](https://support.cloudinary.com/hc/en-us/articles/360017521280-WordPress-Plugin-Overview)
