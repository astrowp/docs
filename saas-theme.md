# AstroWP SaaS Theme

![og-image](https://github.com/astrowp/docs/assets/170225022/1cd16edb-e7fd-42ff-ab45-f5255e17509d)

The SaaS theme consists of a combination of Astro and WordPress pages. Here is everything you need to know about configuring, customizing and styling the AstroWP SaaS theme.

## Config Files

```
 ── src
    └── config/
        └── config.json
        └── scripts.astro
        └── theme.json
```

The SaaS theme comes with three config files. The first one configures the theme's connection to WordPress, the second adds custom js/css files, and the third configures the theme's styling.

### 1. config.json

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

- The ```site:url``` variable is used to **connect your [published/deployed site](deploy.md)** to canonical links, XML sitemap, etc., it should be the full URL e.g. https<span>://</span>astrowp.com

- The ```post_types``` variable **registers ACF custom post types** used on the WordPress site.

To register multiple custom post types, you simply use this syntax:

```
"post_types": ["Glossary", "Coupons"]
```

For more information on how to do WordPress custom fields and post types, see this [ACF](acf.md) tutorial.

### 2. scripts.astro

This is the config file adding in scripts like [Google Analytics](google-analytics.md).

```
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script is:inline>
  window.dataLayer = window.dataLayer || [];
  function gtag() {
    dataLayer.push(arguments);
  }
</script>
<script is:inline>
  document.addEventListener(
    "astro:page-load",
    () => {
      gtag("js", new Date());
      gtag("config", "G-XXXXXXXXXX");
    },
    { once: false },
  );
</script>
```

The custom code you add in here gets added before the closing ```</head>``` tag.

### 3. theme.json

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
      "xl": ["1.35rem", "1.85rem"],
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

- Customize the theme's **Font sizes** using Tailwind CSS syntax.

## Customize Components

```
 ── src
    └── config
        └── components/
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

For example, the homepage hero section, the ```hero.json``` file.

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

### 1. cta.json

Customize the Call-to-action component.

<img src="https://github.com/astrowp/docs/assets/170225022/c0b6d22e-3a28-405c-84d0-be40d8ddc1b3" width="750px" />

### 2. faq.json

<img src="https://github.com/astrowp/docs/assets/170225022/58ba14ba-c2e4-467b-abff-818ba34bcdc7" width="750px" />

Customize the FAQ component.

### 3. features.json

<img src="https://github.com/astrowp/docs/assets/170225022/f6682772-5cd3-4811-b423-e0d5c506d131" width="750px" />

Customize the Features 3x2 grid component.

Here is how you can use different icons in *features.json* file.

Head over to [Iconify](https://icon-sets.iconify.design/fluent/?category=General)

Icons are Fluent UI System Icons 24 Filled. Search for an icon:

<img src="https://github.com/astrowp/docs/assets/170225022/da74d996-911a-4dd2-94d1-564962a4d443" width="750px" />

Copy the path.

![image](https://github.com/astrowp/docs/assets/170225022/0eef8f6e-ee04-4776-84f5-6cea51bcd016)

and add it in, as the "icon" variable:

```
 {
      "title": "Community Support",
      "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce tempor sed ipsum id auctor. Interdum et malesuada fames ac ante ipsum primis in faucibus.",
      "icon": "fluent:people-audience-24-regular"
    }
```

### 4. feature-alt.json

<img src="https://github.com/astrowp/docs/assets/170225022/14430ff4-566f-4f87-84c4-6be29951e439" width="750px" />

Customize the Features hero component.

### 5. feature-grid.json

<img src="https://github.com/astrowp/docs/assets/170225022/eb826eb0-7730-4c51-b548-80b357d0504c" width="750px" />

Customize the Features 2x3 images grid component.

### 6. footer.json

<img src="https://github.com/astrowp/docs/assets/170225022/3f90a350-8df6-41db-b9d0-cb71de8130f7" width="750px" />

Customize the sitewide Footer, including the links.

### 7. header.json

<img src="https://github.com/astrowp/docs/assets/170225022/37df0e0c-0af7-454f-ba4e-9a145ad13172" width="750px" />

Customize the sitewide Header, including the links.

If you want to create a dropdown menu in the header navigation, then you use this code:

```
{
      "title": "Blog",
      "path": "#",
      "children": [
        { "title": "Blog", "path": "/blog/" },
        { "title": "Category: Astro", "path": "/blog/category/astro/" },
        { "title": "Category: WordPress", "path": "/blog/category/wordpress/" }
      ]
    },
```

### 8. hero.json

<img src="https://github.com/astrowp/docs/assets/170225022/ee45bfb2-4956-4043-961a-2b849bbfdeb8" width="750px" />

Customize the homepage Hero component.

### 9. logos.json

<img src="https://github.com/astrowp/docs/assets/170225022/28a78144-7b05-472a-bd61-a5948d7988f4" width="750px" />

Customize the Logos component.

To change logos, go to ```src/components/logos.astro```.

Paste in the SVG for the new logo.

```
<!-- Paste in SVG icon from https://iconify.design/ -->
<!-- Choose a rectangular logo - toggle on dark mode and check that it displays -->
<!-- Set colors to "currentColor" -->
<!-- Replace the width with "200" and set the height to 100% -->

<svg xmlns="http://www.w3.org/2000/svg" width="200" height="100%" viewBox="0 0 512 139">
<path fill="currentColor" d="m120.218 95.07l-.072-.228l45.523-41.675v-20.08H92.634v20.08h43.624l.072.192L91.251 95.07v20.08h75.152V95.07zm91.022-63.896c-8.424 0-15.29 1.27-20.597 3.812a27.03 27.03 0 0 0-11.952 10.473a38.13 38.13 0 0 0-5.014 15.15l22.16 3.115c.802-4.722 2.406-8.068 4.81-10.04a14.682 14.682 0 0 1 8.5-2.958l1.023.012c4.498 0 7.76 1.202 9.787 3.607c2.01 2.405 3.032 5.735 3.032 10.124v2.189H201.68c-10.845 0-18.637 2.404-23.375 7.214c-4.737 4.81-7.102 11.159-7.094 19.046c0 8.08 2.365 14.093 7.094 18.037c4.73 3.944 10.678 5.903 17.844 5.88c8.89 0 15.729-3.059 20.513-9.175a34.069 34.069 0 0 0 5.928-12.637h.806l3.054 20.08h20.08v-50.85c0-10.51-2.769-18.65-8.308-24.421c-5.54-5.772-14.534-8.658-26.983-8.658m7.023 62.682c-3.187 2.658-7.36 3.98-12.554 3.98c-4.28 0-7.254-.75-8.921-2.248a7.347 7.347 0 0 1-2.514-5.712a7.505 7.505 0 0 1 2.08-5.543a7.731 7.731 0 0 1 4.93-2.083l21.74.003v1.383a12.76 12.76 0 0 1-4.761 10.22m149.689-60.77h-23.723v82.077h23.723zm140.069 0c-6.702 0-11.985 2.365-15.849 7.094c-2.772 3.4-4.88 8.421-6.323 15.067h-.698l-3.103-22.16h-20.26v82.064h23.725V73.066c0-5.306 1.242-9.374 3.727-12.204s7.07-4.245 13.754-4.245H512v-23.53zm-69.777 2.682c-5.537-3.295-12.525-4.938-20.957-4.93c-13.275 0-23.664 3.78-31.166 11.338c-7.505 7.56-11.255 17.98-11.255 31.263a49.82 49.82 0 0 0 5.11 23.195a36.83 36.83 0 0 0 14.549 15.33c6.283 3.632 13.759 5.452 22.426 5.46c7.494 0 13.754-1.155 18.78-3.463a30.2 30.2 0 0 0 11.953-9.44a41.155 41.155 0 0 0 6.492-13.418l-20.44-5.724a18.947 18.947 0 0 1-4.81 8.321c-2.31 2.309-6.177 3.463-11.603 3.463c-6.454 0-11.263-1.848-14.43-5.543c-2.297-2.67-3.74-6.481-4.376-11.423h55.972c.23-2.309.35-4.245.35-5.808v-5.11a45.576 45.576 0 0 0-4.148-19.912a31.166 31.166 0 0 0-12.447-13.6M416.602 50.4c9.62 0 15.072 4.733 16.363 14.2h-34.028a19.545 19.545 0 0 1 3.812-8.669c3.12-3.695 7.736-5.539 13.853-5.531M356.348.008a13.322 13.322 0 0 0-9.704 3.727a12.872 12.872 0 0 0-3.806 8.553l-.005 1.066a13.041 13.041 0 0 0 3.817 9.695a13.037 13.037 0 0 0 8.625 3.804l1.073.005a12.834 12.834 0 0 0 9.62-3.812a13.212 13.212 0 0 0 3.712-8.623l.004-1.069a12.746 12.746 0 0 0-.847-5.195a12.78 12.78 0 0 0-2.872-4.412A12.768 12.768 0 0 0 356.36.02zm-49.01 30.83c-8.08 0-14.574 2.537-19.479 7.61c-3.632 3.76-6.298 9.372-7.996 16.835h-.757l-3.103-22.16h-20.26v105.62h23.722V95.239h.866a44.33 44.33 0 0 0 3.03 8.417a23.897 23.897 0 0 0 9.44 10.557a27.725 27.725 0 0 0 14.02 3.38c9.932 0 17.494-3.869 22.688-11.604c5.195-7.736 7.793-18.53 7.793-32.381c0-13.38-2.514-23.852-7.538-31.42c-5.027-7.567-12.502-11.35-22.426-11.35m2.405 59.471c-2.582 3.741-6.525 5.736-11.83 5.985l-1.157.027a15.301 15.301 0 0 1-12.72-5.807c-3.072-3.856-4.602-9.135-4.594-15.836v-1.563c0-6.806 1.53-12.017 4.593-15.632c3.061-3.615 7.303-5.403 12.72-5.363c5.998 0 10.354 1.904 13.072 5.712s4.076 9.118 4.076 15.932c.017 7.046-1.362 12.561-4.137 16.545z" />
<path fill="currentColor" d="M82.077 95.071H0v20.104h82.077z" />
</svg>

<!-- END SVG icon code -->
```

### 10. pricing.json

<img src="https://github.com/astrowp/docs/assets/170225022/1fce9017-4f72-456a-9879-9554ac0f40cd" width="750px" />

Customize the Pricing component, its first section.

### 11. compare-pricing.json

<img src="https://github.com/astrowp/docs/assets/170225022/73767b4d-accf-4ec8-a090-a581e8736a6e" width="750px" />

Customize the Pricing comparison table component.

### 12. testimonials.json

<img src="https://github.com/astrowp/docs/assets/170225022/0f934ac9-a6e2-4629-9dc3-84aee142bb86" width="750px" />

Customize the Client testimonials component.

## Customize Pages

```
 ── src
    └── config
        └── pages/
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

Here is where you **update the SEO page title, meta description, noindex and content** for the pages. 

For example the contact page, the ```contact.json``` file.

```
{
  "meta_title": "Contact Us",
  "meta_description": "Contact Us Meta Description",
  "noindex": false,
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

### 1. 404.json

The 404 error page. Customize this page's SEO metadata and if it should be indexed or noindexed.

### 2. about.json

The about page. Customize this page's SEO metadata and if it should be indexed or noindexed.

### 3. blog.json

The blog index page. Customize this page's SEO metadata and if it should be indexed or noindexed.

### 4. features.json

The features page. Customize this page's SEO metadata and if it should be indexed or noindexed.

### 5. home.json

The homepage. Customize this page's SEO metadata and if it should be indexed or noindexed.

### 6. pricing.json

The pricing page. Customize this page's SEO metadata and if it should be indexed or noindexed.

### 7. contact.json

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

Then, edit the file ```/src/config/scripts.astro``` and add in this script tag:

```
<script src="https://challenges.cloudflare.com/turnstile/v0/api.js" async defer></script>
```

Now, your contact form is protected by Cloudflare Turnstile.

> If you use Netlify to deploy your site, they can do form submissions for you. [Find out more here](https://docs.astrowp.com/#/deploy?id=_7-forms).

## Header and Footer Links

```
 ── src
    └── config
        └── pages
            └── footer.json
            └── header.json
```

The header and footer links are in these files:

- **footer.json** (Customize the sitewide Footer, including the links and components)

- **header.json** (Customize the sitewide Header, including the links and components)

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

## Add, Remove or Re-Order Components on Pages

If you want to add, remove or re-order components on pages, you would have to edit the *core* page files in ```/src/pages/```

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

## Publish New Pages

You can create new pages in your WordPress dashboard and link to them from the header and footer menu. For example, the SaaS theme's privacy policy and terms and conditions page are created as WordPress pages.

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

Please note that you cannot use an identical filename (URL slug) for an already existing page on Astro. I.e. if you create a a WordPress page named /features/ it won't work as there is already an existing /features/ page on Astro.

You can, of course, create new pages in Astro, in the ```/src/pages/``` folder. Here is the structure of a simple page, that could be saved as ```test.astro```

```
---
import Layout from "@layouts/Layout.astro";
import Container from "@components/container.astro";
import Cta from "@components/cta.astro"; <--- the CTA component added in
import Testimonials from "@components/testimonials.astro"; <--- the Testimonials component added in
---

<Layout
  title="the page title for this page"
  description="the meta description for this page"
  footerMargin={false}
>
  <Container>
Here goes the content of the page, use Tailwind CSS to structure the content
  </Container>

    <Testimonials /> <--- the Testimonials component added in
    <Cta />  <--- the CTA component added in
</Layout>
```

## Images 

Images are saved in ```src/assets```.

> You **MUST** use the existing image file names for images to work. In other words, you can create your own images but you have to use the existing filenames.

### Logo

You can choose to use either a text logo or an image logo.

In ```src/config/components/header.json``` if you leave logo variable empty, then the title will be used as a text logo.

```
{
  "title": "Astro WP",
  "logo": "",
```

But if you set the variable to logo.png, the image ```logo.png``` will be used as the logo.

```
{
  "title": "Astro WP",
  "logo": "logo.png",
```

You can use a different filename for the logo (e.g., mycompany-logo.png) as long as it is uploaded to the ```src/assets``` folder.

Please note, that the favicon.svg and opengraph.jpg are saved in the ```public``` folder.

### Icons

Head over to [Iconify](https://icon-sets.iconify.design/fluent/?category=General). Icons are Fluent UI System Icons 24 Filled. Search for an icon:

<img src="https://github.com/astrowp/docs/assets/170225022/da74d996-911a-4dd2-94d1-564962a4d443" width="750px" />

Copy the path.

![image](https://github.com/astrowp/docs/assets/170225022/0eef8f6e-ee04-4776-84f5-6cea51bcd016)

and add it in, as the "icon" variable:

### Custom CSS

If you want to include your own custom CSS, you add it in ```base.css```, in the ```/src/styles/base.css``` folder.


