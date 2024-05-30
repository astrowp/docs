# SEO

## Permanent 301 Redirects

Static-generated sites created with Astro use meta-refresh for redirects. You and I both know that is **no bueno** when it comes to SEO. 

There are several ways to set up SEO-friendly redirects, and the exact method depends on where you deploy/host your AstroWP project.

### Create Redirects in Vercel

The vercel.json configuration file lets you configure and override Vercel's default behavior, including the redirect settings.

Create a new file on the root folder for the repo called ```vercel.json```

```
{
  "redirects": [
    {
        source: '/about',
        destination: '/',
        permanent: true,
    }, 
    { 
      "source": "/glossary/what-is-wp/",
      "destination": "/glossary/what-is-wordpress/", 
      "permanent": true
    },
    { 
      "source": "/view-source/",
      "destination": "https://github.com/vercel/vercel/", 
      "permanent": true
    }
  ]
}
```

- **source** is the case-sensitive path you want to redirect.

- **destination** is the URL or path you want to redirect to.

- **permanent property** is a boolean that toggles between permanent and temporary redirect (default true). When true, the status code is 308 (permanent); when false, it is 307 (temporary).

> Your AstroWP project must be [deployed to Vercel](deploy.md) for this to work.

For more information, see [Vercel's redirects documentation](https://vercel.com/docs/edge-network/redirects#static-redirects)

### Create Redirects in Netlify

The netlify.toml file is a configuration file that specifies how Netlify builds and deploys your site, including redirects.

Create a new file on the root folder for the repo called ```netlify.toml```

```
[[redirects]]
  from = "/blog/"
  to = "/posts/"
  status = 301
  force = true

[[redirects]]
  from = "/glossary/what-is-wp/"
  to = "/glossary/what-is-wordpress/"
  status = 301
  force = true

[[redirects]]
  from = "https://somenetlifysite.netlify.app"
  to = "https://mycustomdomain.com"
  status = 301
  force = true
```

- **from** is the case-sensitive path you want to redirect. Special characters must be url-encoded.

- **to** is the URL or path you want to redirect to. Special characters must be url-encoded.

- **status** is the HTTP status code you want to use in that redirect; 301 by default.

- **force** is whether to override any existing content in the path or not.

> Your AstroWP project must be [deployed to Netflify](deploy.md) for this to work.

For more information, see [Netlify's redirects documentation](https://docs.netlify.com/configure-builds/file-based-configuration/#redirects)

### Create Redirects in DigitalOcean

In DigitalOcean's App Platform, go to your project's app settings, and in **HTTP Routes Redirect**, you can create and configure redirects.

![image](https://github.com/astrowp/docs/assets/170225022/710f46d6-2f82-4e86-a859-85d2e66e6650)

- **Route Path**: The existing path to redirect traffic from.

- **Redirect URI**: The path of the destination domain to redirect traffic to.

- **Redirect Authority**: The destination domain to redirect traffic to. If left empty, the requesting authority is used.

- **Redirect Status Code**: The HTTP status code to return when redirecting the user. Valid values are 300, 301, 302, 303, 304, 307, and 308. If not specified, it defaults to 302 (temporary redirect).

- **Redirect Port**: The port of the destination URI to which traffic should be sent. If not specified, the value is omitted from the request or used to send traffic to the port of the original request.

- **Redirect Scheme**: The URI scheme the redirect uses. Must either be HTTP or HTTPS. Defaults to HTTPS if not specified.

- In the example above, *https<span>://</span>starfish-app-6r6mv.ondigitalocean.app/glossary/what-is-wp/* is permanently "301" redirected to *https<span>://</span>starfish-app-6r6mv.ondigitalocean.app/glossary/what-is-wordpress/*

> Your AstroWP project must be [deployed to DigitalOcean](deploy.md) for this to work.

For more information, see [DigitalOcean's redirects documentation](https://docs.digitalocean.com/products/app-platform/how-to/url-rewrites/)

## Robots.txt

The robots.txt file is in ```public/robots.txt```

```
User-agent: *
Allow: /

Sitemap: https://astrowp.com/sitemap-index.xml
```

## XML Sitemaps

The sitemap is automatically generated, and it is exposed at https://**.**/sitemap-index.xml.

Change the domain to the production domain in the ```Sitemap:``` directive, for the Sitemap to be auto-discovered by search engines.

```
Sitemap: https://astrowp.vercel.app/sitemap-index.xml
```
