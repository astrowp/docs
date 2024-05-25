# Advanced Custom Fields (ACF)

The AstroWP Saas Theme .wpress import files come pre-installed with the free ACF WordPress plugin.

## Custom Meta Fields

Create a new Meta Fields Group in ACF, and choose where to display the meta fields (in posts, pages, or custom post types).

![image](https://github.com/astrowp/docs/assets/170225022/b8bfe0f1-00aa-49d7-8c17-7a7e09e6917d)

Then you can use either the ACF shortcode (this only works for simple text-based values):

```
[acf field="discount"]
```

or [GenerateBlocks Dynamic Data](https://docs.generateblocks.com/article/dynamic-data-options-overview/) in a Headline block, and add the meta value in the dynamic data field settings.

![image](https://github.com/astrowp/docs/assets/170225022/27c62be5-f8c8-4858-b9bd-0914db1ca598)

Meta fields are displayed on the front end.

![image](https://github.com/astrowp/docs/assets/170225022/201b61f4-276e-417c-96ec-ff853296c88c)

## Custom Post Types



### Register Custom Post Types

For custom post types to work, you have to register them in the config.json file.

#### config.json

```
 ── src
    └── config
        └── config.json
```

This is the config file for connecting your Headless WordPress site. For more information, see the [SaaS theme](saas-theme.md) page.

~~~
{
  "API_URL": "https://astrowp-demo.instawp.xyz",
  "site": {
    "url": "https://astrowp-saas-theme.vercel.app"
  },
  "post_types": ["Glossary"]
}
~~~

The ```API_URL variable``` is used to connect your WordPress site; it should be the full URL of where it is hosted e.g. https<span>://</span>astrowp-demo.instawp.xyz

The ```site:url variable``` is used to connect your published/deployed site to canonical links, XML sitemap etc., it should be the full URL e.g. https://astrowp.com

**The ```post_types variable``` registers ACF custom post types used on the WordPress site.**

To register multiple custom post types, you simply use this syntax:

```
"post_types": ["Glossary", "Coupons"]
```

```
"post_types": ["Glossary", "Coupons", "Projects"]
```
