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

In the [SaaS demo](https://saas-theme-demo.astrowp.com/) I have created a page that lists custom post types.

If you want to use the two-column Query Loop used on that page, you can copy the below and paste it into a page.

```
<!-- wp:query {"queryId":42,"query":{"perPage":"15","pages":0,"offset":0,"postType":"glossary","order":"desc","orderBy":"date","author":"","search":"","exclude":[],"sticky":"","inherit":false,"parents":[]}} -->
<div class="wp-block-query"><!-- wp:post-template {"layout":{"type":"grid","columnCount":2}} -->
<!-- wp:group {"style":{"spacing":{"padding":{"top":"30px","right":"30px","bottom":"30px","left":"30px"}}},"layout":{"inherit":false}} -->
<div class="wp-block-group" style="padding-top:30px;padding-right:30px;padding-bottom:30px;padding-left:30px"><!-- wp:post-title {"isLink":true} /-->

<!-- wp:post-excerpt {"moreText":"Read more","excerptLength":10} /-->

<!-- wp:paragraph -->
<p></p>
<!-- /wp:paragraph --></div>
<!-- /wp:group -->
<!-- /wp:post-template --></div>
<!-- /wp:query -->
```

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

The ```site:url variable``` is used to connect your published/deployed site to canonical links, XML sitemap etc., it should be the full URL e.g. <span>https://</span>astrowp.com

**The ```post_types variable``` registers ACF custom post types used on the WordPress site.**

To register multiple custom post types, you use this json syntax:

```
"post_types": ["Glossary", "Coupons"]
```

```
"post_types": ["Glossary", "Coupons", "Projects"]
```

### Create Custom Post Types

First, go to **ACF -> Post Types -> Add new**

<img src="https://github.com/astrowp/docs/assets/170225022/3da4bc22-e70f-446a-991b-21846a5f8e33" width="750px" />

1. Give the Post Type a label

> Use the same label for both plural and singular, just use one consistent label, either the plural **OR** singular, for example, **USE** coupons **DON'T USE** coupon/coupons

2. Add Taxonomies (category, tags, author)

3. Make it Active

4. Toggle on the Advanced Configuration

#### Advanced Configuration

**1. General Settings**

<img src="https://github.com/astrowp/docs/assets/170225022/7423feed-ceed-4f37-a0d2-fa9506c4379c" width="750px" />

Enable the features you want to appear in the content editor.

- Title
- Editor
- Featured Image
- Author
- Custom Fields

**2. Labels and Visibility**

You can leave the default settings.

**3. URLs**

<img src="https://github.com/astrowp/docs/assets/170225022/b1ab2183-e260-429f-b960-a00d92e6fa78" width="750px" />

Toggle On **Pagination** and **Publicly Queryable**

**4. Permissions**

You can leave the default settings.

**5. REST API**

<img src="https://github.com/astrowp/docs/assets/170225022/e751dd0c-c36a-46ed-8a21-714895491ace" width="750px" />

Toggle On **Show In REST API**

**6. GraphQL**

<img src="https://github.com/astrowp/docs/assets/170225022/6a8de90c-6d48-45de-ac38-7688bfe84b19" width="750px" />

Toggle On **Show in GraphQL**

Use the same label for the first step, just use one consistent label, either the plural **OR** singular, for example, **USE** coupons **DON'T USE** coupon/coupons

> This is the label you use in ```config.json``` when you [register the post type](https://docs.astrowp.com/#/acf?id=register-custom-post-types)

When you are done, your custom post type will appear in the left-hand side menu in the WordPress editor, and you can start creating custom post types.
