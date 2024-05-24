# AstroWP SaaS Theme

Here is everything you need to know about configuring and customizing the SaaS theme.

## Config Files

```
 ── src
    └── config
        └── config.json
        └── theme.json
```

The SaaS theme comes with two config files, one is for configuring the theme's connection to WordPress, and the other one is for styling.

### config.json

This is the config file for connecting your Headless WordPress site. For more information, see [this page](install-wordpress.md).

```
{
  "API_URL": "https://astrowp-demo.instawp.xyz",
  "site": {
    "url": "https://astrowp-saas-theme.vercel.app"
  },
  "post_types": ["Glossary"]
}
```

- The ```API_URL``` variable is used to **connect your WordPress site**; it should be the full URL of where it is hosted e.g. https:<span>//</span>astrowp-demo.instawp.xyz

- The ```site:url``` variable is used to **connect your published/deployed site** to canonical links, XML sitemap, etc., it should be the full URL e.g. https<span>://</span>astrowp.com

- The ```post_types``` variable **registers ACF custom post types** used on the WordPress site.

To register multiple custom post types, you simply use this syntax:

```
"post_types": ["Glossary", "Coupons"]
```

For more information on how to do WordPress custom fields and post types, see this [ACF](acf.md) tutorial.

### theme.json

This is the config file for customizing the styles.

```
{
  "features": {
    "darkMode": {
      "enabled": true,
      "default": "light"
    }
  },
  "colours": {
    "accent": "#8450b5"
  },
  "fonts": {
    "fontFamily": "Inter:wght@400;500;700",
    "fontSizes": {
      "xs": ["0.75rem", "1rem"],
      "sm": ["0.875rem", "1.25rem"],
      "base": ["1rem", "1.5rem"],
      "lg": ["1.125rem", "1.75rem"],
      "xl": ["1.25rem", "1.75rem"],
      "2xl": ["1.5rem", "2rem"],
      "3xl": ["1.875rem", "2.25rem"],
      "4xl": ["2.25rem", "2.5rem"],
      "5xl": ["3rem", "3.5rem"]
    }
  }
}
```

- Enable/disable the theme's **Dark mode**.

- Set the theme's **Accent color** in HEX.

- Customize the theme's **Font family** (if you prefer another font family like Poppins, simply change this to ```Poppins:wght@400;500;700```).

- Customize the theme's **Font sizes** with Tailwind CSS syntax.

## Customize Components

```
 ── src
    └── config
        └── pages
            └── compare-pricing.json
            └── cta.json
            └── faq.json
            └── feature-alt.json
            └── feature-grid.json
            └── features.json
            └── footer.json
            └── header.json
            └── hero.json
            └── logos.json
            └── pricing.json
            └── testimonials.json
```

Here is where you **update the content for the different sections and components on the pages**.

For example the homepage hero section, the ```hero.json`` file.

```
{
  "title": "AstroWP SaaS Starter Theme",
  "description": "Astro starter theme made for SaaS, startups and businesses. Built with Astro and Headless WordPress.",
  "firstButton": {
    "title": "Get Started Now",
    "href": "#"
  },
  "secondButton": {
    "title": "Learn More",
    "href": "#"
  }
}
```

- **cta.json** (Customize the Call-to-action component)

- **faq.json** (Customize the FAQ component)

- **features.json** (Customize the Features 3x2 grid component)

Here is how you can add in different icons in *features.json*

Head over to [Iconify](https://icon-sets.iconify.design/fluent/?category=General)

Icons are Fluent UI System Icons 24 Filled

![image](https://github.com/astrowp/docs/assets/170225022/da74d996-911a-4dd2-94d1-564962a4d443)

Copy the path

![image](https://github.com/astrowp/docs/assets/170225022/0eef8f6e-ee04-4776-84f5-6cea51bcd016)

```
"icon": "fluent:people-audience-24-regular"
```

- **feature-alt.json** (Customize the Features hero component)

- **feature-grid.json** (Customize the Features 2x3 images grid component)

- **footer.json** (Customize the sitewide Footer, including the links, components)

- **header.json** (Customize the sitewide Header, including the links, components)

- **hero.json** (Customize the homepage Hero component)

- **logos.json** (Customize the Logos component)

- **pricing.json** (Customize the Pricing, first section, component)

- **compare-pricing.json** (Customize the Pricing comparison table component)

- **testimonials.json** (Customize the Client testimonials component)

## Customize Pages

```
 ── src
    └── config
        └── pages
            └── compare-pricing.json
            └── 404.json
            └── about.json
            └── blog.json
            └── features.json
            └── home.json
            └── pricing.json
            └── privacy.md
            └── terms.md
            └── config.json
            └── theme.json
```

Here is where you **update the SEO page title, meta description, and content** for the pages. 

For example the contact page, the ```contact.json`` file.

