Config files:
config.json
theme.json

## Components

```src/config/components```

Here is where you upate the content for the different sections and components on the pages.

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

- cta.json (the call-to-action component)
- faq.json (the faq component)
- features.json (the features 3x2 grid component)
- feature-alt.json (the features hero component)
- feature-grid.json (the features 2x3 images grid component)
- footer.json (the sitewide footer, including the links, component)
- header.json (the sitewide header, including the links, component)
- hero.json (the homepage hero component)
- logos.json (the logos component)
- pricing.json (the pricing, first section, component)
- compare-pricing.json (the pricing comparison table component)
- testimonials.json (the client testimonials component)

## Pages

```src/config/pages```

Here is where you update the SEO page title, meta description, and content for the pages. 

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

Edit the file contactform.astro in ```/src/components/contactform.astro```, line 16 add your access key

```
<input type="hidden" name="access_key" value="YOUR_ACCESS_KEY_HERE" />
```
