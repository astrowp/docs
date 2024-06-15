# AstroWP Portfolio Theme

![image](https://github.com/astrowp/docs/assets/170225022/abf30806-15af-44d5-858a-c0104ef70beb)

The Portfolio theme [(demo link here)](https://portfolio-theme-demo.astrowp.com/) is created almost entirely with WordPress posts. Posts assigned in the /posts/ category will become *posts*, and posts assigned in /projects/ will become *projects*.

Here is everything you need to know about configuring, customizing and styling this theme.

## Config Files

```
 ── src
    └── config/
        └── config.ts
        └── scripts.astro
        └── theme.json
```

The Portfolio theme comes with three config files. The first one configures the theme's connection to WordPress, the second adds custom js/css files, and the third configures the theme's styling.

### 1. config.ts

This is the config file for connecting your Headless WordPress site and for customizing the homepage and social profiles.

```
// Site and homepage settings

export const SITE: Site = {
  API_URL: "https://portfolio-demo.instawp.xyz", // Replace this with your WordPress site URL
  website: "https://portfolio-theme-demo.astrowp.com/", // Replace this with your deployed site URL
  author: "Mathias Ahlgren", // Specify the author
  desc: "Astro portfolio theme with Headless WordPress.", // homepage SEO meta description
  title: "AstroWP Portfolio Theme", // homepage SEO page title
  ogImage: "astrowp-og.jpg", // Specify opengraph image for the homepage
  lightAndDarkMode: true, // If you specify => false, darkmode will be disabled
  postPerPage: 5, // Specify how many posts to show
};

// HTML language settings

export const LOCALE = {
  lang: "en", // html lang code. Set this empty and default will be "en"
  langTag: ["en-US"], // BCP 47 Language Tags. Set this empty [] to use the environment default
} as const;

// You have to specify logo.png or logo.svg under /public/assets directory.
// Only svg and png formats are supported. (Important! logo name has to be logo.png or logo.svg)

export const LOGO_IMAGE = {
  enable: true, // If you specify => false, above SITE.title will be used as a text logo
  svg: true, // If you specify => true, svg logo (recommmended) image will be used as the site’s main logo. Set light- and darkmode in "public/assets/"
  width: 250, // 216px is default
  height: 50, // 46px is default
};

// Enable/disable social profiles => true or => false.
// Replace # with full URL

export const SOCIALS: SocialObjects = [
  {
    name: "Facebook",
    href: "#",
    linkTitle: `${SITE.title} on Facebook`,
    active: false,
  },
  {
    name: "Instagram",
    href: "#",
    linkTitle: `${SITE.title} on Instagram`,
    active: false,
  },
  {
    name: "LinkedIn",
    href: "#",
    linkTitle: `${SITE.title} on LinkedIn`,
    active: true,
  },
```

- The ```API_URL``` variable is used to connect your WordPress site; it should be the full URL of where it is hosted e.g. https://astrowp-portfolio-demo.instawp.xyz

- The ```website``` variable is used to connect your [published/deployed](deploy.md) site to canonical links, XML sitemap, etc., it should be the full URL

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

The custom code you add in here gets added before the closing </head> tag.

### 3. theme.json

This is the config file for customizing the styles.

```
{
  "light-color-scheme": {
    "--color-fill": "255, 255, 255",
    "--color-text-base": "53, 53, 56",
    "--color-accent": "17, 88, 209",
    "--color-card": "119, 196, 255",
    "--color-card-muted": "187, 199, 137",
    "--color-border": "124, 173, 255"
  },
  "dark-color-scheme": {
    "--color-fill": "0, 1, 35",
    "--color-accent": "97, 123, 255",
    "--color-text-base": "234, 237, 243",
    "--color-card": "21, 139, 229",
    "--color-card-muted": "12, 14, 79",
    "--color-border": "48, 63, 138"
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
      "5xl": ["3rem", "1"]
    }
  }
}
```

- Customize the color scheme for lightmode, and darkmode.

- Customize the theme's Font family (if you prefer another font family like Poppins, simply change this to Poppins:wght@400;500;700).

- Customize the theme's Font sizes using Tailwind CSS syntax.

## Customize the Homepage

In ```/src/config/pages/homepage.md``` you can customize the hompage content and profile image.

```
---
heading: Hi, I'm Luke
image: /assets/profile-image.png
---

I'm **Luke Donovan**, a web developer at Acme Studios, dedicated to the realms of collaboration and artificial intelligence.

My approach involves embracing intuition, conducting just enough research, and leveraging aesthetics as a catalyst for exceptional products.

> I have a profound appreciation for top-notch software, visual design, and the principles of product-led growth.
```

This supports [markdown syntax](https://www.markdownguide.org/basic-syntax/).

## Customize the Footer

In ```/src/config/components/footer.json``` you can customize the footer.

```
{
  "copyright": "Copyright ©",
  "text": "All rights reserved.",
  "link": "/privacy-policy/",
  "anchor": "Privacy Policy",
  "classes": ""
}

```

## Customize the Header

In ```/src/config/components/header.json``` you can customize the header links.

```
{
  "links": [
    {
      "name": "Projects",
      "href": "/projects/"
    },
    {
      "name": "Posts",
      "href": "/posts/"
    },
    {
      "name": "Tags",
      "href": "/tags/"
    },
    {
      "name": "About",
      "href": "/about-me/"
    }
  ]
}

```

## Customizing the Logo and Favicon

The favicon.svg file is in the ```public``` folder. Simply overwrite the  existing favicon.svg with your own favicon.

The logo is in the ```/public/assets/``` folder

```
logo.svg
logo-dark.svg
```

Again, you can just overwrite the existing light- and dark logos.

I personally use [Canva.com](https://canva.com/), it's a great design tool for creating and designing svg favicons and icons.

## Create Posts and Pages

This is entirely handled in WordPress.

Only published posts are shown. You must assign posts to either the **/posts/** category or the **/projects/** category.

## Images

This is entirely handled in WordPress. You can use the native media library or the pre-installed [Cloudinary](cloudinary.md) integration for handling media.

## Custom CSS

If you want to include your own custom CSS, you add it to base.css, in the ```/src/styles/base.css``` folder.
