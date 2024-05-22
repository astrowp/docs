# AstroWP SaaS Theme

Here is evertying you need to know about configuring and customizing the SaaS theme.

## Config Files

The SaaS theme comes with two config files for configuring the theme's connection to WordPress and its styling.

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

- The ```API_URL``` variable is used to **connect your WordPress site**; it should be the full URL of where it is hosted e.g. https://astrowp-demo.instawp.xyz

- The ```site:url``` variable is used to **connect your published/deployed site** to canonical links, XML sitemap etc., it should be the full URL e.g. https://astrowp.com

- The ```post_types``` variable **registers ACF custom post types** used on the WordPress site.

To register multiple custom post types, you simply use this syntax:

```
"post_types": ["Glossary", "Coupons"]
```

For more information on WordPress custom fields and post types, see [ACF](acf.md)

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

- Enable/disable the theme's **Dark mode**

- Set the theme's **Accent color** in HEX

- Customize the theme's **Font family** (if you prefer another font family like Poppins, simply change this to ```Poppins:wght@400;500;700```)

- Customize the theme's **Font sizes** with Tailwind CSS syntax

## Components

```src/config/components```

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

- cta.json (Customize the Call-to-action component)

- faq.json (Customize the FAQ component)

- features.json (Customize the Features 3x2 grid component)

- feature-alt.json (Customize the Features hero component)

- feature-grid.json (Customize the Features 2x3 images grid component)

- footer.json (Customize the sitewide Footer, including the links, components)

- header.json (Customize the sitewide Header, including the links, components)

- hero.json (Customize the homepage Hero component)

- logos.json (Customize the Logos component)

- pricing.json (Customize the Pricing, first section, component)

- compare-pricing.json (Customize the Pricing comparison table component)

- testimonials.json (Customize the Client testimonials component)

## Pages

```src/config/pages```

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

- 404.json (the 404 error page)

- about.json (the about page)

- blog.json (the blog index page)

- features.json (the features page)

- home.json (the homepage)

- pricing.json (the pricing page)

- contact.json (the contact page)

To make the contact page's submission form to work, you need to create your free access key from [Web3 Forms](https://web3forms.com/). Then you will get all form submissions in your email inbox.

Edit the file ```contactform.astro``` in ```/src/components/contactform.astro```, go to line 16 add your access key

```
<input type="hidden" name="access_key" value="YOUR_ACCESS_KEY_HERE" />
```

### Remove or Re-Order Components on Pages

If you want to remove or re-order components on pages you would have to edit the *core* page files in ```/src/pages/```

For example, let's say you want to remove the FAQ component from the homepage

Then you would have to edit the ```src/pages/index.astro``` file and delete the ```<Faq />``` component

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

### Publish New Pages

You can create new pages in WordPress and manage them in your WordPress dashboard.

For example, the theme's privacy policy and terms and conditions page are created as WordPress pages.

Simply add the path to the new page in the header and or the footer menu.