```
{
  "meta_title": "Contact Us",
  "meta_description": "Contact Us Meta Description",
  "title": "Contact",
  "description": "Have a Question? We Want To Hear From You!",
  "details": {
    "title": "Contact Us",
    "description": "We are here to help you. Fill up this form or send an email or call us.",
    "address": "484 Fairway Drive, San Jose, CA 95113",
    "email": "hello@example.com",
    "phone": "707-413-0172"
  }
}
```

- **404.json** (the 404 error page)

- **about.json** (the about page)

- **blog.json** (the blog index page)

- **features.json** (the features page)

- **home.json** (the homepage)

- **pricing.json** (the pricing page)

- **contact.json** (the contact page)

  ### Contact Form

To make the contact page's submission form to work, you need to create your free access key from [Web3 Forms](https://web3forms.com/). Then, you will receive all form submissions in your email inbox.

Edit the file ```contactform.astro``` in ```/src/components/contactform.astro```, go to line 16 add your access key.

```
<input type="hidden" name="access_key" value="YOUR_ACCESS_KEY_HERE" />
```

I also recommend that you add spam protection to the form. [Cloudflare Turnstile](https://developers.cloudflare.com/turnstile/get-started/) is a great, free option for this.

Before the closing </form> tag, add in *<div class="cf-turnstile mt-8" data-sitekey="XXXXXXXXXXXXX"></div>*

```
  <Button type="submit" size="lg" block>Send Message</Button>
  <div id="result" class="mt-3 text-center"></div>

<div class="cf-turnstile mt-8" data-sitekey="XXXXXXXXXXXXX"></div>

</form>
```

Then, edit the file ```layout.astro``` in ```src/layouts/layout.astro```, go to line 91 add in this script tag

```
<script src="https://challenges.cloudflare.com/turnstile/v0/api.js" async defer></script>
```

Now your contact form is protected by Cloudflare Turnstile.

## Add or Edit Header and Footer Links

```
 ── src
    └── config
        └── pages
            └── footer.json
            └── header.json
```

The header and footer links are in these files:

- **footer.json** (Customize the sitewide Footer, including the links, components)

- **header.json** (Customize the sitewide Header, including the links, components)

Here, you can edit, add or delete links in the header and the footer.

```
{
  "title": "Astro WP",
  "logo": "logo.png",
  "link": {
    "title": "",
    "href": "#"
  },
  "button": {
    "title": "Get Started Now",
    "href": "#"
  },
  "menu": [
    {
      "title": "Features",
      "path": "/features/"
    },
    {
      "title": "Pricing",
      "path": "/pricing/"
    },
    {
      "title": "Blog",
      "path": "#",
      "children": [
        { "title": "Blog", "path": "/blog/" },
        { "title": "Category: Astro", "path": "/blog/category/astro/" },
        { "title": "Category: WordPress", "path": "/blog/category/wordpress/" }
      ]
    },
    {
      "title": "About Us",
      "path": "/about/"
    },
    {
      "title": "Contact Us",
      "path": "/contact/"
    }
  ]
}
```

### Remove or Re-Order Components on Pages

If you want to remove or re-order components on pages, you would have to edit the *core* page files in ```/src/pages/```

```
 ── src
    └── pages
        └── 404.astro
        └── about.astro
        └── contact.astro
        └── features.astro
        └── index.astro
        └── pricing.astro
```

For example, let's say you want to remove the FAQ component from the homepage.

Then you would have to edit the ```src/pages/index.astro``` file and delete the ```<Faq />``` component.

```
---
import Container from "@components/container.astro";
import Cta from "@components/cta.astro";
import FeatureAlt from "@components/feature-alt.astro";
import FeatureGrid from "@components/feature-grid.astro";
import Features from "@components/features.astro";
import Hero from "@components/hero.astro";
import Logos from "@components/logos.astro";
import Testimonials from "@components/testimonials.astro";
import Layout from "@layouts/Layout.astro";
import Faq from "@components/faq.astro";
import home from "@config/pages/home.json";
---

<Layout
  title={home.meta_title}
  description={home.meta_description}
  footerMargin={false}
>
  <Hero />
  <Container>
    <Logos />
    <FeatureAlt />
  </Container>
  <Testimonials />
  <Container>
    <FeatureGrid />
    <Features />
    <Faq />   <-------- REMOVE THIS
  </Container>
  <Cta />
</Layout>
```

*Tip: If a component is not inside the <Container></Container> then it's displayed as full-width on the page.*

### Publish New Pages

You can create new pages in your WordPress dashboard and link to them from the header and footer menu. For example, the theme's privacy policy and terms and conditions page are created as WordPress pages.

Simply add the path to the new page in the header and or the footer menu.

```
"policies": [
      {
        "title": "Privacy Policy",
        "path": "/privacy-policy/"
      },
      {
        "title": "Terms & Conditions",
        "path": "/terms-conditions/"
    }
    ]
```

Please note that you cannot use an identical filename (URL slug) for an already existing page on Astro. I.e. a WordPress page named /features/ won't work as there is already an existing /features/ page on Astro.

## Images & Icons

Iconify
