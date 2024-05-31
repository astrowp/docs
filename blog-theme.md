# AstroWP Blog Theme

The SaaS blog is almost entirely made up of WordPress posts and pages and is managed in WordPress.

Here is everything you need to know about configuring, customizing and styling the AstroWP blog/portfolio theme.

## Config Files

```
 ── src
    └── config/
        └── config.json
        └── scripts.astro
        └── theme.json
```

The Blog theme comes with three config files. The first one configures the theme's connection to WordPress, the second adds custom js/css files, and the third configures the theme's styling.

### 1. config.json

This is the config file for connecting your Headless WordPress site and for customizing the header navigation.

```
{
  "API_URL": "https://astrowp-blog-demo.instawp.xyz",
  "site": {
    "url": "https://headlesswp-blog-theme.vercel.app"
  },
  "pages": {
    "leftmenu": [
      {
        "title": "About",
        "slug": "about"
      },
      {
        "title": "Archive",
        "slug": "archive"
      }
    ],
    "rightmenu": [
      {
        "title": "Contact",
        "slug": "contact"
      },
      {
        "title": "Privacy Policy",
        "slug": "privacy-policy"
      }
    ]
  }
}
```

- The ```API_URL``` variable is used to **connect your WordPress site**; it should be the full URL of where it is hosted e.g. https:<span>//</span>astrowp-blog-demo.instawp.xyz

- The ```site:url``` variable is used to **connect your [published/deployed site](deploy.md)** to canonical links, XML sitemap, etc., it should be the full URL e.g. https<span>://</span>astrowp.com

- The ```pages``` variable sets the header navigation links, to the left and to the right of the logo.

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
      "enabled": true
    },
    "enableSidebar": true
  },
  "colours": {
    "categoryLabel": {
      "light": "#0ea5e9",
      "dark": "#a78bfa"
    },
    "postUnderline": {
      "light": {
        "from": "#0ea5e9",
        "to": "#a78bfa"
      },
      "dark": {
        "from": "#a78bfa",
        "to": "#0ea5e9"
      }
    }
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

- Enable/disable **the floating sidebar** on blog posts.

- Set the **category colour** for light mode and for dark mode.

- Set the **underline from/to colour** for light mode and for dark mode.

- Customize the theme's **Font family** (if you prefer another font family like Poppins, simply change this to ```Poppins:wght@400;500;700```).

- Customize the theme's **Font sizes** using Tailwind CSS syntax.

## Customize the Footer

```
 ── src
    └── config/
        └── components/
            └── footer.json
```

Here is where you customize the footer.

```
{
  "site_name": "AstroWP Blog",
  "legal": "All rights reserved.",
  "made_by": {
    "name": "AstroWP",
    "href": "/",
    "links": [
      {
        "name": "Privacy Policy",
        "href": "/privacy-policy/"
      },
      {
        "name": "Terms & Conditions",
        "href": "/terms-conditions/"
      }
    ]
  }
}
```

## Customize the Contact Page

```
 ── src
    └── config/
        └── pages
            └── contact.json
```

Here is where you customize the contact page.

```
{
  "meta_title": "Contact Us Page",
  "meta_description": "Contact Us Meta Description",
  "title": "Contact Us",
  "description": "Get in touch, we are a here to help.",
  "details": {
    "title": "Contact Us",
    "description": "We are here to help. Fill up the form or send email or call phone.",
    "address": "484 Fairway Drive, San Jose, CA 95113",
    "email": "hello@example.com",
    "phone": "707-413-0172"
  }
}
```

To make the contact page's submission form to work, you need to create your free access key from [Web3 Forms](https://web3forms.com/). Then, you will receive all form submissions in your email inbox.

Edit the file ```contactform.astro``` in ```/src/components/contactform.astro```, go to line 15 add your access key.

```
<input type="hidden" name="access_key" value="YOUR_ACCESS_KEY_HERE" />
```

I also recommend that you add spam protection to the form. [Cloudflare Turnstile](https://developers.cloudflare.com/turnstile/get-started/) is a great, free option for this.

In line 61, before the closing </form> tag, add in you SITE KEY *<div class="cf-turnstile mt-8" data-sitekey="TURNSTILE-SITE-KEY"></div>*

```
  <Button type="submit" size="lg" block>Send Message</Button>
  <div id="result" class="mt-3 text-center"></div>

  <!-- Add in your Cloudflare Turnstile SITE KEY --> 
  <div class="cf-turnstile mt-8" data-sitekey="TURNSTILE-SITE-KEY"></div> 
</form>
```

Then, edit the file ```/src/config/scripts.astro``` and add in this script tag:

```
<script src="https://challenges.cloudflare.com/turnstile/v0/api.js" async defer></script>
```

Now, your contact form is protected by Cloudflare Turnstile.

> If you use Netlify to deploy your site, they can do form submissions for you. [Find out more here](https://docs.astrowp.com/#/deploy?id=_7-forms).

## Customizing the Logo

src/components/header/navbar.astro

## Create Posts and Pages

This is handled in WordPress.

## Images

This is handled in WordPress.
