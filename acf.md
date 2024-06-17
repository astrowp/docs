# Advanced Custom Fields (ACF)

The AstroWP Saas Theme .wpress import files come pre-installed with the free ACF WordPress plugin.

> Only the SaaS theme comes with ACF integration

## Meta Fields

Create a new Meta Fields Group in ACF, and choose where to display the meta fields (in posts, pages, or custom post types).

<img src="https://github.com/astrowp/docs/assets/170225022/8c65468c-2ab6-4bf4-9d07-af90ed9fb10c" width="750px" />

Meta fields will appear in the settings of the post/page where you add the information.

![image](https://github.com/astrowp/docs/assets/170225022/c5a6cfd5-4469-4a9c-8498-a388a7071af9)

Then you can insert a shortcode to display the meta field in posts, pages and custom post types (this works best for simple text-based values):

```
Year founded: [acf field="founded"]
```

will display as:

> **Year founded: 2020**


```
CEO/founder: [acf field="CEO"]
```

will display as:

> CEO/founder: Fred Schott

```
Website: [acf field="website"]
```

will display as:

> Website: <span>www.</span>astro.build

For a live example, [see this custom post type](https://saas-theme-demo.astrowp.com/glossary/what-is-astro/).

### Create Meta Fields

First, go to **ACF -> Field Groups -> Add new**

<img src="https://github.com/astrowp/docs/assets/170225022/e4595814-489a-4c59-825a-71a3ff57ad63" width="750px" />

Give the field group a name and create fields.

Then, in the settings **Location Rules**, decide where you want the meta fields to show (on posts, pages, or custom post types)

<img src="https://github.com/astrowp/docs/assets/170225022/33743525-2092-4f45-bc34-3acfe9216ca9" width="750px" />

Then, and importantly, in the settings **GraphQL**

<img src="https://github.com/astrowp/docs/assets/170225022/ea480c24-6b9a-4929-afd2-38cf39543c06" width="750px" />

**Toggle ON** Manually Set GraphQL Types for Field Group, and also **Toggle ALL** GraphQL Types to Show the Field Group On.

## Custom Post Types

First, go to **ACF -> Post Types -> Add new**


### Register Custom Post Types

For custom post types to work, you have to first register them in the config.json file.

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

### Create Custom Post Types
